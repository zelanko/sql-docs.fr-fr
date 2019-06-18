---
title: Installation de Microsoft ODBC Driver for SQL Server sur Linux et macOS | Microsoft Docs
ms.custom: ''
ms.date: 12/05/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- driver, installing
ms.assetid: f78b81ed-5214-43ec-a600-9bfe51c5745a
author: MightyPen
ms.author: v-jizho2
manager: kenvh
ms.openlocfilehash: 3550e17c8f4d6384ceafabb77aa9ca70cd80c44b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63190667"
---
# <a name="installing-the-microsoft-odbc-driver-for-sql-server-on-linux-and-macos"></a>Installation de Microsoft ODBC Driver for SQL Server sur Linux et macOS
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Cet article explique comment installer [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur Linux et macOS, ainsi que les outils en ligne de commande facultatifs pour SQL Server (`bcp` et `sqlcmd`) et les en-têtes de développement unixODBC.

## <a name="microsoft-odbc-driver-17-for-sql-server"></a>Microsoft ODBC Driver 17 for SQL Server 

> [!IMPORTANT]
> Si vous avez installé le package `msodbcsql` v17 qui n’a pas été disponible longtemps, vous devez le supprimer avant d’installer le package `msodbcsql17`. Cette opération évitera les conflits. Le package `msodbcsql17` peut être installé côte à côte avec le package `msodbcsql` v13.

### <a name="debian-8-and-9"></a>Debian 8 et 9
```
sudo su 
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -

#Download appropriate package for the OS version
#Choose only ONE of the following, corresponding to your OS version

#Debian 8
curl https://packages.microsoft.com/config/debian/8/prod.list > /etc/apt/sources.list.d/mssql-release.list

#Debian 9
curl https://packages.microsoft.com/config/debian/9/prod.list > /etc/apt/sources.list.d/mssql-release.list

exit
sudo apt-get update
sudo ACCEPT_EULA=Y apt-get install msodbcsql17
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y apt-get install mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo apt-get install unixodbc-dev
```

### <a name="redhat-enterprise-server-6-and-7"></a>RedHat Enterprise Server 6 et 7
```
sudo su

#Download appropriate package for the OS version
#Choose only ONE of the following, corresponding to your OS version

#RedHat Enterprise Server 6
curl https://packages.microsoft.com/config/rhel/6/prod.repo > /etc/yum.repos.d/mssql-release.repo

#RedHat Enterprise Server 7
curl https://packages.microsoft.com/config/rhel/7/prod.repo > /etc/yum.repos.d/mssql-release.repo

exit
sudo yum remove unixODBC-utf16 unixODBC-utf16-devel #to avoid conflicts
sudo ACCEPT_EULA=Y yum install msodbcsql17
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y yum install mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo yum install unixODBC-devel
```

### <a name="suse-linux-enterprise-server-11sp4-12-and-15"></a>SUSE Linux Enterprise Server 11SP4, 12 et 15

```
sudo su

#Download appropriate package for the OS version
#Choose only ONE of the following, corresponding to your OS version

#SUSE Linux Enterprise Server 11 SP4
zypper ar https://packages.microsoft.com/config/sles/11/prod.repo

#SUSE Linux Enterprise Server 12
zypper ar https://packages.microsoft.com/config/sles/12/prod.repo

#SUSE Linux Enterprise Server 15
zypper ar https://packages.microsoft.com/config/sles/15/prod.repo
SUSEConnect -p sle-module-legacy/15/x86_64

exit
sudo ACCEPT_EULA=Y zypper install msodbcsql17
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y zypper install mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo zypper install unixODBC-devel
``` 

### <a name="ubuntu-1404-1604-1710-and-1804"></a>Ubuntu 14.04, 16.04, 17.10 et 18.04
```
sudo su 
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -

#Download appropriate package for the OS version
#Choose only ONE of the following, corresponding to your OS version

#Ubuntu 14.04
curl https://packages.microsoft.com/config/ubuntu/14.04/prod.list > /etc/apt/sources.list.d/mssql-release.list

#Ubuntu 16.04
curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list > /etc/apt/sources.list.d/mssql-release.list

#Ubuntu 18.04
curl https://packages.microsoft.com/config/ubuntu/18.04/prod.list > /etc/apt/sources.list.d/mssql-release.list

#Ubuntu 18.10
curl https://packages.microsoft.com/config/ubuntu/18.10/prod.list > /etc/apt/sources.list.d/mssql-release.list

exit
sudo apt-get update
sudo ACCEPT_EULA=Y apt-get install msodbcsql17
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y apt-get install mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo apt-get install unixodbc-dev
```
> [!NOTE]
> - Le pilote version 17.2 ou ultérieure est requise pour la prise en charge d’Ubuntu 18.04.
> - Le pilote version 17.3 ou ultérieure est requise pour la prise en charge d’Ubuntu 18.10.   

### <a name="os-x-1011-el-capitan-macos-1012-sierra-macos-1013-high-sierra-and-macos-1014-mojave"></a>OS X 10.11 (El Capitan), macOS 10.12 (Sierra), macOS 10.13 (High Sierra) et macOS 10.14 (Mojave)

```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
brew tap microsoft/mssql-release https://github.com/Microsoft/homebrew-mssql-release
brew update
brew install msodbcsql17 mssql-tools
```

## <a name="microsoft-odbc-driver-131-for-sql-server"></a>Microsoft ODBC Driver 13.1 for SQL Server 

### <a name="debian-8"></a>Debian 8
```
sudo su 
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
curl https://packages.microsoft.com/config/debian/8/prod.list > /etc/apt/sources.list.d/mssql-release.list
exit
sudo apt-get update
sudo ACCEPT_EULA=Y apt-get install msodbcsql
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y apt-get install mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo apt-get install unixodbc-dev
```

### <a name="redhat-enterprise-server-6"></a>RedHat Enterprise Server 6
```
sudo su
curl https://packages.microsoft.com/config/rhel/6/prod.repo > /etc/yum.repos.d/mssql-release.repo
exit
sudo yum remove unixODBC-utf16 unixODBC-utf16-devel #to avoid conflicts
sudo ACCEPT_EULA=Y yum install msodbcsql
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y yum install mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo yum install unixODBC-devel
```

### <a name="redhat-enterprise-server-7"></a>RedHat Enterprise Server 7
```
sudo su
curl https://packages.microsoft.com/config/rhel/7/prod.repo > /etc/yum.repos.d/mssql-release.repo
exit
sudo yum remove unixODBC-utf16 unixODBC-utf16-devel #to avoid conflicts
sudo ACCEPT_EULA=Y yum install msodbcsql
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y yum install mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo yum install unixODBC-devel
```

### <a name="suse-linux-enterprise-server-11"></a>SUSE Linux Enterprise Server 11

```
sudo su
zypper ar https://packages.microsoft.com/config/sles/11/prod.repo
exit
sudo ACCEPT_EULA=Y zypper install msodbcsql
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y zypper install mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo zypper install unixODBC-devel
``` 

### <a name="suse-linux-enterprise-server-12"></a>SUSE Linux Enterprise Server 12

```
sudo su
zypper ar https://packages.microsoft.com/config/sles/12/prod.repo
exit
sudo ACCEPT_EULA=Y zypper install msodbcsql
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y zypper install mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo zypper install unixODBC-devel
``` 

### <a name="ubuntu-1510"></a>Ubuntu 15.10
```
sudo su 
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
curl https://packages.microsoft.com/config/ubuntu/15.10/prod.list > /etc/apt/sources.list.d/mssql-release.list
exit
sudo apt-get update
sudo ACCEPT_EULA=Y apt-get install msodbcsql
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y apt-get install mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo apt-get install unixodbc-dev
```

### <a name="ubuntu-1604"></a>Ubuntu 16.04
```
sudo su 
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list > /etc/apt/sources.list.d/mssql-release.list
exit
sudo apt-get update
sudo ACCEPT_EULA=Y apt-get install msodbcsql
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y apt-get install mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo apt-get install unixodbc-dev
```

### <a name="ubuntu-1610"></a>Ubuntu 16.10
```
sudo su 
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
curl https://packages.microsoft.com/config/ubuntu/16.10/prod.list > /etc/apt/sources.list.d/mssql-release.list
exit
sudo apt-get update
sudo ACCEPT_EULA=Y apt-get install msodbcsql
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y apt-get install mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo apt-get install unixodbc-dev
```

### <a name="os-x-1011-el-capitan-and-macos-1012-sierra"></a>OS X 10.11 (El Capitan) et macOS 10.12 (Sierra)

```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
brew tap microsoft/mssql-release https://github.com/Microsoft/homebrew-mssql-release
brew update
brew install msodbcsql@13.1.9.2 mssql-tools@14.0.6.0
```

## <a name="microsoft-odbc-driver-13-for-sql-server"></a>Microsoft ODBC Driver 13 for SQL Server

### <a name="redhat-enterprise-server-6"></a>RedHat Enterprise Server 6
```
sudo su
curl https://packages.microsoft.com/config/rhel/6/prod.repo > /etc/yum.repos.d/mssql-release.repo
exit
sudo yum update
sudo yum remove unixODBC #to avoid conflicts
sudo ACCEPT_EULA=Y yum install msodbcsql-13.0.1.0-1 mssql-tools-14.0.2.0-1
sudo yum install unixODBC-utf16-devel #this step is optional but recommended*
#Create symlinks for tools
ln -sfn /opt/mssql-tools/bin/sqlcmd-13.0.1.0 /usr/bin/sqlcmd 
ln -sfn /opt/mssql-tools/bin/bcp-13.0.1.0 /usr/bin/bcp
```

### <a name="redhat-enterprise-server-7"></a>RedHat Enterprise Server 7
```
sudo su
curl https://packages.microsoft.com/config/rhel/7/prod.repo > /etc/yum.repos.d/mssql-release.repo
exit
sudo yum update
sudo yum remove unixODBC #to avoid conflicts
sudo ACCEPT_EULA=Y yum install msodbcsql-13.0.1.0-1 mssql-tools-14.0.2.0-1
sudo yum install unixODBC-utf16-devel #this step is optional but recommended*
#Create symlinks for tools
ln -sfn /opt/mssql-tools/bin/sqlcmd-13.0.1.0 /usr/bin/sqlcmd 
ln -sfn /opt/mssql-tools/bin/bcp-13.0.1.0 /usr/bin/bcp
```

### <a name="ubuntu-1510"></a>Ubuntu 15.10
```
sudo su 
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
curl https://packages.microsoft.com/config/ubuntu/15.10/prod.list > /etc/apt/sources.list.d/mssql-release.list
exit
sudo apt-get update
sudo ACCEPT_EULA=Y apt-get install msodbcsql=13.0.1.0-1 mssql-tools=14.0.2.0-1
sudo apt-get install unixodbc-dev-utf16 #this step is optional but recommended*
#Create symlinks for tools
ln -sfn /opt/mssql-tools/bin/sqlcmd-13.0.1.0 /usr/bin/sqlcmd 
ln -sfn /opt/mssql-tools/bin/bcp-13.0.1.0 /usr/bin/bcp
```

### <a name="ubuntu-1604"></a>Ubuntu 16.04
```
sudo su 
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list > /etc/apt/sources.list.d/mssql-release.list
exit
sudo apt-get update
sudo ACCEPT_EULA=Y apt-get install msodbcsql=13.0.1.0-1 mssql-tools=14.0.2.0-1
sudo apt-get install unixodbc-dev-utf16 #this step is optional but recommended*
#Create symlinks for tools
ln -sfn /opt/mssql-tools/bin/sqlcmd-13.0.1.0 /usr/bin/sqlcmd 
ln -sfn /opt/mssql-tools/bin/bcp-13.0.1.0 /usr/bin/bcp
```

### <a name="suse-linux-enterprise-server-12"></a>SUSE Linux Enterprise Server 12

```
sudo su 
zypper ar https://packages.microsoft.com/config/sles/12/prod.repo 
zypper update 
sudo ACCEPT_EULA=Y zypper install msodbcsql-13.0.1.0-1 mssql-tools-14.0.2.0-1
zypper install unixODBC-utf16-devel
#Create symlinks for tools
ln -sfn /opt/mssql-tools/bin/sqlcmd-13.0.1.0 /usr/bin/sqlcmd 
ln -sfn /opt/mssql-tools/bin/bcp-13.0.1.0 /usr/bin/bcp
```

### <a name="offline-installation"></a>Installation hors connexion
Si vous préférez/nécessitez que [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 13 soit installé sur un ordinateur sans connexion Internet, vous devez résoudre manuellement les dépendances de package. [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 13 a les dépendances directes suivantes :
- Ubuntu : libc6 (>= 2.21), libstdc++6 (>= 4.9), libkrb5-3, libcurl3, openssl, debconf (>= 0.5), unixodbc (>= 2.3.1-1)
- Red Hat : ```glibc, e2fsprogs, krb5-libs, openssl, unixODBC```
- SuSE : ```glibc, libuuid1, krb5, openssl, unixODBC```

Chacun de ces packages a ses propres dépendances, qui peuvent ou non être présentes sur le système. Pour une solution générale à ce problème, reportez-vous à la documentation du gestionnaire de package de votre distribution : [Redhat](https://wiki.centos.org/HowTos/CreateLocalRepos), [Ubuntu](https://unix.stackexchange.com/questions/87130/how-to-quickly-create-a-local-apt-repository-for-random-packages-using-a-debian) et [SUSE](https://en.opensuse.org/Portal:Zypper)

Il est également courant de télécharger manuellement tous les packages dépendants et de les placer ensemble sur l’ordinateur d’installation, puis d’installer manuellement chaque package tour à tour, en terminant par le package [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 13.

#### <a name="redhat-linux-enterprise-server-7"></a>Redhat Linux Enterprise Server 7
  - Téléchargez le dernier package `msodbcsql` `.rpm` ici : https://packages.microsoft.com/rhel/7/prod/
  - Installez les dépendances et le pilote.
  
```
yum install glibc e2fsprogs krb5-libs openssl unixODBC unixODBC-devel #install dependencies
sudo rpm -i  msodbcsql-13.1.X.X-X.x86_64.rpm #install the Driver
```

#### <a name="ubuntu-1604"></a>Ubuntu 16.04
- Téléchargez le dernier package `msodbcsql` `.deb` ici : https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/msodbcsql/ 
- Installez les dépendances et le pilote. 

```
sudo apt-get install libc6 libstdc++6 libkrb5-3 libcurl3 openssl debconf unixodbc unixodbc-dev #install dependencies
sudo dpkg -i msodbcsql_13.1.X.X-X_amd64.deb #install the Driver
```

#### <a name="suse-linux-enterprise-server-12"></a>SUSE Linux Enterprise Server 12
- Téléchargez le dernier package `msodbcsql` `.rpm` ici : https://packages.microsoft.com/sles/12/prod/
- Installez les dépendances et le pilote.

```
zypper install glibc, libuuid1, krb5, openssl, unixODBC unixODBC-devel #install dependencies
sudo rpm -i  msodbcsql-13.1.X.X-X.x86_64.rpm #install the Driver
```

Une fois l’installation du package terminée, vous pouvez vérifier que [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 13 peut trouver toutes ses dépendances en exécutant ldd et en inspectant sa sortie pour déterminer les bibliothèques manquantes :
```
ldd /opt/microsoft/msodbcsql/lib64/libmsodbcsql-*
```
  
## <a name="microsoft-odbc-driver-11-for-sql-server-on-linux"></a>Microsoft ODBC Driver 11 for SQL Server sur Linux

Avant d’utiliser le pilote, installez le Gestionnaire de pilotes unixODBC. Pour plus d’informations, consultez [Installation du Gestionnaire de pilotes](../../../connect/odbc/linux-mac/installing-the-driver-manager.md).

**Étapes d’installation**  

> [!IMPORTANT]  
> Ces instructions font référence à `msodbcsql-11.0.2270.0.tar.gz`, qui est le fichier d’installation pour Red Hat Linux. Si vous installez la préversion pour SUSE Linux, le nom du fichier est `msodbcsql-11.0.2260.0.tar.gz`.  
  
Pour installer le pilote :

1.  Assurez-vous de disposer d’une autorisation d’accès à la racine.  

2.  Accédez au répertoire où le téléchargement a placé le fichier `msodbcsql-11.0.2270.0.tar.gz`. Assurez-vous de disposer du fichier \*.tar.gz correspondant à votre version de Linux. Pour extraire les fichiers, exécutez la commande suivante : `tar xvzf msodbcsql-11.0.2270.0.tar.gz`.  
  
3.  Accédez au répertoire `msodbcsql-11.0.2270.0`, où devrait se trouver un fichier nommé **install.sh**.  
  
4.  Pour afficher la liste des options d’installation disponibles, exécutez la commande suivante : **./install.sh**.  
  
5.  Effectuez une sauvegarde de **odbcinst.ini**. L’installation du pilote met à jour **odbcinst.ini**. odbcinst.ini contient la liste des pilotes enregistrés auprès du Gestionnaire de pilotes unixODBC. Pour découvrir l’emplacement du fichier odbcinst.ini sur votre ordinateur, exécutez la commande suivante : ```odbc_config --odbcinstini```.  
  
6.  Avant d’installer le pilote, exécutez la commande suivante : `./install.sh verify`. La sortie de `./install.sh verify` indique si votre ordinateur dispose des logiciels requis pour prendre en charge le pilote ODBC sur Linux.  
  
7.  Quand vous êtes prêt à installer le pilote ODBC sur Linux, exécutez la commande suivante : `./install.sh install`. Si vous devez spécifier une commande d’installation (`bin-dir` ou `lib-dir`), spécifiez-la après l’option **install**.  
  
8.  Après avoir examiné le contrat de licence, tapez **YES** pour poursuivre l’installation.  
  
L’installation place le pilote dans `/opt/microsoft/msodbcsql/11.0.2270.0`. Le pilote et ses fichiers associés doivent être dans `/opt/microsoft/msodbcsql/11.0.2270.0`.  
  
Pour vérifier que le pilote Microsoft ODBC sur Linux a été inscrit correctement, exécutez la commande suivante : ```odbcinst -q -d -n "ODBC Driver 11 for SQL Server"```.  
  
La page de blog[Use Existing MSDN C++ ODBC Samples for the ODBC Driver on Linux](https://blogs.msdn.com/b/sqlblog/archive/2012/01/26/use-existing-msdn-c-odbc-samples-for-microsoft-linux-odbc-driver.aspx) présente un exemple de code qui se connecte à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à l’aide du pilote ODBC sur Linux.  
  
**Désinstallation**  
  
Vous pouvez désinstaller le pilote ODBC 11 sur Linux, en exécutant les commandes suivantes :  
  
1.  `rm -f /usr/bin/sqlcmd`
  
2.  `rm -f /usr/bin/bcp`  
  
3.  `rm -rf /opt/microsoft/msodbcsql`  
  
4.  `odbcinst -u -d -n "ODBC Driver 11 for SQL Server"`
  
## <a name="troubleshooting-connection-problems"></a>Résolution des problèmes de connexion  
Si vous ne parvenez pas à établir de connexion à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à l’aide du pilote ODBC, utilisez les informations suivantes pour identifier le problème.  
  
Le problème de connexion le plus courant est dû à l’installation de deux copies du Gestionnaire de pilotes UnixODBC. Recherchez /usr for libodbc\*.so\*. Si plusieurs versions du fichier apparaissent, vous avez (probablement) plusieurs gestionnaires de pilotes installés. Votre application risque alors d’utiliser la mauvaise version.
  
Activez le journal de connexion en modifiant votre fichier `/etc/odbcinst.ini` afin qu’il contienne la section suivante avec les éléments ci-après :

```
[ODBC]
Trace = Yes
TraceFile = (path to log file, or /dev/stdout to output directly to the terminal)
```  
  
Si vous obtenez un autre échec de connexion et que vous ne voyez pas de fichier journal, il existe (peut-être) deux copies du Gestionnaire de pilotes sur votre ordinateur. Sinon, la sortie du journal doit ressembler à ce qui suit :  
  
```  
[ODBC][28783][1321576347.077780][SQLDriverConnectW.c][290]  
        Entry:  
            Connection = 0x17c858e0  
            Window Hdl = (nil)  
            Str In = [DRIVER={ODBC Driver 13 for SQL Server};SERVER={contoso.com};Trusted_Connection={YES};WSID={mydb.contoso.com};AP...][length = 139 (SQL_NTS)]  
            Str Out = (nil)  
            Str Out Max = 0  
            Str Out Ptr = (nil)  
            Completion = 0  
        UNICODE Using encoding ASCII 'UTF8' and UNICODE 'UTF16LE'  
```  
  
Si l’encodage de caractères ASCII n’est pas UTF-8, par exemple : 
  
```  
UNICODE Using encoding ASCII 'ISO8859-1' and UNICODE 'UCS-2LE'  
```  
  
Il existe plusieurs gestionnaires de pilotes installés et votre application n’utilise pas le bon, ou le gestionnaire de pilotes n’a pas été créé correctement.  
  
Pour plus d’informations sur la résolution des échecs de connexion, consultez :  
  
-   [Procédure de résolution des problèmes de connectivité SQL](https://blogs.msdn.com/b/sql_protocols/archive/2008/04/30/steps-to-troubleshoot-connectivity-issues.aspx)  
  
-   [Résolution des problèmes de connectivité SQL Server 2005 - 1re partie](https://blogs.msdn.com/b/sql_protocols/archive/2005/10/22/sql-server-2005-connectivity-issue-troubleshoot-part-i.aspx)  
  
-   [Résolution des problèmes de connectivité dans SQL Server 2008 avec le tampon en anneau de connectivité](https://blogs.msdn.com/b/sql_protocols/archive/2008/05/20/connectivity-troubleshooting-in-sql-server-2008-with-the-connectivity-ring-buffer.aspx)  
  
-   [Résolution des problèmes d’authentification SQL Server](https://blogs.msdn.com/b/sqlsecurity/archive/2010/03/29/sql-server-authentication-troubleshooter.aspx)  
  
-   [Détails des erreurs (https://www.microsoft.com/products/ee/transform.aspx?ProdName=Microsoft+SQL+Server&EvtSrc=MSSQLServer&EvtID=11001)](https://www.microsoft.com/products/ee/transform.aspx?ProdName=Microsoft+SQL+Server&EvtSrc=MSSQLServer&EvtID=001)  
  
    Le numéro d’erreur spécifié dans l’URL (11001) doit être modifié pour correspondre à l’erreur que vous voyez.  
  
## <a name="driver-files"></a>Fichiers de pilote
Le pilote ODBC sur Linux et MacOS est constitué des composants suivants :

### <a name="linux"></a>Linux

|Composant|Description|  
|---------------|-----------------|  
|libmsodbcsql-17.X.so.X.X ou libmsodbcsql-13.X.so.X.X|Fichier bibliothèque dynamique (`so`) d’objets partagés contenant l’ensemble des fonctionnalités du pilote. Ce fichier est installé dans `/opt/microsoft/msodbcsql17/lib64/` pour Driver 17 et dans `/opt/microsoft/msodbcsql/lib64/` pour Driver 13.|  
|`msodbcsqlr17.rll` ou `msodbcsqlr13.rll`|Fichier de ressources qui accompagne la bibliothèque du pilote. Ce fichier est installé dans `[driver .so directory]../share/resources/en_US/`| 
|msodbcsql.h|Fichier d’en-tête qui contient toutes les nouvelles définitions nécessaires à l’utilisation du pilote.<br /><br /> **Remarque :**  vous ne pouvez pas référencer msodbcsql.h et odbcss.h dans le même programme.<br /><br /> msodbcsql.h est installé dans `/opt/microsoft/msodbcsql17/include/` pour Driver 17 et dans `/opt/microsoft/msodbcsql/include/` pour Driver 13. |
|LICENSE.txt|Fichier texte qui contient les termes du contrat de licence utilisateur final. Ce fichier est placé dans `/usr/share/doc/msodbcsql17/` pour Driver 17 et dans `/usr/share/doc/msodbcsql/` pour Driver 13.|
|RELEASE_NOTES|Fichier texte qui contient les notes de publication. Ce fichier est placé dans `/usr/share/doc/msodbcsql17/` pour Driver 17 et dans `/usr/share/doc/msodbcsql/` pour Driver 13.|


### <a name="macos"></a>MacOS

|Composant|Description|  
|---------------|-----------------|  
|libmsodbcsql.17.dylib ou libmsodbcsql.13.dylib|Fichier de bibliothèque dynamique (`dylib`) contenant l’ensemble des fonctionnalités du pilote. Ce fichier est installé dans `/usr/local/lib/`.|  
|`msodbcsqlr17.rll` ou `msodbcsqlr13.rll`|Fichier de ressources qui accompagne la bibliothèque du pilote. Ce fichier est installé dans `[driver .dylib directory]../share/msodbcsql17/resources/en_US/` pour Driver 17 et dans `[driver .dylib directory]../share/msodbcsql/resources/en_US/` pour Driver 13. | 
|msodbcsql.h|Fichier d’en-tête qui contient toutes les nouvelles définitions nécessaires à l’utilisation du pilote.<br /><br /> **Remarque :**  vous ne pouvez pas référencer msodbcsql.h et odbcss.h dans le même programme.<br /><br /> msodbcsql.h est installé dans `/usr/local/include/msodbcsql17/` pour Driver 17 et dans `/usr/local/include/msodbcsql/` pour Driver 13. |
|LICENSE.txt|Fichier texte qui contient les termes du contrat de licence utilisateur final. Ce fichier est placé dans `/usr/local/share/doc/msodbcsql17/` pour Driver 17 et dans `/usr/local/share/doc/msodbcsql/` pour Driver 13. |
|RELEASE_NOTES|Fichier texte qui contient les notes de publication. Ce fichier est placé dans `/usr/local/share/doc/msodbcsql17/` pour Driver 17 et dans `/usr/local/share/doc/msodbcsql/` pour Driver 13. |

## <a name="resource-file-loading"></a>Chargement du fichier de ressources

Le pilote doit charger le fichier de ressources pour pouvoir fonctionner. Ce fichier est appelé `msodbcsqlr17.rll` ou `msodbcsqlr13.rll` selon la version du pilote. L’emplacement du fichier `.rll` est relatif à l’emplacement du pilote lui-même (`so` ou `dylib`), comme indiqué dans le tableau ci-dessus. Depuis la version 17.1, le pilote peut aussi essayer de charger le fichier `.rll` à partir du répertoire par défaut si le chargement échoue à partir du chemin d’accès relatif. Les chemins de fichier de ressources par défaut sont :

Linux : `/opt/microsoft/msodbcsql17/share/resources/en_US/`

MacOS : `/usr/local/share/msodbcsql17/resources/en_US/`


  
## <a name="see-also"></a>Voir aussi

[Installation du Gestionnaire de pilotes](../../../connect/odbc/linux-mac/installing-the-driver-manager.md)

[Notes de publication](../../../connect/odbc/linux-mac/release-notes-odbc-sql-server-linux-mac.md)

[Configuration système requise](../../../connect/odbc/linux-mac/system-requirements.md)
