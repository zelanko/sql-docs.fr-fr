---
title: 'Tutoriel : Installation sur Linux et macOS des pilotes Microsoft pour PHP pour SQL Server | Microsoft Docs'
ms.date: 06/21/2019
ms.prod: sql
ms.prod_service: connectivity
ms.custom: ''
ms.technology: connectivity
ms.topic: conceptual
author: ulvii
ms.author: v-ulibra
manager: v-mabarw
ms.openlocfilehash: 90d2b5850010d49e881ea0169566fe8e7d046f0d
ms.sourcegitcommit: 630f7cacdc16368735ec1d955b76d6d030091097
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2019
ms.locfileid: "67343911"
---
# <a name="linux-and-macos-installation-tutorial-for-the-microsoft-drivers-for-php-for-sql-server"></a>Tutoriel : Installation sur Linux et macOS des pilotes Microsoft pour PHP pour SQL Server
Les instructions suivantes partent du principe que votre environnement est propre. Elles montrent comment installer PHP 7.x, le pilote Microsoft ODBC, Apache et les pilotes Microsoft pour PHP pour SQL Server sur Ubuntu 16.04, 18.04 et 18.10, Red Hat 7, Debian 8 et 9, Suse 12 et 15 et macOS 10.12, 10.13 et 10.14. Ces instructions conseillent d’installer les pilotes à l’aide de PECL, mais vous pouvez également télécharger les fichiers binaires prédéfinis à partir de la page de projet Github des [pilotes Microsoft pour PHP pour SQL Server](https://github.com/Microsoft/msphpsql/releases) et les installer en suivant les instructions fournies dans [Chargement des pilotes Microsoft SQL Server pour PHP](../../connect/php/loading-the-php-sql-driver.md). Pour obtenir une explication concernant le chargement d’extension et savoir pourquoi nous n’ajoutons pas les extensions à php.ini, consultez la section sur le [chargement des pilotes](../../connect/php/loading-the-php-sql-driver.md##loading-the-driver-at-php-startup).

Ces instructions installent PHP 7.3 par défaut. Notez que certaines distributions de Linux prises en charge utilisent par défaut pour PHP 7.0 ou version antérieure, n’est pas pris en charge pour les pilotes PHP pour SQL Server. Consultez les notes au début de chaque section pour installer PHP 7.1 ou 7.2 à la place.

## <a name="contents-of-this-page"></a>Contenu de cette page :

- [Installation des pilotes sur Ubuntu 16.04, 18.04 et 18.10](#installing-the-drivers-on-ubuntu-1604-1804-and-1810)
- [Installation des pilotes sur Red Hat 7](#installing-the-drivers-on-red-hat-7)
- [Installation des pilotes sur Debian 8 et 9](#installing-the-drivers-on-debian-8-and-9)
- [Installation des pilotes sur Suse 12 et 15](#installing-the-drivers-on-suse-12-and-15)
- [Installation des pilotes sur macOS Sierra, High Sierra et Mojave](#installing-the-drivers-on-macos-sierra-high-sierra-and-mojave)

## <a name="installing-the-drivers-on-ubuntu-1604-1804-and-1810"></a>Installation des pilotes sur Ubuntu 16.04, 18.04 et 18.10

> [!NOTE]
> Pour installer PHP 7.1 ou 7.2, remplacez 7.3 par 7.1 ou 7.2 dans les commandes suivantes.

### <a name="step-1-install-php"></a>Étape 1. Installer PHP
```
sudo su
add-apt-repository ppa:ondrej/php -y
apt-get update
apt-get install php7.3 php7.3-dev php7.3-xml -y --allow-unauthenticated
```
### <a name="step-2-install-prerequisites"></a>Étape 2. Prérequis à installer
Installez le pilote ODBC pour Ubuntu en suivant les instructions fournies dans la [page d’installation de Linux et macOS](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md).

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Étape 3. Installer les pilotes PHP pour Microsoft SQL Server
```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
sudo su
printf "; priority=20\nextension=sqlsrv.so\n" > /etc/php/7.3/mods-available/sqlsrv.ini
printf "; priority=30\nextension=pdo_sqlsrv.so\n" > /etc/php/7.3/mods-available/pdo_sqlsrv.ini
exit
sudo phpenmod -v 7.3 sqlsrv pdo_sqlsrv
```

Si qu’une seule version PHP dans le système, la dernière étape peut être simplifiée en `phpenmod sqlsrv pdo_sqlsrv`.

### <a name="step-4-install-apache-and-configure-driver-loading"></a>Étape 4. Installer Apache et configurer le chargement du pilote
```
sudo su
apt-get install libapache2-mod-php7.3 apache2
a2dismod mpm_event
a2enmod mpm_prefork
a2enmod php7.3
exit
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>Étape 5. Redémarrer Apache et tester l’exemple de script
```
sudo service apache2 restart
```
Pour tester votre installation, consultez [Test de votre installation](#testing-your-installation) à la fin de ce document.

## <a name="installing-the-drivers-on-red-hat-7"></a>Installation des pilotes sur Red Hat 7

> [!NOTE]
> Pour installer PHP 7.1 ou 7.2, remplacez remi-php73 respectivement par remi-php71 ou remi-php72 dans les commandes suivantes.

### <a name="step-1-install-php"></a>Étape 1. Installer PHP

```
sudo su
wget https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
wget https://rpms.remirepo.net/enterprise/remi-release-7.rpm
rpm -Uvh remi-release-7.rpm epel-release-latest-7.noarch.rpm
subscription-manager repos --enable=rhel-7-server-optional-rpms
yum install yum-utils
yum-config-manager --enable remi-php73
yum update
yum install php php-pdo php-xml php-pear php-devel re2c gcc-c++ gcc
```
### <a name="step-2-install-prerequisites"></a>Étape 2. Prérequis à installer
Installez le pilote ODBC pour Red Hat 7 en suivant les instructions fournies dans la [page d’installation de Linux et macOS](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md).

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Étape 3. Installer les pilotes PHP pour Microsoft SQL Server
```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
sudo su
echo extension=pdo_sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/pdo_sqlsrv.ini
echo extension=sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/sqlsrv.ini
exit
```

Vous pouvez également télécharger les fichiers binaires prédéfinis à partir de la [page de projet Github](https://github.com/Microsoft/msphpsql/releases), ou installer à partir du dépôt Remi :
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

## <a name="installing-the-drivers-on-debian-8-and-9"></a>Installation des pilotes sur Debian 8 et 9

> [!NOTE]
> Pour installer PHP 7.1 ou 7.2, remplacez 7.3 par 7.1 ou 7.2 dans les commandes suivantes.

### <a name="step-1-install-php"></a>Étape 1. Installer PHP
```
sudo su
apt-get install curl apt-transport-https
wget -O /etc/apt/trusted.gpg.d/php.gpg https://packages.sury.org/php/apt.gpg
echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" > /etc/apt/sources.list.d/php.list
apt-get update
apt-get install -y php7.3 php7.3-dev php7.3-xml
```
### <a name="step-2-install-prerequisites"></a>Étape 2. Prérequis à installer
Installez le pilote ODBC pour Debian en suivant les instructions fournies dans la [page d’installation de Linux et macOS](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md). 

Vous devrez peut-être aussi générer les paramètres régionaux corrects pour que la sortie PHP s’affiche correctement dans un navigateur. Par exemple, pour les paramètres régionaux UTF-8 en_US, exécutez les commandes suivantes :
```
sudo su
sed -i 's/# en_US.UTF-8 UTF-8/en_US.UTF-8 UTF-8/g' /etc/locale.gen
locale-gen
```

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Étape 3. Installer les pilotes PHP pour Microsoft SQL Server
```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
sudo su
printf "; priority=20\nextension=sqlsrv.so\n" > /etc/php/7.3/mods-available/sqlsrv.ini
printf "; priority=30\nextension=pdo_sqlsrv.so\n" > /etc/php/7.3/mods-available/pdo_sqlsrv.ini
exit
sudo phpenmod -v 7.3 sqlsrv pdo_sqlsrv
```

Si qu’une seule version PHP dans le système, la dernière étape peut être simplifiée en `phpenmod sqlsrv pdo_sqlsrv`.

### <a name="step-4-install-apache-and-configure-driver-loading"></a>Étape 4. Installer Apache et configurer le chargement du pilote
```
sudo su
apt-get install libapache2-mod-php7.3 apache2
a2dismod mpm_event
a2enmod mpm_prefork
a2enmod php7.3
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>Étape 5. Redémarrer Apache et tester l’exemple de script
```
sudo service apache2 restart
```
Pour tester votre installation, consultez [Test de votre installation](#testing-your-installation) à la fin de ce document.

## <a name="installing-the-drivers-on-suse-12-and-15"></a>Installation des pilotes sur Suse 12 et 15

> [!NOTE]
> Dans les instructions suivantes, remplacez <SuseVersion> par votre version de Suse. Si vous utilisez Suse Enterprise Linux 15, il s’agira de SLE_15 ou SLE_15_SP1, et de même pour les autres versions. Toutes les versions de PHP ne sont pas disponibles pour toutes les versions de Suse Linux. Consultez `http://download.opensuse.org/repositories/devel:/languages:/php` afin de savoir pour quelles versions de Suse la version par défaut de PHP est disponible, ou `http://download.opensuse.org/repositories/devel:/languages:/php:/` pour savoir quelles autres versions de PHP sont disponibles pour les différentes versions de Suse.

> [!NOTE]
> Les packages pour PHP 7.3 ne sont pas disponibles pour Suse 12. Pour installer PHP 7.1, remplacez l’URL du référentiel ci-dessous par l’URL suivante : `https://download.opensuse.org/repositories/devel:/languages:/php:/php71/<SuseVersion>/devel:languages:php:php71.repo`.
> Pour installer PHP 7.2, remplacez l’URL du référentiel ci-dessous par l’URL suivante : `https://download.opensuse.org/repositories/devel:/languages:/php:/php72/<SuseVersion>/devel:languages:php:php72.repo`.

### <a name="step-1-install-php"></a>Étape 1. Installer PHP
```
sudo su
zypper -n ar -f https://download.opensuse.org/repositories/devel:languages:php/<SuseVersion>/devel:languages:php.repo
zypper --gpg-auto-import-keys refresh
zypper -n install php7 php7-pear php7-devel php7-openssl
```
### <a name="step-2-install-prerequisites"></a>Étape 2. Prérequis à installer
Installez le pilote ODBC pour Suse en suivant les instructions fournies dans la [page d’installation de Linux et macOS](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md).

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Étape 3. Installer les pilotes PHP pour Microsoft SQL Server
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

## <a name="installing-the-drivers-on-macos-sierra-high-sierra-and-mojave"></a>Installation des pilotes sur macOS Sierra, High Sierra et Mojave

Si ce n’est déjà fait, installez brew comme suit :
```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

> [!NOTE]
> Pour installer PHP 7.1 ou 7.2, remplacez php@7.3 respectivement par php@7.1 ou php@7.2 dans les commandes suivantes.

### <a name="step-1-install-php"></a>Étape 1. Installer PHP

```
brew tap
brew tap homebrew/core
brew install php@7.3
```
PHP doit maintenant être présent dans votre chemin. Exécutez `php -v` pour vérifier que vous exécutez la version correcte de PHP. Si PHP n’est pas dans votre chemin, ou s’il ne s’agit pas de la version correcte, exécutez la commande suivante :
```
brew link --force --overwrite php@7.3
```

### <a name="step-2-install-prerequisites"></a>Étape 2. Prérequis à installer
Installez le pilote ODBC pour macOS en suivant les instructions fournies dans la [page d’installation de Linux et macOS](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md). 

Vous devrez peut-être aussi installer les outils de création GNU :
```
brew install autoconf automake libtool
```

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Étape 3. Installer les pilotes PHP pour Microsoft SQL Server
```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
```
### <a name="step-4-install-apache-and-configure-driver-loading"></a>Étape 4. Installer Apache et configurer le chargement du pilote
```
brew install apache2
```
Pour rechercher le fichier de configuration Apache pour votre installation Apache, exécutez 
```
apachectl -V | grep SERVER_CONFIG_FILE
``` 
et remplacez le chemin de `httpd.conf` dans les commandes suivantes :
```
echo "LoadModule php7_module /usr/local/opt/php@7.3/lib/httpd/modules/libphp7.so" >> /usr/local/etc/httpd/httpd.conf
(echo "<FilesMatch .php$>"; echo "SetHandler application/x-httpd-php"; echo "</FilesMatch>";) >> /usr/local/etc/httpd/httpd.conf
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>Étape 5. Redémarrer Apache et tester l’exemple de script
```
sudo apachectl restart
```
Pour tester votre installation, consultez [Test de votre installation](#testing-your-installation) à la fin de ce document.

## <a name="testing-your-installation"></a>Test de votre installation

Pour tester cet exemple de script, créez un fichier nommé testsql.php à la racine de document de votre système. Il s’agit de `/var/www/html/` sur Ubuntu, Red Hat et Debian, de `/srv/www/htdocs` sur SUSE, ou de `/usr/local/var/www` sur macOS. Copiez-y le script suivant, en remplaçant le serveur de base de données, le nom d’utilisateur et le mot de passe comme il convient.
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
