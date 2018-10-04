---
title: Fichiers de base de données de destination | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferdatabasetask.destdbfiles.f1
ms.assetid: f6f90417-86fb-4b8c-a790-0b215c344ef6
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: fb6f834ab26fb6d5cc7535d217745af92e97c2a5
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48135272"
---
# <a name="destination-database-files"></a>Fichiers de la base de données de destination
  Utilisez la boîte de dialogue **Fichiers de la base de données de destination** pour afficher ou modifier le nom et l'emplacement des fichiers de la base de données sur le serveur de destination ou pour spécifier un emplacement de fichier réseau pour la tâche de transfert de bases de données. Pour plus d’informations sur cette tâche, consultez [Tâche de transfert de bases de données](control-flow/transfer-database-task.md).  
  
 Pour remplir automatiquement cette boîte de dialogue avec le nom et l'emplacement des fichiers de base de données sur le serveur source, spécifiez d'abord **SourceConnection**, **SourceDatabaseName**et **SourceDatabaseFiles** dans la page **Bases de données** de la boîte de dialogue **Éditeur de tâche de transfert de bases de données** .  
  
## <a name="options"></a>Options  
 **Fichier de destination**  
 Nom des fichiers de la base de données transférés sur le serveur de destination.  
  
 Entrez le nom du fichier ou cliquez dessus pour le modifier.  
  
 **Dossier de destination**  
 Dossier du serveur de destination où les fichiers de la base de données seront transférés.  
  
 Entrez le chemin d'accès au dossier, cliquez dessus pour le modifier ou cliquez sur Parcourir pour rechercher le dossier dans lequel transférer les fichiers de la base de données sur le serveur de destination.  
  
 **Partage de fichiers réseau**  
 Dossier réseau partagé du serveur de destination où les fichiers de la base de données seront transférés. Utilisez le **Partage de fichiers réseau** lors du transfert d'une base de données en mode hors connexion en spécifiant **DatabaseOffline** pour **Méthode** dans la page **Bases de données** de la boîte de dialogue **Éditeur de tâche de transfert de bases de données** .  
  
 Entrez l'emplacement du partage de fichiers réseau ou cliquez sur le bouton Parcourir pour le rechercher.  
  
 Lors du transfert d'une base de données en mode hors connexion, les fichiers de base de données sont copiés dans l'emplacement du **Partage de fichiers réseau** avant d'être transférés dans l'emplacement **Dossier de destination** .  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de tâche de base de données de transfert &#40;Page Général&#41;](general-page-of-integration-services-designers-options.md)   
 [Éditeur de tâche de base de données de transfert &#40;Page des bases de données&#41;](../../2014/integration-services/transfer-database-task-editor-databases-page.md)  
  
  
