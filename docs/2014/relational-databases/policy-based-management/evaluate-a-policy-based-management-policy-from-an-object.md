---
title: Évaluer une stratégie de gestion basée sur des stratégies à partir d’un objet | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, evaluate policy
ms.assetid: b9e9d646-4894-4dee-a02a-0c71a8dc020e
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 43116e7fdec059f822a5381696a485aba767402b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62705230"
---
# <a name="evaluate-a-policy-based-management-policy-from-an-object"></a>Évaluer une stratégie de gestion basée sur des stratégies à partir d'un objet
  Cette rubrique explique comment évaluer une stratégie d'une instance de serveur, d'une base de données ou d'un objet de base de données dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour évaluer une stratégie à partir d'un objet à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Le mode d'exécution est défini dans le cadre de la stratégie et ne peut pas être modifié dans la boîte de dialogue **Évaluer les stratégies** .  
  
-   La boîte de dialogue **Évaluer les stratégies** affiche seulement les stratégies appropriées à l'objet de base de données.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Nécessite l'appartenance au rôle PolicyAdministratorRole dans la base de données msdb.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-evaluate-a-policy-from-an-object"></a>Pour évaluer une stratégie à partir d'un objet  
  
1.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur une instance de serveur, une base de données ou un objet de base de données, pointez sur **Stratégies**, puis sélectionnez **Évaluer**.  
  
2.  Dans la boîte de dialogue **Évaluer les stratégies** , sélectionnez une ou plusieurs stratégies, puis cliquez sur **Évaluer** pour exécuter la stratégie en mode d'évaluation. Cela génère un rapport de conformité pour le jeu de cibles mais n'applique pas la conformité future et ne reconfigure pas [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour les cibles qui ne sont pas conformes aux stratégies sélectionnées et ont des propriétés qui peuvent être reconfigurées par la Gestion basée sur des stratégies, vous pouvez imposer la conformité aux stratégies en cliquant sur **Appliquer**. Pour plus d'informations sur les options disponibles de la boîte de dialogue **Évaluer les stratégies** , consultez [Evaluate Policies Dialog Box, Policy Selection Page](evaluate-policies-dialog-box-policy-selection-page.md), [Evaluate Policies Dialog Box, Evaluation Results Page](evaluate-policies-dialog-box-evaluation-results-page.md)et [Results Detailed View Dialog Box](results-detailed-view-dialog-box.md).  
  
3.  Lorsque vous avez terminé, cliquez sur **Fermer**.  
  
  
