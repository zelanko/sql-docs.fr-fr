---
title: Configurer les propriétés générales de la gestion basée sur des stratégies | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.dmf.PolicyManagement.f1
helpviewer_keywords:
- Policy-Based Management, configure properties
ms.assetid: 6d1e0e37-29ea-408a-a055-384984d884be
caps.latest.revision: 8
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 6a33573e8e28464a098a6e958504fe32bdd9aea1
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43811065"
---
# <a name="configure-the-general-properties-of-policy-based-management"></a>Configurer les propriétés générales de la gestion basée sur des stratégies
  Cette rubrique explique comment configurer les propriétés de la gestion basée sur des stratégies dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour configurer la gestion basée sur des stratégies à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 Nécessite l'appartenance au rôle de base de données fixe PolicyAdministratorRole.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-configure-policy-based-management"></a>Pour configurer la Gestion basée sur des stratégies  
  
1.  Dans l’ **Explorateur d’objets**, cliquez sur le signe plus (+) pour développer le serveur sur lequel vous voulez configurer les propriétés de la gestion basée sur des stratégies.  
  
2.  Cliquez sur le signe plus (+) pour développer le dossier **Gestion** .  
  
3.  Cliquez avec le bouton droit sur **Gestion de la stratégie** , puis sélectionnez **Propriétés**.  
  
     Les options suivantes sont disponibles dans la boîte de dialogue **Propriétés de gestion de la stratégie** .  
  
     **Activé**  
     Spécifie si la Gestion basée sur des stratégies est activée.  
  
     **HistoryRetentionInDays**  
     Spécifie le nombre de jours pendant lesquels l'historique des évaluations de stratégies doit être conservé. Si cette valeur est 0 (valeur par défaut), l'historique n'est pas supprimé automatiquement.  
  
     **LogOnSuccess**  
     Spécifie si la Gestion basée sur des stratégies consigne les évaluations de stratégies réussies.  
  
    -   Lorsque cette valeur est False (valeur par défaut), seules les évaluations de stratégies qui ont échoué sont consignées.  
  
    -   Lorsque cette valeur est True, les réussites et les échecs des évaluations de stratégies sont enregistrés.  
  
4.  Lorsque vous avez terminé, cliquez sur **OK**.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-configure-policy-based-management"></a>Pour configurer la Gestion basée sur des stratégies  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    -- enables Policy-Based Management   
    USE msdb;  
    GO  
    EXEC dbo.sp_syspolicy_configure   
         @name = N'Enabled',   
         @value = 1;  
    GO  
    ```  
  
 Pour plus d’informations, consultez [sp_syspolicy_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syspolicy-configure-transact-sql).  
  
  
