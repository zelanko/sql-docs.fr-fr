---
title: Installer les composants de langage R et Python sans accès à Internet
description: Mise en mode hors connexion ou déconnectée Machine Learning R et Python sur une instance SQL Server isolée derrière un pare-feu réseau.
ms.prod: sql
ms.technology: machine-learning
ms.date: 07/30/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: ddeea99addae3229575ca581f344332587e85981
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715823"
---
# <a name="install-sql-server-machine-learning-r-and-python-on-computers-with-no-internet-access"></a>Installer SQL Server Machine Learning R et Python sur des ordinateurs sans accès à Internet
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Par défaut, les programmes d’installation se connectent aux sites de téléchargement Microsoft pour obtenir les composants requis et mis à jour pour Machine Learning sur SQL Server. Si les contraintes de pare-feu empêchent le programme d’installation d’atteindre ces sites, vous pouvez utiliser un appareil connecté à Internet pour télécharger des fichiers, transférer des fichiers vers un serveur hors connexion, puis exécuter le programme d’installation.

L’analyse en base de données se compose d’une instance du moteur de base de données, ainsi que de composants supplémentaires pour l’intégration de R et Python, selon la version de SQL Server. 

+ SQL Server 2017 et versions ultérieures incluent R et Python 
+ SQL Server 2016 est R uniquement.

Sur un serveur isolé, les fonctionnalités spécifiques au langage Machine Learning et R/Python sont ajoutées par le biais de fichiers CAB. 

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
## <a name="sql-server-2017-offline-install"></a>Installation hors connexion SQL Server 2017

Pour installer SQL Server Machine Learning Services (R et Python) sur un serveur isolé, commencez par télécharger la version initiale de SQL Server et les fichiers CAB correspondants pour la prise en charge de R et Python. Même si vous envisagez de mettre à jour immédiatement votre serveur pour utiliser la dernière mise à jour cumulative, vous devez d’abord installer une version initiale.

> [!Note]
> SQL Server 2017 ne dispose pas de service packs. Il s’agit de la première version de SQL Server pour utiliser la version initiale comme seule ligne de base, avec la maintenance uniquement par le biais de mises à jour cumulatives. 

### <a name="1---download-2017-cabs"></a>1-Télécharger 2017 cab

Sur un ordinateur disposant d’une connexion Internet, téléchargez les fichiers CAB fournissant les fonctionnalités R et Python pour la version initiale et le support d’installation pour SQL Server 2017. 

Libérer  |Télécharger le lien  |
---------|---------------|
Microsoft R Open     |[SRO_3.3.3.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851496)|
Microsoft R Server      |[SRS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851507)|
Microsoft python Open     |[SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502) |
Serveur Microsoft python    |[SPS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851508) |

###  <a name="2---get-sql-server-2017-installation-media"></a>2-Télécharger le support d’installation de SQL Server 2017

