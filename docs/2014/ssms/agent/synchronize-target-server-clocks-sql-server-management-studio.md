---
title: Synchroniser les horloges des serveurs cibles (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, target servers
- clocks [SQL Server]
- master servers [SQL Server], clock synchronization
- synchronization [SQL Server], target server clocks
- target servers [SQL Server], clock synchronization
ms.assetid: 4fb80502-d271-4d06-bcbc-bfbbceb5f2a2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6fc706c6313258844dd015421e69828f996c0f1c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48210719"
---
# <a name="synchronize-target-server-clocks-sql-server-management-studio"></a>Synchroniser les horloges des serveurs cibles (SQL Server Management Studio)
  Cette rubrique décrit la procédure de synchronisation des horloges des serveurs cibles dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] avec celle du serveur maître à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)]. La synchronisation de ces horloges système gère vos planifications de travail.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour synchroniser les horloges des serveurs cibles, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 Nécessite l'appartenance au rôle serveur fixe **sysadmin** .  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-synchronize-target-server-clocks"></a>Pour synchroniser les horloges des serveurs cibles  
  
1.  Dans l' **Explorateur d'objets** , cliquez sur le signe plus (+) pour développer le serveur sur lequel vous souhaitez synchroniser les horloges des serveurs cibles avec celle du serveur maître.  
  
2.  Cliquez avec le bouton droit sur **SQL Server Agent**, pointez sur **Administration multiserveur**, puis sélectionnez **Gérer les serveurs cibles**.  
  
3.  Dans la boîte de dialogue **Gérer les serveurs cibles** , cliquez sur **Publier les instructions**.  
  
4.  Dans la liste **Type d'instruction** , cliquez sur **Synchroniser les horloges**.  
  
5.  Sous **Destinataires**, activez l'une des options suivantes :  
  
    -   Cliquez sur **Tous les serveurs cibles** pour synchroniser les horloges de tous les serveurs cibles avec celle du serveur maître.  
  
    -   Cliquez sur **Serveurs cible sélectionnés** pour synchroniser l'horloge de certains serveurs, puis sélectionnez chacun des serveurs cibles dont vous souhaitez synchroniser l'horloge avec celle du serveur maître.  
  
6.  Lorsque vous avez terminé, cliquez sur **OK**.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-synchronize-target-server-clocks"></a>Pour synchroniser les horloges des serveurs cibles  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    USE msdb ;  
    GO  
    -- resynchronizes the SEATTLE1 target server  
    EXEC dbo.sp_resync_targetserver  
        N'SEATTLE1' ;  
    GO  
    ```  
  
 Pour plus d’informations, consultez [sp_resync_targetserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-resync-targetserver-transact-sql).  
  
  
