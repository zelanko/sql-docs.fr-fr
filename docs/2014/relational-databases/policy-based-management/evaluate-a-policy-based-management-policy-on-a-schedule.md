---
title: Évaluer une stratégie de gestion basée sur des stratégies sur une planification | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Policy-Based Management, evaluate policy
ms.assetid: bea09522-ff47-4037-ab55-a98ea7c10099
caps.latest.revision: 6
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 56354766e7000bf5e7d7a1eb214da1be796ae82f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36043124"
---
# <a name="evaluate-a-policy-based-management-policy-on-a-schedule"></a>Évaluer une stratégie de gestion basée sur des stratégies sur une planification
  Cette rubrique explique comment évaluer une stratégie de gestion basée sur des stratégies sur une planification dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour évaluer une stratégie sur une planification à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 Nécessite l'appartenance au rôle PolicyAdministratorRole dans la base de données msdb.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-evaluate-a-policy-on-a-schedule"></a>Pour évaluer une stratégie sur une planification  
  
1.  Dans l' **Explorateur d'objets**, cliquez sur le signe plus (+) pour développer le serveur qui contient la planification que vous souhaitez évaluer.  
  
2.  Cliquez sur le signe plus (+) pour développer le dossier **Gestion** .  
  
3.  Cliquez sur le signe plus (+) pour développer **Gestion de la stratégie**.  
  
4.  Cliquez sur le signe plus (+) pour développer le dossier **Stratégies** .  
  
5.  Cliquez avec le bouton droit sur la stratégie dont vous voulez évaluer une planification, puis sélectionnez **Propriétés**.  
  
6.  Dans la boîte de dialogue **Ouvrir une stratégie –***nom_stratégie*, dans la liste **Mode d’évaluation**, sélectionnez **Selon la planification**.  
  
7.  Sous **Planification**, cliquez sur **Choisir** pour spécifier une planification existante ou sur **Nouveau** pour créer une planification.  
  
8.  Lorsque vous avez terminé, cliquez sur **OK**.  
  
  