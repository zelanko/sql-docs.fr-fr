---
title: Installer de nouveaux packages de langage R - Services de SQL Server Machine Learning
description: Ajouter de nouveaux packages R pour SQL Server 2016 R Services ou SQL Server 2017 Machine Learning Services (en base de données)
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/29/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 590dbcc08d433147b61678c2b865ba205a0e547d
ms.sourcegitcommit: 85bfaa5bac737253a6740f1f402be87788d691ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2018
ms.locfileid: "53432793"
---
# <a name="install-new-r-packages-on-sql-server"></a>Installer de nouveaux packages R sur SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article décrit comment installer de nouveaux packages R à une instance de SQL Server où l’apprentissage automatique est activé. Il existe plusieurs méthodes pour l’installation de nouveaux packages R, en fonction de la version de SQL Server que vous avez et indique si le serveur possède une connexion internet. Les approches suivantes pour une nouvelle installation de package sont possibles.

| Approche                           | Autorisations               | Distante/locale |
|------------------------------------|---------------------------|--------------|
| [Utilisation des gestionnaires de package R conventionnelles](use-r-package-managers-on-sql-server.md)  | Administratifs | Local |
| [Utiliser RevoScaleR](use-revoscaler-to-manage-r-packages.md) |  Administrateur activé par la suite les rôles de base de données | both|
| [Utiliser T-SQL (créer une bibliothèque externe)](install-r-packages-tsql.md) | Administrateur activé par la suite les rôles de base de données | both 

## <a name="who-installs-permissions"></a>Qui l’installe (autorisations)

La bibliothèque de packages R se trouve physiquement dans le dossier Program Files de votre instance de SQL Server, dans un dossier sécurisé avec un accès restreint. L’écriture à cet emplacement nécessite des autorisations d’administrateur.

Non, les administrateurs peuvent installer des packages, mais cela requiert complétez configuration et fonctionnalité non disponible dans les installations initiales. Il existe deux approches pour les installations de package non administrateur : RevoScaleR à l’aide de la version 9.0.1 et version ultérieure, ou en utilisant CREATE EXTERNAL LIBRARY (SQL Server 2017 uniquement). Dans SQL Server 2017, **dbo_owner** ou un autre utilisateur avec l’autorisation de créer une bibliothèque externe peut installer des packages R à la base de données actuelle.

R développeurs sont habitués à créer des bibliothèques utilisateur pour les packages que dont ils ont besoin si les bibliothèques centralisées sont hors d’atteinte. Cette pratique est problématique pour le code R exécuté dans une instance du moteur de base de données SQL Server. SQL Server ne peut pas charger des packages à partir de bibliothèques externes, même si cette bibliothèque est sur le même ordinateur. Uniquement les packages à partir de la bibliothèque d’instance peuvent être utilisés dans le code R dans SQL Server.

Accès au système de fichiers est généralement limité sur le serveur, et même si vous avez des droits d’administrateur et l’accès à un dossier de documents d’utilisateur sur le serveur, le runtime de script externe qui s’exécute dans SQL Server ne peut pas accéder à tous les packages installés à l’extérieur de l’instance par défaut bibliothèque. 

## <a name="considerations-for-package-installation"></a>Considérations pour l’installation du package

Avant d’installer de nouveaux packages, vérifiez si les fonctionnalités activées par un package donné sont appropriées dans un environnement SQL Server. Dans un environnement sécurisé de manière renforcé de SQL Server, vous souhaiterez sans doute éviter les éléments suivants :

+ Packages qui nécessitent un accès réseau
+ Packages qui nécessitent Java ou autres frameworks généralement pas utilisés dans un environnement de SQL Server
+ Packages qui nécessitent un accès de système de fichier avec élévation de privilèges
+ Package est utilisé pour le développement web ou d’autres tâches qui ne bénéficient pas en cours d’exécution à l’intérieur de SQL Server

## <a name="offline-installation-no-internet-access"></a>Installation hors connexion (aucun accès internet)

