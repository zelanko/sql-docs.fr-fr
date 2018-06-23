---
title: Comment les curseurs sont implémentés | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, cursors
- ODBC cursors, about ODBC cursors
- ODBC applications, cursors
- cursors [ODBC], about ODBC cursors
ms.assetid: 2b1d7dd4-08a4-43fc-b3eb-70c183d0941f
caps.latest.revision: 31
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8f64f5e6c4d57fdc7b0165875394b9d33a62b95c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36039945"
---
# <a name="how-cursors-are-implemented"></a>Comment les curseurs sont implémentés
  Les applications ODBC contrôlent le comportement d'un curseur en définissant un ou plusieurs attributs d'instruction avant d'exécuter une instruction SQL. ODBC permet de spécifier les caractéristiques d'un curseur de deux façons différentes :  
  
-   Type de curseur  
  
     Types de curseurs sont définies à l’aide de l’attribut SQL_ATTR_CURSOR_TYPE de [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md). Les types de curseurs ODBC sont les suivants : avant uniquement, statiques, de jeu de clés, mixtes et dynamiques. La définition du type de curseur était la méthode employée à l'origine pour spécifier des curseurs dans ODBC.  
  
-   Comportements des curseurs  
  
     Comportement du curseur est défini à l’aide des attributs SQL_ATTR_CURSOR_SCROLLABLE et SQL_ATTR_CURSOR_SENSITIVITY de **SQLSetStmtAttr**. Ces attributs sont modélisés sur les mots clés SCROLL et SENSITIVE définis pour l'instruction DECLARE CURSOR dans les normes ISO. Ces deux options ISO ont été introduites dans version 3.0 d'ODBC.  
  
 Les caractéristiques d'un curseur ODBC doivent être spécifiées à l'aide de l'une de ces deux méthodes, avec pour recommandation d'utiliser les types de curseurs ODBC.  
  
 Outre la définition du type d'un curseur, les applications ODBC définissent également d'autres options, telles que le nombre de lignes retournées sur chaque extraction, les options de concurrence et les niveaux d'isolation de la transaction. Ces options peuvent être définies pour des curseurs de style ODBC (avant uniquement, statiques, de eu de clés, mixtes et dynamiques) ou des curseurs de style ISO (capacité de défilement et sensibilité).  
  
 Le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pilote ODBC Native Client prend en charge plusieurs façons d’implémenter physiquement les différents types de curseurs. Le pilote implémente certains types de curseurs à l'aide d'un jeu de résultats par défaut [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], et d'autres en tant que curseurs côté serveur ou à l'aide de la bibliothèque de curseurs ODBC.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Utilisation de jeux de résultats SQL Server par défaut](using-sql-server-default-result-sets.md)  
  
-   [Utilisation des curseurs côté serveur](using-server-cursors.md)  
  
-   [Bibliothèque de curseurs ODBC](odbc-cursor-library.md)  
  
## <a name="see-also"></a>Voir aussi  
 [L’utilisation de curseurs &#40;ODBC&#41;](../using-cursors-odbc.md)  
  
  