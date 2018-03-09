---
title: "Supprimer une stratégie de gestion basée sur des stratégies | Microsoft Docs"
ms.custom: 
ms.date: 08/01/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance-monitor
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Policy-Based Management, delete policies
ms.assetid: 488f0305-190c-4223-aa5c-e9bd43b520eb
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0152154d83930ab677a29fc70fa605a61ae5ead0
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/18/2018
---
# <a name="delete-a-policy-based-management-policy"></a>Supprimer une stratégie de gestion basée sur des stratégies
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Cette rubrique explique comment supprimer une stratégie de gestion basée sur des stratégies dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour supprimer une stratégie à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 Nécessite l'appartenance au rôle PolicyAdministratorRole dans la base de données msdb.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-delete-a-policy"></a>Pour supprimer une stratégie  
  
1.  Dans l'Explorateur d'objets, cliquez sur le signe plus (+) pour développer la stratégie de gestion basée sur des stratégies que vous souhaitez supprimer.  
  
2.  Cliquez sur le signe plus (+) pour développer le dossier **Gestion** .  
  
3.  Cliquez sur le signe plus (+) pour développer **Gestion de la stratégie**.  
  
4.  Cliquez sur le signe plus (+) pour développer le dossier **Stratégies** .  
  
5.  Cliquez avec le bouton droit sur la stratégie à supprimer, puis sélectionnez **Supprimer**.  
  
6.  Dans la boîte de dialogue **Supprimer un objet** , assurez-vous que la condition correcte est sélectionnée, puis cliquez sur **OK**.  
  
  
