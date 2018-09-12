---
title: Exporter une stratégie de gestion basée sur des stratégies | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, export policy
ms.assetid: f0001b33-9078-4432-8460-496736fb325a
caps.latest.revision: 7
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: b740a5934caedabf72d7aede9aa240849ace45f4
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43820935"
---
# <a name="export-a-policy-based-management-policy"></a>Exporter une stratégie de gestion basée sur des stratégies
  Cette rubrique explique comment exporter une stratégie de gestion basée sur des stratégies dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour exporter une stratégie à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 Nécessite l'appartenance au rôle PolicyAdministratorRole dans la base de données msdb.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-export-a-policy"></a>Pour exporter une stratégie  
  
1.  Dans l'Explorateur d'objets, cliquez sur le signe plus (+) pour développer la stratégie de gestion basée sur des stratégies que vous souhaitez exporter.  
  
2.  Cliquez sur le signe plus (+) pour développer le dossier **Gestion** .  
  
3.  Cliquez sur le signe plus (+) pour développer **Gestion de la stratégie**.  
  
4.  Cliquez sur le signe plus (+) pour développer le dossier **Stratégies** .  
  
5.  Cliquez avec le bouton droit sur la stratégie à exporter, puis sélectionnez **Exporter la stratégie**.  
  
6.  Dans la boîte de dialogue **Exporter la stratégie** , tapez le chemin d'accès et le nom du fichier dans la barre d'adresses. Ou bien, recherchez un emplacement approprié pour le fichier dans le volet de navigation de la boîte de dialogue, puis tapez le nom du fichier XML dans la zone **Nom de fichier** .  
  
7.  Lorsque vous avez terminé, cliquez sur **Enregistrer**.  
  
  
