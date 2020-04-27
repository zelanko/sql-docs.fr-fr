---
title: Estimer la taille d’une table | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 403e0af44fc1db7efaf674d02ed0e3b94e81a5b6
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62916873"
---
# <a name="estimate-the-size-of-a-table"></a>Estimer la taille d'une table
  Vous pouvez procéder de la manière suivante pour estimer l'espace nécessaire au stockage des données dans une table :  
  
1.  Calculez l’espace nécessaire pour le segment de mémoire ou index cluster en suivant les instructions fournies dans [Estimer la taille d’un segment de mémoire](estimate-the-size-of-a-heap.md) ou [Estimer la taille d’un index cluster](estimate-the-size-of-a-clustered-index.md).  
  
2.  Pour chaque index non-cluster, calculez l’espace nécessaire en suivant les instructions fournies dans [Estimer la taille d’un index non-cluster](estimate-the-size-of-a-nonclustered-index.md).  
  
3.  Additionnez les valeurs obtenues aux étapes 1 et 2.  
  
## <a name="see-also"></a>Voir aussi  
 [Estimer la taille d'une base de données](estimate-the-size-of-a-database.md)   
 [Estimer la taille d’un segment de mémoire](estimate-the-size-of-a-heap.md)   
 [Estimer la taille d’un index cluster](estimate-the-size-of-a-clustered-index.md)   
 [Estimer la taille d'un index non-cluster](estimate-the-size-of-a-nonclustered-index.md)  
  
  
