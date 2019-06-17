---
title: Installer les composants de Python sans accès à internet - SQL Server Machine Learning et de langage R
description: En mode hors connexion ou déconnecté Machine Learning R et Python le programme d’installation sur isolé instance de SQL Server derrière un pare-feu réseau.
ms.prod: sql
ms.technology: machine-learning
ms.date: 03/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: da9676f029bb917adf15690b6870583fb0465fc4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65836216"
---
# <a name="install-sql-server-machine-learning-r-and-python-on-computers-with-no-internet-access"></a>Installer SQL Server d’apprentissage R et Python sur des ordinateurs sans accès à internet
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Par défaut, les programmes d’installation de se connecter à des sites de téléchargement Microsoft pour obtenir requis et les composants mis à jour pour machine learning sur SQL Server. Si des contraintes de pare-feu empêchent le programme d’installation d’atteindre ces sites, vous pouvez utiliser un périphérique connecté à internet pour télécharger les fichiers, transférer des fichiers vers un serveur hors connexion, puis exécutez le programme d’installation.

Dans la base de données analytique se composent d’instance du moteur de base de données, ainsi que des composants supplémentaires pour l’intégration de R et Python, selon la version de SQL Server. 

+ SQL Server 2017 inclut R et Python 
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

Analytique en base de données de SQL Server 2016 est R uniquement, avec deux fichiers CAB pour les packages de produit et de distribution Microsoft de R open source, respectivement. Démarrez en installant l’une de ces versions : RTM, SP 1, SP 2. Une fois qu’une installation de base est en place, les mises à jour cumulatives peuvent être appliquées comme prochaine étape.

Sur un ordinateur ayant une connexion internet, téléchargez les fichiers CAB utilisés par le programme d’installation pour installer la base de données analytique sur SQL Server 2016. 

### <a name="1---download-2016-cabs"></a>1 - télécharger des fichiers CAB 2016

