---
title: Installer SQL Server Machine Learning Services (R, Python, Java) sur Linux | Microsoft Docs
description: Cet article décrit comment installer SQL Server Machine Learning Services (R, Python, Java) sur Red Hat et Ubuntu.
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.date: 09/24/2018
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: machine-learning
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 5d10e6646d83d90af60aa748a8265a069d961443
ms.sourcegitcommit: c3e233c13ebb6fbee60723590179da00802c3f3a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2018
ms.locfileid: "47058928"
---
# <a name="install-sql-server-2019-machine-learning-services-r-python-java-on-linux"></a>Installer SQL Server 2019 Machine Learning Services (R, Python, Java) sur Linux

[SQL Server Machine Learning Services](../advanced-analytics/what-is-sql-server-machine-learning.md) s’exécute sur les systèmes d’exploitation Linux à partir de cette version préliminaire de SQL Server 2019. Suivez les étapes décrites dans cet article pour installer l’extension de programmation Java, ou les extensions d’apprentissage pour R et Python. 

Machine learning et extensions de programmation est un module complémentaire pour le moteur de base de données. Bien que vous puissiez [installer le moteur de base de données et les Services Machine Learning simultanément](#install-all), il est recommandé d’installer et configurer le moteur de base de données SQL Server tout d’abord, afin que vous pouvez résoudre les problèmes avant d’ajouter plus d’informations composants. 

Emplacement du package des extensions R, Python et Java sont dans les référentiels de code source SQL Server Linux. Si vous avez déjà configuré installer de référentiels de code source pour le moteur de base de données, vous pouvez exécuter le mssql-mlservices commandes d’installation de package à l’aide de la même inscription de référentiel.

## <a name="prerequisites"></a>Prérequis

+ Système d’exploitation Linux doit être [pris en charge par SQL Server](sql-server-linux-release-notes-2019.md#supported-platforms), il est en cours d’exécution en local ou dans un conteneur Docker.

+ Vous devez disposer d’une instance du moteur de base de données SQL Server 2019 sur : 

   + [Red Hat Enterprise Linux (RHEL)](quickstart-install-connect-red-hat.md)

   + [SUSE Enterprise Linux Server](quickstart-install-connect-suse.md)

   + [Ubuntu](quickstart-install-connect-ubuntu.md)

+ Pour R uniquement, [Microsoft R Open](#mro) pour les packages R mssql-mlsservices. 

<a name="mro"></a>

### <a name="microsoft-r-open-mro"></a>Microsoft R Open (MRO)

Distribution de base de Microsoft de R est un prérequis pour utiliser RevoScaleR, MicrosoftML et autres packages R installés avec les Services Machine Learning.

Les commandes suivantes inscrire le référentiel fournissant MRO. Après l’enregistrement, les commandes pour installer les autres packages R inclut automatiquement MRO comme une dépendance de package.

#### <a name="on-ubuntu"></a>Sur Ubuntu

```bash
# Set the location of the package repo the "prod" directory containing the distribution.
# This example specifies 16.04. Replace with 18.04 if you want that version
wget https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb

# Register the repo
dpkg -i packages-microsoft-prod.deb
```

#### <a name="on-rhel"></a>Sur RHEL

```bash
# Set the location of the package repo at the "prod" directory
rpm -Uvh https://packages.microsoft.com/config/rhel/7/packages-microsoft-prod.rpm
```
#### <a name="on-suse"></a>Sur SUSE

```bash
# Set the location of the package repo
zypper ar -f https://packages.microsoft.com/sles/12/prod packages-microsoft-com
```

## <a name="package-list"></a>Liste des packages

Sur un appareil connecté à internet, les packages sont téléchargés et installés indépendamment le moteur de base de données à l’aide de l’installeur de package pour chaque système d’exploitation. Le tableau suivant décrit tous les packages disponibles, mais pour les installations connecté à internet, vous devez uniquement *un* package R ou Python pour obtenir une combinaison spécifique de fonctionnalités.

| Nom du package | S’applique à | Description |
|--------------|----------|-------------|
|MSSQL-server-extensibilité  | All | Infrastructure d’extensibilité permettant d’exécuter le code R, Python ou Java. |
|MSSQL-server-extensibilité-java | Java | Extension de Java pour le chargement d’un environnement d’exécution Java. Il n’existe aucune des bibliothèques supplémentaires ou des packages pour Java. |
| Microsoft-openmpi  | Python, R | Message passant interface utilisée par les bibliothèques Revo * pour la parallélisation sur Linux. |
| Microsoft-r-open | R | Distribution Open source de R. |
| MSSQL-mlservices-python | Python | Distribution Open source d’Anaconda et Python. |
|MSSQL-mlservices-mlm-py  | Python | Installation complète. Fournit des revoscalepy, microsoftml, de modèles pour l’analyse de sentiments de caractérisation et texte image préformés.| 
|MSSQL-mlservices-mml-py  | Python | Installation partielle. Fournit des revoscalepy, microsoftml. <br/>Exclut les modèles préentraînés. | 
|MSSQL-mlservices-packages-py  | Python | Installation partielle. Fournit des revoscalepy. <br/>Exclut microsoftml et modèles préentraînés. | 
|MSSQL-mlservices-mlm-r  | R | Installation complète. Fournit des RevoScaleR, MicrosoftML, sqlRUtils, olapR, de modèles pour l’analyse de sentiments de caractérisation et texte image préformés.| 
|MSSQL-mlservices-mml-r  | R | Installation partielle. Fournit des RevoScaleR, MicrosoftML, sqlRUtils, olapR. <br/>Exclut les modèles préentraînés.  |
|MSSQL-mlservices-packages-r  | R | Installation partielle. Fournit des RevoScaleR, sqlRUtils, olapR. <br/>Exclut les modèles préentraînés et MicrosoftML. | 

<a name="RHEL"></a>

## <a name="rhel-commands"></a>Commandes RHEL

Installer les *un* package R, ainsi que les *un* package Python et Java si vous souhaitez que cette fonctionnalité. Chaque package R et Python inclut un ensemble de fonctions. Choisissez le package qui fournit l’ensemble de fonctionnalités que vous avez besoin. Packages dépendants sont inclus automatiquement.

> [!Tip]
> Si possible, exécutez `yum clean all` pour actualiser les packages sur le système avant l’installation.

### <a name="example-1----full-installation"></a>Exemple 1 : installation complète 

Inclut open source R et Python, infrastructure d’extensibilité, de microsoft-openmpi, extensions (R, Python, Java), avec les bibliothèques machine learning et modèles préentraînés pour R et Python. Pour R et Python, si vous voulez que quelque chose entre une installation complète et minimale - telles que bibliothèques machine learning, mais sans les modèles préentraînés - remplacer `mssql-mlservices-mml-r-9.4.5*` et `mssql-mlservices-mml-py-9.4.5*` à la place.

```bash
# Install as root or sudo
# Add everything (all R, Python, Java)
# Be sure to include -9.4.5* in mlsservices package names
sudo yum install mssql-mlservices-mlm-py-9.4.5*
sudo yum install mssql-mlservices-mlm-r-9.4.5* 
sudo yum install mssql-server-extensibility-java
```

### <a name="example-2---minimum-installation"></a>Exemple 2 : installation minimale 

Inclut des bibliothèques open source R et Python, infrastructure d’extensibilité, de microsoft-openmpi, core Revo * pour R et Python, extension de Java. Exclut les modèles préentraînés et bibliothèques machine learning pour R et Python. 

```bash
# Install as root or sudo
# Minimum install of R, Python, Java extensions
# Be sure to include -9.4.5* in mlsservices package names
sudo yum install mssql-mlservices-packages-py-9.4.5*
sudo yum install mssql-mlservices-packages-r-9.4.5*
sudo yum install mssql-server-extensibility-java
```

<a name="ubuntu"></a>

## <a name="ubuntu-commands"></a>Commandes d’Ubuntu

Installer les *un* package R, ainsi que les *un* package Python et Java si vous souhaitez que cette fonctionnalité. Chaque package R et Python inclut un ensemble de fonctions. Choisissez le package qui fournit l’ensemble de fonctionnalités que vous avez besoin. Packages dépendants sont inclus automatiquement.

> [!Tip]
> Si possible, exécutez `apt-get update` pour actualiser les packages sur le système avant l’installation. En outre, certaines images docker d’Ubuntu peut-être pas l’option de transport apt https. Pour l’installer, utiliser `apt-get install apt-transport-https`.

### <a name="prerequisite-for-1804"></a>Avant de pouvoir suivre 18.04

L’exécution des bibliothèques R mssql-mlservices sur Ubuntu 18.04 requiert **libpng12** du noyau Linux archive. Ce package n’est plus inclus dans la distribution standard et doit être installé manuellement. Pour obtenir cette bibliothèque, exécutez les commandes suivantes :

```bash
wget https://mirrors.kernel.org/ubuntu/pool/main/libp/libpng/libpng12-0_1.2.54-1ubuntu1_amd64.deb
dpkg -i libpng12-01_1.2.54-1ubuntu1_amd64.deb
```

### <a name="example-1----full-installation"></a>Exemple 1 : installation complète 

Inclut open source R et Python, infrastructure d’extensibilité, de microsoft-openmpi, extensions (R, Python, Java), avec les bibliothèques machine learning et modèles préentraînés pour R et Python. Pour R et Python, si vous voulez que quelque chose entre intégral et au minimum installer - telles que bibliothèques machine learning, mais sans les modèles préentraînés - remplacer par mssql-mlservices-mml-r et mssql-mlservices-mml-py.

```bash
# Install as root or sudo
# Add everything (all R, Python, Java)
# There is no asterisk in this full install
sudo apt-get install mssql-mlservices-mlm-py 
sudo apt-get install mssql-mlservices-mlm-r 
sudo apt-get install mssql-server-extensibility-java
```

### <a name="example-2---minimum-installation"></a>Exemple 2 : installation minimale 

Inclut des bibliothèques open source R et Python, infrastructure d’extensibilité, de microsoft-openmpi, core Revo * pour R et Python, extension de Java. Exclut les modèles préentraînés et bibliothèques machine learning pour R et Python. 

```bash
# Install as root or sudo
# Minimum install of R, Python, Java
# No aasterisk
sudo apt-get install mssql-mlservices-packages-py
sudo apt-get install mssql-mlservices-packages-r
sudo apt-get install mssql-server-extensibility-java
```

<a name="suse"></a>

## <a name="suse-commands"></a>Commandes SUSE

Installer les *un* package R, ainsi que les *un* package Python et Java si vous souhaitez que cette fonctionnalité. Chaque package R et Python inclut un ensemble de fonctions. Choisissez le package qui fournit l’ensemble de fonctionnalités que vous avez besoin. Packages dépendants sont inclus automatiquement. 

### <a name="example-1----full-installation"></a>Exemple 1 : installation complète 

Inclut open source R et Python, infrastructure d’extensibilité, de microsoft-openmpi, extensions (R, Python, Java), avec les bibliothèques machine learning et modèles préentraînés pour R et Python. Pour R et Python, si vous voulez que quelque chose entre une installation complète et minimale - telles que bibliothèques machine learning, mais sans les modèles préentraînés - remplacer `mssql-mlservices-mml-r-9.4.5*` et `mssql-mlservices-mml-py-9.4.5*` à la place.

```bash
# Install as root or sudo
# Add everything (all R, Python, Java)
# Be sure to include -9.4.5* in mlsservices package names
sudo zypper install mssql-mlservices-mlm-py-9.4.5*
sudo zypper install mssql-mlservices-mlm-r-9.4.5* 
sudo zypper install mssql-server-extensibility-java
```

### <a name="example-2---minimum-installation"></a>Exemple 2 : installation minimale 

Inclut des bibliothèques open source R et Python, infrastructure d’extensibilité, de microsoft-openmpi, core Revo * pour R et Python, extension de Java. Exclut les modèles préentraînés et bibliothèques machine learning pour R et Python. 

```bash
# Install as root or sudo
# Minimum install of R, Python, Java extensions
# Be sure to include -9.4.5* in mlsservices package names
sudo zypper install mssql-mlservices-packages-py-9.4.5*
sudo zypper install mssql-mlservices-packages-r-9.4.5*
sudo zypper install mssql-server-extensibility-java
```

## <a name="post-install-config-required"></a>Configuration de post-installation (obligatoire)

Une configuration supplémentaire est essentiellement via les [outil mssql-conf](sql-server-linux-configure-mssql-conf.md).


1. Ajoutez le compte d’utilisateur mssql utilisé pour exécuter le service Launchpad de SQL Server.

  ```bash
  sudo /opt/mssql/bin/mssql-conf setup
  ```

2. Accepter les contrats de licence pour open source R et Python. Il existe plusieurs manières de procéder. Si vous avez précédemment accepté la licence SQL Server et que vous ajoutez à présent les extensions R ou Python, la commande suivante est votre consentement pour les conditions d’utilisation :

  ```bash
  # Run as SUDO or root
  # Use set + EULA 
    sudo /opt/mssql/bin/mssql-conf set EULA accepteulaml Y
  ```

  Un autre flux de travail est que, si vous n’avez pas encore accepté le moteur de base de données SQL Server contrat de licence, le programme d’installation détecte les packages de mssql-mlservices et les invites pour l’acceptation du CLUF lorsque `mssql-conf setup` est exécuté. Pour plus d’informations sur les paramètres de l’accord de licence, consultez [configurer SQL Server avec l’outil mssql-conf](sql-server-linux-configure-mssql-conf.md#mlservices-eula).

3. Redémarrez le service Launchpad de SQL Server et l’instance du moteur de base de données.

  ```bash
  systemctl restart mssql-launchpadd

  systemctl restart mssql-server.service
  ```

4. Activer l’exécution du script externe dans SQL Server Management Studio ou un autre outil qui s’exécute Transact-SQL. 

  ```bash
  EXEC sp_configure 'external scripts enabled', 1 
  RECONFIGURE WITH OVERRIDE 
  ```

## <a name="verify-installation"></a>Vérifier l'installation

Vous trouverez les bibliothèques R (MicrosoftML, RevoScaleR, etc.) dans `/opt/mssql/mlservices/libraries/RServer`.

Vous trouverez les bibliothèques Python (microsoftml et revoscalepy) dans `/opt/mssql/mlservices/libraries/PythonServer`.

À l’aide d’un outil de requête SQL Server, exécutez la commande SQL suivante pour tester l’exécution de R dans SQL Server. Si le script ne s’exécute pas, essayez de redémarrage d’un service, `sudo systemctl restart mssql-server`.

```r
EXEC sp_execute_external_script   
@language =N'R', 
@script=N' 
OutputDataSet <- InputDataSet', 
@input_data_1 =N'SELECT 1 AS hello' 
WITH RESULT SETS (([hello] int not null)); 
GO 
```
 
Exécutez la commande SQL suivante pour tester l’exécution de Python dans SQL Server. 
 
```python
EXEC sp_execute_external_script  
@language =N'Python', 
@script=N' 
OutputDataSet = InputDataSet; 
', 
@input_data_1 =N'SELECT 1 AS hello' 
WITH RESULT SETS (([hello] int not null)); 
GO 
```

<a name="install-all"></a>

## <a name="chained-installation"></a>Installation en chaîne

Vous pouvez installer et configurer le moteur de base de données et les Services Machine Learning dans une procédure en ajoutant des packages R, Python ou Java et des paramètres sur une commande qui installe le moteur de base de données. 

L’exemple suivant est une illustration de « modèle » de quoi ressemble une installation de package combiné à l’aide du Gestionnaire de package Yum :

```bash
sudo yum install -y mssql-sqlserver mssql-server-extensibility-java 
```

L’exemple installe le moteur de base de données et ajoute l’extension de langage Java, qui extrait le package de framework d’extensibilité en tant que dépendance. Tous les packages utilisés dans cet exemple sont trouvent sur le même chemin. Si vous deviez ajouter des packages R, l’inscription pour le référentiel de package de microsoft-r-open seraient nécessaire.

Après l’installation, n’oubliez pas de l’outil mssql-conf permettent de configurer l’ensemble de l’installation et acceptez les contrats de licence. CLUF non acceptée pour les composants R et Python open source est détectées automatiquement, et vous êtes invité à les accepter, ainsi que le CLUF pour SQL Server.

```bash
sudo /opt/mssql/bin/mssql-conf setup MSSQL_PID=Developer 
```

## <a name="unattended-installation"></a>Installation sans assistance

À l’aide de la [installation sans assistance](https://docs.microsoft.com/sql/linux/sql-server-linux-setup?view=sql-server-2017#unattended) pour le moteur de base de données, ajoutez les packages pour mssql-mlservices et le CLUF.

Rappelez-vous que le programme d’installation ou de l’outil mssql-conf vous invite à entrer pour l’acceptation du contrat de licence. Si vous déjà configuré le moteur de base de données SQL Server et accepté la CLUF, utilisez un des paramètres spécifiques à mlservices CLUF pour les distributions de R et Python open source :

```bash
sudo /opt/mssql/bin/mssql-conf setup accept-eula-ml
```

Toutes les permutations possibles de l’acceptation du CLUF sont documentées dans [configurer SQL Server sur Linux avec l’outil mssql-conf](sql-server-linux-configure-mssql-conf.md#mlservices-eula).

## <a name="offline-installation"></a>Installation hors connexion

Suivez le [installation hors connexion](sql-server-linux-setup.md#offline) obtenir des instructions pour obtenir des instructions sur l’installation des packages. Recherchez votre site de téléchargement et puis télécharger les packages spécifiques à l’aide de la liste des packages.

> [!Tip]
> Plusieurs outils de gestion de package de fournissent des commandes qui peuvent vous aider à déterminent les dépendances de package. Pour yum, utilisez `sudo yum deplist [package]`. Pour Ubuntu, utilisez `sudo apt-get install --reinstall --download-only [package name]` suivie `dpkg -I [package name].deb`.


#### <a name="download-site"></a>Site de téléchargement

Vous pouvez télécharger des packages à partir de [ https://packages.microsoft.com/ ](https://packages.microsoft.com/). Tous les packages mlservices pour R, Python et Java sont colocalisés avec le package du moteur de base de données. Version de base pour les packages mlservices est 9.4.5. Les packages micrososoft-r-open sont dans un dossier différent.

#### <a name="rhel7-paths"></a>Chemins d’accès RHEL/7

|||
|--|----|
| packages de MSSQL/mlservices | [https://packages.microsoft.com/rhel/7/mssql-server-preview/](https://packages.microsoft.com/rhel/7/mssql-server-preview/) |
| packages Microsoft-r-open | [https://packages.microsoft.com/rhel/7/prod/](https://packages.microsoft.com/rhel/7/prod/) | 


#### <a name="ubuntu1604-paths"></a>Chemins d’accès/16.04 Ubuntu

|||
|--|----|
| packages de MSSQL/mlservices | [https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/) |
| packages Microsoft-r-open | [https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/) | 

#### <a name="sles12-paths"></a>Chemins d’accès du 12/SLES

|||
|--|----|
| packages de MSSQL/mlservices | [ https://packages.microsoft.com/sles/12/mssql-server-preview/](https://packages.microsoft.com/sles/12/mssql-server-preview/) |
| packages Microsoft-r-open | [https://packages.microsoft.com/sles/12/prod/](https://packages.microsoft.com/sles/12/prod/) | 

#### <a name="package-list"></a>Liste des packages

Selon les extensions que vous souhaitez utiliser, télécharger les packages nécessaires pour une langue spécifique. Noms de fichiers incluent des informations sur la plateforme, mais les noms de fichier ci-dessous doivent être suffisamment proches pour vous permettre de déterminer les fichiers à obtenir.

```
# Core packages 
mssql-server-15.0.1000
mssql-server-extensibility-15.0.1000

# Java
mssql-server-extensibility-java-15.0.1000

# R
microsoft-openmpi-3.0.0
microsoft-r-open-foreachiterators-3.4.4
microsoft-r-open-mkl-3.4.4
microsoft-r-open-mro-3.4.4
mssql-mlservices-packages-r-9.4.5
mssql-mlservices-mlm-r-9.4.5
mssql-mlservices-mml-r-9.4.5

# Python
microsoft-openmpi-3.0.0
mssql-mlservices-python-9.4.5
mssql-mlservices-packages-py-9.4.5
mssql-mlservices-mlm-py-9.4.5
mssql-mlservices-mml-py-9.4.5 
```

## <a name="add-more-rpython-packages"></a>Ajoutez d’autres packages R/Python 
 
Vous pouvez installer d’autres packages R et Python et les utiliser dans un script qui s’exécute sur SQL Server 2019.

### <a name="r-packages"></a>Packages R 
 
1. Démarrer une session R.

   ```r
   # sudo /opt/mssql/mlservices/bin/R/R 
   ```

2. Installer un package R appelé [glue](https://mran.microsoft.com/package/glue) pour tester l’installation du package.

   ```r
   # install.packages("glue",lib="/opt/mssql/mlservices/libraries/RServer") 
   ```
   Vous pouvez également installer un package R à partir de la ligne de commande 

   ```r
   # sudo /opt/mssql/mlservices/bin/R/R CMD INSTALL -l /opt/mssql/mlservices/libraries/RServer glue_1.1.1.tar.gz 
   ```

3. Importer le package R dans [sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

   ```r
   EXEC sp_execute_external_script  
   @language = N'R', 
   @script = N'library(glue)' 
   ```

### <a name="python-packages"></a>Packages Python 
 
1. Installer un package Python appelé [httpie](https://httpie.org/) à l’aide de pip. 

   ```python
   # sudo /opt/mssql/mlservices/bin/python/python -m pip install httpie 
   ``` 

2. Importer le package Python dans [sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).
 
   ```python
   EXEC sp_execute_external_script  
   @language = N'Python',  
   @script = N'import httpie' 
   ```

## <a name="limitations-in-ctp-20"></a>Limitations dans CTP 2.0

Les limitations suivantes existent dans cette version CTP.

+ Actuellement, l’authentification implicite n’est pas disponible dans Machine Learning Services sur Linux pour l’instant, ce qui signifie que vous ne peut pas se connecter au serveur à partir d’un script en cours d’exécution de R ou Python pour accéder aux données ou autres ressources. 

+ [CREATE EXTERNAL LIBRARY](../t-sql/statements/create-external-library-transact-sql.md) (pour le stockage des packages R dans la base de données) n’est actuellement pas disponible sur Linux et ne prend pas en charge Python.  

### <a name="resource-governance"></a>Gouvernance des ressources

Il existe une parité entre Linux et Windows pour [gouvernance des ressources](../t-sql/statements/create-external-resource-pool-transact-sql.md) pour les pools de ressources externes, mais les statistiques de [sys.dm_resource_governor_external_resource_pools](../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pools.md) ont actuellement unités différentes sur Linux. Unités sont alignées dans une prochaine version CTP.
 
| Nom de colonne   | Description | Valeur sur Linux | 
|---------------|--------------|---------------|
|peak_memory_kb | La quantité maximale de mémoire utilisée pour le pool de ressources. | Sur Linux, cette statistique provient du sous-système de mémoire « cgroups », où la valeur est memory.max_usage_in_bytes |
|write_io_count | Total d’écriture e/s émises depuis que les statistiques du gouverneur de ressources ont été réinitialisées. | Sur Linux, cette statistique est alimentée à partir du sous-système de blkio « cgroups », où la valeur sur la ligne de l’écriture est blkio.throttle.io_serviced | 
|read_io_count | Total de lecture e/s émises depuis que les statistiques du gouverneur de ressources ont été réinitialisées. | Sur Linux, cette statistique est alimentée à partir du sous-système de blkio « cgroups », où la valeur sur la ligne de lecture est blkio.throttle.io_serviced | 
|total_cpu_kernel_ms | Le temps processeur cumulé utilisateur noyau en millisecondes depuis que les statistiques du gouverneur de ressources ont été réinitialisées. | Sur Linux, cette statistique est alimentée à partir du sous-système de cpuacct « cgroups », où la valeur sur la ligne de l’utilisateur est cpuacct.stat |  
|total_cpu_user_ms | Temps utilisateur processeur cumulé en millisecondes depuis que les statistiques du gouverneur de ressources ont été réinitialisées.| Sur Linux, cette statistique est alimentée à partir du sous-système de cpuacct « cgroups », où la valeur de la valeur de ligne du système est cpuacct.stat | 
|active_processes_count | Le nombre de processus externes en cours d’exécution au moment de la demande.| Sur Linux, cette statistique est alimentée à partir du sous-système de PID GGroups, où la valeur est pids.current | 

## <a name="next-steps"></a>Étapes suivantes

Aux développeurs R peuvent démarrer avec des exemples simples et apprendre les bases du fonctionne de R avec SQL Server. Pour votre prochaine étape, consultez les liens suivants :

+ [Didacticiel : Exécuter R dans T-SQL](../advanced-analytics/tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)
+ [Didacticiel : De base de données analytique pour les développeurs R](../advanced-analytics/tutorials/sqldev-in-database-r-for-sql-developers.md)

Les développeurs Python peuvent apprendre à utiliser Python avec SQL Server en suivant ces didacticiels :

+ [Didacticiel : Exécuter Python dans T-SQL](../advanced-analytics/tutorials/run-python-using-t-sql.md)
+ [Didacticiel : De base de données analytique pour les développeurs Python](../advanced-analytics/tutorials/sqldev-in-database-python-for-sql-developers.md)

Pour afficher des exemples d’apprentissage qui sont basées sur des scénarios réels, consultez [d’apprentissage didacticiels](../advanced-analytics/tutorials/machine-learning-services-tutorials.md).
