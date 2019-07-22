---
title: Créer une condition de gestion basée sur des stratégies | Microsoft Docs
ms.custom: ''
ms.date: 08/01/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, creating policy conditions
ms.assetid: 8a612f7e-6c70-49db-a4de-48431e097cc5
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 739d706749b24720861b7572bde7e29473f1d406
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67901161"
---
# <a name="create-a-new-policy-based-management-condition"></a>Créer une condition de gestion basée sur des stratégies.
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Cette rubrique explique comment créer une condition de gestion basée sur des stratégies dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour créer une condition à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Nécessite l'appartenance au rôle PolicyAdministratorRole dans la base de données msdb.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-create-a-condition"></a>Pour créer une condition  
  
1.  Dans l’ **Explorateur d’objets**, cliquez sur le signe plus (+) pour développer le serveur sur lequel vous souhaitez créer une condition de gestion basée sur des stratégies.  
  
2.  Cliquez sur le signe plus (+) pour développer le dossier **Gestion** .  
  
3.  Cliquez sur le signe plus (+) pour développer **Gestion de la stratégie**.  
  
4.  Cliquez sur le signe plus (+) pour développer le dossier **Facettes** .  
  
5.  Cliquez avec le bouton droit sur la facette dans laquelle vous souhaitez créer une nouvelle condition et sélectionnez **Nouvelle condition**.  
  
6.  Dans la boîte de dialogue **Créer une nouvelle condition** , dans la zone **Nom** , tapez le nom de la nouvelle condition.  
  
7.  Confirmez la facette correcte dans la liste **Facette** ou sélectionnez une facette différente.  
  
8.  Sous **Expression**, construisez des expressions de condition en sélectionnant une propriété de facette dans la zone **Champ** , avec son opérateur et sa valeur associés. Lorsque vous ajoutez plusieurs expressions, celles-ci peuvent être jointes à l'aide de **Et** ou **Ou**. Pour plus d’informations sur les options disponibles dans cette boîte de dialogue, consultez [Boîte de dialogue Créer une nouvelle condition ou Ouvrir une condition, page Général](../../relational-databases/policy-based-management/create-new-condition-or-open-condition-dialog-box-general-page.md), [Boîte de dialogue Créer une nouvelle condition ou Ouvrir une condition, page Description](../../relational-databases/policy-based-management/create-new-condition-or-open-condition-dialog-box-description-page.md) et [Boîte de dialogue Modification avancée &#40;Condition&#41;](../../relational-databases/policy-based-management/advanced-edit-condition-dialog-box.md).  
  
9. Lorsque vous avez terminé, cliquez sur **OK**.  
  
  
