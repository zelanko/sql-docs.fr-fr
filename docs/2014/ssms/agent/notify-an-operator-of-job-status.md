---
title: Notifier l’état d’un travail à un opérateur | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- status information [SQL Server], jobs
- jobs [SQL Server Agent], notification options
- SQL Server Agent jobs, status
- jobs [SQL Server Agent], status
- SQL Server Agent jobs, notification options
- notifications [SQL Server], job status
ms.assetid: e7399505-27ac-48d9-a637-73bf92b9df49
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ff9340d7c9fb768f9e057d00868a9e238421a5f4
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "72798204"
---
# <a name="notify-an-operator-of-job-status"></a>Notify an Operator of Job Status
  Cette rubrique explique comment définir des options de notification [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] dans à [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]l' [!INCLUDE[tsql](../../includes/tsql-md.md)]aide de, ou SQL Server Management Objects [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , de sorte que agent puisse envoyer des notifications aux opérateurs à propos des travaux.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour notifier l'état d'un travail à un opérateur, utilisez :**  
  
     [SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [SQL Server Management Objects](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
 Pour plus d'informations, consultez [Implémenter la sécurité de SQL Server Agent](implement-sql-server-agent-security.md).  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-notify-an-operator-of-job-status"></a>Pour notifier l'état d'un travail à un opérateur  
  
1.  Dans **l’Explorateur d'objets**, connectez-vous à une instance [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] et développez-la.  
  
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
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> Utilisation de Transact-SQL  
  
#### <a name="to-notify-an-operator-of-job-status"></a>Pour notifier l'état d'un travail à un opérateur  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```sql
    -- adds an e-mail notification for the specified alert (Test Alert).  
    -- This example assumes that Test Alert already exists and that Fran??ois Ajenstat is a valid operator name.  
    USE msdb ;  
    GO  
    EXEC dbo.sp_add_notification   
    @alert_name = N'Test Alert',   
    @operator_name = N'Fran??ois Ajenstat',   
    @notification_method = 1 ;  
    GO  
    ```  
  
 Pour plus d’informations, consultez [sp_add_notification &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql).  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a>Utilisation de SQL Server Management Objects  
 **Pour notifier l'état d'un travail à un opérateur**  
  
 Utilisez la classe `Job` à l'aide d'un langage de programmation que vous choisissez, tel que Visual Basic, Visual C# ou PowerShell. Pour plus d’informations, consultez [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).  
