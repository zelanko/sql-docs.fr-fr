---
title: Installer SQL Server Machine Learning Services (R, Python, Java) sur Linux | Microsoft Docs
description: Découvrez comment installer SQL Server Machine Learning Services (R, Python, Java) sur Red Hat et Ubuntu.
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.date: 03/27/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: machine-learning
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: f1ca66c5e376704737a092f21fd25401d20bbdbb
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58493871"
---
# <a name="install-sql-server-2019-machine-learning-services-r-python-java-on-linux"></a>Installer SQL Server 2019 Machine Learning Services (R, Python, Java) sur Linux

[SQL Server Machine Learning Services](../advanced-analytics/what-is-sql-server-machine-learning.md) s’exécute sur les systèmes d’exploitation Linux à partir de cette version préliminaire de SQL Server 2019. Suivez les étapes décrites dans cet article pour installer l’extension de programmation Java, ou les extensions d’apprentissage pour R et Python. 

Machine learning et extensions de programmation est un module complémentaire pour le moteur de base de données. Bien que vous puissiez [installer le moteur de base de données et les Services Machine Learning simultanément](#install-all), il est recommandé d’installer et configurer le moteur de base de données SQL Server tout d’abord, afin que vous pouvez résoudre les problèmes avant d’ajouter plus d’informations composants. 

Emplacement du package pour les extensions R, Python et Java se trouvent dans les référentiels de code source SQL Server Linux. Si vous avez configuré déjà des référentiels de code source pour l’installation du moteur de base de données, vous pouvez exécuter la **mssql-mlservices** commandes d’installation à l’aide de la même inscription de référentiel de package.

Services machine Learning est également pris en charge sur les conteneurs Linux. Nous ne fournissons pas de conteneurs prédéfinis à Machine Learning Services, mais vous pouvez en créer un à partir des conteneurs SQL Server à l’aide de [un exemple de modèle disponible sur GitHub](https://github.com/Microsoft/mssql-docker/tree/master/linux/preview/examples/mssql-mlservices).

## <a name="uninstall-previous-ctp"></a>Désinstaller la version CTP précédente

La liste des packages a changé au CTP versions antérieures, ce qui entraîne moins de packages. Nous vous recommandons de désinstallation de CTP 2.x pour supprimer tous les packages précédentes avant d’installer la version CTP 2.4. Installation côte à côte de plusieurs versions n’est pas pris en charge.

### <a name="1-confirm-package-installation"></a>1. Confirmer l’installation du package

Vous pouvez souhaiter vérifier l’existence d’une installation précédente dans un premier temps. Les fichiers suivants indiquent une installation existante : checkinstallextensibility.sh, exthost, launchpad.

```bash
ls /opt/microsoft/mssql/bin
```

### <a name="2-uninstall-previous-ctp-2x-packages"></a>2. Désinstaller des packages de 2.x CTP précédentes

Désinstallez au niveau du package le plus bas. N’importe quel package amont dépendant d’un package de niveau inférieur est automatiquement désinstallé.

  + Pour l’intégration de R, supprimer **microsoft-r-open***
  + Pour l’intégration de Python, supprimer **mssql-mlservices-python**
  + Pour l’intégration de Java, vous devez supprimer **mssql-server-extensibilité-java**

Commandes de suppression de packages apparaissent dans le tableau suivant.

| Plateforme  | Commandes de suppression de package | 
|-----------|----------------------------|
| RHEL  | `sudo yum remove microsoft-r-open-mro-3.4.4`<br/>`sudo yum remove msssql-mlservices-python`<br/>`sudo yum remove msssql-server-extensibility-java` |
| SLES  | `sudo zypper remove microsoft-r-open-mro-3.4.4`<br/>`sudo zypper remove msssql-mlservices-python`<br/>`sudo zypper remove msssql-server-extensibility-java` |
| Ubuntu    | `sudo apt-get remove microsoft-r-open-mro-3.4.4`<br/>`sudo apt-get remove msssql-mlservices-python`<br/>`sudo apt-get remove msssql-server-extensibility-java`|

> [!Note]
> Microsoft R Open est composée de trois packages. Si un de ces packages restent après la suppression de microsoft-r-open-mro-3.4.4, vous devez les supprimer individuellement.
> ```
> microsoft-r-open-foreachiterators-3.4.4
> microsoft-r-open-mkl-3.4.4
> microsoft-r-open-mro-3.4.4
> ```

### <a name="3-proceed-with-ctp-24-install"></a>3. Poursuivre l’installation du CTP 2.4

Installez au niveau du package le plus élevé en suivant les instructions dans cet article pour votre système d’exploitation.

Pour chaque ensemble de spécifiques du système d’exploitation d’instructions d’installation, *plus haut niveau de package* est soit **exemple 1 : installation complète** pour l’ensemble de packages, ou **exemple 2 : installation minimale**  pour le plus petit nombre de packages requis pour une installation viable.

1. Pour l’intégration de R, commencez par [MRO](#mro) car il s’agit d’une condition préalable. Intégration de R n’installera pas sans lui.

2. Exécutez les commandes d’installation à l’aide de gestionnaires de packages et de la syntaxe de votre système d’exploitation : 

   + [RedHat](#RHEL)
   + [Ubuntu](#ubuntu)
   + [SUSE](#suse)

## <a name="prerequisites"></a>Prérequis

+ La version de Linux doit être [pris en charge par SQL Server](sql-server-linux-release-notes-2019.md#supported-platforms), mais n’inclut ne pas le moteur Docker. Versions prises en charge sont les suivantes :

   + [Red Hat Enterprise Linux (RHEL)](quickstart-install-connect-red-hat.md)

   + [SUSE Enterprise Linux Server](quickstart-install-connect-suse.md)

   + [Ubuntu](quickstart-install-connect-ubuntu.md)

+ R (uniquement) [Microsoft R Open](#mro) fournit la distribution R de base de la fonctionnalité de R dans SQL Server

+ Vous devez disposer d’un outil pour l’exécution des commandes T-SQL. Un éditeur de requête est nécessaire pour la validation et la configuration de post-installation. Nous vous recommandons de [Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/download?view=sql-server-2017#get-azure-data-studio-for-linux), téléchargeable gratuitement qui s’exécute sur Linux.

<a name="mro"></a>

### <a name="microsoft-r-open-mro-installation"></a>Installation de Microsoft R Open (MRO)

Distribution de base de Microsoft de R est un prérequis pour utiliser RevoScaleR, MicrosoftML et autres packages R installés avec les Services Machine Learning.

La version requise est MRO 3.4.4.

Choisissez le des deux approches suivantes pour installer MRO :

+ Téléchargez l’archive tar MRO à partir de MRAN, décompressez-le et exécutez son script install.sh. Vous pouvez suivre la [instructions d’installation sur MRAN](https://mran.microsoft.com/releases/3.4.4) si vous souhaitez que cette approche.

+ Vous pouvez également inscrire le **packages.microsoft.com** référentiel comme décrit ci-dessous pour installer les trois packages comprenant la distribution MRO : microsoft-r-open-mro, microsoft-r-open-mkl et Microsoft-r-open-foreachiterators. 

Les commandes suivantes inscrire le référentiel fournissant MRO. Après l’enregistrement, les commandes pour installer les autres packages R, tel que mssql-mlservices-mml-r inclut automatiquement MRO comme une dépendance de package.

#### <a name="mro-on-ubuntu"></a>MRO sur Ubuntu

```bash
# Install as root
sudo su

# Optionally, if your system does not have the https apt transport option
apt-get install apt-transport-https

# Add the **azure-cli** repo to your apt sources list
AZ_REPO=$(lsb_release -cs)

echo "deb [arch=amd64] https://packages.microsoft.com/repos/azure-cli/ $AZ_REPO main" | sudo tee /etc/apt/sources.list.d/azure-cli.list

# Set the location of the package repo the "prod" directory containing the distribution.
# This example specifies 16.04. Replace with 14.04 if you want that version
wget https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb

# Register the repo
dpkg -i packages-microsoft-prod.deb

# Update packages on your system (required), including MRO installation
sudo apt-get update
```

#### <a name="mro-on-rhel"></a>MRO sur RHEL

```bash
# Import the Microsoft repository key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Create local `azure-cli` repository
sudo sh -c 'echo -e "[azure-cli]\nname=Azure CLI\nbaseurl=https://packages.microsoft.com/yumrepos/azure-cli\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/azure-cli.repo'

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

Sur un appareil connecté à internet, les packages sont téléchargés et installés indépendamment le moteur de base de données à l’aide de l’installeur de package pour chaque système d’exploitation. Le tableau suivant décrit tous les packages disponibles, mais pour R et Python, vous spécifiez des packages qui fournissent l’installation de fonctionnalités complet ou l’installation minimale.

| Nom du package | Applies-to | Description |
|--------------|----------|-------------|
|mssql-server-extensibility  | All | Infrastructure d’extensibilité permettant d’exécuter le code R, Python ou Java. |
|mssql-server-extensibility-java | Java | Extension de Java pour le chargement d’un environnement d’exécution Java. Il n’existe aucune des bibliothèques supplémentaires ou des packages pour Java. |
| microsoft-openmpi  | Python, R | Message passant interface utilisée par les bibliothèques Revo * pour la parallélisation sur Linux. |
| mssql-mlservices-python | Python | Distribution Open source d’Anaconda et Python. |
|mssql-mlservices-mlm-py  | Python | *Installation complète*. Fournit des revoscalepy, microsoftml, de modèles pour l’analyse de sentiments de caractérisation et texte image préformés.| 
|mssql-mlservices-packages-py  | Python | *Installation légère*. Fournit des revoscalepy et microsoftml. <br/>Exclut les modèles préentraînés. | 
| [microsoft-r-open*](#mro) | R | Distribution Open source de R, composée de trois packages. |
|mssql-mlservices-mlm-r  | R | *Installation complète*. Fournit des RevoScaleR, MicrosoftML, sqlRUtils, olapR, de modèles pour l’analyse de sentiments de caractérisation et texte image préformés.| 
|mssql-mlservices-packages-r  | R | *Installation légère*. Fournit des RevoScaleR, sqlRUtils, MicrosoftML, olapR. <br/>Exclut les modèles préentraînés. | 
|mssql-mlservices-mml-py  | CTP 2.0-2.1 | Obsolète dans CTP 2.2 en raison de la consolidation de package Python dans mssql-mslservices-python. Fournit des revoscalepy. Exclut microsoftml et modèles préentraînés.| 
|mssql-mlservices-mml-r  | CTP 2.0-2.1 | Obsolète dans CTP 2.2 en raison de la consolidation de package R dans mssql-mslservices-python. Fournit des RevoScaleR, sqlRUtils, olapR. Exclut les modèles préentraînés et MicrosoftML.  |

<a name="RHEL"></a>

## <a name="rhel-commands"></a>Commandes RHEL

Vous pouvez installer la prise en charge linguistique dans la combinaison, vous avez besoin (un ou plusieurs langages). Pour R et Python, il existe deux packages sélectionnables. Un fournit toutes les fonctionnalités disponibles, caractérisées par le *installation complète*. Le choix autre exclut les modèles d’apprentissage préformés et est considéré comme le *installation minimale*.

> [!Tip]
> Si possible, exécutez `yum clean all` pour actualiser les packages sur le système avant l’installation.

### <a name="example-1----full-installation"></a>Exemple 1 : installation complète 

Inclut open source R et Python, infrastructure d’extensibilité, de microsoft-openmpi, extensions (R, Python, Java), avec les bibliothèques machine learning et modèles préentraînés pour R et Python. 

```bash
# Install as root or sudo
# Add everything (all R, Python, Java)
# Be sure to include -9.4.6* in mlsservices package names
sudo yum install mssql-mlservices-mlm-py-9.4.6*
sudo yum install mssql-mlservices-mlm-r-9.4.6* 
sudo yum install mssql-server-extensibility-java
```

### <a name="example-2---minimum-installation"></a>Exemple 2 : installation minimale 

Inclut open source R et Python, infrastructure d’extensibilité, microsoft openmpi, Revo * bibliothèques principales et bibliothèques machine learning pour R et Python et l’extension de Java. Exclut les modèles préformés.

```bash
# Install as root or sudo
# Minimum install of R, Python, Java extensions
# Be sure to include -9.4.6* in mlsservices package names
sudo yum install mssql-mlservices-packages-py-9.4.6*
sudo yum install mssql-mlservices-packages-r-9.4.6*
sudo yum install mssql-server-extensibility-java
```

<a name="ubuntu"></a>

## <a name="ubuntu-commands"></a>Commandes d’Ubuntu

Vous pouvez installer la prise en charge linguistique dans la combinaison, vous avez besoin (un ou plusieurs langages). Pour R et Python, il existe deux packages sélectionnables. Un fournit toutes les fonctionnalités disponibles, caractérisées par le *installation complète*. Le choix autre exclut les modèles d’apprentissage préformés et est considéré comme le *installation minimale*.

> [!Tip]
> Si possible, exécutez `apt-get update` pour actualiser les packages sur le système avant l’installation. En outre, certaines images docker d’Ubuntu peut-être pas l’option de transport apt https. Pour l’installer, utiliser `apt-get install apt-transport-https`.

<!---
### Prerequisite for 18.04

Running mssql-mlservices R libraries on Ubuntu 18.04 requires **libpng12** from the Linux Kernel archives. This package is no longer included in the standard distribution and must be installed manually. To get this library, run the following commands:

```bash
wget https://mirrors.kernel.org/ubuntu/pool/main/libp/libpng/libpng12-0_1.2.54-1ubuntu1_amd64.deb
dpkg -i libpng12-0_1.2.54-1ubuntu1_amd64.deb
```--->

### <a name="example-1----full-installation"></a>Exemple 1 : installation complète 

Inclut open source R et Python, infrastructure d’extensibilité, de microsoft-openmpi, extensions (R, Python, Java), avec les bibliothèques machine learning et modèles préentraînés pour R et Python. 

```bash
# Install as root or sudo
# Add everything (all R, Python, Java)
# There is no asterisk in this full install
sudo apt-get install mssql-mlservices-mlm-py 
sudo apt-get install mssql-mlservices-mlm-r 
sudo apt-get install mssql-server-extensibility-java
```

### <a name="example-2---minimum-installation"></a>Exemple 2 : installation minimale 

Inclut open source R et Python, infrastructure d’extensibilité, microsoft openmpi, Revo * bibliothèques principales et bibliothèques machine learning pour R et Python et l’extension de Java. Exclut les modèles préformés. 

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

Vous pouvez installer la prise en charge linguistique dans la combinaison, vous avez besoin (un ou plusieurs langages). Pour R et Python, il existe deux packages sélectionnables. Un fournit toutes les fonctionnalités disponibles, caractérisées par le *installation complète*. Le choix autre exclut les modèles d’apprentissage préformés et est considéré comme le *installation minimale*.

### <a name="example-1----full-installation"></a>Exemple 1 : installation complète 

Inclut open source R et Python, infrastructure d’extensibilité, de microsoft-openmpi, extensions (R, Python, Java), avec les bibliothèques machine learning et modèles préentraînés pour R et Python. 

```bash
# Install as root or sudo
# Add everything (all R, Python, Java)
# Be sure to include -9.4.6* in mlsservices package names
sudo zypper install mssql-mlservices-mlm-py-9.4.6*
sudo zypper install mssql-mlservices-mlm-r-9.4.6* 
sudo zypper install mssql-server-extensibility-java
```

### <a name="example-2---minimum-installation"></a>Exemple 2 : installation minimale 

Inclut open source R et Python, infrastructure d’extensibilité, microsoft openmpi, Revo * bibliothèques principales et bibliothèques machine learning pour R et Python et l’extension de Java. Exclut les modèles préformés. 

```bash
# Install as root or sudo
# Minimum install of R, Python, Java extensions
# Be sure to include -9.4.6* in mlsservices package names
sudo zypper install mssql-mlservices-packages-py-9.4.6*
sudo zypper install mssql-mlservices-packages-r-9.4.6*
sudo zypper install mssql-server-extensibility-java
```

## <a name="post-install-config-required"></a>Configuration de post-installation (obligatoire)

Une configuration supplémentaire est essentiellement via les [outil mssql-conf](sql-server-linux-configure-mssql-conf.md).


1. Ajoutez le compte d’utilisateur mssql utilisé pour exécuter le service SQL Server. Cela est nécessaire si vous n’avez pas exécuté le programme d’installation précédemment.

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

3. Activer l’accès réseau sortant. Un accès réseau sortant est désactivé par défaut. Pour activer les demandes sortantes, définissez le « outboundnetworkaccess » à l’aide de l’outil mssql-conf de propriété booléenne. Pour plus d’informations, consultez [configurer SQL Server sur Linux avec mssql-conf](sql-server-linux-configure-mssql-conf.md#mlservices-outbound-access).

   ```bash
   # Run as SUDO or root
   # Enable outbound requests over the network
   sudo /opt/mssql/bin/mssql-conf set extensibility outboundnetworkaccess 1
   ```

4. Pour R fonctionnalité intégration uniquement, définie le **MKL_CBWR** variable d’environnement [résultat homogène](https://software.intel.com/articles/introduction-to-the-conditional-numerical-reproducibility-cnr) des calculs d’Intel Math Kernel Library (MKL).

   + Modifiez ou créez un fichier nommé **.bash_profile** dans votre répertoire de base de l’utilisateur, ajoutez la ligne `export MKL_CBWR="AUTO"` au fichier.

   + Exécutez ce fichier en tapant `source .bash_profile` à une invite de commandes bash.

5. Redémarrez le service Launchpad de SQL Server et l’instance du moteur de base de données pour lire les valeurs mises à jour à partir du fichier INI. Un message de redémarrage vous rappelle chaque fois qu’un paramètre dépendant de l’extensibilité est modifié.  

   ```bash
   systemctl restart mssql-launchpadd

   systemctl restart mssql-server.service
   ```

6. Activer l’exécution de script externe à l’aide d’Azure Data Studio ou un autre outil comme SQL Server Management Studio (Windows uniquement) qui s’exécute Transact-SQL. 

   ```bash
   EXEC sp_configure 'external scripts enabled', 1 
   RECONFIGURE WITH OVERRIDE 
   ```

7. Redémarrez le service Launchpad.

## <a name="verify-installation"></a>Vérifier l'installation

Vous trouverez les bibliothèques R (MicrosoftML, RevoScaleR, etc.) dans `/opt/mssql/mlservices/libraries/RServer`.

Vous trouverez les bibliothèques Python (microsoftml et revoscalepy) dans `/opt/mssql/mlservices/libraries/PythonServer`.

Intégration des fonctionnalités Java n’inclut pas les bibliothèques, mais vous pouvez exécuter `grep -r JAVA_HOME /etc` pour confirmer la création de la variable d’environnement JAVA_HOME.

Pour valider l’installation, exécutez un script T-SQL qui exécute une procédure stockée système appel R ou Python. Vous aurez besoin un outil de requête pour cette tâche. Azure Data Studio est un bon choix. Autres outils couramment utilisés tels que SQL Server Management Studio ou PowerShell sont Windows uniquement. Si vous avez un ordinateur Windows grâce à ces outils, utilisez-le pour vous connecter à votre installation de Linux du moteur de base de données.

Exécutez la commande SQL suivante pour tester l’exécution de R dans SQL Server. Si le script ne s’exécute pas, essayez de redémarrage d’un service, `sudo systemctl restart mssql-server.service`.

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

## <a name="chained-combo-install"></a>Chaînées « zone de liste déroulante » installer

Vous pouvez installer et configurer le moteur de base de données et les Services Machine Learning dans une procédure en ajoutant des packages R, Python ou Java et des paramètres sur une commande qui installe le moteur de base de données. 

1. Pour l’intégration de R, installez [Microsoft R Open](#mro) comme condition préalable. Ignorez cette étape si vous n’installez pas la fonctionnalité R.

2. Fournir une ligne de commande qui inclut le moteur de base de données, ainsi que les fonctionnalités d’extension de langage.

  Vous pouvez ajouter une fonctionnalité unique, tels que Java installer integration, un moteur de base de données.

  ```bash
  sudo yum install -y mssql-server mssql-server-extensibility-java 
  ```

  Ou bien, ajoutez toutes les extensions (Java, R, Python).

  ```bash
  sudo yum install -y mssql-server mssql-server-extensibility-java mssql-mlservices-packages-r-9.4.6* mssql-mlservices-packages-py-9.4.6*
  ```

3. Accepter les contrats de licence et terminer la configuration de post-installation. Utilisez le **mssql-conf** outil pour cette tâche.

  ```bash
  sudo /opt/mssql/bin/mssql-conf setup
  ```

  Vous êtes invité à accepter le contrat de licence pour le moteur de base de données, choisissez une édition et définir le mot de passe administrateur. Vous êtes également invité à accepter le contrat de licence pour Machine Learning Services.

4. Redémarrez le service, si vous êtes invité à le faire.

  ```bash
  sudo systemctl restart mssql-server.service
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

Vous pouvez télécharger des packages à partir de [ https://packages.microsoft.com/ ](https://packages.microsoft.com/). Tous les packages mlservices pour R, Python et Java sont colocalisés avec le package du moteur de base de données. Version de base pour les packages mlservices est 9.4.5 (pour CTP 2.0) 9.4.6 (CTP 2.1 et versions ultérieures). Souvenez-vous que les packages microsoft-r-open se trouvent dans un [autre dépôt](#mro).

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
| packages de MSSQL/mlservices | [https://packages.microsoft.com/sles/12/mssql-server-preview/](https://packages.microsoft.com/sles/12/mssql-server-preview/) |
| packages Microsoft-r-open | [https://packages.microsoft.com/sles/12/prod/](https://packages.microsoft.com/sles/12/prod/) | 

#### <a name="package-list"></a>Liste des packages

Selon les extensions que vous souhaitez utiliser, télécharger les packages nécessaires pour une langue spécifique. Noms de fichiers incluent des informations sur la plateforme dans le suffixe, mais les noms de fichier ci-dessous doivent être suffisamment proches pour vous permettre de déterminer les fichiers à obtenir.

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
mssql-mlservices-packages-r-9.4.6.523
mssql-mlservices-mlm-r-9.4.6.523
mssql-mlservices-mml-r-9.4.6.523

# Python
microsoft-openmpi-3.0.0
mssql-mlservices-python-9.4.6.523
mssql-mlservices-packages-py-9.4.6.523
mssql-mlservices-mlm-py-9.4.6.523
mssql-mlservices-mml-py-9.4.6.523
```

#### <a name="package-list-for-original-ctp-20-and-21"></a>Liste des packages d’origine CTP 2.0 et 2.1

Supprime de la CTP 2.2 **mssql-mlservices-mlm-py** et **mssql-mlservices-mlm-r** grâce à la consolidation de package dans **mssql-mlservices-packages-py** et **mssql-mlservices-packages-r**, respectivement.

Si vous avez besoin en particulier le CTP 2.0 d’origine ou 2.1 packages, téléchargez les packages suivants :

* Pour CTP 2.0, téléchargez les versions de package 9.4.5

* Pour CTP 2.1, téléchargez les versions de package 9.4.6.237


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

## <a name="limitations-in-ctp-releases"></a>Limitations dans les versions CTP

Intégration de R, Python et Java sur Linux est toujours en cours de développement. Les fonctionnalités suivantes ne sont pas encore disponibles dans la version d’évaluation.

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
+ [Didacticiel : Analytique en base de données pour les développeurs R](../advanced-analytics/tutorials/sqldev-in-database-r-for-sql-developers.md)

Les développeurs Python peuvent apprendre à utiliser Python avec SQL Server en suivant ces didacticiels :

+ [Didacticiel : Exécutez le code Python dans T-SQL](../advanced-analytics/tutorials/run-python-using-t-sql.md)
+ [Didacticiel : Analytique en base de données pour les développeurs Python](../advanced-analytics/tutorials/sqldev-in-database-python-for-sql-developers.md)

Pour afficher des exemples d’apprentissage qui sont basées sur des scénarios réels, consultez [d’apprentissage didacticiels](../advanced-analytics/tutorials/machine-learning-services-tutorials.md).
