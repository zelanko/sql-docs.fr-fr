---
title: Comment les curseurs sont implémentés | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, cursors
- ODBC cursors, about ODBC cursors
- ODBC applications, cursors
- cursors [ODBC], about ODBC cursors
ms.assetid: 2b1d7dd4-08a4-43fc-b3eb-70c183d0941f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4c92391b1d8874da3a8901ccc5c6245e48334241
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63188520"
---
# <a name="how-cursors-are-implemented"></a>Comment les curseurs sont implémentés
  Les applications ODBC contrôlent le comportement d'un curseur en définissant un ou plusieurs attributs d'instruction avant d'exécuter une instruction SQL. ODBC permet de spécifier les caractéristiques d'un curseur de deux façons différentes :  
  
-   Type de curseur  
  
     Les types de curseurs sont définis à l’aide de l’attribut SQL_ATTR_CURSOR_TYPE de [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md). Les types de curseurs ODBC sont les suivants : avant uniquement, statiques, de jeu de clés, mixtes et dynamiques. La définition du type de curseur était la méthode employée à l'origine pour spécifier des curseurs dans ODBC.  
  
-   Comportements des curseurs  
  
     Le comportement de curseur est défini à l’aide des attributs SQL_ATTR_CURSOR_SCROLLABLE et SQL_ATTR_CURSOR_SENSITIVITY de **SQLSetStmtAttr**. Ces attributs sont modélisés sur les mots clés SCROLL et SENSITIVE définis pour l'instruction DECLARE CURSOR dans les normes ISO. Ces deux options ISO ont été introduites dans version 3.0 d'ODBC.  
  
 Les caractéristiques d'un curseur ODBC doivent être spécifiées à l'aide de l'une de ces deux méthodes, avec pour recommandation d'utiliser les types de curseurs ODBC.  
  
 Outre la définition du type d'un curseur, les applications ODBC définissent également d'autres options, telles que le nombre de lignes retournées sur chaque extraction, les options de concurrence et les niveaux d'isolation de la transaction. Ces options peuvent être définies pour des curseurs de style ODBC (avant uniquement, statiques, de eu de clés, mixtes et dynamiques) ou des curseurs de style ISO (capacité de défilement et sensibilité).  
  
 Le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pilote ODBC Native Client prend en charge plusieurs méthodes pour implémenter physiquement les différents types de curseurs. Le pilote implémente certains types de curseurs à l'aide d'un jeu de résultats par défaut [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], et d'autres en tant que curseurs côté serveur ou à l'aide de la bibliothèque de curseurs ODBC.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Utilisation de jeux de résultats SQL Server par défaut](using-sql-server-default-result-sets.md)  
  
-   [Utilisation des curseurs côté serveur](using-server-cursors.md)  
  
-   [Bibliothèque de curseurs ODBC](odbc-cursor-library.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de curseurs &#40;ODBC&#41;](../using-cursors-odbc.md)  
  
  
