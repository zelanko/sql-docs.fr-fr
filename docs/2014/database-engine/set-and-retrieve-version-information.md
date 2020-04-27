---
title: Définir et récupérer les informations de version | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- historical information [SQL Server]
- source controls [SQL Server Management Studio], version information
- retrieving version information
- current file version information
- version control services [SQL Server], retrieving version information
- version control services [SQL Server], setting version information
- status information [SQL Server], source control files
- historical information [SQL Server], source control files
ms.assetid: c3f253c4-4e3d-48e8-8d90-bd6ee899faf7
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 68113c6de003aea94924f6e220373664212becf1
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62843480"
---
# <a name="set-and-retrieve-version-information"></a>Définir et récupérer des informations sur la version
  Les informations sur une version comprennent l'historique et l'état en cours d'un fichier sous contrôle de code source. [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe gère un historique complet pour chaque fichier sous contrôle de code source, de sorte que vous puissiez suivre l'évolution d'un ou de plusieurs fichiers dans le temps. Vous pouvez également utiliser ces informations pour récupérer une copie locale d'une version d'un fichier ou pour comparer deux versions d'un fichier.  
  
 L'historique d'un fichier comprend les informations suivantes :  
  
-   Numéro de version, indiquant la séquence de la version parmi les autres versions du même fichier  
  
-   action effectuée. Parmi les opérations de suivi figurent la création, l'archivage et la suppression de fichiers.  
  
-   Nom d'utilisateur de la personne à l'origine de l'action impliquant le fichier  
  
-   Date et heure d'exécution de l'opération  
  
 Visual SourceSafe gère également les informations relatives à l'état en cours de la solution actuellement chargée. Ces informations fournissent un instantané de l'état actuel du fichier :  
  
-   Identité de l'utilisateur ayant extrait le fichier  
  
-   Dernier numéro de la version du fichier sélectionné  
  
-   Date de création de la version  
  
-   Commentaire de l'utilisateur associé à la version  
  
-   Chemins vers les projets avec lesquels le fichier est partagé  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Afficher l'historique d'un fichier](../../2014/database-engine/view-file-history.md)  
  
-   [Afficher l'historique d'un projet](../../2014/database-engine/view-project-history.md)  
  
-   [Afficher l'état d'un fichier](../../2014/database-engine/view-file-status.md)  
  
-   [Récupérer des fichiers](../../2014/database-engine/retrieve-files.md)  
  
-   [Désigner une version comme étant la dernière version](../../2014/database-engine/specify-a-version-as-the-latest-version.md)  
  
-   [Comparer des fichiers](../../2014/database-engine/compare-files.md)  
  
-   [Partager des fichiers](../../2014/database-engine/share-files.md)  
  
-   [Créer des rapports d'état et historiques](../../2014/database-engine/create-history-and-status-reports.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation du contrôle de code source](../../2014/database-engine/source-control-basics.md)  
  
  
