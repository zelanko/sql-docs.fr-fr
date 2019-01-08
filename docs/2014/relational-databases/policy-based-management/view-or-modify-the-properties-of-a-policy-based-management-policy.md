---
title: Afficher ou modifier les propriétés d’une stratégie de gestion basée sur des stratégies | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, modify policies
- Policy-Based Management, view policies
ms.assetid: ba805504-5db5-4731-a8da-a0e89cb20c37
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: a61e48294d39c955e806b8dd4f127bf8bfec2027
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52758151"
---
# <a name="view-or-modify-the-properties-of-a-policy-based-management-policy"></a>Afficher ou modifier les propriétés d'une stratégie de gestion basée sur des stratégies
  Cette rubrique décrit comment afficher ou modifier les propriétés d'une stratégie de gestion basée sur des stratégies dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour afficher ou modifier les propriétés d’une stratégie à l’aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 Nécessite l'appartenance au rôle PolicyAdministratorRole dans la base de données msdb.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-view-the-properties-of-all-policies-on-an-object"></a>Pour afficher les propriétés de toutes les stratégies sur un objet  
  
1.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur un serveur, un objet de serveur, une base de données ou un objet de base de données, pointez sur **Stratégies** et sélectionnez **Afficher**. Pour plus d’informations sur les options disponibles dans la boîte de dialogue **Afficher les stratégies -***nom_objet*, consultez [Boîte de dialogue Afficher les stratégies](view-policies-dialog-box.md).  
  
2.  Lorsque vous avez terminé, cliquez sur **Fermer**.  
  
#### <a name="to-view-or-modify-a-specific-policys-properties"></a>Pour afficher ou modifier les propriétés d'une stratégie spécifique  
  
1.  Dans **l’Explorateur d’objets**, cliquez sur le signe plus (+) pour développer la stratégie de gestion basée sur des stratégies que vous souhaitez afficher ou modifier.  
  
2.  Cliquez sur le signe plus (+) pour développer le dossier **Gestion** .  
  
3.  Cliquez sur le signe plus (+) pour développer **Gestion de la stratégie**.  
  
4.  Cliquez sur le signe plus (+) pour développer le dossier **Stratégies** .  
  
5.  Cliquez avec le bouton droit sur la stratégie que vous souhaitez afficher ou modifier, puis sélectionnez **Propriétés**. Pour plus d’informations sur les options disponibles dans la boîte de dialogue **Créer une nouvelle stratégie-***nom_stratégie*, consultez [Boîte de dialogue Créer une nouvelle stratégie ou Ouvrir une stratégie, page Général](../../integration-services/general-page-of-integration-services-designers-options.md) ou [Boîte de dialogue Créer une nouvelle stratégie ou Ouvrir une stratégie, page Description](create-new-policy-or-open-policy-dialog-box-description-page.md).  
  
6.  Lorsque vous avez terminé, cliquez sur **OK**.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-view-a-policys-properties"></a>Pour afficher les propriétés d'une stratégie  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    USE msdb;  
    GO  
    SELECT name,  
       execution_mode,  
       description,  
       is_enabled,  
       job_id  
    FROM syspolicy_policies;  
    GO  
    ```  
  
 Pour plus d’informations, consultez [syspolicy_policies &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/syspolicy-policies-transact-sql).  
  
  
