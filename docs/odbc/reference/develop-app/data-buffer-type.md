---
title: Type de tampon de données (en anglais) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], buffers
- data buffers [ODBC], types
- buffers [ODBC], data
- C data types [ODBC], buffers
ms.assetid: 58bea3e9-d552-447f-b3ad-ce1dab213b72
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9b98ed2ab0865b98884f6dfa1ff20142540ff314
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305245"
---
# <a name="data-buffer-type"></a>Type de tampon de données
Le type de données C d’un tampon est spécifié par l’application. Avec une seule variable, cela se produit lorsque l’application alloue la variable. Avec la mémoire générique - c’est-à-dire, la mémoire pointée par un pointeur de vide de type - cela se produit lorsque l’application jette la mémoire à un type particulier. Le conducteur découvre ce type de deux façons :  
  
-   **Argument de type tampon de données.** Les tampons utilisés pour transférer les valeurs de paramètres et les données de jeu de résultats, telles que le tampon lié à *TargetValuePtr* dans **SQLBindCol**, ont généralement un argument de type associé, comme l’argument *TargetType* dans **SQLBindCol**. Dans le présent argument, l’application passe l’identifiant de type C qui correspond au type de tampon. Par exemple, dans l’appel suivant à **SQLBindCol**, la valeur SQL_C_TYPE_DATE indique au conducteur que le tampon *Date* est un SQL_DATE_STRUCT :  
  
    ```  
    SQL_DATE_STRUCT Date;  
    SQLINTEGER  DateInd;  
    SQLBindCol(hstmt, 1, SQL_C_TYPE_DATE, &Date, 0, &DateInd);  
    ```  
  
     Pour plus d’informations sur les identifiants de type, consultez les types de données dans la section [ODBC,](../../../odbc/reference/develop-app/data-types-in-odbc.md) plus tard dans cette section.  
  
-   **Type prédéfini.** Les tampons utilisés pour envoyer et récupérer des options ou des attributs, tels que le tampon pointé par *l’argument InfoValuePtr* dans **SQLGetInfo**, ont un type fixe qui dépend de l’option spécifiée. Le conducteur suppose que le tampon de données est de ce type; il incombe à l’application d’allouer un tampon de ce type. Par exemple, dans l’appel suivant à **SQLGetInfo**, le conducteur suppose que le tampon est un intégrateur 32 bits parce que c’est ce que l’option SQL_STRING_FUNCTIONS exige :  
  
    ```  
    SQLUINTEGER StringFuncs;  
    SQLGetInfo(hdbc, SQL_STRING_FUNCTIONS, (SQLPOINTER) &StringFuncs, 0,  
                NULL);  
    ```  
  
 Le conducteur utilise le type de données C pour interpréter les données dans le tampon.
