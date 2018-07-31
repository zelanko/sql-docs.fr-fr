---
title: Linux et macOS didacticiel d’Installation pour le Microsoft Drivers for PHP for SQL Server | Microsoft Docs
ms.date: 07/20/2018
ms.prod: sql
ms.prod_service: connectivity
ms.suite: sql
ms.custom: ''
ms.technology: connectivity
ms.topic: conceptual
author: ulvii
ms.author: v-ulibra
manager: v-mabarw
ms.openlocfilehash: 5b22d2c74ad356a9466c8441f979414857865386
ms.sourcegitcommit: c37da15581fb34250d426a8d661f6d0d64f9b54c
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2018
ms.locfileid: "39174896"
---
# <a name="linux-and-macos-installation-tutorial-for-the-microsoft-drivers-for-php-for-sql-server"></a>Linux et macOS didacticiel d’Installation pour le Microsoft Drivers for PHP for SQL Server
Les instructions suivantes supposent un environnement propre et montrent comment installer PHP 7.x, le pilote ODBC de Microsoft, Apache et le Microsoft Drivers for PHP for SQL Server sur Ubuntu 16.04, 17.10 et 18.04, Red Hat 7, Debian 8 et 9, Suse 12 et macOS 10.11 , 10.12 et 10.13. Ces instructions conseiller l’installation des pilotes à l’aide de PECL, mais vous pouvez également télécharger les fichiers binaires prédéfinis à partir de la [Microsoft Drivers for PHP for SQL Server](https://github.com/Microsoft/msphpsql/releases) Github page de projet et les installer en suivant les instructions de [ Chargement des pilotes Microsoft pour PHP pour SQL Server](../../connect/php/loading-the-php-sql-driver.md). Pour obtenir une explication de chargement de l’extension et pourquoi nous n’ajoutez pas les extensions à php.ini, consultez la section sur [chargement des pilotes](../../connect/php/loading-the-php-sql-driver.md##loading-the-driver-at-php-startup).

Ces installation instructions PHP 7.2 par défaut, consultez les remarques au début de chaque section pour installer PHP 7.0 ou 7.1.

## <a name="contents-of-this-page"></a>Contenu de cette page :

- [Installation des pilotes sur Ubuntu 16.04, 17.10 et 18.04](#installing-the-drivers-on-ubuntu-1604-1710-and-1804)
- [Installation des pilotes sur Red Hat 7](#installing-the-drivers-on-red-hat-7)
- [Installation des pilotes sur Debian 8 et 9](#installing-the-drivers-on-debian-8-and-9)
- [Installation des pilotes sur Suse 12](#installing-the-drivers-on-suse-12)
- [Installation des pilotes sur macOS El Capitan, Sierra et High Sierra](#installing-the-drivers-on-macos-el-capitan-sierra-and-high-sierra)

## <a name="installing-the-drivers-on-ubuntu-1604-1710-and-1804"></a>Installation des pilotes sur Ubuntu 16.04, 17.10 et 18.04

> [!NOTE]
> Pour installer PHP 7.0 ou 7.1, remplacez-les par 7.2 7.0 ou 7.1 dans les commandes suivantes.
> Pour Ubuntu 18.04, l’étape pour ajouter le référentiel ondrej n’est pas obligatoire, sauf si PHP 7.0 ou 7.1 est nécessaire. Toutefois, l’installation de PHP 7.0 ou 7.1 dans Ubuntu 18.04 ne peut ne pas fonctionne comme des packages à partir du référentiel ondrej sont fournis avec des dépendances qui peuvent être en conflit avec une base Ubuntu 18.04 installer.

### <a name="step-1-install-php"></a>Étape 1. Installer PHP
```
sudo su
add-apt-repository ppa:ondrej/php -y
apt-get update
apt-get install php7.2 php7.2-dev php7.2-xml -y --allow-unauthenticated
```
### <a name="step-2-install-prerequisites"></a>Étape 2. Prérequis à installer
Installer le pilote ODBC pour Ubuntu en suivant les instructions la [page d’installation de Linux et macOS](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md).

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Étape 3. Installez les pilotes PHP pour Microsoft SQL Server
```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
sudo su
echo extension=pdo_sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/30-pdo_sqlsrv.ini
echo extension=sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/20-sqlsrv.ini
exit
```
### <a name="step-4-install-apache-and-configure-driver-loading"></a>Étape 4. Installer Apache et configurer le chargement du pilote
```
sudo su
apt-get install libapache2-mod-php7.2 apache2
a2dismod mpm_event
a2enmod mpm_prefork
a2enmod php7.2
echo "extension=pdo_sqlsrv.so" >> /etc/php/7.2/apache2/conf.d/30-pdo_sqlsrv.ini
echo "extension=sqlsrv.so" >> /etc/php/7.2/apache2/conf.d/20-sqlsrv.ini
exit
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>Étape 5. Redémarrez Apache et tester l’exemple de script
```
sudo service apache2 restart
```
Pour tester votre installation, consultez [tester votre installation](#testing-your-installation) à la fin de ce document.

## <a name="installing-the-drivers-on-red-hat-7"></a>Installation des pilotes sur Red Hat 7

> [!NOTE]
> Pour installer PHP 7.0 ou 7.1, remplacez-les par ance-php72 ance-php70 ou ance-php71 respectivement dans les commandes suivantes.

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
### <a name="step-2-install-prerequisites"></a>Étape 2. Prérequis à installer
Installer le pilote ODBC pour Red Hat 7 en suivant les instructions la [page d’installation de Linux et macOS](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md).

Compilation les pilotes PHP avec PECL avec PHP 7.2 nécessite un GCC plus récente que la valeur par défaut :
```
sudo yum-config-manager --enable rhel-server-rhscl-7-rpms
sudo yum install devtoolset-7
scl enable devtoolset-7 bash
```
### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Étape 3. Installez les pilotes PHP pour Microsoft SQL Server
```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
sudo su
echo extension=pdo_sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/30-pdo_sqlsrv.ini
echo extension=sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/20-sqlsrv.ini
exit
```
Un problème dans PECL peut empêcher l’installation correcte de la dernière version des pilotes même si vous avez mis à niveau GCC. Pour installer, de télécharger les packages et de compiler manuellement (des étapes similaires pour pdo_sqlsrv) :
```
pecl download sqlsrv
tar xvzf sqlsrv-5.3.0.tgz
cd sqlsrv-5.3.0/
phpize
./configure --with-php-config=/usr/bin/php-config
make
sudo make install
```
Vous pouvez également télécharger les fichiers binaires prédéfinis à partir de la [page de projet Github](https://github.com/Microsoft/msphpsql/releases), ou l’installer à partir du dépôt ance :
```
sudo yum install php-sqlsrv php-pdo_sqlsrv
```
### <a name="step-4-install-apache"></a>Étape 4. Installer Apache
```
sudo yum install httpd
```
SELinux est installé par défaut et s’exécute en mode d’application. Pour autoriser Apache pour se connecter aux bases de données via SELinux, exécutez la commande suivante :
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
> Pour installer PHP 7.0 ou 7.1, remplacez 7.2 dans les commandes suivantes avec la version 7.0 ou 7.1.

### <a name="step-1-install-php"></a>Étape 1. Installer PHP
```
sudo su
apt-get install curl apt-transport-https
wget -O /etc/apt/trusted.gpg.d/php.gpg https://packages.sury.org/php/apt.gpg
echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" > /etc/apt/sources.list.d/php.list
apt-get update
apt-get install -y php7.2 php7.2-dev php7.2-xml
```
### <a name="step-2-install-prerequisites"></a>Étape 2. Prérequis à installer
Installer le pilote ODBC pour Debian en suivant les instructions la [page d’installation de Linux et macOS](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md). 

Vous serez peut-être amené à générer les paramètres régionaux corrects pour obtenir une sortie PHP s’affichent correctement dans un navigateur. Par exemple, pour les paramètres régionaux de UTF-8 fr_FR, exécutez les commandes suivantes :
```
sudo su
sed -i 's/# en_US.UTF-8 UTF-8/en_US.UTF-8 UTF-8/g' /etc/locale.gen
locale-gen
```

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Étape 3. Installez les pilotes PHP pour Microsoft SQL Server
```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
sudo su
echo extension=pdo_sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/30-pdo_sqlsrv.ini
echo extension=sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/20-sqlsrv.ini
exit
```
### <a name="step-4-install-apache-and-configure-driver-loading"></a>Étape 4. Installer Apache et configurer le chargement du pilote
```
sudo su
apt-get install libapache2-mod-php7.2 apache2
a2dismod mpm_event
a2enmod mpm_prefork
a2enmod php7.2
echo "extension=pdo_sqlsrv.so" >> /etc/php/7.2/apache2/conf.d/30-pdo_sqlsrv.ini
echo "extension=sqlsrv.so" >> /etc/php/7.2/apache2/conf.d/20-sqlsrv.ini
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>Étape 5. Redémarrez Apache et tester l’exemple de script
```
sudo service apache2 restart
```
Pour tester votre installation, consultez [tester votre installation](#testing-your-installation) à la fin de ce document.

## <a name="installing-the-drivers-on-suse-12"></a>Installation des pilotes sur Suse 12

> [!NOTE]
> Pour installer PHP 7.0, ignorer la commande ci-dessous Ajout du référentiel - 7.0 est la valeur par défaut PHP sur suse 12.
> Pour installer PHP 7.1, remplacez l’URL du référentiel ci-dessous avec l’URL suivante : `http://download.opensuse.org/repositories/devel:/languages:/php:/php71/SLE_12/devel:languages:php:php71.repo`

### <a name="step-1-install-php"></a>Étape 1. Installer PHP
```
sudo su
zypper -n ar -f http://download.opensuse.org/repositories/devel:languages:php/SLE_12/devel:languages:php.repo
zypper --gpg-auto-import-keys refresh
zypper -n install php7 php7-pear php7-devel
```
### <a name="step-2-install-prerequisites"></a>Étape 2. Prérequis à installer
Installer le pilote ODBC pour Suse 12 en suivant les instructions la [page d’installation de Linux et macOS](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md).

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Étape 3. Installez les pilotes PHP pour Microsoft SQL Server
```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
sudo su
echo extension=pdo_sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/pdo_sqlsrv.ini
echo extension=sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/sqlsrv.ini
exit
```
### <a name="step-4-install-apache-and-configure-driver-loading"></a>Étape 4. Installer Apache et configurer le chargement du pilote
```
sudo su
zypper install apache2 apache2-mod_php7
a2enmod php7
echo "extension=sqlsrv.so" >> /etc/php7/apache2/php.ini
echo "extension=pdo_sqlsrv.so" >> /etc/php7/apache2/php.ini
exit
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>Étape 5. Redémarrez Apache et tester l’exemple de script
```
sudo systemctl restart apache2
```
Pour tester votre installation, consultez [tester votre installation](#testing-your-installation) à la fin de ce document.

## <a name="installing-the-drivers-on-macos-el-capitan-sierra-and-high-sierra"></a>Installation des pilotes sur macOS El Capitan, Sierra et High Sierra

Si vous ne l’avez pas déjà, installez brew comme suit :
```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

> [!NOTE]
> Pour installer PHP 7.0 ou 7.1, remplacez php@7.2 avec php@7.0 ou php@7.1 respectivement dans les commandes suivantes.

### <a name="step-1-install-php"></a>Étape 1. Installer PHP

```
brew tap
brew tap homebrew/core
brew install php@7.2
```
PHP doit être présent dans votre chemin d’accès--exécuter `php -v` pour vérifier que vous exécutiez la version appropriée de PHP. Si PHP n’est pas dans votre chemin d’accès, ou il n’est pas la version correcte, exécutez la commande suivante :
```
brew link --force --overwrite php@7.2
```

### <a name="step-2-install-prerequisites"></a>Étape 2. Prérequis à installer
Installer le pilote ODBC pour macOS en suivant les instructions la [page d’installation de Linux et macOS](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md). 

En outre, vous devrez peut-être installer les outils de création de GNU :
```
brew install autoconf automake libtool
```

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Étape 3. Installez les pilotes PHP pour Microsoft SQL Server
```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
```
### <a name="step-4-install-apache-and-configure-driver-loading"></a>Étape 4. Installer Apache et configurer le chargement du pilote
```
brew install apache2
```
Pour rechercher des fichiers de configuration pour votre installation Apache Apache, exécutez 
```
apachectl -V | grep SERVER_CONFIG_FILE
``` 
puis remplacez le chemin d’accès pour `httpd.conf` dans les commandes suivantes :
```
echo "LoadModule php7_module /usr/local/opt/php@7.2/lib/httpd/modules/libphp7.so" >> /usr/local/etc/httpd/httpd.conf
(echo "<FilesMatch .php$>"; echo "SetHandler application/x-httpd-php"; echo "</FilesMatch>";) >> /usr/local/etc/httpd/httpd.conf
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>Étape 5. Redémarrez Apache et tester l’exemple de script
```
sudo apachectl restart
```
Pour tester votre installation, consultez [tester votre installation](#testing-your-installation) à la fin de ce document.

## <a name="testing-your-installation"></a>Test de votre installation

Pour tester cet exemple de script, créez un fichier appelé testsql.php dans la racine du document de votre système. Il s’agit de `/var/www/html/` sur Ubuntu, Red Hat et Debian `/srv/www/htdocs` sur SUSE, ou `/usr/local/var/www` sur macOS. Copier le script suivant, en remplaçant le serveur de base de données, nom d’utilisateur et mot de passe comme il convient.
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
Dirigez votre navigateur vers http://localhost/testsql.php (http://localhost:8080/testsql.php sur macOS). Vous devez maintenant être en mesure de se connecter à votre base de données SQL Server/SQL Azure.

## <a name="see-also"></a> Voir aussi  
[Mise en route avec les pilotes Microsoft pour PHP pour SQL Server](../../connect/php/getting-started-with-the-php-sql-driver.md)

[Chargement de Microsoft Drivers for PHP for SQL Server](../../connect/php/loading-the-php-sql-driver.md)

[Configuration système requise pour Microsoft Drivers for PHP for SQL Server](../../connect/php/system-requirements-for-the-php-sql-driver.md)
