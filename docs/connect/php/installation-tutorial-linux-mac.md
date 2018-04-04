---
title: Linux et macOS didacticiel d’Installation pour le Microsoft Drivers for PHP for SQL Server | Documents Microsoft
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: php
ms.suite: sql
ms.custom: ''
ms.technology:
- drivers
ms.topic: article
author: ulvii
ms.author: v-ulibra
manager: v-mabarw
ms.workload: Inactive
ms.openlocfilehash: f7c9542294be520b6861262e814b9fda31b06d5d
ms.sourcegitcommit: 2e130e9f3ce8a7ffe373d7fba8b09e937c216386
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="linux-and-macos-installation-tutorial-for-the-microsoft-drivers-for-php-for-sql-server"></a>Linux et macOS didacticiel d’Installation pour le Microsoft Drivers for PHP for SQL Server
Les instructions suivantes supposent un environnement propre et indiquent comment installer PHP 7.x, le pilote ODBC de Microsoft, Apache et le Microsoft Drivers for PHP pour SQL Server sur Ubuntu RedHat 16.04 et 17.10, 7, Debian 8 et 9, Suse 12 et macOS X 10.11 et 10.12. Ces instructions informer de l’installation des pilotes à l’aide de PECL, mais vous pouvez également télécharger les binaires prédéfinis à partir de la [Microsoft Drivers for PHP for SQL Server](https://github.com/Microsoft/msphpsql/releases) Github page de projet et les installer en suivant les instructions de [ Chargement des pilotes Microsoft SQL Server pour PHP](../../connect/php/loading-the-php-sql-driver.md). Pour obtenir une explication de chargement de l’extension et pourquoi nous n’ajoutez pas les extensions à php.ini, consultez la section sur [chargement des pilotes](../../connect/php/loading-the-php-sql-driver.md##loading-the-driver-at-php-startup).

Ces installation instruction 7.2 de PHP par défaut, consultez les notes au début de chaque section pour installer PHP 7.0 ou 7.1.

## <a name="contents-of-this-page"></a>Contenu de cette page :

- [Installation des pilotes sur Ubuntu 16.04 et 17.10](#installing-the-drivers-on-ubuntu-1604-and-1710)
- [Installation des pilotes sur Red Hat 7](#installing-the-drivers-on-red-hat-7)
- [Installation des pilotes sur Debian 8 et 9](#installing-the-drivers-on-debian-8-and-9)
- [Installation des pilotes sur Suse 12](#installing-the-drivers-on-suse-12)
- [Installation des pilotes sur macOS El Capitan et Sierra](#installing-the-drivers-on-macos-el-capitan-and-sierra)

## <a name="installing-the-drivers-on-ubuntu-1604-and-1710"></a>Installation des pilotes sur Ubuntu 16.04 et 17.10

    > [!NOTE]
    > To install PHP 7.0 or 7.1, replace 7.2 with 7.0 or 7.1 in the following commands.

### <a name="step-1-install-php"></a>Étape 1. Installer PHP
```
sudo su
add-apt-repository ppa:ondrej/php -y
apt-get update
apt-get install php7.2 php7.2-dev php7.2-xml -y --allow-unauthenticated
```
### <a name="step-2-install-prerequisites"></a>Étape 2. Installez les composants requis
Installer le pilote ODBC pour Ubuntu en suivant les instructions de la [page d’installation Linux et macOS](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md).

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Étape 3. Installer les pilotes PHP pour Microsoft SQL Server
```
sudo su
echo extension=pdo_sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/30-pdo_sqlsrv.ini
echo extension=sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/20-sqlsrv.ini
exit
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
```
### <a name="step-4-install-apache-and-configure-driver-loading"></a>Étape 4. Installer Apache et configurer le chargement du pilote
```
sudo su
apt-get install libapache2-mod-php7.2 apache2
a2dismod mpm_event
a2enmod mpm_prefork
a2enmod php7.2
echo "extension=sqlsrv.so" >> /etc/php/7.2/apache2/php.ini
echo "extension=pdo_sqlsrv.so" >> /etc/php/7.2/apache2/php.ini
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>Étape 5. Redémarrez Apache et tester l’exemple de script
```
sudo service apache2 restart
```
Pour tester votre installation, consultez [tester votre installation](#testing-your-installation) à la fin de ce document.

## <a name="installing-the-drivers-on-red-hat-7"></a>Installation des pilotes sur Red Hat 7

    > [!NOTE]
    > To install PHP 7.0 or 7.1, replace remi-php72 with remi-php70 or remi-php71 respectively in the following commands.

### <a name="step-1-install-php"></a>Étape 1. Installer PHP

```
sudo su
wget https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
wget http://rpms.remirepo.net/enterprise/remi-release-7.rpm
rpm -Uvh remi-release-7.rpm epel-release-latest-7.noarch.rpm
subscription-manager repos --enable=rhel-7-server-optional-rpms
yum-config-manager --enable remi-php72
yum update
yum install php php-pdo php-xml php-pear php-devel re2c gcc-c++ gcc
```
### <a name="step-2-install-prerequisites"></a>Étape 2. Installez les composants requis
Installer le pilote ODBC pour Red Hat 7 en suivant les instructions de la [page d’installation Linux et macOS](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md).

La compilation les pilotes PHP avec PECL avec PHP 7.2 nécessite un GCC plus récente que la valeur par défaut :
```
sudo yum-config-manager --enable rhel-server-rhscl-7-rpms
sudo yum install devtoolset-7
scl enable devtoolset-7 bash
```
### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Étape 3. Installer les pilotes PHP pour Microsoft SQL Server
```
sudo su
echo extension=pdo_sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/30-pdo_sqlsrv.ini
echo extension=sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/20-sqlsrv.ini
exit
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
```
Un problème dans PECL peut empêcher l’installation correcte de la dernière version des pilotes même si vous avez mis à niveau GCC. Pour installer, de télécharger les packages et de compiler manuellement :
```
pecl download sqlsrv
tar xvzf sqlsrv-5.2.0.tgz
cd sqlsrv-5.2.0/
phpize
./configure --with-php-config=/usr/bin/php-config
make
sudo make install
```
Vous pouvez également télécharger les binaires prédéfinis à partir de la [page de projet Github](https://github.com/Microsoft/msphpsql/releases), ou installer à partir du référentiel ance :
```
sudo yum install php-sqlsrv php-pdo_sqlsrv
```
### <a name="step-4-install-apache"></a>Étape 4. Installer Apache
```
sudo yum install httpd
```
SELinux est installé par défaut et s’exécute en mode d’application. Pour autoriser pour se connecter aux bases de données via SELinux Apache, exécutez la commande suivante :
```
sudo setsebool -P httpd_can_network_connect_db 1
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>Étape 5. Redémarrez Apache et tester l’exemple de script
```
sudo apachectl restart
```
Pour tester votre installation, consultez [tester votre installation](#testing-your-installation) à la fin de ce document.

## <a name="installing-the-drivers-on-debian-8-and-9"></a>Installation des pilotes sur Debian 8 et 9

    > [!NOTE]
    > To install PHP 7.0 or 7.1, replace 7.2 in the following commands with 7.0 or 7.1.

### <a name="step-1-install-php"></a>Étape 1. Installer PHP
```
sudo su
apt-get install curl apt-transport-https
wget -O /etc/apt/trusted.gpg.d/php.gpg https://packages.sury.org/php/apt.gpg
echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" > /etc/apt/sources.list.d/php.list
apt-get update
apt-get install –y php7.2 php7.2-dev php7.2-xml
```
### <a name="step-2-install-prerequisites"></a>Étape 2. Installez les composants requis
Installer le pilote ODBC pour Debian en suivant les instructions de la [page d’installation Linux et macOS](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md). 

Vous devez également générer les paramètres régionaux corrects pour obtenir une sortie PHP s’affichent correctement dans un navigateur. Par exemple, pour les paramètres régionaux de UTF-8 en_US, exécutez les commandes suivantes :
```
sudo su
sed -i 's/# en_US.UTF-8 UTF-8/en_US.UTF-8 UTF-8/g' /etc/locale.gen
locale-gen
```

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Étape 3. Installer les pilotes PHP pour Microsoft SQL Server
```
sudo su
echo extension=pdo_sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/30-pdo_sqlsrv.ini
echo extension=sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/20-sqlsrv.ini
exit
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
```
### <a name="step-4-install-apache-and-configure-driver-loading"></a>Étape 4. Installer Apache et configurer le chargement du pilote
```
sudo su
apt-get install libapache2-mod-php7.2 apache2
a2dismod mpm_event
a2enmod mpm_prefork
a2enmod php7.2
echo "extension=sqlsrv.so" >> /etc/php/7.2/apache2/php.ini
echo "extension=pdo_sqlsrv.so" >> /etc/php/7.2/apache2/php.ini
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>Étape 5. Redémarrez Apache et tester l’exemple de script
```
sudo service apache2 restart
```
Pour tester votre installation, consultez [tester votre installation](#testing-your-installation) à la fin de ce document.

## <a name="installing-the-drivers-on-suse-12"></a>Installation des pilotes sur Suse 12

    > [!NOTE]
    > To install PHP 7.0, skip the command below adding the repository - 7.0 is the default PHP on suse 12.
    > To install PHP 7.1, replace the repository URL below with the following URL:
      `http://download.opensuse.org/repositories/devel:/languages:/php:/php71/SLE_12/devel:languages:php:php71.repo`

### <a name="step-1-install-php"></a>Étape 1. Installer PHP
```
sudo su
zypper -n ar -f http://download.opensuse.org/repositories/devel:languages:php/SLE_12/devel:languages:php.repo
zypper --gpg-auto-import-keys refresh
zypper -n install php7 php7-pear php7-devel
```
### <a name="step-2-install-prerequisites"></a>Étape 2. Installez les composants requis
Installer le pilote ODBC pour Suse 12 en suivant les instructions de la [page d’installation Linux et macOS](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md).

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Étape 3. Installer les pilotes PHP pour Microsoft SQL Server
```
sudo su
echo extension=pdo_sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/pdo_sqlsrv.ini
echo extension=sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/sqlsrv.ini
exit
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
```
### <a name="step-4-install-apache-and-configure-driver-loading"></a>Étape 4. Installer Apache et configurer le chargement du pilote
```
sudo su
zypper install apache2 apache2-mod_php7
a2enmod php7
echo "extension=sqlsrv.so" >> /etc/php7/apache2/php.ini
echo "extension=pdo_sqlsrv.so" >> /etc/php7/apache2/php.ini
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>Étape 5. Redémarrez Apache et tester l’exemple de script
```
sudo systemctl restart apache2
```
Pour tester votre installation, consultez [tester votre installation](#testing-your-installation) à la fin de ce document.

## <a name="installing-the-drivers-on-macos-el-capitan-and-sierra"></a>Installation des pilotes sur macOS El Capitan et Sierra

Si vous ne l’avez pas encore, installez brew comme suit :
```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

    > [!NOTE]
    > To install PHP 7.0 or 7.1, replace php72 with php70 or php71 respectively in the following commands.

### <a name="step-1-install-php"></a>Étape 1. Installer PHP

```
brew tap
brew tap homebrew/dupes
brew tap homebrew/versions
brew tap homebrew/homebrew-php
brew install php72 --with-pear --with-httpd24 --with-cgi
echo 'export PATH="/usr/local/sbin:$PATH"' >> ~/.bash_profile
echo 'export PATH="/usr/local/bin:$PATH"' >> ~/.bash_profile
source ~/.bash_profile
```
### <a name="step-2-install-prerequisites"></a>Étape 2. Installez les composants requis
Installer le pilote ODBC pour macOS en suivant les instructions de la [page d’installation Linux et macOS](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md). 

En outre, vous devrez peut-être installer les outils de création de GNU :
```
brew install autoconf automake libtool
```

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Étape 3. Installer les pilotes PHP pour Microsoft SQL Server
```
chmod -R ug+w /usr/local/opt/php72/lib/php
pear config-set php_ini /usr/local/etc/php/7.2/php.ini system
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
```
### <a name="step-4-install-apache-and-configure-driver-loading"></a>Étape 4. Installer Apache et configurer le chargement du pilote
```
(echo "<FilesMatch .php$>"; echo "SetHandler application/x-httpd-php"; echo "</FilesMatch>";) >> /usr/local/etc/httpd/httpd.conf
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>Étape 5. Redémarrez Apache et tester l’exemple de script
```
sudo apachectl restart
```
Pour tester votre installation, consultez [tester votre installation](#testing-your-installation) à la fin de ce document.

## <a name="testing-your-installation"></a>Test de votre Installation

Pour tester cet exemple de script, créez un fichier appelé testsql.php dans la racine du document de votre système. Il s’agit de `/var/www/html/` sur Red Hat, Debian et Ubuntu `/srv/www/htdocs` sur SUSE, ou `/usr/local/var/www` sur macOS. Copiez le script suivant, en remplaçant le serveur de base de données, nom d’utilisateur et mot de passe comme il convient.
```
<?php
$serverName = "yourServername";
$connectionOptions = array(
    "Database" => "yourDatabase",
    "Uid" => "yourUsername",
    "PWD" => "yourPassword"
);

//Establishes the connection
$conn = sqlsrv_connect($serverName, $connectionOptions);
if( $conn === false ) {
    die( FormatErrors( sqlsrv_errors()));
}

//Select Query
$tsql= "SELECT @@Version as SQL_VERSION";

//Executes the query
$getResults= sqlsrv_query($conn, $tsql);

//Error handling
if ($getResults == FALSE)
    die(FormatErrors(sqlsrv_errors()));
?>

<h1> Results : </h1>

<?php
while ($row = sqlsrv_fetch_array($getResults, SQLSRV_FETCH_ASSOC)) {
    echo ($row['SQL_VERSION']);
    echo ("<br/>");
}

sqlsrv_free_stmt($getResults);

function FormatErrors( $errors )
{
    /* Display errors. */
    echo "Error information: <br/>";
    foreach ( $errors as $error )
    {
        echo "SQLSTATE: ".$error['SQLSTATE']."<br/>";
        echo "Code: ".$error['code']."<br/>";
        echo "Message: ".$error['message']."<br/>";
    }
}
?>
```
Pointez votre navigateur sur http://localhost/testsql.php (http://localhost:8080/testsql.php sur macOS). Vous devez maintenant être en mesure de se connecter à votre base de données SQL Server/Azure SQL.

## <a name="see-also"></a>Voir aussi  
[Mise en route avec les pilotes Microsoft PHP pour SQL Server](../../connect/php/getting-started-with-the-php-sql-driver.md)

[Chargement des pilotes Microsoft SQL Server pour PHP](../../connect/php/loading-the-php-sql-driver.md)

[Configuration système requise pour les pilotes Microsoft pour PHP pour SQL Server](../../connect/php/system-requirements-for-the-php-sql-driver.md)
