---
title: Utilisation d’identifiants de type de données (en anglais seulement) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], identifiers
- identifiers [ODBC], data types
ms.assetid: 467e0c0c-a818-4737-8a24-3d8e15c7e162
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8be8eef0441d48ed03ea6ccf8f656627c1dd9b63
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301420"
---
# <a name="using-data-type-identifiers"></a>Utilisation d’identificateurs de types de données
Les applications utilisent les identifiants de type de données de deux façons : décrire leurs tampons au conducteur, et pour récupérer les métadonnées sur le résultat défini par le conducteur afin qu’ils puissent déterminer quel type de tampons C utiliser pour stocker les données. Les applications appellent les fonctions suivantes pour effectuer ces tâches :  
  
-   **SQLBindParameter**, **SQLBindCol**, et **SQLGetData** - pour décrire le type de données C des tampons d’application.  
  
-   **SQLBindParameter** - pour décrire le type de données SQL de paramètres dynamiques.  
  
-   **SQLColAttribute** et **SQLDescribeCol** - pour récupérer les types de données SQL des colonnes de jeu de résultat.  
  
-   **SQLDescribeParameter** - pour récupérer les types de données SQL de paramètres.  
  
-   **SQLColumns**, **SQLProcedureColumns**, et **SQLSpecialColumns** - pour récupérer les types de données SQL de diverses informations schémas  
  
-   **SQLGetTypeInfo** - pour récupérer une liste de types de données pris en charge  
  
 Les identificateurs de type de données sont stockés dans le champ SQL_DESC_CONCISE_TYPE d’un descripteur. Les fonctions descripteur **SQLSetDescField** et **SQLSetDescRec** peuvent être utilisées avec les types appropriés pour effectuer les tâches énumérées dans la liste précédente. Pour plus d’informations, voir [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).
