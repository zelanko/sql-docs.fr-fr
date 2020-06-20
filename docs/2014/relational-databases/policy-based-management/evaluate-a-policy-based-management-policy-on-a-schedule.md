---
title: Évaluer une stratégie de gestion basée sur des stratégies sur une planification | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, evaluate policy
ms.assetid: bea09522-ff47-4037-ab55-a98ea7c10099
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a39b00bdb22cce3a15c06366c504f62305ded1f9
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85047799"
---
# <a name="evaluate-a-policy-based-management-policy-on-a-schedule"></a>Évaluer une stratégie de gestion basée sur des stratégies sur une planification
  Cette rubrique explique comment évaluer une stratégie de gestion basée sur des stratégies sur une planification dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour évaluer une stratégie sur une planification à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 Nécessite l'appartenance au rôle PolicyAdministratorRole dans la base de données msdb.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-evaluate-a-policy-on-a-schedule"></a>Pour évaluer une stratégie sur une planification  
  
1.  Dans l' **Explorateur d'objets**, cliquez sur le signe plus (+) pour développer le serveur qui contient la planification que vous souhaitez évaluer.  
  
2.  Cliquez sur le signe plus (+) pour développer le dossier **Gestion** .  
  
3.  Cliquez sur le signe plus (+) pour développer **Gestion de la stratégie**.  
  
4.  Cliquez sur le signe plus (+) pour développer le dossier **Stratégies** .  
  
5.  Cliquez avec le bouton droit sur la stratégie dont vous voulez évaluer une planification, puis sélectionnez **Propriétés**.  
  
6.  Dans la boîte de dialogue **Ouvrir une stratégie -** _nom_stratégie_, dans la liste **Mode d’évaluation**, sélectionnez **Selon la planification**.  
  
7.  Sous **Planification**, cliquez sur **Choisir** pour spécifier une planification existante ou sur **Nouveau** pour créer une planification.  
  
8.  Lorsque vous avez terminé, cliquez sur **OK**.  
  
  
