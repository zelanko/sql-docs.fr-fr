---
title: "Probl&#232;mes li&#233;s aux articles | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.newpubwizard.articleissues.f1"
ms.assetid: bde57da2-dd47-412f-9df7-9224968b2448
caps.latest.revision: 23
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 23
---
# Probl&#232;mes li&#233;s aux articles
  Le **problèmes d’Article** page répertorie les conditions qui ont été trouvées pour les articles et les modifications nécessaires en raison de ces conditions. Le tableau suivant répertorie les problèmes potentiels et les actions nécessaires pour vous assurer que la réplication et les applications existantes fonctionnent correctement.  
  
|Problème d'article|Détails|Action requise|  
|-------------------|-------------|---------------------|  
|Les colonnes Uniqueidentifier seront ajoutées aux tables|La réplication nécessite une colonne de type de données **uniqueidentifier** pour tous les articles dans une publication de fusion ou une publication transactionnelle qui autorise les abonnements mis à jour.|La réplication ajoute automatiquement une colonne de type de données **uniqueidentifier** aux tables publiées qui n’en avez pas lors de la première capture instantanée. Assurez-vous que les instructions INSERT et UPDATE appelant ces tables utilisent bien des listes de colonnes. Vérifiez également que l'espace disque est suffisant pour autoriser l'ajout de cette colonne.|  
|Les colonnes IDENTITY nécessitent l'option NOT FOR REPLICATION.|La réplication nécessite que toutes les colonnes IDENTITY utilisent l'option NOT FOR REPLICATION. Si une colonne IDENTITY publiée n'utilise pas cette option, les commandes INSERT risquent de ne pas se répliquer correctement.|S’applique aux publications créées sur des serveurs de publication exécutant [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] et versions antérieures. Vous devez indiquer la propriété NOT FOR REPLICATION pour toutes les colonnes IDENTITY.|  
|La propriété IDENTITY n'est pas transférée aux abonnés.|Cette publication ne permet pas de mise à jour sur les Abonnés. Lorsque les colonnes IDENTITY sont transmises à l'Abonné, la propriété IDENTITY ne l'est cependant pas. Par exemple, une colonne définie en tant que INT IDENTITY sur le serveur de publication est définie en tant que INT sur l'Abonné.|S'applique aux publications créées sur des serveurs de publication exécutant [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] ou antérieur. Aucune action n'est nécessaire.|  
|Des tables référencées par des vues sont nécessaires.|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] requiert que toutes les tables référencées par des vues et des vues indexées publiées soient disponibles sur l’abonné. Si les tables référencées ne sont pas publiées en tant qu'articles dans cette publication, elles doivent être créées manuellement sur l'abonné.|Utilisez le **retour** bouton pour accéder à la **Articles** page. Ajoutez ensuite tout objet nécessaire.|  
|Des objets référencés par des procédures stockées sont nécessaires.|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] requiert que tous les objets référencés par des procédures stockées publiées, telles que des tables et des fonctions définies par l’utilisateur, soient disponibles sur l’abonné. Si les objets référencés ne sont pas publiés en tant qu'articles dans cette publication, ils doivent être créés manuellement sur l'abonné.|Utilisez le **retour** bouton pour accéder à la **Articles** page. Ajoutez ensuite tout objet nécessaire.|  
  
## Voir aussi  
 [Publier des données et des objets de base de données](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)  
  
  