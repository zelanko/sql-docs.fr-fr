---
title: Installer de nouveaux packages de langage R
description: Ajouter de nouveaux packages R à SQL Server 2016 R services ou SQL Server 2017 Machine Learning Services (en base de données)
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 1a6459d45d36ff69bdafb62a712e18937bf8eb30
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68470102"
---
# <a name="install-new-r-packages-on-sql-server"></a>Installer de nouveaux packages R sur SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cet article explique comment installer de nouveaux packages R sur une instance de SQL Server où Machine Learning est activé. Il existe plusieurs méthodes pour installer de nouveaux packages R, en fonction de la version de SQL Server que vous possédez et si le serveur dispose d’une connexion Internet. Les approches suivantes pour l’installation de nouveaux packages sont possibles.

| Approche                           | Autorisations               | Distant/local |
|------------------------------------|---------------------------|--------------|
| [Utiliser les gestionnaires de packages R conventionnels](use-r-package-managers-on-sql-server.md)  | Admin | Local |
| [Utiliser RevoScaleR](use-revoscaler-to-manage-r-packages.md) |  Rôles de base de données activés par l’administrateur | both|
| [Utiliser T-SQL (créer une bibliothèque externe)](install-r-packages-tsql.md) | Rôles de base de données activés par l’administrateur | both 

## <a name="who-installs-permissions"></a>Qui installe (autorisations)

La bibliothèque de packages R se trouve physiquement dans le dossier Program Files de votre instance SQL Server, dans un dossier sécurisé avec accès restreint. L’écriture dans cet emplacement nécessite des autorisations d’administrateur.

Les non-administrateurs peuvent installer des packages, mais cela nécessite une configuration et des fonctionnalités supplémentaires qui ne sont pas disponibles dans les installations initiales. Il existe deux approches pour les installations de packages non-administrateur: RevoScaleR à l’aide de la version 9.0.1 et ultérieure, ou à l’aide de CREATe EXTERNAL LIBRARY (SQL Server 2017 uniquement). Dans SQL Server 2017, **dbo_owner** ou un autre utilisateur disposant de l’autorisation CREATE external library peut installer des packages R dans la base de données actuelle.

Les développeurs R sont habitués à créer des bibliothèques utilisateur pour les packages dont ils ont besoin si les bibliothèques situées de manière centralisée sont hors limites. Cette pratique est problématique pour le code R s’exécutant dans une instance de moteur de base de données SQL Server. SQL Server ne peut pas charger les packages à partir de bibliothèques externes, même si cette bibliothèque est sur le même ordinateur. Seuls les packages de la bibliothèque d’instances peuvent être utilisés dans le code R s’exécutant dans SQL Server.

L’accès au système de fichiers est généralement limité sur le serveur, et même si vous disposez des droits d’administrateur et de l’accès à un dossier de documents utilisateur sur le serveur, le runtime de script externe qui s’exécute dans SQL Server ne peut pas accéder aux packages installés en dehors de l’instance par défaut Bibliothèque. 

## <a name="considerations-for-package-installation"></a>Considérations relatives à l’installation de packages

Avant d’installer de nouveaux packages, déterminez si les fonctionnalités activées par un package donné sont appropriées dans un environnement de SQL Server. Dans un environnement de SQL Server renforcé, vous souhaiterez peut-être éviter ce qui suit:

+ Packages qui nécessitent un accès réseau
+ Packages nécessitant un accès avec système de fichiers élevé
+ Le package est utilisé pour le développement Web ou d’autres tâches qui ne bénéficient pas de l’exécution dans SQL Server

## <a name="offline-installation-no-internet-access"></a>Installation hors connexion (pas d’accès Internet)

En général, les serveurs qui hébergent des bases de données de production bloquent les connexions Internet. Pour installer de nouveaux packages R ou python dans de tels environnements, vous devez préparer les packages et les dépendances à l’avance, puis copier les fichiers dans un dossier sur le serveur pour une installation hors connexion.

