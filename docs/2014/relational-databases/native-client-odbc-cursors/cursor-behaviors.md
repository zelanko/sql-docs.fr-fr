---
title: Comportements des curseurs | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 7d6b41e72d3421d24a160dbcc226ce285e37981c
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82702043"
---
# <a name="cursor-behaviors"></a>Comportements des curseurs
  ODBC prend en charge les options ISO pour spécifier le comportement des curseurs en termes de capacité de défilement et de sensibilité. Ces comportements sont spécifiés en définissant les options SQL_ATTR_CURSOR_SCROLLABLE et SQL_ATTR_CURSOR_SENSITIVITY sur un appel à [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md). Le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client implémente ces options en demandant des curseurs côté serveur avec les caractéristiques suivantes.  
  
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
 Lorsque SQL_ATTR_CURSOR_SCROLLABLE a la valeur SQL_SCROLLABLE, le curseur prend en charge toutes les valeurs différentes pour le paramètre *FetchOrientation* de [SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md). Lorsque SQL_ATTR_CURSOR_SCROLLABLE est défini sur SQL_NONSCROLLABLE, le curseur prend en charge uniquement la valeur *FetchOrientation* de SQL_FETCH_NEXT.  
  
## <a name="sensitivity"></a>Sensibilité  
 Quand SQL_ATTR_CURSOR_SENSITIVITY est défini avec la valeur SQL_SENSITIVE, le curseur reflète les modifications des données effectuées par l'utilisateur en cours ou validées par d'autres utilisateurs. Quand SQL_ATTR_CURSOR_SENSITIVITY est défini avec la valeur SQL_INSENSITIVE, le curseur ne reflète pas les modifications des données.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de curseurs &#40;ODBC&#41;](using-cursors-odbc.md)  
  
  
