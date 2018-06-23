---
title: Alias de colonne dans la clause ORDER BY ne peut pas être précédées d’alias de table | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- aliases [SQL Server], columns
ms.assetid: fee7328f-6e8d-4005-930b-56fb6f17e0b2
caps.latest.revision: 20
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 18c65604efb2d1b0ff93d09b8d03f7ee6cb213cd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36044189"
---
# <a name="column-aliases-in-order-by-clause-cannot-be-prefixed-by-table-alias"></a>Les alias de colonne dans la clause ORDER BY ne peuvent pas avoir un alias de table pour préfixe
  Dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ou version ultérieure, les alias de colonne dans la clause ORDER BY ne peuvent pas avoir l'alias de table pour préfixe.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Par exemple, la requête suivante s'exécute dans [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], mais retourne une erreur dans [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
```  
USE AdventureWorks2012;  
GO  
SELECT FirstName AS f, LastName AS l  
FROM Person.Contact p  
ORDER BY p.l  
```  
  
 Le [!INCLUDE[ssDEversion10](../../includes/ssdeversion10-md.md)] ne fait pas correspondre `p.l` dans la clause `ORDER BY` à une colonne valide dans la table.  
  
### <a name="exception"></a>Exception  
 Si l'alias de colonne préfixé qui est spécifié dans la clause ORDER BY est un nom de colonne valide dans la table spécifiée, la requête s'exécute sans erreur ; dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], la sémantique de l'instruction peut être différente. Par exemple, l'alias de colonne (`id`) spécifié dans l'instruction suivante est un nom de colonne valide dans la table `sysobjects`. Dans [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], lorsque l'instruction s'exécute, l'opération `CAST` est effectuée une fois que le jeu de résultats a été trié. Cela signifie que la colonne `name` est utilisée dans l'opération de tri. Dans [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], l'opération `CAST` se produit avant l'opération de tri. Cela signifie que la colonne `id` dans la table est utilisée dans l'opération de tri et retourne le jeu de résultats dans un ordre inattendu.  
  
```  
SELECT CAST (o.name AS char(128)) AS id  
FROM sysobjects AS o  
ORDER BY o.id;  
```  
  
## <a name="corrective-action"></a>Action corrective  
 Modifiez les requêtes qui utilisent des alias de colonne préfixés par des alias de table dans la clause ORDER BY d'une des manières suivantes :  
  
-   N'ajoutez pas de préfixe à l'alias de colonne dans la clause ORDER BY, si possible.  
  
-   Remplacez l'alias de colonne par le nom de la colonne.  
  
 Par exemple, les deux requêtes suivantes s'exécutent sans erreur dans [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] :  
  
```  
USE AdventureWorks2012;  
GO  
SELECT FirstName AS f, LastName AS l  
FROM Person.Contact p  
ORDER BY l  
  
USE AdventureWorks2012;  
GO  
SELECT FirstName AS f, LastName AS l  
FROM Person.Contact p  
ORDER BY p.LastName  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau du moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
