---
title: Détermination des fonctionnalités de curseur | Microsoft Docs
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
ms.openlocfilehash: 14715e40cd99f3f1a03c2ae19e825705a8376e30
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68040006"
---
# <a name="determining-cursor-capabilities"></a>Détermination des fonctionnalités du curseur
Les quatre options suivantes de **SQLGetInfo** décrivent les types de curseurs pris en charge et leurs fonctionnalités :  
  
-   SQL_CURSOR_SENSITIVITY. Indique si un curseur est sensible aux modifications apportées par un autre curseur.  
  
-   SQL_SCROLL_OPTIONS. Répertorie les types de curseurs pris en charge (avant uniquement, statique, piloté par jeu de clés, dynamique ou mixte). Toutes les sources de données doivent prendre en charge les curseurs avant uniquement.  
  
-   SQL_DYNAMIC_CURSOR_ATTRIBUTES1, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR_ATTRIBUTES1 ou SQL_STATIC_CURSOR_ATTRIBUTES1 (selon le type du curseur). Répertorie les types d’extraction pris en charge par les curseurs à défilement. Les bits de la valeur de retour correspondent aux types d’extraction dans **SQLFetchScroll**.  
  
-   SQL_KEYSET_CURSOR_ATTRIBUTES2 ou SQL_STATIC_CURSOR_ATTRIBUTES2 (selon le type de curseur). Indique si les curseurs statiques et pilotés par keyset peuvent détecter leurs propres mises à jour, suppressions et insertions.  
  
 Une application peut déterminer les fonctionnalités de curseur au moment de l’exécution en appelant **SQLGetInfo** avec ces options. Cette opération est généralement effectuée par les applications génériques. Les fonctionnalités de curseur peuvent également être déterminées pendant le développement de l’application et leur utilisation codée en dur dans l’application. Cette opération est généralement effectuée par des applications verticales et personnalisées, mais elle peut également être effectuée par des applications génériques qui utilisent une implémentation de curseur côté client, telle que la bibliothèque de curseurs ODBC.
