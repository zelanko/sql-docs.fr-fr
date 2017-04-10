---
title: "T&#226;che Notifier l&#39;op&#233;rateur (Plan de maintenance) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.swb.maint.notifyoperator.f1"
helpviewer_keywords: 
  - "Tâche Notifier l'opérateur (boîte de dialogue)"
ms.assetid: 39c0797c-ad2b-4591-85c9-a23a7f902895
caps.latest.revision: 32
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 32
---
# T&#226;che Notifier l&#39;op&#233;rateur (Plan de maintenance)
  Utilisez la boîte de dialogue **Tâche Notifier l’opérateur** pour ajouter une notification automatique à ce plan de maintenance. Pour utiliser cette tâche, la messagerie de base de données doit être activée et correctement configurée avec MSDB en tant que base de données hôte de messagerie, et vous devez disposer d’un opérateur [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent avec une adresse de messagerie valide.  
  
 Cette tâche utilise la procédure stockée sp_notify_operator.  
  
## Options  
 **Connexion**  
 Sélectionnez la connexion serveur à utiliser pour exécuter la tâche.  
  
 **Nouveau**  
 Crée une nouvelle connexion serveur à utiliser pour exécuter la tâche. La boîte de dialogue **Nouvelle connexion** est décrite ci-dessous.  
  
 **Opérateurs à notifier**  
 Spécifiez le destinataire du courrier électronique.  
  
 **Objet du message de notification**  
 Spécifiez le texte à inclure dans la ligne Objet du message de notification.  
  
 **Corps du message de notification**  
 Spécifiez le texte à inclure dans le corps du message de notification.  
  
 **Vue T-SQL**  
 Affiche les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] exécutées sur le serveur pour cette tâche, selon les options sélectionnées.  
  
> [!NOTE]  
>  Si le nombre d'objets impliqués est élevé, l'affichage des instructions peut prendre un temps considérable.  
  
## Boîte de dialogue Nouvelle connexion  
 **Nom de la connexion**  
 Entrez un nom pour la nouvelle connexion.  
  
 **Sélectionnez ou entrez un nom de serveur.**  
 Sélectionnez un serveur auquel établir la connexion pour exécuter la tâche.  
  
 **Actualiser**  
 Actualise la liste des serveurs disponibles.  
  
 **Entrez des informations pour vous connecter au serveur**  
 Spécifiez le mode d'authentification sur le serveur.  
  
 **Utiliser la sécurité intégrée à Windows NT**  
 Permet de se connecter à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide de l’authentification [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.  
  
 **Utiliser un nom d'utilisateur et un mot de passe spécifiques**  
 Permet de se connecter à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide de l’authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette option n'est pas disponible.  
  
 **Nom d'utilisateur**  
 Fournit le nom d'utilisateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à utiliser pour l'authentification. Cette option n'est pas disponible.  
  
 **Mot de passe**  
 Fournit un mot de passe à utiliser pour l'authentification. Cette option n'est pas disponible.  
  
## Voir aussi  
 [Messagerie de base de données](../../relational-databases/database-mail/database-mail.md)   
 [sp_notify_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-notify-operator-transact-sql.md)  
  
  