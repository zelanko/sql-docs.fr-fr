---
title: Transfert de l’éditeur de tâche de base de données (Page bases de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferdatabasetask.database.f1
helpviewer_keywords:
- Transfer Database Task Editor
ms.assetid: ccdb74d0-4bea-420c-a726-2e0eb8957e0a
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 8d93d2e95f6a18174a6d9b2f05e434a5443701ed
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66055109"
---
# <a name="transfer-database-task-editor-databases-page"></a>Éditeur de tâche de transfert de bases de données (page Bases de données)
  Utilisez la page **Bases de données** de la boîte de dialogue **Éditeur de tâche de transfert de bases de données** pour spécifier les propriétés des bases de données source et de destination concernées par la tâche de transfert de bases de données. La tâche de transfert de bases de données copie ou déplace une base de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] entre deux instances de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Cette tâche peut également servir à copier une base de données sur le même serveur. Pour plus d’informations sur cette tâche, consultez [Tâche de transfert de bases de données](control-flow/transfer-database-task.md).  
  
## <a name="options"></a>Options  
 **SourceConnection**  
 Sélectionnez un gestionnaire de connexions SMO dans la liste ou cliquez sur **\<Nouvelle connexion...>** pour créer une connexion au serveur source.  
  
 **DestinationConnection**  
 Sélectionnez un gestionnaire de connexions SMO dans la liste, ou cliquez sur **\<Nouvelle connexion...>** pour créer une connexion au serveur de destination.  
  
 **DestinationDatabaseName**  
 Spécifiez le nom de la base de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sur le serveur de destination.  
  
 Pour remplir automatiquement ce champ avec le nom de la base de données source, spécifiez d’abord **SourceConnection** et **SourceDatabaseName** .  
  
 Pour renommer la base de données sur le serveur de destination, tapez son nouveau nom dans ce champ.  
  
 **DestinationDatabaseFiles**  
 Spécifiez le nom et l'emplacement des fichiers de base de données sur le serveur de destination.  
  
 Pour remplir automatiquement ce champ avec le nom de la base de données source, spécifiez d’abord **SourceConnection**, **SourceDatabaseName**et **SourceDatabaseFiles** .  
  
 Pour renommer les fichiers de base de données ou pour spécifier les nouveaux emplacements sur le serveur de destination, remplissez ce champ avec les informations sur la base de données source, puis cliquez sur le bouton Parcourir. Dans la boîte de dialogue **Fichiers de la base de données de destination** , modifiez **Fichier de destination**, **Dossier de destination**ou **Partage de fichiers réseau**.  
  
> [!NOTE]  
>  Si vous trouvez l’emplacement des fichiers de la base de données à l’aide du bouton Parcourir, l’emplacement des fichiers est entré en utilisant la notation de lecteur local : par exemple, c:\\. Vous devez remplacer cette notation par la notation de partage réseau, qui comporte le nom de l'ordinateur et le nom du partage. Si le partage administratif par défaut est utilisé, vous devez utiliser la notation $ et disposer d'un accès administratif au partage.  
  
 **DestinationOverwrite**  
 Spécifiez si la base de données sur le serveur de destination peut être remplacée.  
  
 Cette propriété dispose des options répertoriées dans le tableau suivant :  
  
|Value|Description|  
|-----------|-----------------|  
|**True**|Remplace la base de données du serveur de destination.|  
|**False**|Ne remplace pas la base de données du serveur de destination.|  
  
> [!CAUTION]  
>  Les données de la base de données du serveur de destination seront remplacées si vous spécifiez **True** pour **DestinationOverwrite**, ce qui peut provoquer la perte de données. Pour l'éviter, sauvegardez la base de données du serveur de destination dans un autre emplacement avant d'exécuter la tâche de transfert de bases de données.  
  
 **Action**  
 Spécifiez si la tâche doit **Copier** ou **Déplacer** la base de données sur le serveur de destination.  
  
 **Méthode**  
 Spécifiez si la tâche est exécutée pendant que la base de données sur le serveur source est en ligne ou en mode hors connexion.  
  
 Pour transférer une base de données en mode hors connexion, l’utilisateur qui exécute le package doit être membre du rôle serveur fixe **sysadmin** .  
  
 Pour transférer une base de données en mode en ligne, l’utilisateur qui exécute le package doit être membre du rôle serveur fixe **sysadmin** ou propriétaire de la base de données sélectionnée (**dbo**).  
  
 **SourceDatabaseName**  
 Sélectionnez le nom de la base de données à copier ou à déplacer.  
  
 **SourceDatabaseFiles**  
 Cliquez sur le bouton Parcourir pour sélectionner les fichiers de base de données.  
  
 **ReattachSourceDatabase**  
 Spécifiez si la tâche va tenter de rattacher la base de données source en cas d'échec.  
  
 Cette propriété dispose des options répertoriées dans le tableau suivant :  
  
|Value|Description|  
|-----------|-----------------|  
|**True**|Rattache la base de données source.|  
|**False**|Ne rattache pas la base de données source.|  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Tâches Integration Services](control-flow/integration-services-tasks.md)   
 [Éditeur de tâche de transfert de bases de données &#40;Page Général&#41;](general-page-of-integration-services-designers-options.md)   
 [Page Expressions](expressions/expressions-page.md)   
 [Gestionnaire de connexions SMO](connection-manager/smo-connection-manager.md)  
  
  
