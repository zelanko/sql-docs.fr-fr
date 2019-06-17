---
title: Déterminer les fonctionnalités de curseur | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- scrollable cursors [ODBC]
- cursors [ODBC], capabilities
- cursors [ODBC], scrollable
ms.assetid: 35be486c-8f2d-4cec-beb8-df14151abfef
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 716471786400c030febb62ebf41c8422770a8c09
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62744378"
---
# <a name="determining-cursor-capabilities"></a>Détermination des fonctionnalités du curseur
Les quatre options suivantes dans **SQLGetInfo** décrivent les types de curseurs sont pris en charge et leurs capacités :  
  
-   SQL_CURSOR_SENSITIVITY. Indique si un curseur est sensible aux modifications effectuées par un autre curseur.  
  
-   SQL_SCROLL_OPTIONS. Répertorie les types de curseurs pris en charge (avant uniquement, statiques, commandé par keyset, dynamiques ou mixtes). Toutes les sources de données doivent prendre en charge les curseurs avant uniquement.  
  
-   SQL_DYNAMIC_CURSOR_ATTRIBUTES1, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR_ATTRIBUTES1 ou SQL_STATIC_CURSOR_ATTRIBUTES1 (selon le type du curseur). Répertorie les types d’extraction prises en charge par les curseurs avec défilement. Les bits dans la valeur de retour correspondent aux types de fetch dans **SQLFetchScroll**.  
  
-   SQL_KEYSET_CURSOR_ATTRIBUTES2 ou SQL_STATIC_CURSOR_ATTRIBUTES2 (selon le type du curseur). Indique si les curseurs statiques et pilotés par peuvent détecter leurs propres mises à jour, les suppressions et insertions.  
  
 Une application peut déterminer les fonctionnalités du curseur en cours d’exécution en appelant **SQLGetInfo** avec ces options. Cette situation est fréquente par les applications génériques. Fonctionnalités du curseur également peuvent être déterminées pendant le développement d’applications et leur utilisation codées en dur dans l’application. Cela est fréquente par applications verticales et personnalisées, mais peut également être effectuée par les applications génériques qui utilisent une implémentation de curseur côté client telles que la bibliothèque de curseurs ODBC.
