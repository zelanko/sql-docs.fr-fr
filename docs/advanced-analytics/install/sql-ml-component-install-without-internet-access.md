---
title: Installer sans accès à Internet
description: Installer les composants de machine learning SQL Server R et Python sur un ordinateur isolé derrière un pare-feu réseau.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/04/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: e966406a20df723c453a5c8083f00f2e4989d9d0
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "74064127"
---
# <a name="install-sql-server-machine-learning-r-and-python-on-computers-with-no-internet-access"></a>Installer les composants de machine learning SQL Server R et Python sur un ordinateur sans accès à Internet
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Par défaut, les programmes d’installation se connectent aux sites de téléchargement Microsoft pour obtenir les composants nécessaires à jour pour le machine learning sur SQL Server. Si les contraintes de pare-feu empêchent le programme d’installation d’y accéder, vous pouvez utiliser un appareil connecté à Internet pour télécharger les fichiers, transférer ces fichiers vers un serveur hors connexion, puis exécuter le programme d’installation.

L’analytique en base de données repose sur une instance du moteur de base de données et des composants supplémentaires pour l’intégration de R et Python selon la version de SQL Server. 

+ SQL Server 2019 comprend R, Python et Java.
+ SQL Server 2017 comprend R et Python.
+ SQL Server 2016 comprend R uniquement.

Sur un serveur isolé, des fonctionnalités spécifiques au machine learning et aux langages R/Python sont ajoutées par le biais de fichiers CAB. 

::: moniker range="=sql-server-ver15||=sqlallproducts-allversions"
## <a name="sql-server-2019-offline-install"></a>Installation hors connexion de SQL Server 2019

Pour installer SQL Server Machine Learning Services (R et Python) sur un serveur isolé, commencez par télécharger la version initiale de SQL Server et les fichiers CAB correspondants pour la prise en charge de R et Python. Même si vous envisagez de mettre à jour immédiatement votre serveur pour utiliser la mise à jour cumulative la plus récente, vous devez d’abord installer une version initiale.

> [!Note]
> SQL Server 2019 ne dispose pas de Service Packs. La version initiale est la seule base de référence. Sa maintenance s’effectue par le biais de mises à jour cumulatives uniquement.

### <a name="1---download-2019-cabs"></a>1 - Télécharger les fichiers CAB 2019

Sur un ordinateur disposant d’une connexion Internet, téléchargez les fichiers CAB fournissant les fonctionnalités R et Python pour la version initiale et le support d’installation pour SQL Server 2019.

