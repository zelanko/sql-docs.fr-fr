---
title: Requêtes de bases de données croisées | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a0305f5b-91bd-4d18-a2fc-ec235b062fd3
caps.latest.revision: 6
author: stevestein
ms.author: sstein
manager: jhubbard
ms.openlocfilehash: dd86d3e1c67cb1a87690919a6d9336a434d14954
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36042716"
---
# <a name="cross-database-queries"></a>Requêtes de bases de données croisées
  Dans [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], les tables mémoire optimisées ne prennent pas en charge les transactions entre bases de données. Vous ne pouvez pas accéder à une autre base de données à partir de la même transaction ou de la même requête qui accède également à une table mémoire optimisée. Vous ne pouvez pas facilement copier les données d'une table d'une base de données, à une table mémoire optimisée d'une autre base de données.  
  
 Les variables de table ne sont pas transactionnelles. Par conséquent, les variables des tables mémoire optimisées peuvent être utilisées dans des requêtes de bases de données croisées, et peuvent donc faciliter le déplacement des données d'une base de données dans des tables mémoire optimisées dans une autre base de données. Vous pouvez utiliser deux transactions. Dans la première transaction, insérez les données de la table distante dans la variable. Dans la seconde transaction, insérez les données dans la table mémoire optimisée locale depuis la variable.  
  
 Par exemple, pour copier la ligne de la table t1 dans la base de données db1 vers la table t2 dans db2, à l’aide de la variable @v1 de type dbo.tt1, vous pouvez utiliser quelque chose comme :  
  
```tsql  
USE db2   
GO   
DECLARE @v1 dbo.tt1   
INSERT @v1 SELECT * FROM db1.dbo.t1   
INSERT dbo.t2 SELECT * FROM @v1   
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Migration vers OLTP en mémoire](migrating-to-in-memory-oltp.md)  
  
  