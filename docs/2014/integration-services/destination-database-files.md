---
title: Fichiers de base de données de destination | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.transferdatabasetask.destdbfiles.f1
ms.assetid: f6f90417-86fb-4b8c-a790-0b215c344ef6
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 97d8a955b199aeb617171ed29f27271252a9fc4b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36039133"
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
 [Éditeur de tâche de transfert de &#40;Page Général&#41;](general-page-of-integration-services-designers-options.md)   
 [Éditeur de tâche de transfert de &#40;Page de bases de données&#41;](../../2014/integration-services/transfer-database-task-editor-databases-page.md)  
  
  