---
title: "Valeurs HOST_NAME | Microsoft Docs"
ms.custom: ""
ms.date: "03/06/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.newsubwizard.hostnamevalue.f1"
ms.assetid: 21548f08-2910-4a55-baac-b911ba9afaf1
caps.latest.revision: 20
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 20
---
# Valeurs HOST_NAME
  Les publications de fusion associées à des filtres paramétrés utilisent la fonction SUSER_SNAME() et/ou HOST_NAME() pour filtrer les données. La fonction concernée est spécifiée dans l'Assistant Nouvelle publication ou la boîte de dialogue **Propriétés de la publication** .  
  
 Par défaut, la fonction HOST_NAME() retourne le nom de l'ordinateur qui se connecte au serveur de publication. Lors de l'utilisation de filtres paramétrés, il est fréquent de remplacer cette valeur par une autre dans cette page de l'Assistant. La fonction HOST_NAME() retourne alors la valeur spécifiée à la place du nom de l'ordinateur. Pour plus d’informations, consultez la section « Substitution de la valeur de HOST_NAME() » de [filtres de lignes paramétrable](../../relational-databases/replication/merge/parameterized-row-filters.md).  
  
> [!NOTE]  
>  Si vous remplacez la valeur de HOST_NAME(), tous les appels de la fonction HOST_NAME() retourneront la valeur que vous avez spécifiée. Assurez-vous que les autres applications ne dépendent pas de la fonction HOST_NAME() avec retour du nom de l'ordinateur.  
  
## Options  
 **Propriétés de l'abonnement**  
 Entrez une valeur pour chaque abonné dans la **valeur de HOST_NAME** colonne ou acceptez la valeur par défaut, qui est le nom de l’ordinateur de l’abonné.  
  
## Voir aussi  
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [View and Modify Pull Subscription Properties](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)   
 [View and Modify Push Subscription Properties](../../relational-databases/replication/view-and-modify-push-subscription-properties.md)   
 [HOST_NAME & #40 ; Transact-SQL & #41 ;](../../t-sql/functions/host-name-transact-sql.md)   
 [S'abonner à des publications](../../relational-databases/replication/subscribe-to-publications.md)  
  
  