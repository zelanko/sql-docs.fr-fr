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
ms.openlocfilehash: de9a356589ac6bceb532ed4cecf509f957e3c337
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2019
ms.locfileid: "70153403"
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
 [Tutoriel : SQL Server la sauvegarde et la restauration dans le service](../relational-databases/tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md)de stockage d’objets BLOB Azure.  
  
  
