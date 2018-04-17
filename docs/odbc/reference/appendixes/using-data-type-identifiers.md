---
title: À l’aide d’identificateurs de Type de données | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- data types [ODBC], identifiers
- identifiers [ODBC], data types
ms.assetid: 467e0c0c-a818-4737-8a24-3d8e15c7e162
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 283a4b6ed0fe2af5d29b619301f5a5dd283d22b5
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="using-data-type-identifiers"></a>À l’aide d’identificateurs de Type de données
Applications utilisent des identificateurs de type de données de deux façons : pour décrire les tampons pour le pilote et de récupérer des métadonnées relatives à l’ensemble du pilote afin qu’ils puissent identifier le type de C met en mémoire tampon pour stocker les données de résultats. Les applications appellent les fonctions suivantes pour effectuer ces tâches :  
  
-   **SQLBindParameter**, **SQLBindCol**, et **SQLGetData** — pour décrire le type de données C de mémoires tampons d’application.  
  
-   **SQLBindParameter** — pour décrire le type de données SQL de paramètres dynamiques.  
  
-   **SQLColAttribute** et **SQLDescribeCol** — pour récupérer les types de données SQL des colonnes du jeu de résultats.  
  
-   **SQLDescribeParameter** — pour récupérer les types de données SQL de paramètres.  
  
-   **SQLColumns**, **SQLProcedureColumns**, et **SQLSpecialColumns** — pour récupérer les types de données SQL de diverses informations de schéma  
  
-   **SQLGetTypeInfo** — pour récupérer une liste de prise en charge de types de données  
  
 Les identificateurs de type de données sont stockées dans le champ SQL_DESC_CONCISE_TYPE d’un descripteur. Les fonctions de descripteur **SQLSetDescField** et **SQLSetDescRec** peut être utilisé avec les types appropriés pour effectuer les tâches répertoriées dans la liste précédente. Pour plus d’informations, consultez [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).
