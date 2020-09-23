---
title: 在 Linux 和 macOS 上安装 Drivers for PHP
description: 这些说明介绍了如何在 Linux 或 macOS 上安装 Microsoft Drivers for PHP for SQL Server。
ms.date: 04/15/2020
ms.prod: sql
ms.prod_service: connectivity
ms.custom: ''
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
manager: v-mabarw
ms.openlocfilehash: ee4938e8a0d226f668fabf3aaf4db1359ab6bf61
ms.sourcegitcommit: 33e774fbf48a432485c601541840905c21f613a0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/25/2020
ms.locfileid: "88807020"
---
# <a name="linux-and-macos-installation-tutorial-for-the-microsoft-drivers-for-php-for-sql-server"></a>Microsoft Drivers for PHP for SQL Server 的 Linux 和 macOS 安装教程
以下说明假定环境是干净的，展示了如何在 Ubuntu 16.04、18.04 和 20.04、RedHat 7 和 8、Debian 8、9 和 10、Suse 12 和 15、Alpine 3.11 以及 macOS 10.13、10.14 和 10.15 上安装 PHP 7.x、Microsoft ODBC 驱动程序、Apache Web 服务器和 Microsoft Drivers for PHP for SQL Server。 这些说明建议使用 PECL 安装驱动程序，但也可以从 [Microsoft Drivers for PHP for SQL Server](https://github.com/Microsoft/msphpsql/releases) GitHub 项目页下载预生成的二进制文件，并按照[下载 Microsoft Drivers for PHP for SQL Server](../../connect/php/loading-the-php-sql-driver.md) 中的说明安装它们。 有关扩展加载以及为什么不将扩展添加到 php.ini 的说明，请参阅[加载驱动程序](../../connect/php/loading-the-php-sql-driver.md#loading-the-driver-at-php-startup)部分。

这些说明默认使用 `pecl install` 安装 PHP 7.4。 你可能需要先运行 `pecl channel-update pecl.php.net`。 注意，一些受支持的 Linux 发行版默认为 PHP 7.1 或更早版本，而 SQL Server 的 PHP 驱动程序的最新版本不支持这些版本，请参阅每一节开头的说明，以安装 PHP 7.2 或 7.3。

还包括有关在 Ubuntu 上安装 PHP FastCGI 进程管理器 (PHP-FPM) 的说明。 如果使用的是 nginx Web 服务器而不是 Apache，则需要此服务。

## <a name="contents-of-this-page"></a>此页的内容

- [在 Ubuntu 16.04、18.04 和 20.04 上安装驱动程序](#installing-the-drivers-on-ubuntu-1604-1804-and-2004)
- [在 Ubuntu 上安装带有 PHP-FPM 的驱动程序](#installing-the-drivers-with-php-fpm-on-ubuntu)
- [在 Red Hat 7 和 8 上安装驱动程序](#installing-the-drivers-on-red-hat-7-and-8)
- [在 Debian 8、9 和 10 上安装驱动程序](#installing-the-drivers-on-debian-8-9-and-10)
- [在 Suse 12 和 15 上安装驱动程序](#installing-the-drivers-on-suse-12-and-15)
- [在 Alpine 3.11 上安装驱动程序](#installing-the-drivers-on-alpine-311)
- [在 macOS High Sierra、Mojave 和 Catalina 上安装驱动程序](#installing-the-drivers-on-macos-high-sierra-mojave-and-catalina)

## <a name="installing-the-drivers-on-ubuntu-1604-1804-and-2004"></a>在 Ubuntu 16.04、18.04 和 20.04 上安装驱动程序

> [!NOTE]
> 若要安装 PHP 7.2 或 7.3，请使用以下命令将 7.4 替换为 7.2 或 7.3。

### <a name="step-1-install-php"></a>步骤 1。 安装 PHP
```bash
sudo su
add-apt-repository ppa:ondrej/php -y
apt-get update
apt-get install php7.4 php7.4-dev php7.4-xml -y --allow-unauthenticated
```
### <a name="step-2-install-prerequisites"></a>步骤 2. 安装先决条件
按照[“Linux 安装”一文](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)中的说明安装适用于 Ubuntu 的 ODBC 驱动程序。

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>步骤 3. 安装适用于 Microsoft SQL Server 的 PHP 驱动程序
```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
sudo su
printf "; priority=20\nextension=sqlsrv.so\n" > /etc/php/7.4/mods-available/sqlsrv.ini
printf "; priority=30\nextension=pdo_sqlsrv.so\n" > /etc/php/7.4/mods-available/pdo_sqlsrv.ini
exit
sudo phpenmod -v 7.4 sqlsrv pdo_sqlsrv
```

如果系统中只有一个 PHP 版本，则可以将最后一个步骤简化为 `phpenmod sqlsrv pdo_sqlsrv`。

### <a name="step-4-install-apache-and-configure-driver-loading"></a>步骤 4. 安装 Apache 并配置驱动程序加载
```
sudo su
apt-get install libapache2-mod-php7.4 apache2
a2dismod mpm_event
a2enmod mpm_prefork
a2enmod php7.4
exit
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>步骤 5。 重启 Apache 并测试示例脚本
```
sudo service apache2 restart
```
若要测试安装，请参阅本文档末尾的[测试安装](#testing-your-installation)。

## <a name="installing-the-drivers-with-php-fpm-on-ubuntu"></a>在 Ubuntu 上安装带有 PHP-FPM 的驱动程序

> [!NOTE]
> 若要安装 PHP 7.2 或 7.3，请使用以下命令将 7.4 替换为 7.2 或 7.3。

### <a name="step-1-install-php"></a>步骤 1。 安装 PHP
```bash
sudo su
add-apt-repository ppa:ondrej/php -y
apt-get update
apt-get install php7.4 php7.4-dev php7.4-xml php7.4-fpm -y --allow-unauthenticated
```
通过运行验证 PHP-FPM 服务的状态
```
systemctl status php7.4-fpm
```
### <a name="step-2-install-prerequisites"></a>步骤 2. 安装先决条件
按照[“Linux 安装”一文](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)中的说明安装适用于 Ubuntu 的 ODBC 驱动程序。

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>步骤 3. 安装适用于 Microsoft SQL Server 的 PHP 驱动程序
```
sudo pecl config-set php_ini /etc/php/7.4/fpm/php.ini
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
sudo su
printf "; priority=20\nextension=sqlsrv.so\n" > /etc/php/7.4/mods-available/sqlsrv.ini
printf "; priority=30\nextension=pdo_sqlsrv.so\n" > /etc/php/7.4/mods-available/pdo_sqlsrv.ini
exit
sudo phpenmod -v 7.4 sqlsrv pdo_sqlsrv
```
如果系统中只有一个 PHP 版本，则可以将最后一个步骤简化为 `phpenmod sqlsrv pdo_sqlsrv`。

验证 `sqlsrv.ini` 和 `pdo_sqlsrv.ini` 是否位于 `/etc/php/7.4/fpm/conf.d/`：
```
ls /etc/php/7.4/fpm/conf.d/*sqlsrv.ini
```
重新启动 PHP-FPM 服务：
```
sudo systemctl restart php7.4-fpm
```

### <a name="step-4-install-and-configure-nginx"></a>步骤 4. 安装并配置 nginx
```
sudo apt-get update
sudo apt-get install nginx
sudo systemctl status nginx
```
若要配置 nginx，必须编辑 `/etc/nginx/sites-available/default` 文件。 将 `index.php` 添加到指示 `# Add index.php to the list if you are using PHP` 的部分下的列表中：
```
# Add index.php to the list if you are using PHP
index index.html index.htm index.nginx-debian.html index.php;
```
接下来，修改以下 `# pass PHP scripts to FastCGI server` 部分，如下所示：
```
# pass PHP scripts to FastCGI server
#
location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/run/php/php7.4-fpm.sock;
}
```
### <a name="step-5-restart-nginx-and-test-the-sample-script"></a>步骤 5。 重启 nginx 并测试示例脚本
```
sudo systemctl restart nginx.service
```
若要测试安装，请参阅本文档末尾的[测试安装](#testing-your-installation)。

## <a name="installing-the-drivers-on-red-hat-7-and-8"></a>在 Red Hat 7 和 8 上安装驱动程序

### <a name="step-1-install-php"></a>步骤 1。 安装 PHP

若要在 Red Hat 7 上安装 PHP，请运行以下命令：
> [!NOTE]
> 若要安装 PHP 7.2 或 7.3，请在以下命令中分别用 remi- php72 或 remi-php73 替换 remi-php74。
```
sudo su
yum install https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
yum install https://rpms.remirepo.net/enterprise/remi-release-7.rpm
subscription-manager repos --enable=rhel-7-server-optional-rpms
yum install yum-utils
yum-config-manager --enable remi-php74
yum update
yum install php php-pdo php-xml php-pear php-devel re2c gcc-c++ gcc
```

若要在 Red Hat 8 上安装 PHP，请运行以下命令：
> [!NOTE]
> 若要安装 PHP 7.2 或7.3，请在以下命令中分别用 remi-7.2 或 remi-7.3 替换 remi-7.4。
```
sudo su
dnf install https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm
dnf install https://rpms.remirepo.net/enterprise/remi-release-8.rpm
dnf install yum-utils
dnf module reset php
dnf module install php:remi-7.4
subscription-manager repos --enable codeready-builder-for-rhel-8-x86_64-rpms
dnf update
dnf install php-pdo php-pear php-devel
```

### <a name="step-2-install-prerequisites"></a>步骤 2. 安装先决条件
按照[“Linux 安装”一文](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)中的说明安装适用于 Red Hat 7 或 8 的 ODBC 驱动程序。

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>步骤 3. 安装适用于 Microsoft SQL Server 的 PHP 驱动程序
```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
sudo su
echo extension=pdo_sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/30-pdo_sqlsrv.ini
echo extension=sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/20-sqlsrv.ini
exit
```

也可以从 Remi 存储库进行安装：
```
sudo yum install php-sqlsrv
```
### <a name="step-4-install-apache"></a>步骤 4. 安装 Apache
```
sudo yum install httpd
```
默认安装 SELinux，并在强制模式下运行。 若要允许 Apache SELinux 通过连接到数据库，请运行以下命令：
```
sudo setsebool -P httpd_can_network_connect_db 1
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>步骤 5。 重启 Apache 并测试示例脚本
```
sudo apachectl restart
```
若要测试安装，请参阅本文档末尾的[测试安装](#testing-your-installation)。

## <a name="installing-the-drivers-on-debian-8-9-and-10"></a>在 Debian 8、9 和 10 上安装驱动程序

> [!NOTE]
> 若要安装 PHP 7.2 或 7.3，请使用以下命令将 7.4 替换为 7.2 或 7.3。

### <a name="step-1-install-php"></a>步骤 1。 安装 PHP
```
sudo su
apt-get install curl apt-transport-https
wget -O /etc/apt/trusted.gpg.d/php.gpg https://packages.sury.org/php/apt.gpg
echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" > /etc/apt/sources.list.d/php.list
apt-get update
apt-get install -y php7.4 php7.4-dev php7.4-xml php7.4-intl
```
### <a name="step-2-install-prerequisites"></a>步骤 2. 安装先决条件
按照[“Linux 安装”一文](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)中的说明安装适用于 Debian 的 ODBC 驱动程序。 

可能还需要生成正确的区域设置，以使 PHP 输出在浏览器中正确显示。 例如，对于 en_US UTF-8 区域设置，运行以下命令：
```
sudo su
sed -i 's/# en_US.UTF-8 UTF-8/en_US.UTF-8 UTF-8/g' /etc/locale.gen
locale-gen
```
可能需要将 `/usr/sbin` 添加到 `$PATH` 中，因为 `locale-gen` 可执行文件位于该位置。

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>步骤 3. 安装适用于 Microsoft SQL Server 的 PHP 驱动程序
```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
sudo su
printf "; priority=20\nextension=sqlsrv.so\n" > /etc/php/7.4/mods-available/sqlsrv.ini
printf "; priority=30\nextension=pdo_sqlsrv.so\n" > /etc/php/7.4/mods-available/pdo_sqlsrv.ini
exit
sudo phpenmod -v 7.4 sqlsrv pdo_sqlsrv
```

如果系统中只有一个 PHP 版本，则可以将最后一个步骤简化为 `phpenmod sqlsrv pdo_sqlsrv`。 与 `locale-gen` 一样，`phpenmod` 位于 `/usr/sbin` 中，因此可能需要将此目录添加到 `$PATH`。

### <a name="step-4-install-apache-and-configure-driver-loading"></a>步骤 4. 安装 Apache 并配置驱动程序加载
```
sudo su
apt-get install libapache2-mod-php7.4 apache2
a2dismod mpm_event
a2enmod mpm_prefork
a2enmod php7.4
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>步骤 5。 重启 Apache 并测试示例脚本
```
sudo service apache2 restart
```
若要测试安装，请参阅本文档末尾的[测试安装](#testing-your-installation)。

## <a name="installing-the-drivers-on-suse-12-and-15"></a>在 Suse 12 和 15 上安装驱动程序

> [!NOTE]
> 在下面的说明中，将 `<SuseVersion>` 替换为 Suse 版本，如果使用的是 Suse Enterprise Linux 15，它将是 SLE_15 或 SLE_15_SP1。 对于 Suse 12，请使用 SLE_12_SP4（或更高版本，如果适用）。 并不是所有版本的 PHP 都适用于所有版本的 Suse Linux，请参阅 `http://download.opensuse.org/repositories/devel:/languages:/php` 以查看哪些版本的 Suse 具有默认版本的 PHP 可用，或者参阅 `http://download.opensuse.org/repositories/devel:/languages:/php:/` 查看哪些其他版本的 PHP 可用于哪些版本的 Suse。

> [!NOTE]
> PHP 7.4 的包不可用于 Suse 12。 若要安装 PHP 7.2，用以下 URL 替换下面的存储库 URL：`https://download.opensuse.org/repositories/devel:/languages:/php:/php72/<SuseVersion>/devel:languages:php:php72.repo`。
> 若要安装 PHP 7.3，用以下 URL 替换下面的存储库 URL：`https://download.opensuse.org/repositories/devel:/languages:/php:/php73/<SuseVersion>/devel:languages:php:php73.repo`。

### <a name="step-1-install-php"></a>步骤 1。 安装 PHP
```
sudo su
zypper -n ar -f https://download.opensuse.org/repositories/devel:languages:php/<SuseVersion>/devel:languages:php.repo
zypper --gpg-auto-import-keys refresh
zypper -n install php7 php7-devel php7-openssl
```
### <a name="step-2-install-prerequisites"></a>步骤 2. 安装先决条件
按照[“Linux 安装”一文](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)中的说明安装适用于 Suse 的 ODBC 驱动程序。

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>步骤 3. 安装适用于 Microsoft SQL Server 的 PHP 驱动程序
> [!NOTE]
> 如果收到错误消息 `Connection to 'pecl.php.net:443' failed: Unable to find the socket transport "ssl"`，请编辑 /usr/bin/pecl 中的 pecl 脚本并删除最后一行的 `-n` 开关。 此开关可防止 PECL 在调用 PHP 时加载 ini 文件，从而防止加载 OpenSSL 扩展。

```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
sudo su
echo extension=pdo_sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/pdo_sqlsrv.ini
echo extension=sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/sqlsrv.ini
exit
```
### <a name="step-4-install-apache-and-configure-driver-loading"></a>步骤 4. 安装 Apache 并配置驱动程序加载
```
sudo su
zypper install apache2 apache2-mod_php7
a2enmod php7
echo "extension=sqlsrv.so" >> /etc/php7/apache2/php.ini
echo "extension=pdo_sqlsrv.so" >> /etc/php7/apache2/php.ini
exit
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>步骤 5。 重启 Apache 并测试示例脚本
```
sudo systemctl restart apache2
```
若要测试安装，请参阅本文档末尾的[测试安装](#testing-your-installation)。

## <a name="installing-the-drivers-on-alpine-311"></a>在 Alpine 3.11 上安装驱动程序

> [!NOTE]
> PHP 的默认版本为 7.3。 可以从 Alpine 3.11 的其他存储库中获取 PHP 的备用版本。 可以改为从源编译 PHP。

### <a name="step-1-install-php"></a>步骤 1。 安装 PHP
可以在 `edge/community` 存储库中找到用于 Alpine 的 PHP 包。 请查看 Wiki 页上的[启用社区存储库](https://wiki.alpinelinux.org/wiki/Enable_Community_Repository)。 将以下行添加到 `/etc/apt/repositories`，并将 `<mirror>` 替换为 Alpine 存储库镜像的 URL：
```
http://<mirror>/alpine/edge/community
```
然后运行：
```
sudo su
apk update
apk add php7 php7-dev php7-pear php7-pdo php7-openssl autoconf make g++
```
### <a name="step-2-install-prerequisites"></a>步骤 2. 安装先决条件
按照[“Linux 安装”一文](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)中的说明安装适用于 Alpine 的 ODBC 驱动程序。 

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>步骤 3. 安装适用于 Microsoft SQL Server 的 PHP 驱动程序
```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
sudo su
echo extension=pdo_sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/10_pdo_sqlsrv.ini
echo extension=sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/00_sqlsrv.ini
```

### <a name="step-4-install-apache-and-configure-driver-loading"></a>步骤 4. 安装 Apache 并配置驱动程序加载
```
sudo apk add php7-apache2 apache2
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>步骤 5。 重启 Apache 并测试示例脚本
```
sudo rc-service apache2 restart
```
若要测试安装，请参阅本文档末尾的[测试安装](#testing-your-installation)。


## <a name="installing-the-drivers-on-macos-high-sierra-mojave-and-catalina"></a>在 macOS High Sierra、Mojave 和 Catalina 上安装驱动程序

如果还没有安装 brew，请按照以下步骤安装：
```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

> [!NOTE]
> 若要安装 PHP 7.2 或 7.3，请在以下命令中分别用 php@7.2 或 php@7.3 替换 php@7.4。

### <a name="step-1-install-php"></a>步骤 1。 安装 PHP

```
brew tap
brew tap homebrew/core
brew install php@7.4
```
PHP 现应在路径中 - 运行 `php -v` 以验证正在运行正确版本的 PHP。 如果 PHP 不在路径中或版本不正确，则运行以下命令：
```
brew link --force --overwrite php@7.4
```

### <a name="step-2-install-prerequisites"></a>步骤 2. 安装先决条件
按照[“Linux 安装”一文](../../connect/odbc/linux-mac/install-microsoft-odbc-driver-sql-server-macos.md)中的说明安装适用于 macOS 的 ODBC 驱动程序。 

此外，可能需要安装 GNU make 工具：
```
brew install autoconf automake libtool
```

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>步骤 3. 安装适用于 Microsoft SQL Server 的 PHP 驱动程序
```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
```
### <a name="step-4-install-apache-and-configure-driver-loading"></a>步骤 4. 安装 Apache 并配置驱动程序加载
```
brew install apache2
```
若要查找用于 Apache 安装的 Apache 配置文件 `httpd.conf`，请运行 
```
/usr/local/bin/apachectl -V | grep SERVER_CONFIG_FILE
``` 
以下命令将所需的配置追加到 `httpd.conf`。 请确保用上一个命令返回的路径替换 `/usr/local/etc/httpd/httpd.conf`：
```
echo "LoadModule php7_module /usr/local/opt/php@7.4/lib/httpd/modules/libphp7.so" >> /usr/local/etc/httpd/httpd.conf
(echo "<FilesMatch .php$>"; echo "SetHandler application/x-httpd-php"; echo "</FilesMatch>";) >> /usr/local/etc/httpd/httpd.conf
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>步骤 5。 重启 Apache 并测试示例脚本
```
sudo apachectl restart
```
若要测试安装，请参阅本文档末尾的[测试安装](#testing-your-installation)。

## <a name="testing-your-installation"></a>测试安装

若要测试此示例脚本，请在系统的文档根目录中创建名为“testsql.php”的文件。 这在 Ubuntu、Debian 和 Redhat 上为 `/var/www/html/`，在 SUSE 上为 `/srv/www/htdocs`，在 macOS 上为 `/var/www/localhost/htdocs`，在 macOS 上为 `/usr/local/var/www`。 将以下脚本复制到其中，酌情替换服务器、数据库、用户名和密码。
```
<?php
$serverName = "yourServername";
$connectionOptions = array(
    "database" => "yourDatabase",
    "uid" => "yourUsername",
    "pwd" => "yourPassword"
);

// Establishes the connection
$conn = sqlsrv_connect($serverName, $connectionOptions);
if ($conn === false) {
    die(formatErrors(sqlsrv_errors()));
}

// Select Query
$tsql = "SELECT @@Version AS SQL_VERSION";

// Executes the query
$stmt = sqlsrv_query($conn, $tsql);

// Error handling
if ($stmt === false) {
    die(formatErrors(sqlsrv_errors()));
}
?>

<h1> Results : </h1>

<?php
while ($row = sqlsrv_fetch_array($stmt, SQLSRV_FETCH_ASSOC)) {
    echo $row['SQL_VERSION'] . PHP_EOL;
}

sqlsrv_free_stmt($stmt);
sqlsrv_close($conn);

function formatErrors($errors)
{
    // Display errors
    echo "Error information: <br/>";
    foreach ($errors as $error) {
        echo "SQLSTATE: ". $error['SQLSTATE'] . "<br/>";
        echo "Code: ". $error['code'] . "<br/>";
        echo "Message: ". $error['message'] . "<br/>";
    }
}
?>
```
将浏览器指向 https://localhost/testsql.php （macOS 上的 https://localhost:8080/testsql.php ）。 现在应能够连接到 SQL Server/Azure SQL 数据库。

## <a name="see-also"></a>另请参阅  
[开始使用 Microsoft Drivers for PHP for SQL Server](../../connect/php/getting-started-with-the-php-sql-driver.md)

[加载 Microsoft Drivers for PHP for SQL Server](../../connect/php/loading-the-php-sql-driver.md)

[Microsoft Drivers for PHP for SQL Server 系统要求](../../connect/php/system-requirements-for-the-php-sql-driver.md)
