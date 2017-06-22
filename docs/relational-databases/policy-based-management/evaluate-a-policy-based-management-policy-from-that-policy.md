---
title: "Évaluer une stratégie de gestion basée sur des stratégies à partir de cette stratégie | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Policy-Based Management, evaluate policy
ms.assetid: 0b3214bd-d0ab-45ab-9281-3d95507abe54
caps.latest.revision: 6
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: b7d900248ead5e2de6b6aa2423296d0723f32ba5
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="evaluate-a-policy-based-management-policy-from-that-policy"></a>Évaluer une stratégie de gestion basée sur des stratégies pour cette stratégie
  Cette rubrique explique comment évaluer une stratégie à l'aide de cette stratégie dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour évaluer une stratégie à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Nécessite l'appartenance au rôle PolicyAdministratorRole dans la base de données msdb.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-evaluate-a-policy"></a>Pour évaluer une stratégie  
  
1.  Dans l' **Explorateur d'objets**, cliquez sur le signe plus (+) pour développer le serveur qui contient la stratégie que vous souhaitez évaluer.  
  
2.  Cliquez sur le signe plus (+) pour développer le dossier **Gestion** .  
  
3.  Cliquez sur le signe plus (+) pour développer **Gestion de la stratégie**.  
  
4.  Cliquez sur le signe plus (+) pour développer le dossier **Stratégies** .  
  
5.  Cliquez avec le bouton droit sur la stratégie à évaluer, puis sélectionnez **Évaluer**.  
  
6.  La boîte de dialogue **Résultats d'évaluation**  indique les résultats de l'évaluation de la stratégie. Pour les cibles qui ne sont pas conformes à la stratégie et ont des propriétés qui peuvent être reconfigurées par la Gestion basée sur des stratégies, vous pouvez imposer la conformité en cliquant sur **Appliquer**. Pour plus d'informations sur les options disponibles de la boîte de dialogue **Évaluer les stratégies** , consultez [Evaluate Policies Dialog Box, Policy Selection Page](../../relational-databases/policy-based-management/evaluate-policies-dialog-box-policy-selection-page.md) et [Evaluate Policies Dialog Box, Evaluation Results Page](../../relational-databases/policy-based-management/evaluate-policies-dialog-box-evaluation-results-page.md).  
  
7.  Lorsque vous avez terminé, cliquez sur **Fermer**.  
  
  
