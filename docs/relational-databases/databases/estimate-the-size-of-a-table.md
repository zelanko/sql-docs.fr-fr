---
title: "Estimer la taille d&#39;une table | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pages [SQL Server], espace"
  - "espace [SQL Server], tables"
  - "taille de ligne [SQL Server]"
  - "taille [SQL Server], tables"
  - "taille de colonne [SQL Server]"
  - "évaluation de la taille des tables [SQL Server]"
  - "taille de table [SQL Server]"
  - "estimation de la taille de table"
  - "index cluster, taille de la table"
  - "espace disque [SQL Server], tables"
  - "allocation de l’espace [SQL Server], taille de la table"
  - "conception des bases de données [SQL Server], estimation de la taille"
  - "lignes libres réservées par page [SQL Server]"
  - "calcul de la taille de table"
ms.assetid: 15c17c92-616f-402e-894b-907a296efe5f
caps.latest.revision: 30
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 30
---
# Estimer la taille d&#39;une table
  Vous pouvez procéder de la manière suivante pour estimer l'espace nécessaire au stockage des données dans une table :  
  
1.  Calculez l’espace nécessaire pour le segment de mémoire ou index cluster en suivant les instructions fournies dans [Estimer la taille d’un segment de mémoire](../../relational-databases/databases/estimate-the-size-of-a-heap.md) ou [Estimer la taille d’un index cluster](../../relational-databases/databases/estimate-the-size-of-a-clustered-index.md).  
  
2.  Pour chaque index non-cluster, calculez l’espace nécessaire en suivant les instructions fournies dans [Estimer la taille d’un index non-cluster](../../relational-databases/databases/estimate-the-size-of-a-nonclustered-index.md).  
  
3.  Additionnez les valeurs obtenues aux étapes 1 et 2.  
  
## Voir aussi  
 [Estimer la taille d'une base de données](../../relational-databases/databases/estimate-the-size-of-a-database.md)   
 [Estimer la taille d'un segment de mémoire](../../relational-databases/databases/estimate-the-size-of-a-heap.md)   
 [Estimer la taille d'un index cluster](../../relational-databases/databases/estimate-the-size-of-a-clustered-index.md)   
 [Estimer la taille d'un index non-cluster](../../relational-databases/databases/estimate-the-size-of-a-nonclustered-index.md)  
  
  