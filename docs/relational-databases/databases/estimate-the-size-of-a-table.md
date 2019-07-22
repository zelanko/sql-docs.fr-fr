---
title: Estimer la taille d’une table | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
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
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: cb75aede7c32d8217bcae71b55997d3700a04a7b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67934473"
---
# <a name="estimate-the-size-of-a-table"></a>Estimer la taille d'une table
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Vous pouvez procéder de la manière suivante pour estimer l'espace nécessaire au stockage des données dans une table :  
  
1.  Calculez l’espace nécessaire pour le segment de mémoire ou index cluster en suivant les instructions fournies dans [Estimer la taille d’un segment de mémoire](../../relational-databases/databases/estimate-the-size-of-a-heap.md) ou [Estimer la taille d’un index cluster](../../relational-databases/databases/estimate-the-size-of-a-clustered-index.md).  
  
2.  Pour chaque index non-cluster, calculez l’espace nécessaire en suivant les instructions fournies dans [Estimer la taille d’un index non-cluster](../../relational-databases/databases/estimate-the-size-of-a-nonclustered-index.md).  
  
3.  Additionnez les valeurs obtenues aux étapes 1 et 2.  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

## <a name="see-also"></a>Voir aussi  
 [Estimer la taille d'une base de données](../../relational-databases/databases/estimate-the-size-of-a-database.md)   
 [Estimer la taille d’un segment de mémoire](../../relational-databases/databases/estimate-the-size-of-a-heap.md)   
 [Estimer la taille d’un index cluster](../../relational-databases/databases/estimate-the-size-of-a-clustered-index.md)   
 [Estimer la taille d’un index non-cluster](../../relational-databases/databases/estimate-the-size-of-a-nonclustered-index.md)  
  
  
