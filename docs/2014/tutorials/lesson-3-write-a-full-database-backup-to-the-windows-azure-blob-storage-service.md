---
title: 'Leçon 3 : Écrire une sauvegarde de base de données complète dans le Service de stockage Windows Azure Blob | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 454c8296-64e9-46ed-b141-5ebfbc8a4fe2
caps.latest.revision: 9
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 4a28465f0175be0bfc12e5c9d51a267ae6597ec6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37236079"
---
# <a name="lesson-3-write-a-full-database-backup-to-the-windows-azure-blob-storage-service"></a>Leçon 3 : Écrire une sauvegarde de base de données complète dans le service de Stockage Blob Windows Azure
  Cette leçon illustre l'utilisation de l'instruction TSQL pour effectuer une sauvegarde de base de données complète dans le service de stockage d'objets blob Windows Azure.  
  
## <a name="perform-a-full-database-backup-to-the-windows-azure-blob-storage-service"></a>Effectuer une sauvegarde de base de données complète dans le service de stockage d'objets blob Windows Azure  
 Pour créer une sauvegarde de base de données complète, procédez comme suit :  
  
1.  Se connecter à [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
2.  Dans le **Explorateur d’objets**, connectez-vous à l’instance de [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
3.  Dans la barre de menus standard, cliquez sur **Nouvelle requête**.  
  
4.  Copiez et collez l'exemple suivant dans la fenêtre de requête, modifiez-le si nécessaire, puis cliquez sur **Exécuter**.  
  
    ```  
    BACKUP DATABASE[AdventureWorks2012]   
    TO URL = 'https://mystorageaccount.blob.core.windows.net/privatecontainertest/AdventureWorks2012.bak'   
    /* URL includes the endpoint for the BLOB service, followed by the container name, and the name of the backup file*/   
    WITH CREDENTIAL = 'mycredential';  
    /* name of the credential you created in the previous step */   
    GO  
  
    ```  
  
5.  Dans l'Explorateur d'objets, connectez-vous au stockage Azure. Recherchez le conteneur et les fichiers de sauvegarde récemment créés.  
  
## <a name="next-lesson"></a>Leçon suivante  
 [Leçon 4 : Effectuer une restauration à partir d’une sauvegarde de base de données complète](../../2014/tutorials/lesson-4-perform-a-restore-from-a-full-database-backup.md).  
  
  