1. Sur un ordinateur disposant d’une connexion Internet, téléchargez le [programme d’installation SQL Server 2017](https://www.microsoft.com/sql-server/sql-server-downloads). 

2. Double-cliquez sur Configuration, puis choisissez le type d’installation du **média de téléchargement** . Avec cette option, le programme d’installation crée un fichier. ISO (ou. cab) local contenant le support d’installation.

   ![Choisir le type d’installation du média de téléchargement](media/offline-download-tile.png "Télécharger le support")

::: moniker-end

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"

## <a name="sql-server-2016-offline-install"></a>Installation hors connexion SQL Server 2016

SQL Server l’analytique en base de données 2016 est R uniquement, avec seulement deux fichiers CAB pour les packages de produits et la distribution de R Open source de Microsoft, respectivement. Commencez par installer l’une des versions suivantes: RTM, SP 1, SP 2. Une fois qu’une installation de base est en place, les mises à jour cumulatives peuvent être appliquées à l’étape suivante.

Sur un ordinateur disposant d’une connexion Internet, téléchargez les fichiers CAB utilisés par le programme d’installation pour installer l’analyse en base de données sur SQL Server 2016. 

### <a name="1---download-2016-cabs"></a>1-Télécharger 2016 cab

Libérer  | Microsoft R Open | Microsoft R Server |
---------|-----------------|---------------------|
**SQL Server 2016 RTM**     | [SRO_3.2.2.803_1033.cab](https://go.microsoft.com/fwlink/?LinkId=761266) |[SRS_8.0.3.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=735051) |
**SQL Server 2016 SP 1**     | [SRO_3.2.2.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824879) |[SRS_8.0.3.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824881) | 
**SQL Server 2016 SP 2**  |[SRO_3.2.2.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866039) |[SRS_8.0.3.17000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=850317) |

### <a name="2---get-sql-server-2016-installation-media"></a>2-Télécharger le support d’installation de SQL Server 2016

Vous pouvez installer SQL Server 2016 RTM, SP 1 ou SP 2 comme première installation sur l’ordinateur cible. L’une de ces versions peut accepter une mise à jour cumulative.

L’une des méthodes permettant d’accéder à un fichier. ISO contenant le support d’installation consiste à [Visual Studio dev Essentials](https://visualstudio.microsoft.com/dev-essentials/). Connectez-vous, puis utilisez le lien **téléchargements** pour trouver la version de SQL Server 2016 que vous souhaitez installer. Le téléchargement se présente sous la forme d’un fichier. ISO, que vous pouvez copier sur l’ordinateur cible pour une installation hors connexion.

::: moniker-end

## <a name="transfer-files"></a>Transférer des fichiers

Copiez le support d’installation SQL Server (. ISO ou. cab) et les fichiers CAB d’analyse dans la base de données sur l’ordinateur cible. Placez les fichiers CAB et le fichier du support d’installation dans le même dossier sur l’ordinateur cible, tel que le dossier% TEMP * de l’utilisateur du programme d’installation.

Le dossier% TEMP% est requis pour les fichiers CAB Python. Pour R, vous pouvez utiliser% TEMP% ou définir le paramètre myrcachedirectory sur le chemin d’accès au fichier CAB.

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
La capture d’écran suivante montre SQL Server fichiers CAB et ISO. 

![Liste des fichiers à transférer](media/offline-file-list.png "Liste des fichiers")
::: moniker-end

## <a name="run-setup"></a>Exécuter le programme d’installation

Lorsque vous exécutez le programme d’installation de SQL Server sur un ordinateur déconnecté d’Internet, le programme d’installation ajoute une page d' **installation hors connexion** à l’Assistant afin que vous puissiez spécifier l’emplacement des fichiers CAB copiés à l’étape précédente.

1. Pour commencer l’installation, double-cliquez sur le fichier. ISO ou. cab pour accéder au support d’installation. Vous devez voir le fichier **Setup. exe** .

2. Cliquez avec le bouton droit sur **Setup. exe** et exécutez en tant qu’administrateur.

3. Quand l’Assistant installation affiche la page de licence pour les composants R ou python Open source, cliquez sur **accepter**. L’acceptation des termes du contrat de licence vous permet de passer à l’étape suivante.

4. Lorsque vous accédez à la page d' **installation hors connexion** , dans **chemin d’installation**, spécifiez le dossier contenant les fichiers CAB que vous avez copiés précédemment.

   ![Page de l’Assistant pour la sélection du dossier CAB](media/screenshot-sql-offline-cab-page.png "Dossier CAB")

5. Continuez à suivre les invites à l’écran pour terminer l’installation.

<a name="apply-cu"></a>

## <a name="apply-cumulative-updates"></a>Appliquer des mises à jour cumulatives

Nous vous recommandons d’appliquer la dernière mise à jour cumulative au moteur de base de données et aux composants de Machine Learning. Les mises à jour cumulatives sont installées par le biais du programme d’installation de. 

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
1. Démarrez avec une instance de ligne de base. Vous pouvez uniquement appliquer des mises à jour cumulatives à des installations existantes de la version initiale de SQL Server.

2. Sur un appareil connecté à Internet, accédez à la liste des mises à jour cumulatives pour votre version de SQL Server:

  + [Mises à jour de SQL Server 2017](https://sqlserverupdates.com/sql-server-2017-updates/)
::: moniker-end

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
1. Démarrez avec une instance de ligne de base. Vous pouvez uniquement appliquer des mises à jour cumulatives à des installations existantes de la version initiale de SQL Server 2016, SQL Server 2016 SP 1 ou SQL Server 2016 SP 2.

2. Sur un appareil connecté à Internet, accédez à la liste des mises à jour cumulatives pour votre version de SQL Server:

  + [Mises à jour de SQL Server 2016](https://sqlserverupdates.com/sql-server-2016-updates/)
::: moniker-end

3. Sélectionnez la dernière mise à jour cumulative pour télécharger l’exécutable.

4. Obtenir les fichiers CAB correspondants pour R et Python. Pour obtenir des liens de téléchargement, consultez la page [téléchargements cab pour les mises à jour cumulatives sur SQL Server instances analytiques dans la base de données](sql-ml-cab-downloads.md).

5. Transférez tous les fichiers, fichiers exécutables et fichiers CAB dans le même dossier sur l’ordinateur hors connexion.

6. Exécutez le programme d'installation. Acceptez les termes du contrat de licence et, dans la page sélection de fonctionnalités, passez en revue les fonctionnalités pour lesquelles des mises à jour cumulatives sont appliquées. Vous devez voir toutes les fonctionnalités installées pour l’instance actuelle, y compris les fonctionnalités de Machine Learning.

    ![Sélectionner des fonctionnalités dans l’arborescence de fonctionnalités](media/cumulative-update-feature-selection.png "liste des fonctionnalités")

5. Poursuivez avec l’Assistant, en acceptant les termes du contrat de licence pour les distributions R et Python. Pendant l’installation, vous êtes invité à choisir l’emplacement du dossier contenant les fichiers CAB mis à jour.

## <a name="set-environment-variables"></a>Définition des variables d'environnement

Pour l’intégration de fonctionnalités R uniquement, vous devez définir la variable d’environnement **MKL_CBWR** pour [garantir la cohérence](https://software.intel.com/articles/introduction-to-the-conditional-numerical-reproducibility-cnr) de la sortie des calculs d’Intel Math Kernel Library (MKL).

1. Dans le panneau de configuration, cliquez sur système **et sécurité** >  > **paramètres** > système avancés**variables d’environnement**.

2. Créez un utilisateur ou une variable système. 

  + Définir le nom de la variable sur`MKL_CBWR`
  + Affectez à la variable la valeur`AUTO`

Cette étape nécessite un redémarrage du serveur. Si vous êtes sur le ou l’activation du script, vous pouvez maintenir le redémarrage jusqu’à ce que le travail de configuration soit terminé.

## <a name="post-install-configuration"></a>Configuration consécutive à l’installation

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
Une fois l’installation terminée, redémarrez le service, puis configurez le serveur pour activer l’exécution du script:

+ [Activer l’exécution du script externe](sql-machine-learning-services-windows-install.md#bkmk_enableFeature)

Une installation hors connexion initiale de SQL Server Machine Learning Services requiert la même configuration qu’une installation en ligne:

+ [Vérifier l’installation](sql-machine-learning-services-windows-install.md#verify-installation)
+ [Configuration supplémentaire si nécessaire](sql-machine-learning-services-windows-install.md#additional-configuration)
::: moniker-end

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
Une fois l’installation terminée, redémarrez le service, puis configurez le serveur pour activer l’exécution du script:

+ [Activer l’exécution du script externe](sql-r-services-windows-install.md#bkmk_enableFeature)

Une installation hors connexion initiale de SQL Server R Services nécessite la même configuration qu’une installation en ligne:

+ [Vérifier l’installation](sql-r-services-windows-install.md#verify-installation)
+ [Configuration supplémentaire si nécessaire](sql-r-services-windows-install.md#bkmk_FollowUp)
::: moniker-end

## <a name="next-steps"></a>Étapes suivantes

Pour vérifier l’état d’installation de l’instance et résoudre les problèmes courants, consultez [rapports personnalisés pour SQL Server](../r/monitor-r-services-using-custom-reports-in-management-studio.md).

Pour obtenir de l’aide sur les messages ou les entrées de journal qui ne sont pas familiers, consultez [FAQ sur la mise à niveau et l’installation-machine learning services](../r/upgrade-and-installation-faq-sql-server-r-services.md).
