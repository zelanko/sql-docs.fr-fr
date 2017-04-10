---
title: "Indiquer que les suppressions ne doivent pas &#234;tre suivies pour les articles de fusion (programmation Transact-SQL de la r&#233;plication) | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "suivi des suppressions conditionnelles [réplication SQL Server]"
  - "réplication de fusion [réplication SQL Server], suivi des suppressions conditionnelles"
ms.assetid: 0fe330ca-5fb5-422e-ad6f-92fb5d6a3b6c
caps.latest.revision: 34
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Indiquer que les suppressions ne doivent pas &#234;tre suivies pour les articles de fusion (programmation Transact-SQL de la r&#233;plication)
    
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
 Par défaut, la réplication de fusion synchronise les commandes DELETE entre le serveur de publication et l'Abonné. La réplication de fusion vous permet de conserver des lignes qui ont été supprimées de la publication dans la base de données d'abonnement, et vice versa. Vous pouvez spécifier par programme que les commandes DELETE doivent être ignorées lors de la création d'un article ou vous pouvez activer cette fonctionnalité ultérieurement à l'aide de procédures stockées de réplication.  
  
> [!IMPORTANT]  
>  L'activation de cette fonctionnalité conduit à une non-convergence ; autrement dit, les données présentes au niveau de l'Abonné ne reflèteront pas correctement les données présentes au niveau du serveur de publication. Vous devez implémenter votre propre mécanisme de manière à supprimer manuellement les lignes supprimées.  
  
### Pour spécifier que les suppressions doivent être ignorées pour un nouvel article de fusion  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_addmergearticle & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md). Spécifiez la valeur **false** pour **@delete_tracking**. Pour plus d'informations, voir [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
    > [!NOTE]  
    >  Si la table source d’un article est déjà publiée dans une autre publication, la valeur de **delete_tracking** doivent être identiques pour les deux articles.  
  
### Pour spécifier que les suppressions doivent être ignorées pour un article de fusion existant  
  
1.  Pour déterminer si la compensation d’erreur est activée pour un article, exécutez [sp_helpmergearticle & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md) Notez la valeur de **delete_tracking** dans le résultat défini. Si cette valeur est **0**, suppressions sont déjà ignorées.  
  
2.  Si la valeur de l’étape 1 est **1**, exécutez [sp_changemergearticle & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md) sur la base de données de publication de l’éditeur. Spécifiez la valeur **delete_tracking** pour **@property**, et la valeur **false** pour **@value**.  
  
    > [!NOTE]  
    >  Si la table source d’un article est déjà publiée dans une autre publication, la valeur de **delete_tracking** doivent être identiques pour les deux articles.  
  
## Voir aussi  
 [Optimiser les performances de la réplication de fusion avec le suivi conditionnel des suppressions](../../../relational-databases/replication/merge/optimize-merge-replication-performance-with-conditional-delete-tracking.md)  
  
  