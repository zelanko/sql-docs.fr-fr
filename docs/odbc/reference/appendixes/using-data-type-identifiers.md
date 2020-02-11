---
title: Utilisation des identificateurs de type de données | Microsoft Docs
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
ms.openlocfilehash: 2b5e9fea64986bf595676540d74bb87a6e62521c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68070016"
---
# <a name="using-data-type-identifiers"></a>Utilisation d’identificateurs de types de données
Les applications utilisent des identificateurs de type de données de deux façons : pour décrire leurs mémoires tampons au pilote et pour récupérer les métadonnées sur le jeu de résultats à partir du pilote afin qu’elles puissent déterminer le type de tampons C à utiliser pour stocker les données. Les applications appellent les fonctions suivantes pour effectuer ces tâches :  
  
-   **SQLBindParameter**, **SQLBindCol**et **SQLGetData** -pour décrire le type de données C des mémoires tampons d’application.  
  
-   **SQLBindParameter** -pour décrire le type de données SQL des paramètres dynamiques.  
  
-   **SQLColAttribute** et **SQLDescribeCol** -pour récupérer les types de données SQL des colonnes de jeu de résultats.  
  
-   **SQLDescribeParameter** : pour récupérer les types de données SQL des paramètres.  
  
-   **SQLColumns**, **SQLProcedureColumns**et **SQLSpecialColumns** -pour récupérer les types de données SQL des diverses informations de schéma  
  
-   **SQLGetTypeInfo** : pour récupérer la liste des types de données pris en charge  
  
 Les identificateurs de type de données sont stockés dans le champ SQL_DESC_CONCISE_TYPE d’un descripteur. Les fonctions de descripteur **SQLSetDescField** et **SQLSetDescRec** peuvent être utilisées avec les types appropriés pour effectuer les tâches répertoriées dans la liste précédente. Pour plus d’informations, consultez [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).