En général, les serveurs qui hébergent les bases de données de production bloquent des connexions internet. L’installation de nouveaux packages R ou Python dans de tels environnements nécessite que vous préparez à l’avance les packages et les dépendances et copiez les fichiers dans un dossier sur le serveur pour l’installation hors connexion.

Identifier toutes les dépendances se complique. Pour R, nous vous recommandons d’utiliser [miniCRAN pour créer un référentiel local](create-a-local-package-repository-using-minicran.md) , puis transférer le référentiel entièrement défini à une instance de SQL Server isolée.

Également, vous pouvez effectuer cette procédure manuellement :

1. Identifier toutes les dépendances de package. 
2. Vérifiez si tous les packages requis sont déjà installés sur le serveur. Si le package est installé, vérifiez que la version est correcte.
3. Téléchargez le package et toutes les dépendances sur un ordinateur distinct.
4. Déplacer les fichiers vers un dossier accessible par le serveur.
5. Exécuter une commande d’installation pris en charge ou une instruction DDL pour installer le package dans la bibliothèque de l’instance.

### <a name="download-the-package-as-a-zipped-file"></a>Télécharger le package dans un fichier compressé

Pour l’installation sur un serveur sans accès à internet, vous devez télécharger une copie du package dans le format d’un fichier compressé pour l’installation hors connexion. **Ne décompressez pas le package.**

Par exemple, la procédure suivante décrit dès maintenant pour obtenir la version correcte de la [FISHalyseR](https://bioconductor.org/packages/release/bioc/html/FISHalyseR.html) package à partir de Bioconductor, en supposant que l’ordinateur a accès à internet.

1.  Dans la liste d’ **archives de package** , recherchez la version **binaire Windows** .

2.  Cliquez sur le lien vers la. Fichier ZIP, puis sélectionnez **enregistrer la cible sous**.

3.  Accédez au dossier local dans lequel les packages compressés sont stockés, puis cliquez sur **enregistrer**.

    Ce processus crée une copie locale du package. 

4. Si vous obtenez une erreur de téléchargement, essayez un site miroir différents.

5. Une fois que l’archive du package a été téléchargé, vous pouvez installer le package, ou copier le package compressé vers un serveur qui n’a pas accès à internet.

> [!TIP]
> Si par inadvertance, vous installez le package au lieu de télécharger les fichiers binaires, une copie du fichier compressé téléchargé est également enregistrée sur votre ordinateur. Regardez les messages d’état que le package est installé pour déterminer l’emplacement du fichier. Vous pouvez copier ce fichier compressé au serveur qui n’a pas accès à internet.
> 
> Toutefois, lorsque vous obtenez des packages à l’aide de cette méthode, les dépendances ne sont pas inclus. 


## <a name="side-by-side-installation-with-standalone-r-or-python-servers"></a>Installation côte à côte avec Standalone R ou Python serveurs

Fonctionnalités de R et Python sont incluses dans plusieurs produits Microsoft, qui peut coexister sur le même ordinateur.

Si vous avez installé SQL Server 2017 Microsoft Machine Learning Server (autonome) ou SQL Server 2016 R Server (autonome) en plus de l’analytique en base de données (SQL Server 2017 Machine Learning Services et SQL Server 2016 R Services), votre ordinateur a distinct installations de R pour chacune, avec les doublons de tous les outils R et les bibliothèques.

Les packages qui sont installés dans la bibliothèque R_SERVER sont utilisés uniquement par un serveur autonome et ne sont pas accessibles par une instance de SQL Server (en base de données). Utilisez toujours le `R_SERVICES` bibliothèque lors de l’installation des packages que vous souhaitez utiliser dans la base de données sur SQL Server. Pour plus d’informations sur les chemins d’accès, consultez [emplacement de la bibliothèque du Package](installing-and-managing-r-packages.md#package-library-location).


## <a name="see-also"></a>Voir aussi

+ [Installer de nouveaux packages Python](../python/install-additional-python-packages-on-sql-server.md)
+ [Didacticiels, exemples, solutions](../tutorials/machine-learning-services-tutorials.md)