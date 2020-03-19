---
title: Installer SQL Server Machine Learning Services (Python, R) sur Linux
description: 'Découvrez comment installer SQL Server Machine Learning Services (Python et R) sur Linux : Red Hat, Ubuntu et SUSE.'
author: cawrites
ms.author: chadam
ms.reviewer: vanto
manager: cgronlun
ms.date: 03/05/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: machine-learning
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: bf474ff8a7587c916591e6d7ba4dc82052b516f7
ms.sourcegitcommit: fc99fdd586eabc2d60f33056123398f263d5913d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/09/2020
ms.locfileid: "78937651"
---
# <a name="install-sql-server-machine-learning-services-python-and-r-on-linux"></a>Installer SQL Server Machine Learning Services (Python et R) sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Cet article vous guide lors de l’installation de [SQL Server Machine Learning Services](../advanced-analytics/index.yml) sur Linux. Les scripts Python et R peuvent être exécutés dans la base de données à l’aide de Machine Learning Services.

[!NOTE]
> Machine Learning Services est installé par défaut sur des Clusters Big Data SQL Server. Pour plus d’informations, consultez [Utiliser Machine Learning Services (Python et R) sur des clusters Big Data](../big-data-cluster/machine-learning-services.md).

## <a name="what-are-machine-learning-services"></a>Qu’est-ce que Machine Learning Services ?

Machine Learning Services est un module complémentaire de fonctionnalités du moteur de base de données.

Installez et configurez d’abord le moteur de base de données SQL Server pour pouvoir résoudre les éventuels problèmes avant d’ajouter d’autres composants.

## <a name="pre-install-checklist"></a>Liste de contrôle avant l’installation

