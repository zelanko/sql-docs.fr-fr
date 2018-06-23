---
title: Estimer la taille d’une base de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- space allocation [SQL Server], database size
- calculating database size
- increasing database size
- database size [SQL Server], estimating
- predicting database size
- size [SQL Server], databases
- estimating database size
- designing databases [SQL Server], estimating size
ms.assetid: 5b240161-eba4-44b0-946c-61a8fc00fc8c
caps.latest.revision: 19
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 12013bd903a6ce0343e67ab500b7c3c2356f5e55
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36151918"
---
# <a name="estimate-the-size-of-a-database"></a>Estimer la taille d'une base de données
  Lorsque vous concevez une base de données, il peut être utile d'estimer quelle taille elle aura une fois remplie. Cette estimation peut vous aider à déterminer la configuration matérielle dont vous aurez besoin pour :  
  
-   atteindre le niveau de performances requis par vos applications ;  
  
-   garantir la quantité d'espace disque physique nécessaire pour stocker les données et les index.  
  
 L'estimation de la taille de la base de données peut aussi vous aider à déterminer si des améliorations de conception s'imposent. Par exemple, vous pouvez arriver à la conclusion que la base de données risque d'atteindre une taille trop importante pour que son implémentation s'effectue dans de bonnes conditions dans votre organisation et qu'il faut aller dans le sens d'une plus grande normalisation. À l'inverse, la taille estimée peut être plus petite que prévu, ce qui vous donne la possibilité de dénormaliser la base de données pour améliorer les performances des requêtes.  
  
 Pour estimer la taille d'une base de données, faites une estimation pour chaque table, puis additionnez les valeurs trouvées. La taille d'une table dépend de la présence ou non d'index et, le cas échéant, de leur type.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Estimer la taille d'une table](estimate-the-size-of-a-table.md)|Définit les étapes et les calculs nécessaires pour estimer l'espace requis pour le stockage des données dans une table et les index associés.|  
|[Estimer la taille d’un segment de mémoire](estimate-the-size-of-a-heap.md)|Définit les étapes et les calculs nécessaires pour estimer l'espace requis pour le stockage des données dans un segment. Un segment est une table qui n'a pas d'index cluster.|  
|[Estimer la taille d'un index cluster](estimate-the-size-of-a-clustered-index.md)|Définit les étapes et les calculs nécessaires pour estimer l'espace requis pour le stockage des données dans un index cluster.|  
|[Estimer la taille d'un index non-cluster](estimate-the-size-of-a-nonclustered-index.md)|Définit les étapes et les calculs nécessaires pour estimer l'espace requis pour le stockage des données dans un index non-cluster.|  
  
  