L’identification de toutes les dépendances devient compliquée. Pour R, nous vous recommandons d’utiliser [miniCRAN pour créer un référentiel local](create-a-local-package-repository-using-minicran.md) , puis de transférer le référentiel entièrement défini vers une instance SQL Server isolée.

Vous pouvez également effectuer ces étapes manuellement:

1. Identifiez toutes les dépendances du package. 
2. Vérifiez si des packages requis sont déjà installés sur le serveur. Si le package est installé, vérifiez que la version est correcte.
3. Téléchargez le package et toutes les dépendances sur un ordinateur distinct.
4. Déplacez les fichiers vers un dossier accessible par le serveur.
5. Exécutez une commande d’installation prise en charge ou une instruction DDL pour installer le package dans la bibliothèque d’instances.

### <a name="download-the-package-as-a-zipped-file"></a>Télécharger le package en tant que fichier zippé

Pour une installation sur un serveur sans accès à Internet, vous devez télécharger une copie du package au format d’un fichier zippé pour une installation hors connexion. **Ne Décompressez pas le package.**

Par exemple, la procédure suivante décrit maintenant comment obtenir la version correcte du package [FISHalyseR](https://bioconductor.org/packages/release/bioc/html/FISHalyseR.html) à partir du bioconductrice, en supposant que l’ordinateur a accès à Internet.

1.  Dans la liste d’ **archives de package** , recherchez la version **binaire Windows** .

2.  Cliquez avec le bouton droit sur le lien vers le. Fichier ZIP, puis sélectionnez **enregistrer la cible sous**.

3.  Accédez au dossier local dans lequel les packages compressés sont stockés, puis cliquez sur **Enregistrer**.

    Ce processus crée une copie locale du package. 

4. Si vous recevez une erreur de téléchargement, essayez un autre site miroir.

5. Une fois l’archive du package téléchargée, vous pouvez installer le package ou copier le package compressé sur un serveur qui n’a pas accès à Internet.

> [!TIP]
> Si, par erreur, vous installez le package au lieu de télécharger les fichiers binaires, une copie du fichier compressé téléchargé est également enregistrée sur votre ordinateur. Observez les messages d’état lors de l’installation du package pour déterminer l’emplacement du fichier. Vous pouvez copier ce fichier compressé sur le serveur qui n’a pas accès à Internet.
> 
> Toutefois, lorsque vous obtenez des packages à l’aide de cette méthode, les dépendances ne sont pas incluses. 


## <a name="side-by-side-installation-with-standalone-r-or-python-servers"></a>Installation côte à côte avec des serveurs R ou python autonomes

Les fonctionnalités R et Python sont incluses dans plusieurs produits Microsoft, qui peuvent tous coexister sur le même ordinateur.

Si vous avez installé SQL Server 2017 Microsoft Machine Learning Server (autonome) ou SQL Server 2016 R Server (autonome) en plus de l’analyse en base de données (SQL Server 2017 Machine Learning Services et 2016 SQL Server R services R), votre ordinateur a des installations de R pour chaque, avec des doublons de tous les outils et bibliothèques R.

Les packages qui sont installés dans la bibliothèque R_SERVER sont utilisés uniquement par un serveur autonome et ne sont pas accessibles par une instance SQL Server (dans la base de données). Utilisez toujours la `R_SERVICES` bibliothèque lors de l’installation des packages que vous souhaitez utiliser dans la base de données sur SQL Server. Pour plus d’informations sur les chemins d’accès, consultez emplacement de la [bibliothèque de packages](../package-management/default-packages.md).

## <a name="see-also"></a>Voir aussi

+ [Installer de nouveaux packages Python](../python/install-additional-python-packages-on-sql-server.md)
+ [Didacticiels, exemples, solutions](../tutorials/machine-learning-services-tutorials.md)
