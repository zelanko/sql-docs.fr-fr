---
title: Spécifier l’ordre de traitement des Articles de Table de fusion (programmation Transact-SQL de la réplication) | Microsoft Docs
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
- articles [SQL Server replication], processing order
- merge replication [SQL Server replication], article processing order
ms.assetid: 9fe576a2-f5fb-4fdf-bd7d-cb322021b669
caps.latest.revision: 32
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c2327f90e3ff8b8ad33d7766fec48596d4461611
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37299935"
---
# <a name="specify-the-processing-order-of-merge-table-articles-replication-transact-sql-programming"></a>Spécifier l'ordre de traitement d'articles de table de fusion (programmation Transact-SQL de la réplication)
  La réplication de fusion vous permet de spécifier l'ordre dans lequel les articles sont traités par l'Agent de fusion pendant le processus de synchronisation. Vous pouvez attribuer par programme un ordre à chaque article lors de la création de l'article à l'aide des procédures stockées de réplication. Les articles sont traités à partir de la valeur la plus faible vers la valeur la plus élevée. Si deux articles ont la même valeur, ils sont traités simultanément. Pour plus d’informations, consultez [Spécifier l’ordre de traitement d’articles de fusion](../merge/specify-the-processing-order-of-merge-articles.md).  
  
### <a name="to-specify-the-processing-order-for-a-new-merge-article"></a>Pour spécifier l'ordre de traitement d'un nouvel article de fusion  
  
1.  Dans la base de données de publication sur le serveur de publication, exécutez [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql). Spécifiez une valeur entière qui représente l'ordre de traitement de l'article pour **@processing_order**. Pour plus d'informations, voir [Define an Article](define-an-article.md).  
  
    > [!NOTE]  
    >  Lorsque vous créez des articles ordonnés, vous devez laisser des intervalles entre les valeurs d'ordre des articles. Cela permet de définir facilement de nouvelles valeurs dans le futur. Par exemple, si vous avez trois articles pour lesquels vous devez spécifier un ordre de traitement fixe, affectez à **@processing_order** les valeurs 10, 20 et 30 plutôt que 1, 2 et 3, respectivement.  
  
### <a name="to-change-the-processing-order-of-a-merge-article"></a>Pour modifier l'ordre de traitement d'un article de fusion  
  
1.  Pour déterminer l’ordre de traitement d’un article, exécutez [sp_helpmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql) et notez la valeur de **processing_order** dans le jeu de résultats.  
  
2.  Dans la base de données de publication sur le serveur de publication, exécutez [sp_changemergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql). Spécifiez une valeur de **processing_order** pour **@property** et une valeur entière qui représente l'ordre de traitement pour **@value**.  
  
## <a name="see-also"></a>Voir aussi  
 [Spécifier l’ordre de traitement d’articles de fusion](../merge/specify-the-processing-order-of-merge-articles.md)  
  
  
