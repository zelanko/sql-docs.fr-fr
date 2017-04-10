---
title: "T&#226;che de nettoyage d&#39;historique (Plan de maintenance) | Microsoft Docs"
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
  - "sql13.swb.maint.historycleanup.f1"
helpviewer_keywords: 
  - "Tâche de nettoyage d'historique (boîte de dialogue)"
ms.assetid: 66bb6c39-958c-4053-a27f-b1118d2567f5
caps.latest.revision: 21
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 21
---
# T&#226;che de nettoyage d&#39;historique (Plan de maintenance)
  La boîte de dialogue **Tâche de nettoyage d'historique** vous permet de supprimer les informations d'historique anciennes des tables de la base de données msdb. Cette tâche prend en charge la suppression de l'historique de sauvegarde et de restauration, l'historique des travaux de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et l'historique du plan de maintenance.  
  
 Cette instruction utilise les instructions **sp_purge_jobhistory** et **sp_delete_backuphistory**.  
  
## Liste des éléments de l'interface utilisateur  
 **Connexion**  
 Sélectionnez la connexion serveur à utiliser pour exécuter la tâche.  
  
 **Nouveau**  
 Crée une nouvelle connexion serveur à utiliser pour exécuter la tâche. La boîte de dialogue **Nouvelle connexion** est décrite ultérieurement dans cette rubrique.  
  
 **Sauvegarder et restaurer l'historique**  
 La conservation des enregistrements indiquant à quel moment des sauvegardes récentes ont été créées peut aider [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à créer un plan de récupération lorsque vous souhaitez restaurer une base de données. La période de rétention doit être au moins égale à la fréquence des sauvegardes complètes de base de données.  
  
 **Historique des travaux de SQL Server Agent**  
 Cet historique vous permet de résoudre les problèmes des travaux ayant échoué ou de déterminer la raison pour laquelle des actions se sont produites.  
  
 **Historique du plan de maintenance**  
 Cet historique vous permet de résoudre les problèmes des travaux de plan de maintenance ayant échoué ou de déterminer la raison pour laquelle des actions se sont produites.  
  
 **Supprimer les données d'historique antérieures à**  
 Permet de spécifier l'ancienneté des éléments à supprimer.  
  
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
 Permet de se connecter à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] SQL Server en utilisant l'authentification Microsoft Windows.  
  
 **Utiliser un nom d'utilisateur et un mot de passe spécifiques**  
 Permet de se connecter à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] SQL Server via l'authentification SQL Server. Cette option n'est pas disponible.  
  
 **Nom d'utilisateur**  
 Fournit le nom d'utilisateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à utiliser pour l'authentification. Cette option n'est pas disponible.  
  
 **Mot de passe**  
 Fournit un mot de passe à utiliser pour l'authentification. Cette option n'est pas disponible.  
  
## Voir aussi  
 [sp_purge_jobhistory &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-purge-jobhistory-transact-sql.md)   
 [sp_delete_backuphistory &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql.md)  
  
  