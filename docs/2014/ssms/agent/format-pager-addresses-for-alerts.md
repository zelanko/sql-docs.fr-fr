---
title: Mettre en forme des adresses de radiomessagerie pour les alertes | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- pager addresses [SQL Server]
- SQL Server Agent, alerts
- formats [SQL Server], pager addresses
- pager notifications [SQL Server]
- addresses [SQL Server]
- alerts [SQL Server], pager addresses
ms.assetid: a9797d01-1050-442c-9038-ed4bfee1e76a
caps.latest.revision: 23
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 83ece1b0392f303d10b7f431789c6829abb87bdf
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37256041"
---
# <a name="format-pager-addresses-for-alerts"></a>Mettre en forme des adresses de radiomessagerie pour les alertes
  Cette rubrique explique comment mettre en forme les adresses de radiomessagerie pour les alertes de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour mettre en forme des adresses de radiomessagerie, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 Par défaut, les membres du rôle serveur fixe **sysadmin** peuvent afficher des informations sur une alerte. Les autres utilisateurs doivent disposer du rôle de base de données fixe **SQLAgentOperatorRole** dans la base de données **msdb** .  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-format-pager-addresses"></a>Pour mettre en forme des adresses de radiomessagerie  
  
1.  Dans l' **Explorateur d'objets**, cliquez sur le signe plus pour développer le serveur qui contient l'alerte que vous souhaitez envoyer à un récepteur de radiomessagerie.  
  
2.  Cliquez avec le bouton droit sur **Agent SQL Server** , puis sélectionnez **Propriétés**.  
  
3.  Sous **Sélectionner une page**, sélectionnez **Système d'alerte**.  
  
4.  Dans les zones **Ligne À** et **Ligne Cc** du champ **Format d’adresse pour les messages de radiomessagerie** , entrez le préfixe ou le suffixe de l’adresse de radiomessagerie. L'adresse réelle de radiomessagerie de l'opérateur est insérée lors de l'envoi d'une notification.  
  
5.  Dans la zone **Objet** , entrez le préfixe ou le suffixe de la ligne Objet.  
  
6.  Cochez la case **Inclure le corps du message dans la page de notification** pour inclure l’e-mail complet, ainsi que le message de radiomessagerie (contrairement à la ligne Objet uniquement).  
  
7.  Lorsque vous avez terminé, cliquez sur **OK**.  
  
  