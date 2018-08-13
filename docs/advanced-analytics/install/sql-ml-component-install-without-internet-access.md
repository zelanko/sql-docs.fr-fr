---
title: Installer les composants de SQL Server machine Learning Services sans accès à internet | Microsoft Docs
description: En mode hors connexion ou déconnecté R Machine Learning et Pytyon le programme d’installation sur l’instance de SQL Server isolé.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/02/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 56624d2a5fcc97035f434cb1ee1d4fdee4dedeba
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39546259"
---
# <a name="install-sql-server-machine-learning-r-and-python-features-on-computers-with-no-internet-access"></a>Installer les fonctionnalités de R et Python sur des ordinateurs sans accès à internet d’apprentissage SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Par défaut, les programmes d’installation de se connecter à des sites de téléchargement Microsoft pour obtenir requis et les composants mis à jour pour machine learning sur SQL Server. Si des contraintes de pare-feu empêchent le programme d’installation d’atteindre ces sites, vous pouvez utiliser un périphérique connecté à internet pour télécharger les fichiers, transférer des fichiers vers un serveur hors connexion, puis exécutez le programme d’installation.

Dans la base de données analytique se composent d’instance du moteur de base de données, ainsi que des composants supplémentaires pour l’intégration de R et Python, selon la version de SQL Server. 

+ SQL Server 2017 inclut R et Python. 
+ SQL Server 2016 est R uniquement. 

Sur un serveur isolé, apprentissage automatique et des fonctionnalités de langage spécifiques R/Python sont ajoutées par le biais des fichiers CAB. 

## <a name="sql-server-2017-offline-install"></a>Installation hors connexion SQL Server 2017

Pour installer SQL Server 2017 Machine Learning Services (R et Python) sur un serveur isolé, commencez par télécharger la version initiale de SQL Server et les fichiers CAB correspondants pour R et Python prennent en charge. Même si vous envisagez de mettre immédiatement à jour votre serveur pour utiliser la mise à jour cumulative la plus récente, une version initiale doit être installée en premier.

> [!Note]
> SQL Server 2017 n’a pas les service packs. Il est la première version de SQL Server à utiliser la version initiale comme la seule ligne de base, avec la maintenance par le biais des mises à jour cumulatives uniquement. 

### <a name="1---download-2017-cabs"></a>1 - télécharger des fichiers CAB 2017

Sur un ordinateur ayant une connexion internet, téléchargez les fichiers CAB proposant des fonctionnalités de R et Python pour la version initiale et le support d’installation SQL Server 2017. 

Version  |Télécharger le lien  |
---------|---------------|
Microsoft R Open     |[SRO_3.3.3.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851496)|
Microsoft R Server      |[SRS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851507)|
Python de Microsoft Open     |[SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502) |
Serveur Microsoft Python    |[SPS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851508) |

###  <a name="2---get-sql-server-2017-installation-media"></a>2 - obtenir le support d’installation de SQL Server 2017

