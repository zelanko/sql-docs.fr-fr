---
title: Tapez des identificateurs | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], identifiers
- type identifiers [ODBC]
- identifiers [ODBC], type
- type identifiers [ODBC], about type identifiers
ms.assetid: 1d9fdfa2-e378-44fe-ac66-9743d9bbdd5a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cbefab0f02f3229d8b4c0a62a568634ec222290b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63305666"
---
# <a name="type-identifiers"></a>Identificateurs de types
Pour décrire les types de données SQL et C, ODBC définit deux ensembles de *tapez identificateurs*. Un identificateur de type décrit le type d’une colonne SQL ou une mémoire tampon C. Il s’agit une **#define** valeur et est généralement passée comme argument de fonction ou retournées dans les métadonnées.  
  
 Par exemple, l’appel suivant à **SQLBindParameter** lie une variable de type SQL_DATE_STRUCT à un paramètre de date dans une instruction SQL. L’identificateur de type C SQL_C_TYPE_DATE Spécifie le type de la *Date* variable et l’identificateur de type SQL SQL_TYPE_DATE Spécifie le type du paramètre dynamique.  
  
```  
SQL_DATE_STRUCT Date;  
SQLINTEGER  DateInd = 0;  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_TYPE_DATE, SQL_TYPE_DATE, 0, 0,  
                  &Date, 0, &DateInd);  
```
