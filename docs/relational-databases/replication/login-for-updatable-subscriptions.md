---
title: "Nom de connexion pour les abonnements pouvant &#234;tre mis &#224; jour | Microsoft Docs"
ms.custom: ""
ms.date: "08/25/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.newsubwizard.updatablesubscriptionslogin.f1"
ms.assetid: 301ea227-0455-40ba-9009-d38f8676b325
caps.latest.revision: 18
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 18
---
# Nom de connexion pour les abonnements pouvant &#234;tre mis &#224; jour
  Pour la mise à jour immédiate, si vous avez sélectionné **répliquer** sur la **à abonnements** page de cet Assistant, vous devez spécifier un compte avec l’abonné sous lequel sont effectuées les connexions au serveur de publication. 
  
 Les connexions sont utilisées par les déclencheurs qui se déclenchent sur l’abonné et de propagent les modifications vers le serveur de publication. Ce compte est nécessaire même si vous avez sélectionné **modifications en file d’attente et valider dès que possible** sur la **à abonnements** page. L’Assistant Nouvel abonnement par défaut configure la mise à jour en file d’attente avec la possibilité de passer à une mise à jour immédiate si nécessaire.  
  
> **IMPORTANT** Le compte spécifié pour la connexion ne doit être autorisé à insérer, mettre à jour et supprimer des données sur les vues que la réplication crée la base de données de publication. Il ne doit pas bénéficier d’autorisations supplémentaires. Accorder des autorisations sur les vues dans la base de données de publication sous la forme **syncobj_***\< HexadecimalNumber>* pour le compte que vous avez configuré sur chaque abonné.  
  
 Trois options sont possibles pour le type de connexion :  
  
-   Un serveur lié ou distant que vous avez déjà défini.  
  
-   Un serveur lié créé par la réplication. La connexion se fait à l'aide des informations d'identification spécifiées dans cet Assistant.  
  
-   Un serveur lié créé par la réplication. La connexion se fait à l'aide des informations d'identification de l'utilisateur qui apporte la modification pour l'abonné.  
  
 Vous pouvez spécifier les deux premières options dans cet Assistant. La dernière option peut uniquement être spécifiée à l’aide de [sp_link_publication &#40 ; Transact-SQL &#41 ;](../../relational-databases/system-stored-procedures/sp-link-publication-transact-sql.md); Spécifiez la valeur **1** pour le paramètre **@security_mode**.  
  
## Options  
 **Créer un serveur lié qui se connecte par une connexion d'authentification SQL Server :**  
 La réplication crée un serveur lié à l’aide des informations d’identification spécifiées dans le **connexion** et **mot de passe** champs.  
  
 **Connexion**  
 Entrez un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion qui possède les autorisations décrites dans cette rubrique.  
  
 **Mot de passe**  
 Entrez un mot de passe fort pour la connexion spécifiée dans **connexion**.  
    
 **Utiliser un serveur lié ou un serveur distant que vous avez déjà défini.**  
 Cette option nécessite un serveur lié ou distant déjà défini. Pour plus d’informations, consultez la page [des serveurs liés &#40 ; le moteur de base de données &#41 ;](../../relational-databases/linked-servers/linked-servers-database-engine.md) et [serveurs distants](../../database-engine/configure-windows/remote-servers.md). Assurez-vous que la connexion utilisée pour le serveur lié ou distant est associée un mot de passe fort et possède uniquement les autorisations décrites dans cette rubrique.  
  
## Voir aussi  
 [Créer un abonnement pouvant être mis à jour pour une publication transactionnelle](https://msdn.microsoft.com/library/ms152769.aspx)   
 [Afficher et modifier les paramètres de sécurité de la réplication](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)   
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [S'abonner à des publications](../../relational-databases/replication/subscribe-to-publications.md)  
  
  