---
title: Supprimer une condition de gestion basée sur des stratégies | Microsoft Docs
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
- Policy-Based Management, delete policy conditions
ms.assetid: e04148b8-f6dd-4c50-a5ef-c650b71dbf4d
caps.latest.revision: 9
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 76159944f4a575efc1de12558a7c84cdc434f557
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36052386"
---
# <a name="delete-a-policy-based-management-condition"></a>Supprimer une condition de gestion basée sur des stratégies
  Cette rubrique explique comment supprimer une condition de gestion basée sur des stratégies dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour supprimer une condition à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 Nécessite l'appartenance au rôle PolicyAdministratorRole dans la base de données msdb.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-delete-a-condition"></a>Pour supprimer une condition  
  
1.  Dans l' **Explorateur d'objets**, cliquez sur le signe plus (+) pour développer le serveur qui contient la condition que vous souhaitez supprimer.  
  
2.  Cliquez sur le signe plus (+) pour développer le dossier **Gestion** .  
  
3.  Cliquez sur le signe plus (+) pour développer **Gestion de la stratégie**.  
  
4.  Cliquez sur le signe plus (+) pour développer le dossier **Conditions** .  
  
5.  Cliquez avec le bouton droit sur la condition à supprimer, puis sélectionnez **Supprimer**.  
  
6.  Dans la boîte de dialogue **Supprimer un objet** , assurez-vous que la condition correcte est sélectionnée, puis cliquez sur **OK**.  
  
  