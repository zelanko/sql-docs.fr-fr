---
title: À l’aide d’identificateurs de Type de données | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f14294b76fc7977de256697c730f7dca31e7a469
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62735128"
---
# <a name="using-data-type-identifiers"></a>Utilisation d’identificateurs de types de données
Applications utilisent des identificateurs de type de données de deux manières : pour décrire les tampons pour le pilote et pour récupérer des métadonnées sur le jeu à partir du pilote afin qu’ils puissent identifier quel type de C met en mémoire tampon pour stocker les données de résultats. Les applications appellent les fonctions suivantes pour effectuer ces tâches :  
  
-   **SQLBindParameter**, **SQLBindCol**, et **SQLGetData** - pour décrire le type de données C de mémoires tampons d’application.  
  
-   **SQLBindParameter** - pour décrire le type de données SQL de paramètres dynamiques.  
  
-   **SQLColAttribute** et **SQLDescribeCol** : pour récupérer les types de données SQL des colonnes de jeu de résultats.  
  
-   **SQLDescribeParameter** : pour récupérer les types de données SQL de paramètres.  
  
-   **SQLColumns**, **SQLProcedureColumns**, et **SQLSpecialColumns** : pour récupérer les types de données SQL différentes des informations de schéma  
  
-   **SQLGetTypeInfo** : pour récupérer une liste de types de données pris en charge  
  
 Les identificateurs de type de données sont stockées dans le champ SQL_DESC_CONCISE_TYPE d’un descripteur. Les fonctions de descripteur **SQLSetDescField** et **SQLSetDescRec** peut être utilisé avec les types appropriés pour effectuer les tâches répertoriées dans la liste précédente. Pour plus d’informations, consultez [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).
