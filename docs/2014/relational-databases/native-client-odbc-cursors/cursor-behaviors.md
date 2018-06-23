---
title: Comportements de curseur | Documents Microsoft
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
- scrollable cursors [SQL Server]
- SQL Server Native Client ODBC driver, cursors
- version-based optimistic concurrency
- cursors [ODBC], cursor behaviors
- ODBC applications, cursors
- SQL_ATTR_CURSOR_SENSITIVITY option
- SQL_ATTR_CURSOR_SCROLLABLE option
- sensitivity behavior of cursor
- ODBC cursors, cursor behaviors
ms.assetid: 742ddcd2-232b-4aa1-9212-027df120ad35
caps.latest.revision: 30
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 15aee78cfc531a7b80e034021b26404e5735a0ec
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36038136"
---
# <a name="cursor-behaviors"></a>Comportements de curseur
  ODBC prend en charge les options ISO pour spécifier le comportement des curseurs en termes de capacité de défilement et de sensibilité. Ces comportements sont spécifiés en définissant les options SQL_ATTR_CURSOR_SCROLLABLE et SQL_ATTR_CURSOR_SENSITIVITY lors d’un appel à [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md). Le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client implémente ces options en demandant des curseurs côté serveur avec les caractéristiques suivantes.  
  
|Paramètres de comportement du curseur|Caractéristiques du curseur côté serveur demandées|  
|------------------------------|---------------------------------------------|  
|SQL_SCROLLABLE et SQL_SENSITIVE|Curseur de jeu de clés et accès concurrentiel optimiste basé sur la version|  
|SQL_SCROLLABLE et SQL_INSENSITIVE|Curseur statique et concurrence en lecture seule|  
|SQL_SCROLLABLE et SQL_UNSPECIFIED|Curseur statique et concurrence en lecture seule|  
|SQL_NONSCROLLABLE et SQL_SENSITIVE|Curseur avant uniquement et accès concurrentiel optimiste basé sur la version|  
|SQL_NONSCROLLABLE et SQL_INSENSITIVE|Jeu de résultats par défaut (avant uniquement, en lecture seule)|  
|SQL_NONSCROLLABLE et SQL_UNSPECIFIED|Jeu de résultats par défaut (avant uniquement, en lecture seule)|  
  
 Accès concurrentiel optimiste basé sur une version nécessite un **timestamp** colonne dans la table sous-jacente. Si le contrôle d’accès concurrentiel optimiste basé sur la version est demandé sur une table qui n’a pas un **timestamp** colonne, le serveur utilise en fonction des valeurs d’accès concurrentiel optimiste.  
  
## <a name="scrollability"></a>Capacité de défilement  
 Quand SQL_ATTR_CURSOR_SCROLLABLE a la valeur SQL_SCROLLABLE, le curseur prend en charge les différentes valeurs pour le *FetchOrientation* paramètre de [SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md). Quand SQL_ATTR_CURSOR_SCROLLABLE a la valeur SQL_NONSCROLLABLE, le curseur prend uniquement en charge un *FetchOrientation* valeur de SQL_FETCH_NEXT.  
  
## <a name="sensitivity"></a>Sensibilité  
 Quand SQL_ATTR_CURSOR_SENSITIVITY est défini avec la valeur SQL_SENSITIVE, le curseur reflète les modifications des données effectuées par l'utilisateur en cours ou validées par d'autres utilisateurs. Quand SQL_ATTR_CURSOR_SENSITIVITY est défini avec la valeur SQL_INSENSITIVE, le curseur ne reflète pas les modifications des données.  
  
## <a name="see-also"></a>Voir aussi  
 [L’utilisation de curseurs &#40;ODBC&#41;](using-cursors-odbc.md)  
  
  