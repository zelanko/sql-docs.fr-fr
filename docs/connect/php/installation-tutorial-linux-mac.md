---
title: Installation sur Linux et macOS pour les pilotes pour PHP
description: Dans ces instructions, découvrez comment installer les pilotes Microsoft pour PHP pour SQL Server sur Linux ou macOS.
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
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88807015"
---
# <a name="linux-and-macos-installation-tutorial-for-the-microsoft-drivers-for-php-for-sql-server"></a>Tutoriel : Installation sur Linux et macOS des pilotes Microsoft pour PHP pour SQL Server
Les instructions suivantes partent du principe que votre environnement est propre. Elles montrent comment installer PHP 7.x, le pilote ODBC Microsoft, le serveur web Apache et les Pilotes Microsoft pour PHP pour SQL Server sur Ubuntu 16.04, 18.04 et 20.04, RedHat 7 et 8, Debian 8, 9 et 10, Suse 12 et 15, Alpine 3.11 ainsi que macOS 10.13, 10.14 et 10.15. Ces instructions conseillent d’installer les pilotes à l’aide de PECL, mais vous pouvez également télécharger les fichiers binaires prédéfinis à partir de la page de projet GitHub des [pilotes Microsoft pour PHP pour SQL Server](https://github.com/Microsoft/msphpsql/releases) et les installer en suivant les instructions fournies dans [Chargement des pilotes Microsoft SQL Server pour PHP](../../connect/php/loading-the-php-sql-driver.md). Pour obtenir une explication concernant le chargement d’extension et savoir pourquoi nous n’ajoutons pas les extensions à php.ini, consultez la section sur le [chargement des pilotes](../../connect/php/loading-the-php-sql-driver.md#loading-the-driver-at-php-startup).

Ces instructions installent PHP 7.4 par défaut avec `pecl install`. Vous devrez peut-être d’abord exécuter `pecl channel-update pecl.php.net`. Notez que certaines distributions de Linux prises en charge utilisent par défaut PHP 7.1 ou une version antérieure, qui ne sont pas prises en charge pour la dernière version des pilotes PHP pour SQL Server. Consultez les notes au début de chaque section pour installer PHP 7.2 ou 7.3 à la place.

Vous trouverez également des instructions pour l’installation du gestionnaire de processus PHP FastCGI, PHP-FPM, sur Ubuntu. C’est nécessaire si vous utilisez le serveur Web nginx au lieu d’Apache.

## <a name="contents-of-this-page"></a>Contenu de cette page

- [Installation des pilotes sur Ubuntu 16.04, 18.04 et 20.04](#installing-the-drivers-on-ubuntu-1604-1804-and-2004)
- [Installation des pilotes avec PHP-FPM sur Ubuntu](#installing-the-drivers-with-php-fpm-on-ubuntu)
- [Installation des pilotes sur Red Hat 7 et 8](#installing-the-drivers-on-red-hat-7-and-8)
- [Installation des pilotes sur Debian 8, 9 et 10](#installing-the-drivers-on-debian-8-9-and-10)
- [Installation des pilotes sur Suse 12 et 15](#installing-the-drivers-on-suse-12-and-15)
- [Installation des pilotes sur Alpine 3.11](#installing-the-drivers-on-alpine-311)
- [Installation des pilotes sur macOS High Sierra, Mojave et Catalina](#installing-the-drivers-on-macos-high-sierra-mojave-and-catalina)

## <a name="installing-the-drivers-on-ubuntu-1604-1804-and-2004"></a>Installation des pilotes sur Ubuntu 16.04, 18.04 et 20.04

> [!NOTE]
> Pour installer PHP 7.2 ou 7.3, remplacez 7.4 par 7.2 ou 7.3 dans les commandes suivantes.

### <a name="step-1-install-php"></a>Étape 1. Installer PHP
```bash
sudo su
add-apt-repository ppa:ondrej/php -y
apt-get update
apt-get install php7.4 php7.4-dev php7.4-xml -y --allow-unauthenticated
```
### <a name="step-2-install-prerequisites"></a>Étape 2. Prérequis à installer
Installez le pilote ODBC pour Ubuntu en suivant les instructions fournies dans l’[article sur l’installation sur Linux](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md).

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Étape 3. Installer les pilotes PHP pour Microsoft SQL Server
```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
sudo su
printf "; priority=20\nextension=sqlsrv.so\n" > /etc/php/7.4/mods-available/sqlsrv.ini
printf "; priority=30\nextension=pdo_sqlsrv.so\n" > /etc/php/7.4/mods-available/pdo_sqlsrv.ini
exit
sudo phpenmod -v 7.4 sqlsrv pdo_sqlsrv
```

S’il n’y a qu’une version de PHP dans le système, la dernière étape peut être simplifiée en `phpenmod sqlsrv pdo_sqlsrv`.

### <a name="step-4-install-apache-and-configure-driver-loading"></a>Étape 4. Installer Apache et configurer le chargement du pilote
```
sudo su
apt-get install libapache2-mod-php7.4 apache2
a2dismod mpm_event
a2enmod mpm_prefork
a2enmod php7.4
exit
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>Étape 5. Redémarrer Apache et tester l’exemple de script
```
sudo service apache2 restart
```
Pour tester votre installation, consultez [Test de votre installation](#testing-your-installation) à la fin de ce document.

## <a name="installing-the-drivers-with-php-fpm-on-ubuntu"></a>Installation des pilotes avec PHP-FPM sur Ubuntu

> [!NOTE]
> Pour installer PHP 7.2 ou 7.3, remplacez 7.4 par 7.2 ou 7.3 dans les commandes suivantes.

### <a name="step-1-install-php"></a>Étape 1. Installer PHP
```bash
sudo su
add-apt-repository ppa:ondrej/php -y
apt-get update
apt-get install php7.4 php7.4-dev php7.4-xml php7.4-fpm -y --allow-unauthenticated
```
Vérifiez l’état du service PHP-FPM en l’exécutant
```
systemctl status php7.4-fpm
```
### <a name="step-2-install-prerequisites"></a>Étape 2. Prérequis à installer
Installez le pilote ODBC pour Ubuntu en suivant les instructions fournies dans l’[article sur l’installation sur Linux](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md).

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Étape 3. Installer les pilotes PHP pour Microsoft SQL Server
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
S’il n’y a qu’une version de PHP dans le système, la dernière étape peut être simplifiée en `phpenmod sqlsrv pdo_sqlsrv`.

Vérifiez que `sqlsrv.ini` et `pdo_sqlsrv.ini` se trouvent dans `/etc/php/7.4/fpm/conf.d/` :
```
ls /etc/php/7.4/fpm/conf.d/*sqlsrv.ini
```
Redémarrez le service PHP-FPM :
```
sudo systemctl restart php7.4-fpm
```

### <a name="step-4-install-and-configure-nginx"></a>Étape 4. Installer et configurer nginx
```
sudo apt-get update
sudo apt-get install nginx
sudo systemctl status nginx
```
Pour configurer nginx, vous devez modifier le fichier `/etc/nginx/sites-available/default`. Ajoutez `index.php` à la liste située sous la section qui indique `# Add index.php to the list if you are using PHP` :
```
# Add index.php to the list if you are using PHP
index index.html index.htm index.nginx-debian.html index.php;
```
Ensuite, modifiez la section suivante `# pass PHP scripts to FastCGI server` comme suit :
```
# pass PHP scripts to FastCGI server
#
location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/run/php/php7.4-fpm.sock;
}
```
### <a name="step-5-restart-nginx-and-test-the-sample-script"></a>Étape 5. Redémarrer nginx et tester l’exemple de script
```
sudo systemctl restart nginx.service
```
Pour tester votre installation, consultez [Test de votre installation](#testing-your-installation) à la fin de ce document.

## <a name="installing-the-drivers-on-red-hat-7-and-8"></a>Installation des pilotes sur Red Hat 7 et 8

### <a name="step-1-install-php"></a>Étape 1. Installer PHP

Pour installer PHP sur Red Hat 7, exécutez la commande suivante :
> [!NOTE]
> Pour installer PHP 7.2 ou 7.3, remplacez remi-php74 respectivement par remi-php72 ou remi-php73 dans les commandes suivantes.
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

Pour installer PHP sur Red Hat 8, exécutez la commande suivante :
> [!NOTE]
> Pour installer PHP 7.2 ou 7.3, remplacez respectivement remi-7.4 par remi-7.2 ou par remi-7.3 dans les commandes suivantes.
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

### <a name="step-2-install-prerequisites"></a>Étape 2. Prérequis à installer
Installez le pilote ODBC pour Red Hat 7 ou 8 en suivant les instructions fournies dans l’[article sur l’installation sur Linux](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md).

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Étape 3. Installer les pilotes PHP pour Microsoft SQL Server
```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
sudo su
echo extension=pdo_sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/30-pdo_sqlsrv.ini
echo extension=sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/20-sqlsrv.ini
exit
```

Vous pouvez également effectuer l’installation à partir du référentiel Remi :
```
sudo yum install php-sqlsrv
```
### <a name="step-4-install-apache"></a>Étape 4. Installer Apache
```
sudo yum install httpd
```
SELinux est installé par défaut et s’exécute en mode forcé. Pour autoriser Apache à se connecter aux bases de données par le biais de SELinux, exécutez la commande suivante :
```
sudo setsebool -P httpd_can_network_connect_db 1
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>Étape 5. Redémarrer Apache et tester l’exemple de script
```
sudo apachectl restart
```
Pour tester votre installation, consultez [Test de votre installation](#testing-your-installation) à la fin de ce document.

## <a name="installing-the-drivers-on-debian-8-9-and-10"></a>Installation des pilotes sur Debian 8, 9 et 10

> [!NOTE]
> Pour installer PHP 7.2 ou 7.3, remplacez 7.4 par 7.2 ou 7.3 dans les commandes suivantes.

### <a name="step-1-install-php"></a>Étape 1. Installer PHP
```
sudo su
apt-get install curl apt-transport-https
wget -O /etc/apt/trusted.gpg.d/php.gpg https://packages.sury.org/php/apt.gpg
echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" > /etc/apt/sources.list.d/php.list
apt-get update
apt-get install -y php7.4 php7.4-dev php7.4-xml php7.4-intl
```
### <a name="step-2-install-prerequisites"></a>Étape 2. Prérequis à installer
Installez le pilote ODBC pour Debian en suivant les instructions fournies dans l’[article sur l’installation sur Linux](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md). 

Vous devrez peut-être aussi générer les paramètres régionaux corrects pour que la sortie PHP s’affiche correctement dans un navigateur. Par exemple, pour les paramètres régionaux UTF-8 en_US, exécutez les commandes suivantes :
```
sudo su
sed -i 's/# en_US.UTF-8 UTF-8/en_US.UTF-8 UTF-8/g' /etc/locale.gen
locale-gen
```
Vous devrez peut-être ajouter `/usr/sbin` à votre `$PATH`, car le fichier exécutable `locale-gen` se trouve ici.

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Étape 3. Installer les pilotes PHP pour Microsoft SQL Server
```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
sudo su
printf "; priority=20\nextension=sqlsrv.so\n" > /etc/php/7.4/mods-available/sqlsrv.ini
printf "; priority=30\nextension=pdo_sqlsrv.so\n" > /etc/php/7.4/mods-available/pdo_sqlsrv.ini
exit
sudo phpenmod -v 7.4 sqlsrv pdo_sqlsrv
```

S’il n’y a qu’une version de PHP dans le système, la dernière étape peut être simplifiée en `phpenmod sqlsrv pdo_sqlsrv`. Comme avec `locale-gen` `phpenmod` se trouve dans `/usr/sbin`, vous devrez peut-être ajouter ce répertoire à votre `$PATH`.

### <a name="step-4-install-apache-and-configure-driver-loading"></a>Étape 4. Installer Apache et configurer le chargement du pilote
```
sudo su
apt-get install libapache2-mod-php7.4 apache2
a2dismod mpm_event
a2enmod mpm_prefork
a2enmod php7.4
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>Étape 5. Redémarrer Apache et tester l’exemple de script
```
sudo service apache2 restart
```
Pour tester votre installation, consultez [Test de votre installation](#testing-your-installation) à la fin de ce document.

## <a name="installing-the-drivers-on-suse-12-and-15"></a>Installation des pilotes sur Suse 12 et 15

> [!NOTE]
> Dans les instructions suivantes, remplacez `<SuseVersion>` par votre version de Suse. Si vous utilisez Suse Enterprise Linux 15, il s’agira de SLE_15 ou SLE_15_SP1. Pour Suse 12, utilisez SLE_12_SP4 (ou une version ultérieure, le cas échéant). Toutes les versions de PHP ne sont pas disponibles pour toutes les versions de Suse Linux. Consultez `http://download.opensuse.org/repositories/devel:/languages:/php` afin de savoir pour quelles versions de Suse la version par défaut de PHP est disponible, ou `http://download.opensuse.org/repositories/devel:/languages:/php:/` pour savoir quelles autres versions de PHP sont disponibles pour les différentes versions de Suse.

> [!NOTE]
> Les packages pour PHP 7.4 ne sont pas disponibles pour Suse 12. Pour installer PHP 7.2, remplacez l’URL du référentiel ci-dessous par l’URL suivante : `https://download.opensuse.org/repositories/devel:/languages:/php:/php72/<SuseVersion>/devel:languages:php:php72.repo`.
> Pour installer PHP 7.3, remplacez l’URL du référentiel ci-dessous par l’URL suivante : `https://download.opensuse.org/repositories/devel:/languages:/php:/php73/<SuseVersion>/devel:languages:php:php73.repo`.

### <a name="step-1-install-php"></a>Étape 1. Installer PHP
```
sudo su
zypper -n ar -f https://download.opensuse.org/repositories/devel:languages:php/<SuseVersion>/devel:languages:php.repo
zypper --gpg-auto-import-keys refresh
zypper -n install php7 php7-devel php7-openssl
```
### <a name="step-2-install-prerequisites"></a>Étape 2. Prérequis à installer
Installez le pilote ODBC pour Suse en suivant les instructions fournies dans l’[article sur l’installation sur Linux](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md).

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Étape 3. Installer les pilotes PHP pour Microsoft SQL Server
> [!NOTE]
> Si vous obtenez le message d’erreur `Connection to 'pecl.php.net:443' failed: Unable to find the socket transport "ssl"`, modifiez le script pecl situé dans /usr/bin/pecl en supprimant le commutateur `-n` sur la dernière ligne. Ce commutateur empêche PECL de charger les fichiers ini quand PHP est appelé, ce qui empêche le chargement de l’extension OpenSSL.

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
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>Étape 5. Redémarrer Apache et tester l’exemple de script
```
sudo systemctl restart apache2
```
Pour tester votre installation, consultez [Test de votre installation](#testing-your-installation) à la fin de ce document.

## <a name="installing-the-drivers-on-alpine-311"></a>Installation des pilotes sur Alpine 3.11

> [!NOTE]
> La version par défaut de PHP est 7.3. D’autres versions de PHP peuvent être disponibles à partir d’autres référentiels pour Alpine 3.11. À la place, vous pouvez compiler PHP à partir de la source.

### <a name="step-1-install-php"></a>Étape 1. Installer PHP
Les packages PHP pour Alpine se trouvent dans le référentiel `edge/community`. Cochez [Activer le référentiel de la communauté](https://wiki.alpinelinux.org/wiki/Enable_Community_Repository) sur sa page WIKI. Ajoutez la ligne suivante à `/etc/apt/repositories` en remplaçant `<mirror>` par l’URL d’un miroir de référentiel Alpine :
```
http://<mirror>/alpine/edge/community
```
Ensuite, exécutez :
```
sudo su
apk update
apk add php7 php7-dev php7-pear php7-pdo php7-openssl autoconf make g++
```
### <a name="step-2-install-prerequisites"></a>Étape 2. Prérequis à installer
Installez le pilote ODBC pour Alpine en suivant les instructions fournies dans l’[article sur l’installation sur Linux](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md). 

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Étape 3. Installer les pilotes PHP pour Microsoft SQL Server
```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
sudo su
echo extension=pdo_sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/10_pdo_sqlsrv.ini
echo extension=sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/00_sqlsrv.ini
```

### <a name="step-4-install-apache-and-configure-driver-loading"></a>Étape 4. Installer Apache et configurer le chargement du pilote
```
sudo apk add php7-apache2 apache2
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>Étape 5. Redémarrer Apache et tester l’exemple de script
```
sudo rc-service apache2 restart
```
Pour tester votre installation, consultez [Test de votre installation](#testing-your-installation) à la fin de ce document.


## <a name="installing-the-drivers-on-macos-high-sierra-mojave-and-catalina"></a>Installation des pilotes sur macOS High Sierra, Mojave et Catalina

Si ce n’est déjà fait, installez brew comme suit :
```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

> [!NOTE]
> Pour installer PHP 7.2 ou 7.3, remplacez respectivement php@7.4 par php@7.2 ou par php@7.3 dans les commandes suivantes.

### <a name="step-1-install-php"></a>Étape 1. Installer PHP

```
brew tap
brew tap homebrew/core
brew install php@7.4
```
PHP doit maintenant être présent dans votre chemin. Exécutez `php -v` pour vérifier que vous exécutez la version correcte de PHP. Si PHP n’est pas dans votre chemin, ou s’il ne s’agit pas de la version correcte, exécutez la commande suivante :
```
brew link --force --overwrite php@7.4
```

### <a name="step-2-install-prerequisites"></a>Étape 2. Prérequis à installer
Installez le pilote ODBC pour macOS en suivant les instructions fournies dans l’[article sur l’installation sur macOS](../../connect/odbc/linux-mac/install-microsoft-odbc-driver-sql-server-macos.md). 

Vous devrez peut-être aussi installer les outils de création GNU :
```
brew install autoconf automake libtool
```

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Étape 3. Installer les pilotes PHP pour Microsoft SQL Server
```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
```
### <a name="step-4-install-apache-and-configure-driver-loading"></a>Étape 4. Installer Apache et configurer le chargement du pilote
```
brew install apache2
```
Pour rechercher le fichier de configuration, `httpd.conf`, pour votre installation Apache, exécutez 
```
/usr/local/bin/apachectl -V | grep SERVER_CONFIG_FILE
``` 
Les commandes suivantes ajoutent la configuration requise à `httpd.conf`. Veillez à substituer le chemin retourné par la commande précédente à `/usr/local/etc/httpd/httpd.conf` :
```
echo "LoadModule php7_module /usr/local/opt/php@7.4/lib/httpd/modules/libphp7.so" >> /usr/local/etc/httpd/httpd.conf
(echo "<FilesMatch .php$>"; echo "SetHandler application/x-httpd-php"; echo "</FilesMatch>";) >> /usr/local/etc/httpd/httpd.conf
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>Étape 5. Redémarrer Apache et tester l’exemple de script
```
sudo apachectl restart
```
Pour tester votre installation, consultez [Test de votre installation](#testing-your-installation) à la fin de ce document.

## <a name="testing-your-installation"></a>Test de votre installation

Pour tester cet exemple de script, créez un fichier nommé testsql.php à la racine de document de votre système. Il s’agit de `/var/www/html/` sur Ubuntu, Debian et Red Hat, de `/srv/www/htdocs` sur SUSE, de `/var/www/localhost/htdocs` sur Alpine ou de `/usr/local/var/www` sur macOS. Copiez-y le script suivant, en remplaçant le serveur de base de données, le nom d’utilisateur et le mot de passe comme il convient.
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
Dirigez votre navigateur vers https://localhost/testsql.php (https://localhost:8080/testsql.php sur macOS). Vous devriez maintenant pouvoir vous connecter à votre base de données SQL Server/SQL Azure.

## <a name="see-also"></a>Voir aussi  
[Bien démarrer avec les pilotes Microsoft pour PHP pour SQL Server](../../connect/php/getting-started-with-the-php-sql-driver.md)

[Chargement de Microsoft Drivers for PHP for SQL Server](../../connect/php/loading-the-php-sql-driver.md)

[Configuration système requise pour Microsoft Drivers for PHP for SQL Server](../../connect/php/system-requirements-for-the-php-sql-driver.md)
