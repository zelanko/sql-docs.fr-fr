---
title: Les fichiers de base de données source | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferdatabasetask.sourcedbfiles.f1
ms.assetid: 7dc6bfeb-37c1-45e8-a705-a87564922265
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: fb0f2659323960e58bb70ff2bb36f8367088dd7a
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58387757"
---
# <a name="source-database-files"></a>Fichiers de la base de données source
  Utilisez la boîte de dialogue **Fichiers de la base de données source** pour afficher le nom et l'emplacement des fichiers de la base de données sur le serveur source ou pour spécifier un emplacement de partage de fichiers réseau pour la tâche de transfert de bases de données. Pour plus d’informations sur cette tâche, consultez [Tâche de transfert de bases de données](control-flow/transfer-database-task.md).  
  
 Pour remplir cette boîte de dialogue avec le nom et l'emplacement des fichiers de base de données sur le serveur source, spécifiez d'abord **SourceConnection** et **SourceDatabaseName** dans la page **Bases de données** de la boîte de dialogue **Éditeur de tâche de transfert de bases de données** .  
  
## <a name="options"></a>Options  
 **Source File**  
 Nom des fichiers de base de données sur le serveur source qui seront transférés. Le**Fichier source** est en lecture seule.  
  
 **Dossier source**  
 Dossier du serveur source où se trouvent les fichiers de base de données à transférer. Le**Dossier source** est en lecture seule.  
  
 **Partage de fichiers réseau**  
 Dossier réseau partagé du serveur source à partir duquel les fichiers de base de données seront transférés. Utilisez le **Partage de fichiers réseau** lors du transfert d'une base de données en mode hors connexion en spécifiant **DatabaseOffline** pour **Méthode** dans la page **Bases de données** de la boîte de dialogue **Éditeur de tâche de transfert de bases de données** .  
  
 Entrez l’emplacement du partage de fichiers réseau ou cliquez sur le bouton Parcourir **(...)** pour le rechercher.  
  
 Lors du transfert d'une base de données en mode hors connexion, les fichiers de base de données sont copiés dans l'emplacement du **Partage de fichiers réseau** sur le serveur source avant d'être transférés sur le serveur de destination.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de tâche de transfert de bases de données &#40;Page Général&#41;](general-page-of-integration-services-designers-options.md)   
 [Éditeur de tâche de transfert de bases de données &#40;page Bases de données&#41;](../../2014/integration-services/transfer-database-task-editor-databases-page.md)  
  
  
