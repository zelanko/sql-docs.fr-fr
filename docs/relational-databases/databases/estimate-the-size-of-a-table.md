---
title: "Estimer la taille d’une table | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pages [SQL Server], space
- space [SQL Server], tables
- row size [SQL Server]
- size [SQL Server], tables
- column size [SQL Server]
- predicting table size [SQL Server]
- table size [SQL Server]
- estimating table size
- clustered indexes, table size
- disk space [SQL Server], tables
- space allocation [SQL Server], table size
- designing databases [SQL Server], estimating size
- reserved free rows per page [SQL Server]
- calculating table size
ms.assetid: 15c17c92-616f-402e-894b-907a296efe5f
caps.latest.revision: 30
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 740800db335b524298c39a3ab9f225e18d785c54
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="estimate-the-size-of-a-table"></a>Estimer la taille d'une table
  Vous pouvez procéder de la manière suivante pour estimer l'espace nécessaire au stockage des données dans une table :  
  
1.  Calculez l’espace nécessaire pour le segment de mémoire ou index cluster en suivant les instructions fournies dans [Estimer la taille d’un segment de mémoire](../../relational-databases/databases/estimate-the-size-of-a-heap.md) ou [Estimer la taille d’un index cluster](../../relational-databases/databases/estimate-the-size-of-a-clustered-index.md).  
  
2.  Pour chaque index non-cluster, calculez l’espace nécessaire en suivant les instructions fournies dans [Estimer la taille d’un index non-cluster](../../relational-databases/databases/estimate-the-size-of-a-nonclustered-index.md).  
  
3.  Additionnez les valeurs obtenues aux étapes 1 et 2.  
  
## <a name="see-also"></a>Voir aussi  
 [Estimer la taille d'une base de données](../../relational-databases/databases/estimate-the-size-of-a-database.md)   
 [Estimer la taille d’un segment de mémoire](../../relational-databases/databases/estimate-the-size-of-a-heap.md)   
 [Estimer la taille d’un index cluster](../../relational-databases/databases/estimate-the-size-of-a-clustered-index.md)   
 [Estimer la taille d’un index non-cluster](../../relational-databases/databases/estimate-the-size-of-a-nonclustered-index.md)  
  
  
