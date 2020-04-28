---
title: Identificateurs de type | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a274a19eaa0a2fdf98bcaa9ef42406ee8a6b6461
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306430"
---
# <a name="type-identifiers"></a>Identificateurs de types
Pour décrire les types de données SQL et C, ODBC définit deux jeux d' *identificateurs de type*. Un identificateur de type décrit le type d’une colonne SQL ou d’une mémoire tampon C. Il s’agit d’une valeur **#define** qui est généralement passée comme argument de fonction ou retournée dans les métadonnées.  
  
 Par exemple, l’appel suivant à **SQLBindParameter** lie une variable de type SQL_DATE_STRUCT à un paramètre date dans une instruction SQL. L’identificateur de type C SQL_C_TYPE_DATE spécifie le type de la variable de *Date* , et l’identificateur de type SQL SQL_TYPE_DATE spécifie le type du paramètre dynamique.  
  
```  
SQL_DATE_STRUCT Date;  
SQLINTEGER  DateInd = 0;  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_TYPE_DATE, SQL_TYPE_DATE, 0, 0,  
                  &Date, 0, &DateInd);  
```
