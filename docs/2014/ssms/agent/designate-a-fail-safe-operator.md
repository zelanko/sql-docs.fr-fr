---
title: Désigner un opérateur de prévention de défaillance | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, operators
- fail-safe operator [SQL Server]
- jobs [SQL Server Agent], operators
- notifications [SQL Server], job status
ms.assetid: 0f4eb513-5c0a-4523-974e-e85c1deeb57f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 73eb11034d185deb9c004d138230fff8fbf27bb6
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84995293"
---
# <a name="designate-a-fail-safe-operator"></a>Désigner un opérateur de prévention de défaillance
  Un opérateur de prévention de défaillance est un utilisateur qui reçoit l'alerte si l'opérateur désigné n'est pas joignable. Cette rubrique explique comment définir un opérateur de prévention de défaillance pour recevoir [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] des notifications d’alerte de l’agent dans à [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] .  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour désigner un opérateur de prévention de défaillance, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Limitations et restrictions  
  
-   Les options de radiomessagerie et **net send** seront supprimées de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’agent dans une version ultérieure de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Évitez d'utiliser ces fonctionnalités dans une nouvelle tâche de développement et prévoyez de modifier les applications qui les utilisent actuellement.  
  
-   Remarque : SQL Server Agent doit être configuré pour utiliser la messagerie de base de données pour envoyer des notifications aux opérateurs par messagerie électronique ou radiomessagerie. Pour plus d'informations, consultez [Affecter des alertes à un opérateur](assign-alerts-to-an-operator.md).  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] est un outil dont l'interface graphique permet de gérer facilement les travaux. Son utilisation est recommandée pour créer et gérer l'infrastructure des travaux.  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** peuvent désigner des opérateurs de prévention de défaillance.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-designate-a-fail-safe-operator"></a>Pour désigner un opérateur de prévention de défaillance  
  
1.  Dans **l’Explorateur d’objets** , cliquez sur le signe plus pour développer le serveur qui contient l’opérateur de SQL Server Agent que vous souhaitez désigner comme opérateur de prévention de défaillance.  
  
2.  Cliquez avec le bouton droit sur **SQL Server Agent** , puis sélectionnez **Propriétés**.  

3.  Dans la boîte de dialogue Propriétés de la **SQL Server Agent-**_Server_name_ , sous **Sélectionner une page**, sélectionnez **système d’alerte**.  
 
4.  Sous **Opérateur de prévention de défaillance**, sélectionnez **Activer l’opérateur de prévention de défaillance**.  
  
5.  Dans la liste **Opérateur** , sélectionnez l’opérateur que vous souhaitez définir comme opérateur de prévention de défaillance.  
  
6.  Cochez tout ou partie des cases suivantes pour spécifier comment l’opérateur doit être informé : **Messagerie électronique**, **Radiomessagerie**ou **NET SEND**.  
  
7.  Lorsque vous avez terminé, cliquez sur **OK**.  
  
  
