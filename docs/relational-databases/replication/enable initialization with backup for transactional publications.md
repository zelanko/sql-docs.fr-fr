---
title: "activer l&#39;initialisation avec une sauvegarde pour les publications transactionnelles (SQL Server Management Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "initialisation manuelle des abonnements [réplication SQL Server]"
  - "abonnements [réplication SQL Server], initialisation"
  - "initialisation d’abonnements [réplication SQL Server], sans instantanés"
  - "réplication transactionnelle, sauvegarde et restauration"
  - "sauvegardes [réplication SQL Server], réplication transactionnelle"
ms.assetid: 9df00514-aa9d-4ac6-9766-d226c9958175
caps.latest.revision: 30
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# activer l&#39;initialisation avec une sauvegarde pour les publications transactionnelles (SQL Server Management Studio)
  Pour initialiser un abonnement à une publication transactionnelle à partir d'une sauvegarde, vous devez configurer la publication de telle sorte qu'elle autorise une initialisation à partir d'une sauvegarde puis spécifier les informations de sauvegarde lors de la création de l'abonnement :  
  
-   Activer la publication sur le **Options d’abonnement** page de le **Propriétés de la Publication - \< Publication>** boîte de dialogue. Pour plus d'informations sur l'accès à cette boîte de dialogue, consultez [View and Modify Publication Properties](../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
-   Spécifiez les informations de sauvegarde avec la procédure stockée [sp_addsubscription & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Pour plus d’informations sur les paramètres requis par **sp_addsubscription**, consultez [initialiser un abonnement transactionnel à partir d’une sauvegarde & #40 ; Programmation de Transact-SQL de réplication & #41 ;](../../relational-databases/replication/initialize a transactional subscription from a backup.md).  
  
### Pour activer l'initialisation avec une sauvegarde  
  
1.  Sur le **Options d’abonnement** page de le **Propriétés de la Publication - \< Publication>** boîte de dialogue, sélectionnez la valeur **True** pour la **autorise l’initialisation à partir de fichiers de sauvegarde** option.  
  
## Voir aussi  
 [Initialiser un abonnement transactionnel sans instantané](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md)  
  
  