Libérer  |Télécharger le lien  |
---------|---------------|
Microsoft R Open        | [SRO_3.5.2.125_1033.cab](https://go.microsoft.com/fwlink/?linkid=2085686) |
Microsoft R Server      | [SRS_9.4.7.25_1033.cab](https://go.microsoft.com/fwlink/?linkid=2085792) |
Microsoft Python Open   | [SPO_4.5.12.120_1033.cab](https://go.microsoft.com/fwlink/?linkid=2085793) |
Microsoft Python Server | [SPS_9.4.7.25_1033.cab](https://go.microsoft.com/fwlink/?linkid=2085685) |

> [!NOTE]
> La fonctionnalité Java est incluse dans le support d’installation de SQL Server et ne nécessite pas de fichier CAB distinct.

###  <a name="2---get-sql-server-2019-installation-media"></a>2 - Récupérer un support d’installation de SQL Server 2019

1. Sur un ordinateur disposant d’une connexion Internet, téléchargez le [programme d’installation de SQL Server 2019](https://www.microsoft.com/sql-server/sql-server-downloads). 

2. Double-cliquez sur le programme d’installation et choisissez le type d’installation **Télécharger le support**. Avec cette option, le programme d’installation crée un fichier .iso (ou .cab) local contenant le support d’installation.

   ![Choisir le type d’installation Télécharger le support](media/2019offline-download-tile.png "Télécharger le support")

::: moniker-end

::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
## <a name="sql-server-2017-offline-install"></a>Installation hors connexion de SQL Server 2017

Pour installer SQL Server Machine Learning Services (R et Python) sur un serveur isolé, commencez par télécharger la version initiale de SQL Server et les fichiers CAB correspondants pour la prise en charge de R et Python. Même si vous envisagez de mettre à jour immédiatement votre serveur pour utiliser la mise à jour cumulative la plus récente, vous devez d’abord installer une version initiale.

> [!Note]
> SQL Server 2017 ne dispose pas de Service Packs. Il s’agit de la première version de SQL Server utilisant la version initiale comme seule base de référence. Sa maintenance s’effectue par le biais de mises à jour cumulatives uniquement. 

### <a name="1---download-2017-cabs"></a>1 - Télécharger les fichiers CAB 2017

Sur un ordinateur disposant d’une connexion Internet, téléchargez les fichiers CAB fournissant les fonctionnalités R et Python pour la version initiale et le support d’installation pour SQL Server 2017. 

Libérer  |Télécharger le lien  |
---------|---------------|
Microsoft R Open     |[SRO_3.3.3.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851496)|
Microsoft R Server      |[SRS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851507)|
Microsoft Python Open     |[SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502) |
Microsoft Python Server    |[SPS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851508) |

###  <a name="2---get-sql-server-2017-installation-media"></a>2 - Récupérer un support d’installation de SQL Server 2017

1. Sur un ordinateur disposant d’une connexion Internet, téléchargez le [programme d’installation de SQL Server 2017](https://www.microsoft.com/sql-server/sql-server-downloads). 

2. Double-cliquez sur le programme d’installation et choisissez le type d’installation **Télécharger le support**. Avec cette option, le programme d’installation crée un fichier .iso (ou .cab) local contenant le support d’installation.

   ![Choisir le type d’installation Télécharger le support](media/offline-download-tile.png "Télécharger le support")

::: moniker-end

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"

## <a name="sql-server-2016-offline-install"></a>Installation hors connexion de SQL Server 2016

L’analytique en base de données sur SQL Server 2016 est en R uniquement. Elle implique seulement deux fichiers CAB : l’un pour les packages de produits et l’autre pour la distribution de R open source de Microsoft. Commencez par installer l’une des versions suivantes : RTM, SP 1 ou SP 2. Une fois qu’une installation de base est en place, les mises à jour cumulatives peuvent être appliquées.

Sur un ordinateur disposant d’une connexion Internet, téléchargez les fichiers CAB utilisés par le programme d’installation pour installer l’analytique en base de données sur SQL Server 2016. 

### <a name="1---download-2016-cabs"></a>1 - Télécharger les fichiers CAB 2016

Libérer  | Microsoft R Open | Microsoft R Server |
---------|-----------------|---------------------|
**SQL Server 2016 RTM**     | [SRO_3.2.2.803_1033.cab](https://go.microsoft.com/fwlink/?LinkId=761266) |[SRS_8.0.3.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=735051) |
**SQL Server 2016 SP 1**     | [SRO_3.2.2.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824879) |[SRS_8.0.3.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824881) | 
**SQL Server 2016 SP 2**  |[SRO_3.2.2.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866039) |[SRS_8.0.3.17000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=850317) |

### <a name="2---get-sql-server-2016-installation-media"></a>2 - Récupérer un support d’installation de SQL Server 2016

Vous pouvez installer SQL Server 2016 RTM, SP 1 ou SP 2 comme première installation sur l’ordinateur cible. Toutes ces versions peuvent accepter une mise à jour cumulative.

Pour obtenir un fichier .iso contenant le support d’installation, vous pouvez, par exemple, utiliser [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/). Connectez-vous, puis utilisez le lien **Téléchargements** pour trouver la version de SQL Server 2016 que vous souhaitez installer. Vous téléchargez alors un fichier .iso, que vous pouvez copier sur l’ordinateur cible pour une installation hors connexion.

::: moniker-end

## <a name="transfer-files"></a>Transférer les fichiers

Copiez le support d’installation de SQL Server (.iso ou .cab) et les fichiers CAB d’analytique en base de données sur l’ordinateur cible. Placez les fichiers CAB et le fichier du support d’installation dans le même dossier sur l’ordinateur cible, par exemple dans le dossier %TEMP% de l’utilisateur du programme d’installation.

Le dossier %TEMP% est requis pour les fichiers CAB Python. Pour R, vous pouvez utiliser le dossier %TEMP% ou définir le paramètre `myrcachedirectory` sur le chemin des fichiers CAB.

## <a name="run-setup"></a>Exécuter le programme d’installation

Quand vous exécutez le programme d’installation de SQL Server sur un ordinateur non connecté à Internet, le programme d’installation ajoute une page **Installation hors connexion** à l’Assistant, vous permettant de spécifier l’emplacement des fichiers CAB copiés à l’étape précédente.

1. Pour commencer l’installation, double-cliquez sur le fichier .iso ou .cab pour accéder au support d’installation. Vous devez voir le fichier **setup.exe**.

2. Cliquez avec le bouton droit sur le fichier **setup.exe** et exécutez-le en tant qu’administrateur.

3. Quand l’Assistant Installation affiche la page du contrat de licence pour les composants R ou Python open source, cliquez sur **Accepter**. L’acceptation des termes du contrat de licence vous permet de passer à l’étape suivante.

4. Quand vous accédez à la page **Installation hors connexion**, sous **Chemin d’installation**, spécifiez le dossier contenant les fichiers CAB que vous avez copiés précédemment.

5. Continuez à suivre les invites à l’écran pour terminer l’installation.

<a name="apply-cu"></a>

## <a name="apply-cumulative-updates"></a>Appliquer les mises à jour cumulatives

Nous vous recommandons d’appliquer la mise à jour cumulative la plus récente au moteur de base de données et aux composants de machine learning. Les mises à jour cumulatives sont installées par le biais du programme d’installation. 

::: moniker range="=sql-server-ver15||=sqlallproducts-allversions"
1. Commencez avec une instance de base. Vous pouvez appliquer des mises à jour cumulatives uniquement aux installations existantes de la version initiale de SQL Server.

2. Sur un appareil connecté à Internet, accédez à la liste des mises à jour cumulative pour votre version de SQL Server :

   + Mises à jour de SQL Server 2019 *(aucune mise à jour n’est actuellement disponible pour la version 2019)*
::: moniker-end

::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
1. Commencez avec une instance de base. Vous pouvez appliquer des mises à jour cumulatives uniquement aux installations existantes de la version initiale de SQL Server.

2. Sur un appareil connecté à Internet, accédez à la liste des mises à jour cumulative pour votre version de SQL Server :

   + [Mises à jour de SQL Server 2017](https://sqlserverupdates.com/sql-server-2017-updates/)
::: moniker-end

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
1. Commencez avec une instance de base. Vous pouvez appliquer des mises à jour cumulatives uniquement aux installations existantes de la version initiale de SQL Server 2016, de SQL Server 2016 SP 1 ou de SQL Server 2016 SP 2.

2. Sur un appareil connecté à Internet, accédez à la liste des mises à jour cumulative pour votre version de SQL Server :

   + [Mises à jour de SQL Server 2016](https://sqlserverupdates.com/sql-server-2016-updates/)
::: moniker-end

3. Sélectionnez la mise à jour cumulative la plus récente pour télécharger l’exécutable.

4. Récupérez les fichiers CAB correspondants pour R et Python. Pour obtenir les liens de téléchargement, consultez [Téléchargement des fichiers CAB pour les mises à jour cumulatives sur les instances d’analytique en base de données SQL Server](sql-ml-cab-downloads.md).

5. Transférez tous les fichiers, le fichier exécutable et les fichiers CAB, vers le même dossier sur l’ordinateur hors connexion.

6. Exécutez le programme d'installation. Acceptez les termes du contrat de licence, puis, dans la page Sélection de fonctionnalités, passez en revue les fonctionnalités pour lesquelles des mises à jour cumulatives sont appliquées. Vous devez voir toutes les fonctionnalités installées pour l’instance actuelle, y compris les fonctionnalités de machine learning.

   ![Sélectionner les fonctionnalités dans l’arborescence](media/cumulative-update-feature-selection.png "Liste des fonctionnalités")

5. Poursuivez avec l’Assistant en acceptant les termes du contrat de licence pour les distributions R et Python. Pendant l’installation, vous êtes invité à choisir l’emplacement du dossier contenant les fichiers CAB mis à jour.

## <a name="set-environment-variables"></a>Définir des variables d’environnement

Pour l’intégration de fonctionnalités R uniquement, vous devez définir la variable d’environnement **MKL_CBWR** pour [garantir la cohérence de la sortie](https://software.intel.com/articles/introduction-to-the-conditional-numerical-reproducibility-cnr) des calculs d’Intel Math Kernel Library (MKL).

1. Dans le Panneau de configuration, cliquez sur **Système et sécurité** > **Système** > **Paramètres système avancés** > **Variables d’environnement**.

2. Créez une variable Utilisateur ou Système. 

   + Nommez la variable `MKL_CBWR`.
   + Définissez la valeur de la variable sur `AUTO`.

Cette étape nécessite un redémarrage du serveur. Si vous vous apprêtez à activer l’exécution de scripts, vous pouvez reporter le redémarrage jusqu’à ce que le travail de configuration soit complètement terminé.

## <a name="post-install-configuration"></a>Configuration consécutive à l’installation

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
Une fois l’installation terminée, redémarrez le service, puis configurez le serveur pour activer l’exécution de scripts :

+ [Activer l’exécution de scripts externes](sql-machine-learning-services-windows-install.md#bkmk_enableFeature)

Une installation hors connexion initiale de SQL Server Machine Learning Services nécessite la même configuration qu’une installation en ligne :

+ [Vérifier l’installation](sql-machine-learning-services-windows-install.md#verify-installation)
+ [Configuration supplémentaire nécessaire](sql-machine-learning-services-windows-install.md#additional-configuration)
::: moniker-end

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
Une fois l’installation terminée, redémarrez le service, puis configurez le serveur pour activer l’exécution de scripts :

+ [Activer l’exécution de scripts externes](sql-r-services-windows-install.md#bkmk_enableFeature)

Une installation hors connexion initiale de SQL Server R Services nécessite la même configuration qu’une installation en ligne :

+ [Vérifier l’installation](sql-r-services-windows-install.md#verify-installation)
+ [Configuration supplémentaire nécessaire](sql-r-services-windows-install.md#bkmk_FollowUp)
::: moniker-end

## <a name="next-steps"></a>Étapes suivantes

Pour vérifier l’état d’installation de l’instance et résoudre les problèmes courants, consultez [Rapports personnalisés pour SQL Server](../r/monitor-r-services-using-custom-reports-in-management-studio.md).

Pour obtenir de l’aide sur les messages ou entrées de journal que vous ne connaissez pas, consultez [FAQ sur la mise à niveau et l’installation - Machine Learning Services](../r/upgrade-and-installation-faq-sql-server-r-services.md).