Version  | Microsoft R Open | Microsoft R Server |
---------|-----------------|---------------------|
**SQL Server 2016 RTM**     | [SRO_3.2.2.803_1033.cab](https://go.microsoft.com/fwlink/?LinkId=761266) |[SRS_8.0.3.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=735051) |
**SQL Server 2016 SP 1**     | [SRO_3.2.2.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824879) |[SRS_8.0.3.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824881) | 
**SQL Server 2016 SP 2**  |[SRO_3.2.2.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866039) |[SRS_8.0.3.17000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=850317) |

### <a name="2---get-sql-server-2016-installation-media"></a>2 - obtenir le support d’installation de SQL Server 2016

Vous pouvez installer SQL Server 2016 RTM, Service Pack 1 ou Service Pack 2 en tant que votre première installation sur l’ordinateur cible. Ces versions peuvent accepter une mise à jour cumulative.

Vous pouvez notamment créer un fichier .iso contenant le support d’installation s’effectue via [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/). Connectez-vous, puis utiliser le **télécharge** lien pour rechercher la version de SQL Server 2016 à installer. Le téléchargement est sous la forme d’un fichier .iso, que vous pouvez copier sur l’ordinateur cible pour une installation hors connexion.

## <a name="transfer-files"></a>Transférer des fichiers

Copiez les fichiers de la base de données analytique CAB et le support d’installation de SQL Server (fichier .iso ou .cab) sur l’ordinateur cible. Placez les fichiers CAB et le fichier de média d’installation dans le même dossier sur l’ordinateur cible, tels que dossier TEMP * % de l’utilisateur le programme d’installation.

Le dossier % Temp% est requis pour les fichiers CAB de Python. Pour R, vous pouvez utiliser %TEMP% ou définissez le paramètre de myrcachedirectory sur le chemin d’accès du fichier CAB.

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

<a name="apply-cu"></a>

## <a name="apply-cumulative-updates"></a>Appliquer des mises à jour cumulatives

Nous vous recommandons d’appliquer la mise à jour cumulative la plus récente pour le moteur de base de données et les composants d’apprentissage. Mises à jour cumulatives sont installées via le programme d’installation. 

1. Démarrez avec une instance de la ligne de base. Vous pouvez uniquement appliquer des mises à jour cumulatives aux installations existantes de SQL Server :

  + Version initiale de SQL Server 2017
  + Version initiale de SQL Server 2016, SQL Server 2016 Service Pack 1 ou SQL Server 2016 Service Pack 2

2. Sur un dispositif connecté à internet, accédez à la liste de mise à jour cumulative pour votre version de SQL Server :

  + [Mises à jour de SQL Server 2017](https://sqlserverupdates.com/sql-server-2017-updates/)
  + [Mises à jour de SQL Server 2016](https://sqlserverupdates.com/sql-server-2016-updates/)

3. Sélectionnez la mise à jour cumulative la plus récente pour télécharger le fichier exécutable.

4. Obtenir les fichiers CAB correspondants pour R et Python. Pour obtenir des liens de téléchargement, consultez [CAB télécharge les mises à jour cumulatives sur analytique en base de données de SQL Server instances](sql-ml-cab-downloads.md).

5. Transférer tous les fichiers, fichier exécutable et les fichiers CAB, dans le même dossier sur l’ordinateur hors connexion.

6. Exécutez le programme d'installation. Acceptez les termes du contrat de licence et sur la page de sélection de fonctionnalités, passez en revue les fonctionnalités pour lesquelles les mises à jour cumulatives sont appliquées. Vous devez voir toutes les fonctionnalités installées pour l’instance actuelle, y compris les fonctionnalités d’apprentissage automatique.

  ![Sélectionner des fonctionnalités à partir de l’arborescence de fonctionnalités](media/cumulative-update-feature-selection.png "liste des fonctionnalités")

5. Suivez les instructions de l’Assistant en acceptant les termes du contrat de licence pour les distributions de R et Python. Pendant l’installation, vous êtes invité à choisir l’emplacement du dossier contenant les fichiers CAB mis à jour.

## <a name="set-environment-variables"></a>Jeu de variables d’environnement

Pour R fonctionnalité d’intégration uniquement, vous devez définir le **MKL_CBWR** variable d’environnement [résultat homogène](https://software.intel.com/articles/introduction-to-the-conditional-numerical-reproducibility-cnr) des calculs d’Intel Math Kernel Library (MKL).

1. Dans le panneau de configuration, cliquez sur **système et sécurité** > **système** > **paramètres système avancés**  >   **Variables d’environnement**.

2. Créer une nouvelle variable utilisateur ou système. 

  + Nom de variable du jeu `MKL_CBWR`
  + La valeur est la valeur de variable `AUTO`

Cette étape nécessite un redémarrage du serveur. Si vous êtes sur le point d’activer l’exécution du script, vous pouvez différez lors du redémarrage jusqu'à ce que tout le travail de configuration est terminée.

## <a name="post-install-configuration"></a>Configuration consécutive à l’installation

Une fois l’installation est terminée, redémarrez le service et puis configurez le serveur pour permettre l’exécution du script :

+ [Activer l’exécution du script externe (SQL Server 2017)](sql-machine-learning-services-windows-install.md#bkmk_enableFeature)
+ [Activer l’exécution du script externe (SQL Server 2016)](sql-r-services-windows-install.md#bkmk_enableFeature)

Une installation hors connexion initiale de SQL Server 2017 Machine Learning Services ou SQL Server 2016 R Services requiert la même configuration qu’une installation en ligne :

+ [Vérifier l’installation](sql-machine-learning-services-windows-install.md#verify-installation) (pour SQL Server 2016, cliquez sur [ici](sql-r-services-windows-install.md#verify-installation)).
+ [Une configuration supplémentaire si nécessaire](sql-machine-learning-services-windows-install.md#additional-configuration) (pour SQL Server 2016, cliquez sur [ici](sql-r-services-windows-install.md#bkmk_FollowUp)).

## <a name="next-steps"></a>Étapes suivantes

Pour vérifier l’état d’installation de l’instance et résoudre les problèmes courants, consultez [rapports personnalisés pour SQL Server R Services](../r/monitor-r-services-using-custom-reports-in-management-studio.md).

Pour plus d’aide sur les messages non connus ou les entrées de journal, consultez [mise à niveau et installation FAQ - Services Machine Learning](../r/upgrade-and-installation-faq-sql-server-r-services.md).

