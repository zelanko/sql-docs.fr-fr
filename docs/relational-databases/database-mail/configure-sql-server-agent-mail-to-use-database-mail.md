---
title: "Configurer la messagerie de l&#39;Agent SQL&#160;Server en vue de l&#39;utilisation de la messagerie de base de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "08/05/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "messagerie de base de données [SQL Server], messagerie de l’Agent SQL Server"
  - "Messagerie de l'Agent SQL Server"
ms.assetid: 4b8b61bd-4bd1-43cd-b6e5-c6ed2e101dce
caps.latest.revision: 31
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 31
---
# Configurer la messagerie de l&#39;Agent SQL&#160;Server en vue de l&#39;utilisation de la messagerie de base de donn&#233;es
  Cette rubrique explique comment configurer l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour utiliser la messagerie de base de données pour envoyer une notification et des alertes dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  Pour plus d’informations sur l’activation et la configuration de la messagerie de base de données, consultez [Configurer la messagerie de base de données](../../relational-databases/database-mail/configure-database-mail.md).  Pour obtenir un exemple faisant appel à [!INCLUDE[tsql](../../includes/tsql-md.md)][Créer un profil de messagerie de base de données](../../relational-databases/database-mail/create-a-database-mail-profile.md)
  
-   **Avant de commencer :**  
  
-   [Conditions préalables](#Prerequisites)  
  
-   [Sécurité](#Security)  
  
-   [Pour configurer l'Agent SQL Server en vue de l'utilisation de la messagerie de base de données, à l'aide de SQL Server Management Studio](#SSMSProcedure)  
  
-   [Tâches de suivi](#Follow_Up)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Prerequisites"></a> Conditions préalables  
  
-   [Activer la messagerie de base de données](../../relational-databases/database-mail/configure-database-mail.md).  
  
-    [Créer un compte de messagerie de base de données](../../relational-databases/database-mail/create-a-database-mail-account.md) pour le compte de service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent à utiliser.  
  
-   [Créer un profil de messagerie de base de données](../../relational-databases/database-mail/create-a-database-mail-profile.md) pour le compte de service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent à utiliser, et ajouter l’utilisateur au rôle **DatabaseMailUserRole** de la base de données **msdb**.  
  
-   Définir le profil comme profil par défaut pour la base de données **msdb** .  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 L'utilisateur qui crée les comptes de profils et exécute des procédures stockées doit être membre du rôle serveur fixe sysadmin.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 **Pour configurer l'Agent SQL Server en vue de l'utilisation de la messagerie de base de données**  
  
-   Dans l'Explorateur d'objets, développez une instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Cliquez avec le bouton droit sur **SQL Server Agent**, puis cliquez sur **Propriétés**.  
  
-   Cliquez sur **Système d'alerte**.  
  
-   Sélectionnez **Activer le profil de messagerie**.  
  
-   Dans la liste **Système de messagerie** , choisissez **Database Mail**.  
  
-   Dans la liste **Profil de la messagerie**, sélectionnez un profil de messagerie pour la messagerie de base de données.  
  
-   Redémarrez l'Agent SQL Server.  
  
##  <a name="Follow_Up"></a> Tâches de suivi  
 Les tâches suivantes sont nécessaires pour terminer la configuration de l'Agent pour envoyer des alertes et des notifications.  
  
-   [Alertes](../../ssms/agent/alerts.md)  
  
     Les alertes peuvent être configurées pour notifier à un opérateur une situation du système d'exploitation ou un événement de base de données particuliers.  
  
-   [Opérateurs](../../ssms/agent/operators.md)  
  
     Les opérateurs sont des alias pour les personnes ou les groupes qui peuvent recevoir une notification électronique  
  
  