[Installez SQL Server sur Linux](https://docs.microsoft.com/sql/linux/sql-server-linux-setup) et vérifiez l’installation.

* Vérifiez la présence des extensions Python et R dans les référentiels Linux SQL Server. 
* Si vous avez déjà configuré des référentiels source pour l’installation du moteur de base de données, vous pouvez exécuter les commandes d’installation du package **mssql-mlservices** à l’aide de la même inscription de référentiel.

* [Microsoft R Open](#mro) fournit la distribution R de base pour la fonctionnalité R dans SQL Server

* Vous devez disposer d’un outil pour l’exécution des commandes T-SQL. 
* Un éditeur de requête est nécessaire pour la configuration et la validation postérieures à l’installation. 
* Nous vous recommandons [Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/download?view=sql-server-2017#get-azure-data-studio-for-linux), un outil en téléchargement gratuit qui s’exécute sur Linux.


<a name="mro"></a>

### <a name="microsoft-r-open-mro-installation"></a>Installation de Microsoft R Open (MRO)

La distribution de base de R de Microsoft est une condition préalable à l’utilisation de RevoScaleR, MicrosoftML et d’autres packages R installés avec Machine Learning Services.

La version requise est MRO 3.5.2.

Choisissez une des deux approches suivantes pour installer MRO :

+ Téléchargez le tarball MRO à partir de MRAN, décompressez-le, puis exécutez son script install.sh. Vous pouvez suivre les [instructions d’installation sur MRAN](https://mran.microsoft.com/releases/3.5.2) si vous souhaitez adopter cette approche.

+ Inscrivez le référentiel **packages.microsoft.com** comme décrit ci-dessous pour installer la distribution MRO : microsoft-r-open-mro et microsoft-r-open-mkl. 

<a name="RHEL"></a>

## <a name="install-on-redhat"></a>Installer sur RedHat

### <a name="install-mro-on-red-hat"></a>Installer (MRO) sur Red Hat

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

Options d’installation pour Python et R :

*  Installez la prise en charge linguistique en fonction de vos besoins (une ou plusieurs langues).
*  L’*installation complète* fournit toutes les fonctionnalités disponibles, y compris les modèles de Machine Learning préentraînés.
*  L’*installation minimale* exclut les modèles mais offre toutes les fonctionnalités.

> [!Tip]
> Si possible, exécutez `yum clean all` pour actualiser les packages sur le système avant l’installation.

### <a name="example-1----full-installation"></a>Exemple 1 : Installation complète

Inclut :
*  Python open source
*  R open source
*  Framework d’extensibilité
*  microsoft-openmpi
*  Extensions (Python, R)
*  Bibliothèques de Machine Learning
*  Modèles préentraînés pour Python et R

```bash
# Install as root or sudo
# Add everything (all R, Python)
# Be sure to include -9.4.7* in mlsservices package names
sudo yum install mssql-mlservices-mlm-py-9.4.7*
sudo yum install mssql-mlservices-mlm-r-9.4.7*
```

### <a name="example-2---minimum-installation"></a>Exemple 2 : Installation minimale

Inclut :
*  Python open source
*  R open source
*  Framework d’extensibilité
*  microsoft-openmpi
*  Bibliothèques Revo* principales
*  Bibliothèques de Machine Learning

```bash
# Install as root or sudo
# Minimum install of R, Python extensions
# Be sure to include -9.4.6* in mlsservices package names
sudo yum install mssql-mlservices-packages-py-9.4.7*
sudo yum install mssql-mlservices-packages-r-9.4.7*
```
<a name="ubuntu"></a>

## <a name="install-on-ubuntu"></a>Installer sur Ubuntu

### <a name="install-mro-on-ubuntu"></a>Installer (MRO) sur Ubuntu

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

Options d’installation pour Python et R :

*  Installez la prise en charge linguistique en fonction de vos besoins (une ou plusieurs langues).
*  L’*installation complète* fournit toutes les fonctionnalités disponibles, y compris les modèles de Machine Learning préentraînés.
*  L’*installation minimale* exclut les modèles mais offre toutes les fonctionnalités.

> [!Tip]
> Si possible, exécutez `apt-get update` pour actualiser les packages sur le système avant l’installation. 

### <a name="example-1----full-installation"></a>Exemple 1 : Installation complète 

Inclut :
*  Python open source
*  R open source
*  Framework d’extensibilité
*  microsoft-openmpi
*  Extensions Python
*  Extensions R
*  Bibliothèques de Machine Learning
*  Modèles préentraînés pour Python et R

```bash
# Install as root or sudo
# Add everything (all R, Python)
# There is no asterisk in this full install
sudo apt-get install mssql-mlservices-mlm-py 
sudo apt-get install mssql-mlservices-mlm-r 
```

### <a name="example-2---minimum-installation"></a>Exemple 2 : Installation minimale 

Inclut :
*  Python open source
*  R open source
*  Framework d’extensibilité
*  microsoft-openmpi
*  Bibliothèques Revo* principales
*  Bibliothèques de Machine Learning

```bash
# Install as root or sudo
# Minimum install of R, Python
# No asterisk
sudo apt-get install mssql-mlservices-packages-py
sudo apt-get install mssql-mlservices-packages-r
```

<a name="SLES"></a>

## <a name="install-on-suse"></a>Installer sur SUSE

### <a name="install-mro-on-susesles"></a>Installer (MRO) sur SUSE(SLES)

```bash
# Install as root
sudo su

# Set the location of the package repo at the "prod" directory containing the distribution
# This example is for SLES12, the only supported version of SUSE in Machine Learning Server
zypper ar -f https://packages.microsoft.com/sles/12/prod packages-microsoft-com

# Update packages on your system (optional)
zypper update
```

Options d’installation pour Python et R :

*  Installez la prise en charge linguistique en fonction de vos besoins (une ou plusieurs langues).
*  L’*installation complète* fournit toutes les fonctionnalités disponibles, y compris les modèles de Machine Learning préentraînés.
*  L’*installation minimale* exclut les modèles mais offre toutes les fonctionnalités.

### <a name="example-1----full-installation"></a>Exemple 1 : Installation complète 

Inclut :
*  Python open source
*  R open source
*  Framework d’extensibilité
*  microsoft-openmpi
*  Extensions pour Python et R
*  Bibliothèques de Machine Learning
*  Modèles préentraînés pour Python et R

```bash
# Install as root or sudo
# Add everything (all R, Python)
# Be sure to include -9.4.7* in mlsservices package names
sudo zypper install mssql-mlservices-mlm-py-9.4.7*
sudo zypper install mssql-mlservices-mlm-r-9.4.7* 
```

### <a name="example-2---minimum-installation"></a>Exemple 2 : Installation minimale 

Inclut :
*  Python open source
*  R open source
*  Framework d’extensibilité
*  microsoft-openmpi
*  Bibliothèques Revo* principales
*  Bibliothèques de Machine Learning 

```bash
# Install as root or sudo
# Minimum install of R, Python extensions
# Be sure to include -9.4.6* in mlsservices package names
sudo zypper install mssql-mlservices-packages-py-9.4.7*
sudo zypper install mssql-mlservices-packages-r-9.4.7*
```

## <a name="post-install-config-required"></a>Configuration après installation (obligatoire)

La configuration supplémentaire s’effectue principalement avec [l’outil mssql-conf](sql-server-linux-configure-mssql-conf.md).


1. Ajoutez le compte d’utilisateur mssql utilisé pour exécuter le service SQL Server.

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

2. Acceptez les contrats de licence pour les extensions Python et R open source. Utilisez la commande suivante :

   ```bash
   # Run as SUDO or root
   # Use set + EULA 
   sudo /opt/mssql/bin/mssql-conf set EULA accepteulaml Y
   ```
3. Le programme d’installation détecte les packages mssql-mlservices et demande l’acceptation du CLUF (s’il n’a pas encore été accepté) lors de l’exécution de `mssql-conf setup`. Pour plus d’informations sur les paramètres de CLUF, consultez [Configurer SQL Server avec l’outil mssql-conf](sql-server-linux-configure-mssql-conf.md#mlservices-eula).

4. Activez l’accès réseau sortant. L’accès réseau sortant est désactivé par défaut. Pour activer les requêtes sortantes, définissez la propriété booléenne « outboundnetworkaccess » à l’aide de l’outil mssql-conf. Pour plus d’informations, consultez [Configurer SQL Server sur Linux avec mssql-conf](sql-server-linux-configure-mssql-conf.md#mlservices-outbound-access).

   ```bash
   # Run as SUDO or root
   # Enable outbound requests over the network
   sudo /opt/mssql/bin/mssql-conf set extensibility outboundnetworkaccess 1
   ```

5. Pour l’intégration de fonctionnalités R uniquement, définissez la variable d' environnement **MKL_CBWR** pour [garantir la cohérence de la sortie](https://software.intel.com/articles/introduction-to-the-conditional-numerical-reproducibility-cnr) des calculs d’Intel Math Kernel Library (MKL).

   + Modifiez ou créez un fichier `named.bash_profile` dans le répertoire racine de votre utilisateur en ajoutant la ligne `export MKL_CBWR="AUTO"` au fichier.

   + Exécutez ce fichier en saisissant `source.bash_profile` à l’invite de commandes bash.

6. Redémarrez le service SQL Server Launchpad et l’instance du moteur de base de données pour lire les valeurs mises à jour à partir du fichier INI. Un message de notification s’affiche quand un paramètre relatif à l’extensibilité est modifié.  

   ```bash
   systemctl restart mssql-launchpadd

   systemctl restart mssql-server.service
   ```

7. Activez l’exécution du script externe à l’aide d’Azure Data Studio ou d’un autre outil comme SQL Server Management Studio (Windows uniquement) qui exécute Transact-SQL. 

   ```bash
   EXEC sp_configure 'external scripts enabled', 1 
   RECONFIGURE WITH OVERRIDE 
   ```

7. Redémarrez le service Launchpad.

## <a name="verify-installation"></a>Vérifier l'installation

Les bibliothèques R (MicrosoftML, RevoScaleR et autres) sont disponibles sur `/opt/mssql/mlservices/libraries/RServer`.

Les bibliothèques Python (microsoftml et revoscalepy) sont disponibles sur `/opt/mssql/mlservices/libraries/PythonServer`.

Pour valider l’installation

- Exécutez un script T-SQL qui exécute une procédure stockée système appelant Python ou R à l’aide d’un outil de requête. 

Pour Windows, utilisez : 
*  Azure Data Studio
*  SQL Server Management Studio ou PowerShell

Si vous disposez d’un ordinateur Windows avec ces outils, utilisez-le pour vous connecter à votre installation Linux du moteur de base de données.

Exécutez la commande SQL suivante pour tester l’exécution de R dans SQL Server. Des erreurs ? Essayez un redémarrage du service, `sudo systemctl restart mssql-server.service`.

```
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

## <a name="unattended-installation"></a>Installation sans assistance

À l'aide de [l’installation sans assistance](https://docs.microsoft.com/sql/linux/sql-server-linux-setup?view=sql-server-2017#unattended) du moteur de base de données, ajoutez les packages pour mssql-mlservices et les CLUF.

 Utilisez l’un des paramètres de CLUF propres à mlservices pour les distributions R et Python open source :

```bash
sudo /opt/mssql/bin/mssql-conf setup accept-eula-ml
```

Le CLUF complet est documenté dans [Configurer SQL Server sur Linux avec l’outil mssql-conf](sql-server-linux-configure-mssql-conf.md#mlservices-eula).

## <a name="offline-installation"></a>Installation hors connexion

Suivez les instructions [d'installation hors connexion](sql-server-linux-setup.md#offline) pour connaître les étapes d’installation des packages. Téléchargez des packages spécifiques en vous référant à la liste de packages ci-dessous.

> [!Tip]
> Plusieurs outils de gestion des packages fournissent des commandes qui peuvent vous aider à déterminer les dépendances du package. Pour yum, utilisez `sudo yum deplist [package]`. Pour Ubuntu, utilisez `sudo apt-get install --reinstall --download-only [package name]`, suivi de `dpkg -I [package name].deb`.


#### <a name="download-site"></a>Site de téléchargement

Téléchargez des packages à partir de [https://packages.microsoft.com/](https://packages.microsoft.com/). Tous les packages mlservices pour Python et R sont colocalisés avec le package du moteur de base de données. La version de base des packages mlservices est 9.4.6 Souvenez-vous que les packages microsoft-r-open se trouvent dans un [autre référentiel](#mro).

#### <a name="rhel7-paths"></a>Chemins d’accès RHEL/7

|||
|--|----|
| Packages mssql/mlservices | [https://packages.microsoft.com/rhel/7/mssql-server-2019/](https://packages.microsoft.com/rhel/7/mssql-server-2019/) |
| Packages microsoft-r-open | [https://packages.microsoft.com/rhel/7/prod/](https://packages.microsoft.com/rhel/7/prod/) | 


#### <a name="ubuntu1604-paths"></a>Chemins d’accès Ubuntu/16.04

|||
|--|----|
| Packages mssql/mlservices | [https://packages.microsoft.com/ubuntu/16.04/mssql-server-2019/pool/main/m/](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2019/pool/main/m/) |
| Packages microsoft-r-open | [https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/) | 

#### <a name="sles12-paths"></a>Chemins d’accès SLES/12

|||
|--|----|
| Packages mssql/mlservices | [https://packages.microsoft.com/sles/12/mssql-server-preview/](https://packages.microsoft.com/sles/12/mssql-server-preview/) |
| Packages microsoft-r-open | [https://packages.microsoft.com/sles/12/prod/](https://packages.microsoft.com/sles/12/prod/) |

## <a name="package-list"></a>Liste des packages

Packages d’installation disponibles :

| Nom du package | S’applique à | Description |
|--------------|----------|-------------|
|mssql-server-extensibility  | Tous | Framework d’extensibilité utilisé pour exécuter Python et R. |
| microsoft-openmpi  | Python, R | Interface de passage de messages utilisée par les bibliothèques Revo* pour la parallélisation sur Linux. |
| mssql-mlservices-python | Python | Distribution open source d’Anaconda et de Python. |
|mssql-mlservices-mlm-py  | Python | *Installation complète*. Fournit des modèles préformés, revoscalepy et microsoftml pour la caractérisation d’images et l’analyse textuelle des sentiments.| 
|mssql-mlservices-packages-py  | Python | *Installation minimale*. Fournit revoscalepy et microsoftml. <br/>Exclut les modèles préformés. | 
| [microsoft-r-open*](#mro) | R | Distribution open source de R, composée de trois packages. |
|mssql-mlservices-mlm-r  | R | *Installation complète*. Fournit : RevoScaleR, MicrosoftML, sqlRUtils, olapR des modèles préentraînés pour la caractérisation d’images et l’analyse des sentiments dans un texte.| 
|mssql-mlservices-packages-r  | R | *Installation minimale*. Fournit RevoScaleR, sqlRUtils, MicrosoftML et olapr. <br/>Exclut les modèles préformés. |

Sélectionnez les extensions que vous souhaitez utiliser et téléchargez les packages nécessaires pour un langage spécifique. Les noms de fichiers incluent des informations sur la plateforme dans le suffixe.

Liste de fichiers :

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

## <a name="next-steps"></a>Étapes suivantes

Les développeurs peuvent démarrer avec quelques exemples simples et découvrir les principes de base du fonctionnement de R avec SQL Server. Pour l’étape suivante, consultez les liens suivants :

+ [Tutoriel : Exécuter R dans T-SQL](../advanced-analytics/tutorials/quickstart-r-create-script.md)
+ [Tutoriel : Analytique dans la base de données pour les développeurs R](../advanced-analytics/tutorials/sqldev-in-database-r-for-sql-developers.md)

Les développeurs Python peuvent apprendre à utiliser Python avec SQL Server en effectuant les didacticiels suivants :

+ [Tutoriel : Exécuter Python dans T-SQL](../advanced-analytics/tutorials/run-python-using-t-sql.md)
+ [Tutoriel : Analytique dans la base de données pour les développeurs Python](../advanced-analytics/tutorials/sqldev-in-database-python-for-sql-developers.md)

Pour consulter des exemples d’apprentissage automatique basés sur des scénarios réels, consultez les [Didacticiels d’apprentissage automatique](../advanced-analytics/tutorials/machine-learning-services-tutorials.md).
