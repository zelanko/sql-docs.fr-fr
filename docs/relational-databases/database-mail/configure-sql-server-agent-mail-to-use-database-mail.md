---
title: "Configurer la messagerie de SQL Server Agent en vue de l’utilisation de la messagerie de base de données | Microsoft Docs"
ms.custom: 
ms.date: 08/05/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Database Mail [SQL Server], SQL Server Agent Mail
- SQL Server Agent Mail
ms.assetid: 4b8b61bd-4bd1-43cd-b6e5-c6ed2e101dce
caps.latest.revision: "31"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 15fafd5b18011c54aee21daeaf9bc4ae295ea205
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="configure-sql-server-agent-mail-to-use-database-mail"></a>Configurer la messagerie de l'Agent SQL Server en vue de l'utilisation de la messagerie de base de données
  Cette rubrique explique comment configurer l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour utiliser la messagerie de base de données pour envoyer une notification et des alertes dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  Pour plus d’informations sur l’activation et la configuration de la messagerie de base de données, consultez [Configurer la messagerie de base de données](../../relational-databases/database-mail/configure-database-mail.md).  Pour obtenir un exemple faisant appel à [!INCLUDE[tsql](../../includes/tsql-md.md)][Créer un profil de messagerie de base de données](../../relational-databases/database-mail/create-a-database-mail-profile.md)
  
-   **Avant de commencer :**  
  
-   [Conditions préalables](#Prerequisites)  
  
-   [Sécurité](#Security)  
  
-   [Pour configurer l'Agent SQL Server en vue de l'utilisation de la messagerie de base de données, à l'aide de SQL Server Management Studio](#SSMSProcedure)  
  
-   [Tâches de suivi](#Follow_Up)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Prerequisites"></a> Conditions préalables  
  
-   [Activer la messagerie de base de données](../../relational-databases/database-mail/configure-database-mail.md).  
  
-    [Créer un compte de messagerie de base de données](../../relational-databases/database-mail/create-a-database-mail-account.md) pour le compte de service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent à utiliser.  
  
-   [Créer un profil de messagerie de base de données](../../relational-databases/database-mail/create-a-database-mail-profile.md) pour le compte de service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent à utiliser, et ajouter l’utilisateur au rôle **DatabaseMailUserRole** de la base de données **msdb** .  
  
-   Définir le profil comme profil par défaut pour la base de données **msdb** .  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 L'utilisateur qui crée les comptes de profils et exécute des procédures stockées doit être membre du rôle serveur fixe sysadmin.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 **Pour configurer l'Agent SQL Server en vue de l'utilisation de la messagerie de base de données**  
  
-   Dans l'Explorateur d'objets, développez une instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Cliquez avec le bouton droit sur **SQL Server Agent**, puis cliquez sur **Propriétés**.  
  
-   Cliquez sur **Système d'alerte**.  
  
-   Sélectionnez **Activer le profil de messagerie**.  
  
-   Dans la liste **Système de messagerie** , choisissez **Database Mail**.  
  
-   Dans la liste **Profil de la messagerie**, sélectionnez un profil de messagerie pour la messagerie de base de données.  
  
-   Redémarrez l'Agent SQL Server.  
  
##  <a name="Follow_Up"></a> Tâches de suivi  
 Les tâches suivantes sont nécessaires pour terminer la configuration de l'Agent pour envoyer des alertes et des notifications.  
  
-   [Alertes](http://msdn.microsoft.com/library/3f57d0f0-4781-46ec-82cd-b751dc5affef)  
  
     Les alertes peuvent être configurées pour notifier à un opérateur une situation du système d'exploitation ou un événement de base de données particuliers.  
  
-   [Opérateurs](http://msdn.microsoft.com/library/38e8488f-2669-4cea-b9c3-5f394a663678)  
  
     Les opérateurs sont des alias pour les personnes ou les groupes qui peuvent recevoir une notification électronique  
  
  
