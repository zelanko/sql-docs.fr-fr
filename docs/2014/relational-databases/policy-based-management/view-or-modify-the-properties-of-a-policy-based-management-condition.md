---
title: Afficher ou modifier les propriétés d’une condition de gestion basée sur des stratégies | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, view policy conditions
- Policy-Based Management, modify policy conditions
ms.assetid: 890d7384-8444-4767-bb6f-f5debb155747
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 340423e23037ae401b1e5749fbed38b1822cfb41
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62677019"
---
# <a name="view-or-modify-the-properties-of-a-policy-based-management-condition"></a>Afficher ou modifier les propriétés d'une condition de gestion basée sur des stratégies
  Cette rubrique explique comment afficher ou modifier les propriétés d'une condition de gestion basée sur des stratégies dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour afficher ou modifier les propriétés d’une condition à l’aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Nécessite l'appartenance au rôle PolicyAdministratorRole dans la base de données msdb.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-view-or-modify-a-conditions-properties"></a>Pour afficher ou modifier les propriétés d'une condition  
  
1.  Dans l' **Explorateur d'objets**, cliquez sur le signe plus (+) pour développer le serveur qui contient la condition que vous souhaitez afficher ou modifier.  
  
2.  Cliquez sur le signe plus (+) pour développer le dossier **Gestion** .  
  
3.  Cliquez sur le signe plus (+) pour développer **Gestion de la stratégie**.  
  
4.  Cliquez sur le signe plus (+) pour développer le dossier **Conditions** .  
  
5.  Cliquez avec le bouton droit sur la condition à afficher ou supprimer, puis sélectionnez **Propriétés**. Pour plus d’informations sur les options disponibles dans la boîte de dialogue **Ouvrir une condition -**_nom_condition_ consultez [Boîte de dialogue Créer une nouvelle condition ou Ouvrir une condition, page Général](../../integration-services/general-page-of-integration-services-designers-options.md), [Boîte de dialogue Ouvrir une condition, page Stratégies dépendantes](open-condition-dialog-box-dependent-policies-page.md), [Boîte de dialogue Créer une nouvelle condition ou Ouvrir une condition, page Description](create-new-condition-or-open-condition-dialog-box-description-page.md) et [Boîte de dialogue Modification avancée &#40;Condition&#41;](advanced-edit-condition-dialog-box.md).  
  
6.  Lorsque vous avez terminé, cliquez sur **OK**.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-view-a-conditions-properties"></a>Pour afficher les propriétés d'une condition  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    USE msdb;  
    GO  
    SELECT name,  
       description,  
       facet,  
       expression,  
       is_name_condition,  
       obj_name  
    FROM syspolicy_conditions;  
    GO  
  
    ```  
  
 Pour plus d’informations, consultez [syspolicy_conditions &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/syspolicy-conditions-transact-sql).  
  
  
