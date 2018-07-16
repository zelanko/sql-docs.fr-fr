---
title: Spécifiez que les suppressions ne doivent pas être suivies pour les Articles de fusion (programmation Transact-SQL de la réplication) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- conditional delete tracking [SQL Server replication]
- merge replication [SQL Server replication], conditional delete tracking
ms.assetid: 0fe330ca-5fb5-422e-ad6f-92fb5d6a3b6c
caps.latest.revision: 34
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 65a4ad119dc985c67eeea811f2102f387b7a5419
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37248509"
---
# <a name="specify-that-deletes-should-not-be-tracked-for-merge-articles-replication-transact-sql-programming"></a>Indiquer que les suppressions ne doivent pas être suivies pour les articles de fusion (programmation Transact-SQL de la réplication)
    
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
 Par défaut, la réplication de fusion synchronise les commandes DELETE entre le serveur de publication et l'Abonné. La réplication de fusion vous permet de conserver des lignes qui ont été supprimées de la publication dans la base de données d'abonnement, et vice versa. Vous pouvez spécifier par programme que les commandes DELETE doivent être ignorées lors de la création d'un article ou vous pouvez activer cette fonctionnalité ultérieurement à l'aide de procédures stockées de réplication.  
  
> [!IMPORTANT]  
>  L'activation de cette fonctionnalité conduit à une non-convergence ; autrement dit, les données présentes au niveau de l'Abonné ne reflèteront pas correctement les données présentes au niveau du serveur de publication. Vous devez implémenter votre propre mécanisme de manière à supprimer manuellement les lignes supprimées.  
  
### <a name="to-specify-that-deletes-be-ignored-for-a-new-merge-article"></a>Pour spécifier que les suppressions doivent être ignorées pour un nouvel article de fusion  
  
1.  Dans la base de données de publication sur le serveur de publication, exécutez [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql). Spécifiez la valeur `false` pour **@delete_tracking**. Pour plus d'informations, voir [Define an Article](define-an-article.md).  
  
    > [!NOTE]  
    >  Si la table source d'un article est déjà publiée dans une autre publication, la valeur de **delete_tracking** doit être la même pour les deux articles.  
  
### <a name="to-specify-that-deletes-be-ignored-for-an-existing-merge-article"></a>Pour spécifier que les suppressions doivent être ignorées pour un article de fusion existant  
  
1.  Pour déterminer si la compensation d’erreur est activée pour un article, exécutez [sp_helpmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql) et notez la valeur de **delete_tracking** dans le jeu de résultats. Si cette valeur est **0**, les suppressions sont déjà ignorées.  
  
2.  Si la valeur à l’étape 1 est **1**, exécutez [sp_changemergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql) sur la base de données de publication au niveau du serveur de publication. Spécifiez la valeur **delete_tracking** pour **@property**et la valeur `false` pour **@value**.  
  
    > [!NOTE]  
    >  Si la table source d'un article est déjà publiée dans une autre publication, la valeur de **delete_tracking** doit être la même pour les deux articles.  
  
## <a name="see-also"></a>Voir aussi  
 [Optimiser les performances de la réplication de fusion avec le suivi conditionnel des suppressions](../merge/optimize-merge-replication-performance-with-conditional-delete-tracking.md)  
  
  