1. Sur un ordinateur ayant une connexion internet, téléchargez le [programme d’installation de SQL Server 2017](https://www.microsoft.com/sql-server/sql-server-downloads). 

2. Double-cliquez sur le programme d’installation et choisissez le **Media télécharger** type d’installation. Avec cette option, le programme d’installation crée un fichier .iso (ou .cab) local contenant le support d’installation.

   ![Choisissez le média de téléchargement de type d’installation](media/offline-download-tile.png "télécharger le support")

## <a name="sql-server-2016-offline-install"></a>Installation hors connexion SQL Server 2016

Analytique en base de données de SQL Server 2016 est R uniquement, avec deux fichiers CAB pour les packages de produit et de distribution Microsoft de R open source, respectivement. Commencez par installer l’une de ces versions : RTM, Service Pack 1, Service Pack 2. Une fois qu’une installation de base est en place, les mises à jour cumulatives peuvent être appliquées comme prochaine étape.

Sur un ordinateur ayant une connexion internet, téléchargez les fichiers CAB utilisés par le programme d’installation pour installer la base de données analytique sur SQL Server 2016. 

### <a name="1---download-2016-cabs"></a>1 - télécharger des fichiers CAB 2016

Version  | Microsoft R Open | Microsoft R Server |
---------|-----------------|---------------------|
**SQL Server 2016 RTM**     | [SRO_3.2.2.803_1033.cab](https://go.microsoft.com/fwlink/?LinkId=761266) |[SRS_8.0.3.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=735051) |
**SQL Server 2016 SP 1**     | [SRO_3.2.2.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824879) |[SRS_8.0.3.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824881) | 
**SQL Server 2016 Service Pack 2**  |[SRO_3.2.2.20000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866039) |[SRS_8.0.3.20000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866038) |

### <a name="2---get-sql-server-2016-installation-media"></a>2 - obtenir le support d’installation de SQL Server 2016

Vous pouvez installer SQL Server 2016 RTM, Service Pack 1 ou Service Pack 2 en tant que votre première installation sur l’ordinateur cible. Ces versions peuvent accepter une mise à jour cumulative.

Vous pouvez notamment créer un fichier .iso contenant le support d’installation s’effectue via [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/). Connectez-vous, puis utiliser le **télécharge** lien pour rechercher la version de SQL Server 2016 à installer. Le téléchargement est sous la forme d’un fichier .iso, que vous pouvez copier sur l’ordinateur cible pour une installation hors connexion.

## <a name="transfer-files"></a>Transférer des fichiers

Copiez les fichiers de la base de données analytique CAB et le support d’installation de SQL Server (fichier .iso ou .cab) sur l’ordinateur cible. Placer les fichiers CAB et le fichier de média d’installation dans le même dossier sur l’ordinateur cible, tel que **télécharge** ou le dossier temp * % de l’utilisateur le programme d’installation.

La capture d’écran suivante montre les fichiers CAB de SQL Server 2017 et ISO. Téléchargements de SQL Server 2016 ont une apparence différentes : nom de fichier moins de fichiers (aucune Python) et le support d’installation est pour 2016.

![Liste des fichiers à transférer](media/offline-file-list.png "liste de fichiers")

## <a name="run-setup"></a>Exécutez le programme d’installation

Lorsque vous exécutez le programme d’installation de SQL Server sur un ordinateur déconnecté d’internet, le programme d’installation ajoute un **installation hors connexion** page Assistant afin que vous pouvez spécifier l’emplacement des fichiers CAB que vous avez copiée à l’étape précédente.

1. Pour commencer l’installation, double-cliquez sur le fichier .iso ou .cab pour accéder au support d’installation. Vous devez voir le **setup.exe** fichier.

2. Avec le bouton droit **setup.exe** et exécuter en tant qu’administrateur.

3. Lorsque l’Assistant Installation affiche la page de licence pour les composants de R ou Python open source, cliquez sur **Accept**. Acceptation des termes du contrat de licence vous permet de passer à l’étape suivante.

4. Lorsque vous arrivez à la **installation hors connexion** page **chemin d’installation**, spécifiez le dossier contenant les fichiers CAB que vous avez copiée précédemment.

   ![Page de l’Assistant pour la sélection du dossier cab](media/screenshot-sql-offline-cab-page.png "dossier du fichier CAB")

5. Continuer suivant les invites à l’écran pour terminer l’installation.

## <a name="post-install-configuration"></a>Configuration de post-installation

Une fois l’installation est terminée, redémarrez le service et puis configurez le serveur pour permettre l’exécution du script :

+ [Activer l’exécution du script externe (SQL Server 2017)](sql-machine-learning-services-windows-install.md#bkmk_enableFeature)
+ [Activer l’exécution du script externe (SQL Server 2016)](sql-r-services-windows-install.md#bkmk_enableFeature)

Une installation hors connexion initiale de SQL Server 2017 Machine Learning Services ou SQL Server 2016 R Services requiert la même configuration qu’une installation en ligne :

+ [Vérifier l’installation](sql-machine-learning-services-windows-install.md#verify-installation) (pour SQL Server 2016, cliquez sur [ici](sql-r-services-windows-install.md#verify-installation)).
+ [Une configuration supplémentaire si nécessaire](sql-machine-learning-services-windows-install.md#additional-configuration) (pour SQL Server 2016, cliquez sur [ici](sql-r-services-windows-install.md#bkmk_FollowUp)).

<a name="slipstream-upgrades"></a>

## <a name="slipstream-upgrades"></a>Mises à niveau de l’installation intégrée

Une installation intégrée renvoie à la possibilité d’appliquer un correctif ou une mise à jour à une installation d’instance défaillante dans le but de corriger les problèmes existants. L’avantage de cette méthode est que SQL Server est mis à jour en même temps que vous effectuez l’installation, ce qui évite d’avoir à effectuer par la suite un redémarrage séparé.

Lorsqu’un serveur n’a pas accès à Internet, les mises à jour de service sont appliquées en téléchargeant une mise à jour SQL Server programme d’installation et les versions correspondantes des fichiers CAB de spécifique à la langue. 

1. Démarrez avec une instance de la ligne de base. Mises à niveau de l’installation intégrée sont pris en charge sur ces versions de SQL Server :

  + Version initiale de SQL Server 2017
  + Version initiale de SQL Server 2016
  + SQL Server 2016 Service Pack 1
  + SQL Server 2016 Service Pack 2

2. Obtenir une version mise à jour du programme d’installation de SQL Server pour une mise à jour cumulative donné. Toute mise à jour les fonctionnalités d’apprentissage (R et Python) de machine est en tandem avec une mise à jour cumulative de l’instance du moteur de base de données sous-jacente.

  + [Mises à jour de SQL Server 2016](https://sqlserverupdates.com/sql-server-2016-updates/)
  + [Mises à jour de SQL Server 2017](https://sqlserverupdates.com/sql-server-2017-updates/)

3. Obtenir les fichiers CAB correspondants pour R et Python. Pour obtenir des liens de téléchargement, consultez [CAB télécharge les mises à jour cumulatives sur analytique en base de données de SQL Server instances](sql-ml-cab-downloads.md).

4. Placez tous les fichiers dans le même dossier, exécutez le programme d’installation. Pendant l’installation, vous êtes invité à choisir l’emplacement du dossier pour les fichiers CAB mis à jour.

## <a name="next-steps"></a>Étapes suivantes

Pour vérifier l’état d’installation de l’instance et résoudre les problèmes courants, consultez [rapports personnalisés pour SQL Server R Services](../r/monitor-r-services-using-custom-reports-in-management-studio.md).

Pour plus d’aide sur les messages non connus ou les entrées de journal, consultez [mise à niveau et installation FAQ - Services Machine Learning](../r/upgrade-and-installation-faq-sql-server-r-services.md).

