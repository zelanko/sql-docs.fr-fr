---
title: Notifier l’état d’un travail à un opérateur | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- status information [SQL Server], jobs
- jobs [SQL Server Agent], notification options
- SQL Server Agent jobs, status
- jobs [SQL Server Agent], status
- SQL Server Agent jobs, notification options
- notifications [SQL Server], job status
ms.assetid: e7399505-27ac-48d9-a637-73bf92b9df49
caps.latest.revision: 32
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 26bb76499741ff1448a30ed818bc07e2d96d1928
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37181446"
---
# <a name="notify-an-operator-of-job-status"></a>Notifier l’état d’un travail à un opérateur
  Cette rubrique explique comment définir des options de notification dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]ou de SQL Server Management Objects, de sorte que [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent puisse envoyer des notifications aux opérateurs à propos des travaux.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour notifier l'état d'un travail à un opérateur, utilisez :**  
  
     [SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [SQL Server Management Objects](#SMO)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
 Pour plus d'informations, consultez [Implémenter la sécurité de SQL Server Agent](implement-sql-server-agent-security.md).  
  
##  <a name="SSMS"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-notify-an-operator-of-job-status"></a>Pour notifier l'état d'un travail à un opérateur  
  
1.  Dans l' **Explorateur d'objets** , connectez-vous à une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]et développez-la.  
  
2.  Développez **Agent SQL Server**, puis **Travaux**, cliquez avec le bouton droit sur le travail à modifier et sélectionnez **Propriétés**.  
  
3.  Dans la boîte de dialogue **Propriétés du travail** , sélectionnez la page **Notifications** .  
  
4.  Pour avertir un opérateur par e-mail, cochez la case **Messagerie électronique**, sélectionnez un opérateur dans la liste, puis l’une des options suivantes :  
  
    -   **Lors de la réussite du travail** pour avertir l'opérateur quand le travail s'est effectué avec succès ;  
  
    -   **Lors de l'échec du travail** pour avertir l'opérateur quand le travail a échoué.  
  
    -   **Lorsque le travail est terminé** pour avertir l'opérateur, quel que soit l'état du travail à son achèvement.  
  
5.  Pour avertir un opérateur par radiomessagerie, activez la case à cocher **Radiomessagerie**, sélectionnez un opérateur dans la liste, puis l'une des options suivantes :  
  
    -   **Lors de la réussite du travail** pour avertir l'opérateur quand le travail s'est effectué avec succès ;  
  
    -   **Lors de l'échec du travail** pour avertir l'opérateur quand le travail a échoué.  
  
    -   **Lorsque le travail est terminé** pour avertir l'opérateur, quel que soit l'état du travail à son achèvement.  
  
6.  Pour avertir un opérateur par envoi réseau, activez la case à cocher **Envoi réseau**, sélectionnez un opérateur dans la liste, puis l'une des options suivantes :  
  
    -   **Lors de la réussite du travail** pour avertir l'opérateur quand le travail s'est effectué avec succès ;  
  
    -   **Lors de l'échec du travail** pour avertir l'opérateur quand le travail a échoué.  
  
    -   **Lorsque le travail est terminé** pour avertir l'opérateur, quel que soit l'état du travail à son achèvement.  
  
##  <a name="TSQL"></a> Utilisation de Transact-SQL  
  
#### <a name="to-notify-an-operator-of-job-status"></a>Pour notifier l'état d'un travail à un opérateur  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    -- adds an e-mail notification for the specified alert (Test Alert).  
    -- This example assumes that Test Alert already exists and that François Ajenstat is a valid operator name.  
    USE msdb ;  
    GO  
    EXEC dbo.sp_add_notification   
    @alert_name = N'Test Alert',   
    @operator_name = N'François Ajenstat',   
    @notification_method = 1 ;  
    GO  
    ```  
  
 Pour plus d’informations, consultez [sp_add_notification &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql).  
  
##  <a name="SMO"></a> À l’aide de SQL Server Management Objects  
 **Pour notifier l'état d'un travail à un opérateur**  
  
 Utilisez la `Job` classe à l’aide d’un langage de programmation que vous choisissez, tel que Visual Basic, Visual c# ou PowerShell. Pour plus d’informations, consultez [SQL Server Management Objects (SMO)](http://msdn.microsoft.com/library/ms162169.aspx).  
  
  
