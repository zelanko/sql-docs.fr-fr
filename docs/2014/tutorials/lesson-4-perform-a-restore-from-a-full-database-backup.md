---
title: 'Leçon 4 : Effectuer une restauration à partir d’une sauvegarde complète de base de données | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 580f76e6-9802-4abc-9043-db6de592c733
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 3af76a0ec664a10d5457dc3d106de3727740ce19
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52523657"
---
# <a name="lesson-4-perform-a-restore-from-a-full-database-backup"></a>Leçon 4 : Effectuer une restauration à partir d’une sauvegarde de base de données complète
  Cette leçon illustre l'utilisation d'une instruction TSQL pour effectuer une restauration d'une sauvegarde de base de données complète créée au cours de la leçon précédente.  
  
## <a name="perform-a-restore-of-a-database-backup"></a>Effectuer une restauration d'une sauvegarde de base de données  
 Pour restaurer une sauvegarde de base de données complète, procédez comme suit :  
  
1.  Se connecter à [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
2.  Dans l' **Explorateur d'objets**, connectez-vous à l'instance de [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
3.  Dans la barre de menus standard, cliquez sur **Nouvelle requête**.  
  
4.  Copiez et collez l'exemple suivant dans la fenêtre de requête et modifiez-le si nécessaire.  
  
    ```  
    RESTORE DATABASE AdventureWorks2012   
    FROM URL = 'https://mystorageaccount.blob.core.windows.net/privatecontainertest/AdventureWorks2012.bak'   
    WITH CREDENTIAL = 'mycredential';  
    , STATS = 5 - use this to see monitor the progress  
    GO  
  
    ```  
  
5.  Vérifiez l'instruction T-SQL et cliquez sur **Exécuter**  
  
### <a name="return-to-tutorials-portal"></a>Revenir au portail des didacticiels  
 [Didacticiel : Service de stockage d’objets Blob SQL Server Backup and Restore sur Windows Azure](../relational-databases/tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md).  
  
  
