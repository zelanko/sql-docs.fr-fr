---
title: Détermination des capacités cursuriques (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 984ad8302f2e1695c8df84a64a18042f4cc9e364
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305880"
---
# <a name="determining-cursor-capabilities"></a>Détermination des fonctionnalités du curseur
Les quatre options suivantes dans **SQLGetInfo** décrivent quels types de curseurs sont pris en charge et quelles sont leurs capacités :  
  
-   SQL_CURSOR_SENSITIVITY. Indique si un curseur est sensible aux modifications apportées par un autre curseur.  
  
-   SQL_SCROLL_OPTIONS. Répertorie les types de curseurs pris en charge (avant seulement, statique, keyset-driven, dynamique ou mixte). Toutes les sources de données doivent prendre en charge les curseurs avant-seulement.  
  
-   SQL_DYNAMIC_CURSOR_ATTRIBUTES1, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR_ATTRIBUTES1 ou SQL_STATIC_CURSOR_ATTRIBUTES1 (selon le type de curseur). Répertorie les types d’aller chercher pris en charge par des curseurs défilants. Les bits de la valeur de retour correspondent aux types d’aller chercher dans **SQLFetchScroll**.  
  
-   SQL_KEYSET_CURSOR_ATTRIBUTES2 ou SQL_STATIC_CURSOR_ATTRIBUTES2 (selon le type de curseur). Liste si les curseurs statiques et pilotés par les clés peuvent détecter leurs propres mises à jour, suppressions et inserts.  
  
 Une application peut déterminer les capacités de curseur au moment de l’exécution en appelant **SQLGetInfo** avec ces options. Ceci est généralement fait par des applications génériques. Les capacités de curseur peuvent également être déterminées pendant le développement de l’application et leur utilisation codée en dur dans l’application. Ceci est généralement fait par des applications verticales et personnalisées, mais peut également être fait par des applications génériques qui utilisent une mise en œuvre de curseur côté client comme la bibliothèque de curseurs ODBC.
