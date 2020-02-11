---
title: Comportements des curseurs | Microsoft Docs
ms.custom: ''
ms.date: 10/24/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
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
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 06a19a173fdd6f70b19e9a63c214616909708eec
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "73784729"
---
# <a name="cursor-behaviors"></a>Comportements des curseurs
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  ODBC prend en charge les options ISO pour spécifier le comportement des curseurs en termes de capacité de défilement et de sensibilité. Ces comportements sont spécifiés en définissant les options SQL_ATTR_CURSOR_SCROLLABLE et SQL_ATTR_CURSOR_SENSITIVITY sur un appel à [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md). Le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client implémente ces options en demandant des curseurs côté serveur avec les caractéristiques suivantes.  
  
|Paramètres de comportement du curseur|Caractéristiques du curseur côté serveur demandées|  
|------------------------------|---------------------------------------------|  
|SQL_SCROLLABLE et SQL_SENSITIVE|Curseur de jeu de clés et accès concurrentiel optimiste basé sur la version|  
|SQL_SCROLLABLE et SQL_INSENSITIVE|Curseur statique et concurrence en lecture seule|  
|SQL_SCROLLABLE et SQL_UNSPECIFIED|Curseur statique et concurrence en lecture seule|  
|SQL_NONSCROLLABLE et SQL_SENSITIVE|Curseur avant uniquement et accès concurrentiel optimiste basé sur la version|  
|SQL_NONSCROLLABLE et SQL_INSENSITIVE|Jeu de résultats par défaut (avant uniquement, en lecture seule)|  
|SQL_NONSCROLLABLE et SQL_UNSPECIFIED|Jeu de résultats par défaut (avant uniquement, en lecture seule)|  
  
 L’accès concurrentiel optimiste basé sur la version nécessite une colonne **timestamp** dans la table sous-jacente. Si le contrôle d’accès concurrentiel optimiste basé sur la version est demandé sur une table qui n’a pas de colonne **timestamp** , le serveur utilise l’accès concurrentiel optimiste basé sur les valeurs.  
  
## <a name="scrollability"></a>Capacité de défilement  
 Lorsque SQL_ATTR_CURSOR_SCROLLABLE a la valeur SQL_SCROLLABLE, le curseur prend en charge toutes les valeurs différentes pour le paramètre *FetchOrientation* de [SQLFetchScroll](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md). Lorsque SQL_ATTR_CURSOR_SCROLLABLE est défini sur SQL_NONSCROLLABLE, le curseur prend en charge uniquement la valeur *FetchOrientation* de SQL_FETCH_NEXT.  
  
## <a name="sensitivity"></a>Sensibilité  
 Quand SQL_ATTR_CURSOR_SENSITIVITY est défini avec la valeur SQL_SENSITIVE, le curseur reflète les modifications des données effectuées par l'utilisateur en cours ou validées par d'autres utilisateurs. Quand SQL_ATTR_CURSOR_SENSITIVITY est défini avec la valeur SQL_INSENSITIVE, le curseur ne reflète pas les modifications des données.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des curseurs (ODBC)](../../relational-databases/native-client-odbc-cursors/using-cursors-odbc.md) des [Propriétés de curseur](properties/cursor-properties.md) 
  
  
