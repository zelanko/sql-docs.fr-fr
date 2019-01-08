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
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52516609"
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
