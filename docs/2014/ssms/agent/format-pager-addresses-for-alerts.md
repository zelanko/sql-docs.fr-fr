---
title: Mettre en forme des adresses de radiomessagerie pour les alertes | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- pager addresses [SQL Server]
- SQL Server Agent, alerts
- formats [SQL Server], pager addresses
- pager notifications [SQL Server]
- addresses [SQL Server]
- alerts [SQL Server], pager addresses
ms.assetid: a9797d01-1050-442c-9038-ed4bfee1e76a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 535ae5f92fea0222468ed64f567154495e329a61
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63044197"
---
# <a name="format-pager-addresses-for-alerts"></a>Format Pager Addresses for Alerts
  Cette rubrique explique comment mettre en forme des adresses [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de radiomessagerie pour [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] les [!INCLUDE[tsql](../../includes/tsql-md.md)]alertes de l’agent dans à l’aide de ou de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour mettre en forme les adresses de radiomessagerie, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Par défaut, les membres du rôle serveur fixe **sysadmin** peuvent afficher des informations sur une alerte. Les autres utilisateurs doivent disposer du rôle de base de données fixe **SQLAgentOperatorRole** dans la base de données **msdb** .  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-format-pager-addresses"></a>Pour mettre en forme des adresses de radiomessagerie  
  
1.  Dans l' **Explorateur d'objets**, cliquez sur le signe plus pour développer le serveur qui contient l'alerte que vous souhaitez envoyer à un récepteur de radiomessagerie.  
  
2.  Cliquez avec le bouton droit sur **SQL Server Agent** et sélectionnez **Propriétés** .  
  
3.  Sous **Sélectionner une page**, sélectionnez **Système d'alerte**.  
  
4.  Dans les zones **Ligne À** et **Ligne Cc** du champ **Format d’adresse pour les messages de radiomessagerie** , entrez le préfixe ou le suffixe de l’adresse de radiomessagerie. L'adresse réelle de radiomessagerie de l'opérateur est insérée lors de l'envoi d'une notification.  
  
5.  Dans la zone **Objet** , entrez le préfixe ou le suffixe de la ligne Objet.  
  
6.  Cochez la case **Inclure le corps du message dans la page de notification** pour inclure l’e-mail complet, ainsi que le message de radiomessagerie (contrairement à la ligne Objet uniquement).  
  
7.  Lorsque vous avez terminé, cliquez sur **OK**.  
  
  
