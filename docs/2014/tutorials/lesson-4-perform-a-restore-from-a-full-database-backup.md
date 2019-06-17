---
title: 'Leçon 4 : Effectuer une restauration à partir d’une sauvegarde complète de base de données | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: 580f76e6-9802-4abc-9043-db6de592c733
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 077fb708f09db0182bc5f1510f0264b139beab13
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63312071"
---
# <a name="lesson-4-perform-a-restore-from-a-full-database-backup"></a>Leçon 4 : Effectuer une restauration d’une sauvegarde de base de données complète
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
 [Tutoriel : Service de stockage d’objets Blob SQL Server Backup and Restore sur Windows Azure](../relational-databases/tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md).  
  
  
