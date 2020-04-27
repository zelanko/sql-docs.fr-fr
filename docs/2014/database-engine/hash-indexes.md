---
title: Index de hachage | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: f4bdc9c1-7922-4fac-8183-d11ec58fec4e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 263fdcd4b09c4acc6c2bba4d67629f867d64c6b3
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62779483"
---
# <a name="hash-indexes"></a>Index de hachage
  Les index sont utilisés comme points d'entrée pour les tables mémoire optimisées. La lecture de lignes dans une table requiert un index pour localiser les données en mémoire.  
  
 Un index de hachage se compose d'une collection de compartiments organisés dans un tableau. Une fonction de hachage mappe les clés d'index aux compartiments correspondants dans l'index de hachage. L'illustration suivante montre trois clés d'index qui sont mappées à trois compartiments différents dans l'index de hachage. Dans l'illustration, le nom de fonction de hachage est f (x).  
  
 ![Clés d'index mappées à des compartiments.](../../2014/database-engine/media/hekaton-tables-2.gif "Clés d'index mappées à des compartiments.")  
  
 La fonction de hachage utilisée pour les index de hachage présente les caractéristiques suivantes :  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] possède une fonction de hachage utilisée pour tous les index de hachage.  
  
-   La fonction de hachage est déterministe. La même clé d'index est toujours mappée vers le même compartiment dans l'index de hachage.  
  
-   Plusieurs clés d'index peuvent être mappées au même compartiment de hachage.  
  
-   La fonction de hachage est équilibrée, ce qui signifie que la distribution des valeurs de clé d'index sur les compartiments de hachage suit généralement une distribution Poisson.  
  
     La distribution Poisson n'est pas une distribution uniforme. Les valeurs de clé d'index ne sont pas distribuées uniformément dans les compartiments de hachage. Par exemple, une distribution Poisson de *n* clés distinctes sur *n* compartiments de hachage résulte dans environ un tiers de compartiments vides, un tiers de compartiments contenant une clé d'index, et le dernier tiers contenant deux clés d'index. Un petit nombre de compartiments contiendra plus de deux clés.  
  
 Si deux clés d'index sont mappées au même compartiment de hachage, il existe une collision de hachage. Un grand nombre de collisions de hachage peut avoir un impact sur les performances des opérations de lecture.  
  
 La structure de l'index de hachage en mémoire comporte un tableau de pointeurs de mémoire. Chaque compartiment mappe à un décalage dans ce tableau. Chaque compartiment dans le tableau pointe sur la première ligne dans ce compartiment de hachage. Chaque ligne dans le compartiment pointe sur la ligne suivante, ce qui résulte dans une chaîne de lignes pour chaque compartiment de hachage, comme illustré dans la figure ci-dessous.  
  
 ![Structure de l'index de hachage en mémoire.](../../2014/database-engine/media/hekaton-tables-3.gif "Structure de l'index de hachage en mémoire.")  
  
 L'illustration comprend trois compartiments avec des lignes. Le deuxième compartiment supérieur contient les trois lignes rouges. La quatrième compartiment contient une seule ligne bleue. Le compartiment inférieur contient les deux lignes vertes. Il peut s'agir de versions différentes de la même ligne.  
  
 Pour plus d'informations sur les index des tables mémoire optimisées, consultez [Guidelines for Using Indexes on Memory-Optimized Tables](../relational-databases/in-memory-oltp/memory-optimized-tables.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Index sur les tables optimisées en mémoire](../../2014/database-engine/indexes-on-memory-optimized-tables.md)  
  
  
