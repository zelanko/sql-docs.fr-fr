---
title: Identificateurs de type | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data types [ODBC], identifiers
- type identifiers [ODBC]
- identifiers [ODBC], type
- type identifiers [ODBC], about type identifiers
ms.assetid: 1d9fdfa2-e378-44fe-ac66-9743d9bbdd5a
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: da01de66ee5b20d873b3b50ea24c72549174e90b
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="type-identifiers"></a>Identificateurs de type
Pour décrire les types de données SQL et C, ODBC définit deux ensembles de *identificateurs de type*. Un identificateur de type décrit le type d’une colonne SQL ou une mémoire tampon C. Il s’agit d’un **#define** valeur et est généralement passée comme un argument de fonction ou retournée dans les métadonnées.  
  
 Par exemple, l’appel suivant à **SQLBindParameter** lie une variable de type SQL_DATE_STRUCT à un paramètre de date dans une instruction SQL. L’identificateur de type C SQL_C_TYPE_DATE Spécifie le type de la *Date* variable et l’identificateur de type SQL SQL_TYPE_DATE Spécifie le type du paramètre dynamique.  
  
```  
SQL_DATE_STRUCT Date;  
SQLINTEGER  DateInd = 0;  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_TYPE_DATE, SQL_TYPE_DATE, 0, 0,  
                  &Date, 0, &DateInd);  
```
