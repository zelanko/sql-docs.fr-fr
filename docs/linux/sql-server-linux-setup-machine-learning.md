---
title: Installer SQL Server Machine Learning Services (Python, R) sur Linux
description: 'Découvrez comment installer SQL Server Machine Learning Services (Python et R) sur Linux : Red Hat, Ubuntu et SUSE.'
author: dphansen
ms.author: davidph
ms.reviewer: vanto
manager: cgronlun
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: machine-learning
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 4f32f4219e438a3f6dc390d11b50e6487c47ee49
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73531251"
---
# <a name="install-sql-server-machine-learning-services-python-and-r-on-linux"></a>Installer SQL Server Machine Learning Services (Python et R) sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Cet article explique comment installer [SQL Server Machine Learning Services](../advanced-analytics/index.yml) sur Linux. Vous pouvez utiliser Machine Learning Services pour exécuter des scripts Python et R en base de données.

Les distributions Linux suivantes sont prises en charge :

- Red Hat Enterprise Linux (RHEL)
- SLES (SUSE Linux Enterprise Server)
- Ubuntu

Machine Learning Services est un module complémentaire de fonctionnalités du moteur de base de données. Bien que vous puissiez [installer le moteur de base de données et Machine Learning Services simultanément](#install-all), il est recommandé d’installer et de configurer le moteur de base de données SQL Server en premier afin de pouvoir résoudre les problèmes avant d’ajouter d’autres composants. 

Les packages pour les extensions Python et R se trouvent dans les dépôts des sources Linux pour SQL Server. Si vous avez déjà configuré des référentiels source pour l’installation du moteur de base de données, vous pouvez exécuter les commandes d’installation du package **mssql-mlservices** à l’aide de la même inscription de référentiel.

Machine Learning Services est également pris en charge sur les conteneurs Linux. Nous ne fournissons pas de conteneurs prédéfinis avec Machine Learning Services, mais vous pouvez en créer un à partir des conteneurs SQL Server à l’aide [d’un exemple de modèle disponible sur GitHub](https://github.com/Microsoft/mssql-docker/tree/master/linux/preview/examples/mssql-mlservices).

Machine Learning Services étant installé par défaut sur Clusters Big Data SQL Server, vous n’avez pas besoin de suivre les étapes dans ce cas. Pour plus d’informations, consultez [Utiliser Machine Learning Services (Python et R) sur Clusters Big Data](../big-data-cluster/machine-learning-services.md).

## <a name="uninstall-preview-release"></a>Désinstaller la préversion

Si vous avez installé une préversion comme CTP (Community Technology Preview) ou RC (Release Candidate), nous vous recommandons de la désinstaller pour supprimer tous les packages précédents avant d’installer SQL Server 2019. L’installation côte à côte de plusieurs versions n’est pas prise en charge et la liste des packages a changé au cours des dernières préversions (CTP/RC).

### <a name="1-confirm-package-installation"></a>1. Confirmer l’installation du package

Vous souhaiterez peut-être vérifier l’existence d’une installation précédente comme première étape. Les fichiers suivants indiquent une installation existante : checkinstallextensibility.sh, exthost, launchpad.

```bash
ls /opt/microsoft/mssql/bin
```

### <a name="2-uninstall-ctprc-packages"></a>2. Désinstaller les packages CTP/RC

Désinstallez au niveau du package le plus bas. Tout package en amont dépendant d’un package de niveau inférieur est automatiquement désinstallé.

  + Pour l’intégration R, supprimez **microsoft-r-open***
  + Pour l’intégration Python, supprimez **mssql-mlservices-python**

Les commandes de suppression des packages s’affichent dans le tableau suivant.

| Plateforme  | Commande(s) de suppression de package | 
|-----------|----------------------------|
| Red Hat   | `sudo yum remove microsoft-r-open-mro-3.4.4`<br/>`sudo yum remove msssql-mlservices-python` |
| SUSE  | `sudo zypper remove microsoft-r-open-mro-3.4.4`<br/>`sudo zypper remove msssql-mlservices-python` |
| Ubuntu    | `sudo apt-get remove microsoft-r-open-mro-3.4.4`<br/>`sudo apt-get remove msssql-mlservices-python`|

> [!Note]
> Microsoft R Open 3.4.4 se compose de deux packages, selon la version de CTP précédemment installée. (Le package foreachiterators a été combiné au package mro principal dans CTP la 2.2.) Si certains de ces packages restent après la suppression de microsoft-r-open-mro-3.4.4, vous devez les supprimer individuellement.
> ```
> microsoft-r-open-foreachiterators-3.4.4
> microsoft-r-open-mkl-3.4.4
> microsoft-r-open-mro-3.4.4
> ```

### <a name="3-proceed-with-install"></a>3. Procéder à l’installation

Installez au niveau de package le plus élevé en suivant les instructions de cet article pour votre système d’exploitation.

Pour chaque ensemble d’instructions d’installation propres au système d’exploitation, le *niveau de package le plus élevé* est soit **Exemple 1 : Installation complète** pour l’ensemble complet de packages soit **Exemple 2 : Installation minimale**  pour le minimum de packages requis pour une installation viable.

1. Pour l’intégration de R, commencez par [MRO](#mro), car il s’agit d’une condition préalable. L’intégration R ne s’installe pas sans.

2. Exécutez les commandes d’installation à l’aide des gestionnaires de package et de la syntaxe pour votre système d’exploitation : 

   + [Red Hat](#RHEL)
   + [Ubuntu](#ubuntu)
   + [SUSE](#suse)

## <a name="prerequisites"></a>Conditions préalables requises

+ La version de Linux doit être [prise en charge par SQL Server](sql-server-linux-release-notes-2019.md#supported-platforms), mais elle n’inclut pas le moteur Docker. Les versions prises en charge sont les suivantes :

   + [Red Hat Enterprise Linux (RHEL)](quickstart-install-connect-red-hat.md)

   + [Serveur SUSE Enterprise Linux](quickstart-install-connect-suse.md)

   + [Ubuntu](quickstart-install-connect-ubuntu.md)

+ (R uniquement) [Microsoft R Open](#mro) fournit la distribution R de base pour la fonctionnalité R dans SQL Server

+ Vous devez disposer d’un outil pour l’exécution des commandes T-SQL. Un éditeur de requête est nécessaire pour la configuration et la validation postérieures à l’installation. Nous vous recommandons [Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/download?view=sql-server-2017#get-azure-data-studio-for-linux), un outil en téléchargement gratuit qui s’exécute sur Linux.

<a name="mro"></a>

### <a name="microsoft-r-open-mro-installation"></a>Installation de Microsoft R Open (MRO)

La distribution de base de R de Microsoft est une condition préalable à l’utilisation de RevoScaleR, MicrosoftML et d’autres packages R installés avec Machine Learning Services.

La version requise est MRO 3.5.2.

Choisissez une des deux approches suivantes pour installer MRO :

+ Téléchargez le tarball MRO à partir de MRAN, décompressez-le, puis exécutez son script install.sh. Vous pouvez suivre les [instructions d’installation sur MRAN](https://mran.microsoft.com/releases/3.5.2) si vous souhaitez adopter cette approche.

+ Vous pouvez également inscrire le référentiel **packages.microsoft.com** comme décrit ci-dessous pour installer les deux packages comprenant la distribution MRO : microsoft-r-open-mro et microsoft-r-open-mkl. 

Les commandes suivantes inscrivent le référentiel fournissant MRO. Après l’inscription, les commandes permettant d’installer d’autres packages R, telles que mssql-mlservices-mml-r, incluent automatiquement MRO en tant que dépendance de package.

#### <a name="mro-on-ubuntu"></a>MRO sur Ubuntu

```bash
# Install as root
sudo su

# Optionally, if your system does not have the https apt transport option
apt-get install apt-transport-https

# Set the location of the package repo the "prod" directory containing the distribution.
# This example specifies 16.04. Replace with 14.04 if you want that version
wget https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb

# Register the repo
dpkg -i packages-microsoft-prod.deb

# Update packages on your system (required), including MRO installation
sudo apt-get update
```

#### <a name="mro-on-red-hat"></a>MRO sur Red Hat

```bash
# Import the Microsoft repository key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc


# Set the location of the package repo at the "prod" directory
# The following command is for version 7.x
# For 6.x, replace 7 with 6 to get that version
rpm -Uvh https://packages.microsoft.com/config/rhel/7/packages-microsoft-prod.rpm

# Update packages on your system (optional)
yum update
```

#### <a name="mro-on-suse"></a>MRO sur SUSE

```bash
# Install as root
sudo su

# Set the location of the package repo at the "prod" directory containing the distribution
# This example is for SLES12, the only supported version of SUSE in Machine Learning Server
zypper ar -f https://packages.microsoft.com/sles/12/prod packages-microsoft-com

# Update packages on your system (optional)
zypper update
```

## <a name="package-list"></a>Liste des packages

Sur un appareil connecté à Internet, les packages sont téléchargés et installés indépendamment du moteur de base de données à l’aide du programme d’installation de package pour chaque système d’exploitation. Le tableau suivant décrit tous les packages disponibles, mais pour R et Python, vous spécifiez des packages qui fournissent soit l’installation complète des fonctionnalités soit l’installation des fonctionnalités minimales.

| Nom du package | S’applique à | Description |
|--------------|----------|-------------|
|mssql-server-extensibility  | All | Framework d’extensibilité utilisé pour exécuter le code R et Python. |
| microsoft-openmpi  | Python, R | Interface de passage de messages utilisée par les bibliothèques Revo* pour la parallélisation sur Linux. |
| mssql-mlservices-python | Python | Distribution open source d’Anaconda et de Python. |
|mssql-mlservices-mlm-py  | Python | *Installation complète*. Fournit des modèles préformés, revoscalepy et microsoftml pour la caractérisation d’images et l’analyse textuelle des sentiments.| 
|mssql-mlservices-packages-py  | Python | *Installation minimale*. Fournit revoscalepy et microsoftml. <br/>Exclut les modèles préformés. | 
| [microsoft-r-open*](#mro) | R | Distribution open source de R, composée de trois packages. |
|mssql-mlservices-mlm-r  | R | *Installation complète*. Fournit des modèles préformés, RevoScaleR, MicrosoftML, sqlRUtils et olapR pour la caractérisation d’images et l’analyse textuelle des sentiments.| 
|mssql-mlservices-packages-r  | R | *Installation minimale*. Fournit RevoScaleR, sqlRUtils, MicrosoftML et olapr. <br/>Exclut les modèles préformés. | 

<a name="RHEL"></a>

## <a name="redhat-commands"></a>Commandes RedHat

Vous pouvez installer la prise en charge linguistique dans la combinaison de votre choix (une ou plusieurs langues). Pour R et Python, vous avez le choix entre deux packages. L’un fournit toutes les fonctionnalités disponibles, caractérisées comme *l'installation complète*. L’autre choix exclut les modèles Machine Learning préformés et est considéré comme une *installation minimale*.

> [!Tip]
> Si possible, exécutez `yum clean all` pour actualiser les packages sur le système avant l’installation.

### <a name="example-1----full-installation"></a>Exemple 1 : Installation complète 

Comprend R et Python open source, le framework d’extensibilité, microsoft-openmpi, les extensions (R, Python) avec des bibliothèques Machine Learning et des modèles préformés pour R et Python. 

```bash
# Install as root or sudo
# Add everything (all R, Python)
# Be sure to include -9.4.7* in mlsservices package names
sudo yum install mssql-mlservices-mlm-py-9.4.7*
sudo yum install mssql-mlservices-mlm-r-9.4.7* 
```

### <a name="example-2---minimum-installation"></a>Exemple 2 : Installation minimale 

Comprend R et Python open source, l’infrastructure d’extensibilité, microsoft-openmpi, les bibliothèques Core Revo * et les bibliothèques Machine Learning pour R et Python. Exclut les modèles préformés.

```bash
# Install as root or sudo
# Minimum install of R, Python extensions
# Be sure to include -9.4.6* in mlsservices package names
sudo yum install mssql-mlservices-packages-py-9.4.7*
sudo yum install mssql-mlservices-packages-r-9.4.7*
```

<a name="ubuntu"></a>

## <a name="ubuntu-commands"></a>Commandes Ubuntu

Vous pouvez installer la prise en charge linguistique dans la combinaison de votre choix (une ou plusieurs langues). Pour R et Python, vous avez le choix entre deux packages. L’un fournit toutes les fonctionnalités disponibles, caractérisées comme *l'installation complète*. L’autre choix exclut les modèles Machine Learning préformés et est considéré comme une *installation minimale*.

> [!Tip]
> Si possible, exécutez `apt-get update` pour actualiser les packages sur le système avant l’installation. En outre, il se peut que certaines images de Docker d’Ubuntu ne disposent pas de l’option de transport https apt. Pour l’installer, utilisez `apt-get install apt-transport-https`.

### <a name="example-1----full-installation"></a>Exemple 1 : Installation complète 

Comprend R et Python open source, le framework d’extensibilité, microsoft-openmpi, les extensions (R, Python) avec des bibliothèques Machine Learning et des modèles préformés pour R et Python. 

```bash
# Install as root or sudo
# Add everything (all R, Python)
# There is no asterisk in this full install
sudo apt-get install mssql-mlservices-mlm-py 
sudo apt-get install mssql-mlservices-mlm-r 
```

### <a name="example-2---minimum-installation"></a>Exemple 2 : Installation minimale 

Comprend R et Python open source, l’infrastructure d’extensibilité, microsoft-openmpi, les bibliothèques Core Revo * et les bibliothèques Machine Learning pour R et Python. Exclut les modèles préformés. 

```bash
# Install as root or sudo
# Minimum install of R, Python
# No aasterisk
sudo apt-get install mssql-mlservices-packages-py
sudo apt-get install mssql-mlservices-packages-r
```

<a name="suse"></a>

## <a name="suse-commands"></a>Commandes SUSE

Vous pouvez installer la prise en charge linguistique dans la combinaison de votre choix (une ou plusieurs langues). Pour R et Python, vous avez le choix entre deux packages. L’un fournit toutes les fonctionnalités disponibles, caractérisées comme *l'installation complète*. L’autre choix exclut les modèles Machine Learning préformés et est considéré comme une *installation minimale*.

### <a name="example-1----full-installation"></a>Exemple 1 : Installation complète 

Comprend R et Python open source, le framework d’extensibilité, microsoft-openmpi, les extensions (R, Python) avec des bibliothèques Machine Learning et des modèles préformés pour R et Python. 

```bash
# Install as root or sudo
# Add everything (all R, Python)
# Be sure to include -9.4.7* in mlsservices package names
sudo zypper install mssql-mlservices-mlm-py-9.4.7*
sudo zypper install mssql-mlservices-mlm-r-9.4.7* 
```

### <a name="example-2---minimum-installation"></a>Exemple 2 : Installation minimale 

Comprend R et Python open source, l’infrastructure d’extensibilité, microsoft-openmpi, les bibliothèques Core Revo * et les bibliothèques Machine Learning pour R et Python. Exclut les modèles préformés. 

```bash
# Install as root or sudo
# Minimum install of R, Python extensions
# Be sure to include -9.4.6* in mlsservices package names
sudo zypper install mssql-mlservices-packages-py-9.4.7*
sudo zypper install mssql-mlservices-packages-r-9.4.7*
```

## <a name="post-install-config-required"></a>Configuration après installation (obligatoire)

La configuration supplémentaire s’effectue principalement avec [l’outil mssql-conf](sql-server-linux-configure-mssql-conf.md).


1. Ajoutez le compte d’utilisateur mssql utilisé pour exécuter le service SQL Server. Cela est requis si vous n’avez pas exécuté l’installation précédemment.

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

2. Acceptez les contrats de licence pour R et Python open source. Il existe plusieurs façons de procéder. Si vous avez précédemment accepté la licence de SQL Server et que vous ajoutez maintenant les extensions R ou Python, la commande suivante indique votre consentement aux conditions :

   ```bash
   # Run as SUDO or root
   # Use set + EULA 
   sudo /opt/mssql/bin/mssql-conf set EULA accepteulaml Y
   ```

   Un autre workflow s’applique si vous n’avez pas encore accepté le contrat de licence du moteur de base de données SQL Server. Le programme d’installation détecte les packages mssql-mlservices et demande l’acceptation du CLUF lorsque `mssql-conf setup` est exécuté. Pour plus d’informations sur les paramètres de CLUF, consultez [Configurer SQL Server avec l’outil mssql-conf](sql-server-linux-configure-mssql-conf.md#mlservices-eula).

3. Activez l’accès réseau sortant. L’accès réseau sortant est désactivé par défaut. Pour activer les requêtes sortantes, définissez la propriété booléenne « outboundnetworkaccess » à l’aide de l’outil mssql-conf. Pour plus d’informations, consultez [Configurer SQL Server sur Linux avec mssql-conf](sql-server-linux-configure-mssql-conf.md#mlservices-outbound-access).

   ```bash
   # Run as SUDO or root
   # Enable outbound requests over the network
   sudo /opt/mssql/bin/mssql-conf set extensibility outboundnetworkaccess 1
   ```

4. Pour l’intégration de fonctionnalités R uniquement, définissez la variable d' environnement **MKL_CBWR** pour [garantir la cohérence de la sortie](https://software.intel.com/articles/introduction-to-the-conditional-numerical-reproducibility-cnr) des calculs d’Intel Math Kernel Library (MKL).

   + Modifiez ou créez un fichier nommé **.bash_profile** dans le répertoire racine de votre utilisateur en ajoutant la ligne `export MKL_CBWR="AUTO"` au fichier.

   + Exécutez ce fichier en saisissant `source .bash_profile` à l’invite de commandes bash.

5. Redémarrez le service SQL Server Launchpad et l’instance du moteur de base de données pour lire les valeurs mises à jour à partir du fichier INI. Un message de redémarrage vous rappelle chaque fois qu’un paramètre relatif à l’extensibilité est modifié.  

   ```bash
   systemctl restart mssql-launchpadd

   systemctl restart mssql-server.service
   ```

6. Activez l’exécution du script externe à l’aide d’Azure Data Studio ou d’un autre outil comme SQL Server Management Studio (Windows uniquement) qui exécute Transact-SQL. 

   ```bash
   EXEC sp_configure 'external scripts enabled', 1 
   RECONFIGURE WITH OVERRIDE 
   ```

7. Redémarrez le service Launchpad.

## <a name="verify-installation"></a>Vérifier l'installation

Les bibliothèques R (MicrosoftML, RevoScaleR et autres) sont disponibles sur `/opt/mssql/mlservices/libraries/RServer`.

Les bibliothèques Python (microsoftml et revoscalepy) sont disponibles sur `/opt/mssql/mlservices/libraries/PythonServer`.

Pour valider l’installation, exécutez un script T-SQL qui exécute une procédure stockée système qui appelle R ou Python. Vous aurez besoin d’un outil de requête pour cette tâche. Azure Data Studio est un bon choix. Les autres outils couramment utilisés, tels que SQL Server Management Studio ou PowerShell, sont uniquement disponibles sous Windows. Si vous disposez d’un ordinateur Windows avec ces outils, utilisez-le pour vous connecter à votre installation Linux du moteur de base de données.

Exécutez la commande SQL suivante pour tester l’exécution de R dans SQL Server. Si le script ne s’exécute pas, essayez de redémarrer le service `sudo systemctl restart mssql-server.service`.

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

## <a name="chained-combo-install"></a>Installation chaînée combinée

Vous pouvez installer et configurer le moteur de base de données et Machine Learning Services en une seule procédure en ajoutant des packages R ou Python et des paramètres sur une commande qui installe le moteur de base de données. 

1. Pour l’intégration de R, installez [Microsoft R Open](#mro) comme condition préalable. Ignorez cette étape si vous n’installez pas la fonctionnalité R.

2. Fournissez une ligne de commande qui comprend le moteur de base de données ainsi que des fonctionnalités d’extension de langage.

  Vous pouvez ajouter une fonctionnalité unique, telle que l’intégration Python, à une installation du moteur de base de données.

  ```bash
  sudo yum install -y mssql-server mssql-mlservices-packages-r-9.4.7* 
  ```

  Ou ajoutez les deux extensions (R, Python).

  ```bash
  sudo yum install -y mssql-server mssql-mlservices-packages-r-9.4.7* mssql-mlservices-packages-py-9.4.7*
  ```

3. Acceptez les contrats de licence et terminez la configuration consécutive à l’installation. Utilisez l'outil **mssql-conf** pour cette tâche.

  ```bash
  sudo /opt/mssql/bin/mssql-conf setup
  ```

  Vous serez invité à accepter le contrat de licence pour le moteur de base de données, à choisir une édition et à définir le mot de passe administrateur. Vous êtes également invité à accepter le contrat de licence pour Machine Learning Services.

4. Redémarrez le service si vous y êtes invité.

  ```bash
  sudo systemctl restart mssql-server.service
  ```

## <a name="unattended-installation"></a>Installation sans assistance

À l'aide de [l’installation sans assistance](https://docs.microsoft.com/sql/linux/sql-server-linux-setup?view=sql-server-2017#unattended) du moteur de base de données, ajoutez les packages pour mssql-mlservices et les CLUF.

Rappelez-vous que le programme d’installation ou l’outil mssql-conf vous invite à accepter le contrat de licence. Si vous avez déjà configuré le moteur de base de données SQL Server et accepté son CLUF, utilisez un des paramètres CLUF spécifiques à mlservices pour les distributions R et Python open source :

```bash
sudo /opt/mssql/bin/mssql-conf setup accept-eula-ml
```

Toutes les permutations possibles de l’acceptation du CLUF sont documentées dans [Configurer SQL Server sur Linux avec l'outil mssql-conf](sql-server-linux-configure-mssql-conf.md#mlservices-eula).

## <a name="offline-installation"></a>Installation hors connexion

Suivez les instructions [d'installation hors connexion](sql-server-linux-setup.md#offline) pour connaître les étapes d’installation des packages. Recherchez votre site de téléchargement, puis téléchargez des packages spécifiques à l’aide de la liste de packages ci-dessous.

> [!Tip]
> Plusieurs outils de gestion des packages fournissent des commandes qui peuvent vous aider à déterminer les dépendances du package. Pour yum, utilisez `sudo yum deplist [package]`. Pour Ubuntu, utilisez `sudo apt-get install --reinstall --download-only [package name]`, suivi de `dpkg -I [package name].deb`.


#### <a name="download-site"></a>Site de téléchargement

Vous pouvez télécharger des packages à partir de [https://packages.microsoft.com/](https://packages.microsoft.com/). Tous les packages mlservices pour R et Python sont colocalisés avec le package du moteur de base de données. La version de base des packages mlservices est 9.4.6 Souvenez-vous que les packages microsoft-r-open se trouvent dans un [autre référentiel](#mro).

#### <a name="rhel7-paths"></a>Chemins d’accès RHEL/7

|||
|--|----|
| Packages mssql/mlservices | [https://packages.microsoft.com/rhel/7/mssql-server-preview/](https://packages.microsoft.com/rhel/7/mssql-server-preview/) |
| Packages microsoft-r-open | [https://packages.microsoft.com/rhel/7/prod/](https://packages.microsoft.com/rhel/7/prod/) | 


#### <a name="ubuntu1604-paths"></a>Chemins d’accès Ubuntu/16.04

|||
|--|----|
| Packages mssql/mlservices | [https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/) |
| Packages microsoft-r-open | [https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/) | 

#### <a name="sles12-paths"></a>Chemins d’accès SLES/12

|||
|--|----|
| Packages mssql/mlservices | [https://packages.microsoft.com/sles/12/mssql-server-preview/](https://packages.microsoft.com/sles/12/mssql-server-preview/) |
| Packages microsoft-r-open | [https://packages.microsoft.com/sles/12/prod/](https://packages.microsoft.com/sles/12/prod/) | 

#### <a name="package-list"></a>Liste des packages

Selon les extensions que vous souhaitez utiliser, téléchargez les packages nécessaires pour un langage spécifique. Les noms de fichiers exacts incluent des informations sur la plateforme dans le suffixe, mais les noms de fichier ci-dessous devraient être suffisamment proches pour vous permettre de déterminer les fichiers à obtenir.

```
# Core packages 
mssql-server-15.0.1000
mssql-server-extensibility-15.0.1000

# R
microsoft-openmpi-3.0.0
microsoft-r-open-mkl-3.5.2
microsoft-r-open-mro-3.5.2
mssql-mlservices-packages-r-9.4.7.64
mssql-mlservices-mlm-r-9.4.7.64


# Python
microsoft-openmpi-3.0.0
mssql-mlservices-python-9.4.7.64
mssql-mlservices-packages-py-9.4.7.64
mssql-mlservices-mlm-py-9.4.7.64
```

## <a name="add-more-rpython-packages"></a>Ajouter d’autres packages R/Python 
 
Vous pouvez installer d’autres packages R et Python et les utiliser dans un script qui s’exécute sur SQL Server 2019.

### <a name="r-packages"></a>Packages R 
 
1. Démarrez une session R.

   ```r
   # sudo /opt/mssql/mlservices/bin/R/R 
   ```

2. Installez un package R appelé [glue](https://mran.microsoft.com/package/glue) pour tester l’installation du package.

   ```r
   # install.packages("glue",lib="/opt/mssql/mlservices/libraries/RServer") 
   ```
   Vous pouvez également installer un package R à partir de la ligne de commande 

   ```r
   # sudo /opt/mssql/mlservices/bin/R/R CMD INSTALL -l /opt/mssql/mlservices/libraries/RServer glue_1.1.1.tar.gz 
   ```

3. Importez le package R dans [sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

   ```r
   EXEC sp_execute_external_script  
   @language = N'R', 
   @script = N'library(glue)' 
   ```

### <a name="python-packages"></a>Packages Python 
 
1. Installez un package Python appelé [httpie](https://httpie.org/) à l’aide de PIP. 

   ```python
   # sudo /opt/mssql/mlservices/bin/python/python -m pip install httpie 
   ``` 

2. Importez le package Python dans [sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).
 
   ```python
   EXEC sp_execute_external_script  
   @language = N'Python',  
   @script = N'import httpie' 
   ```

## <a name="run-in-a-container"></a>Exécuter dans un conteneur

Suivez les étapes ci-dessous pour générer et exécuter SQL Server Machine Learning Services dans un conteneur Docker. Pour plus d’informations, consultez [Configurer des images de conteneur SQL Server sur Docker](sql-server-linux-configure-docker.md).

### <a name="prerequisites"></a>Conditions préalables requises

- Interface de ligne de commande GIT.
- Moteur Docker 1.8+ sur n’importe quelle distribution Linux prise en charge ou Docker pour Mac/Windows. Pour plus d’informations, consultez [Installer Docker](https://docs.docker.com/engine/installation/).
- Au moins 2 gigaoctets (Go) d’espace disque.
- Au moins 2 Go de RAM.
- [Configuration système requise pour SQL Server sur Linux](sql-server-linux-setup.md#system).

### <a name="clone-the-mssql-docker-repository"></a>Clonez le référentiel mssql-docker

1. Ouvrez un terminal Bash sur Linux ou Mac ou ouvrez un terminal WSL sur Windows.

1. Créez un répertoire local pour contenir une copie locale du référentiel mssql-docker.

1. Exécuter la commande clone git pour cloner le référentiel mssql-docker :

    ```bash
    git clone https://github.com/microsoft/mssql-docker mssql-docker
    ```

### <a name="build-a-sql-server-linux-container-image-with-machine-learning-services"></a>Générer une image de conteneur SQL Server Linux avec Machine Learning Services

1. Modifier le répertoire par le répertoire mssql-mlservices :

    ```bash
    cd mssql-docker/linux/preview/examples/mssql-mlservices
    ```

1. Exécuter le script build.sh :

   ```bash
   ./build.sh
   ```

   > [!NOTE]
   > Pour générer l’image Docker, vous devez installer des packages d’une taille de plusieurs Go. Le script peut prendre jusqu’à 20 minutes pour terminer de s’exécuter en fonction de la bande passante réseau.

### <a name="run-the-sql-server-linux-container-image-with-machine-learning-services"></a>Générer l’image de conteneur SQL Server Linux avec Machine Learning Services

1. Définissez des variables d’environnement avant d’exécuter le conteneur. Définir la variable d’environnement PATH_TO_MSSQL sur un répertoire hôte :

   ```bash
    export MSSQL_PID='Developer'
    export ACCEPT_EULA='Y'
    export ACCEPT_EULA_ML='Y'
    export PATH_TO_MSSQL='/home/mssql/'
   ```

1. Exécuter le script run.sh :

   ```bash
   ./run.sh
   ```

   Cette commande crée un conteneur SQL Server avec Machine Learning Services à l’aide de l’édition Développeur (par défaut). Le port SQL Server **1433** est exposé sur l’hôte en tant que port **1401**.

   > [!NOTE]
   > Le processus d’exécution des éditions SQL Server de production dans des conteneurs est légèrement différent. Pour plus d’informations, consultez [Configurer des images de conteneur SQL Server sur Docker](sql-server-linux-configure-docker.md). Si vous utilisez les mêmes noms et ports de conteneurs, le reste de cette procédure pas à pas fonctionne toujours avec les conteneurs de production.

1. Pour afficher vos conteneurs Docker, exécutez la commande `docker ps` :

   ```bash
   sudo docker ps -a
   ```

1. Si la colonne **ÉTAT** affiche **En cours d’exécution**, SQL Server est en cours d’exécution dans le conteneur et écoute sur le port spécifié dans la colonne **PORTS**. Si la colonne **ÉTAT** pour votre conteneur SQL Server affiche **Quitté**, consultez la [section Résolution des problèmes dans le guide de configuration](sql-server-linux-configure-docker.md#troubleshooting).

   ```bash
   $ sudo docker ps -a
   ```

    Sortie : 
    
    ```
    CONTAINER ID        IMAGE                          COMMAND                  CREATED             STATUS              PORTS                    NAMES
    941e1bdf8e1d        mcr.microsoft.com/mssql/server/mssql-server-linux   "/bin/sh -c /opt/m..."   About an hour ago   Up About an hour     0.0.0.0:1401->1433/tcp   sql1
    ```

## <a name="next-steps"></a>Étapes suivantes

Les développeurs peuvent démarrer avec quelques exemples simples et découvrir les principes de base du fonctionnement de R avec SQL Server. Pour l’étape suivante, consultez les liens suivants :

+ [Tutoriel : Exécuter R dans T-SQL](../advanced-analytics/tutorials/quickstart-r-create-script.md)
+ [Tutoriel : Analytique dans la base de données pour les développeurs R](../advanced-analytics/tutorials/sqldev-in-database-r-for-sql-developers.md)

Les développeurs Python peuvent apprendre à utiliser Python avec SQL Server en effectuant les didacticiels suivants :

+ [Tutoriel : Exécuter Python dans T-SQL](../advanced-analytics/tutorials/run-python-using-t-sql.md)
+ [Tutoriel : Analytique dans la base de données pour les développeurs Python](../advanced-analytics/tutorials/sqldev-in-database-python-for-sql-developers.md)

Pour consulter des exemples d’apprentissage automatique basés sur des scénarios réels, consultez les [Didacticiels d’apprentissage automatique](../advanced-analytics/tutorials/machine-learning-services-tutorials.md).
