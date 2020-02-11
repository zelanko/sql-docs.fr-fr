---
title: Type de tampon de données | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 615625ca396e5f2ae094962457cc9e746730ddcf
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68067415"
---
# <a name="data-buffer-type"></a>Type de tampon de données
Le type de données C d’une mémoire tampon est spécifié par l’application. Avec une seule variable, cela se produit lorsque l’application alloue la variable. Avec la mémoire générique, c’est-à-dire la mémoire vers laquelle pointe un pointeur de type void. cela se produit lorsque l’application convertit la mémoire en un type particulier. Le pilote Découvre ce type de deux manières :  
  
-   **Argument de type de tampon de données.** Les mémoires tampons utilisées pour transférer des valeurs de paramètres et des données de jeu de résultats, telles que la mémoire tampon liée à *TargetValuePtr* dans **SQLBindCol**, ont généralement un argument de type associé, tel que l’argument *TargetType* dans **SQLBindCol**. Dans cet argument, l’application passe l’identificateur de type C qui correspond au type de la mémoire tampon. Par exemple, dans l’appel suivant à **SQLBindCol**, la valeur SQL_C_TYPE_DATE indique au pilote que la mémoire tampon de *DATE* est un SQL_DATE_STRUCT :  
  
    ```  
    SQL_DATE_STRUCT Date;  
    SQLINTEGER  DateInd;  
    SQLBindCol(hstmt, 1, SQL_C_TYPE_DATE, &Date, 0, &DateInd);  
    ```  
  
     Pour plus d’informations sur les identificateurs de type, consultez la section [types de données dans ODBC](../../../odbc/reference/develop-app/data-types-in-odbc.md) , plus loin dans cette section.  
  
-   **Type prédéfini.** Les mémoires tampons utilisées pour envoyer et récupérer des options ou des attributs, tels que la mémoire tampon pointée par l’argument *InfoValuePtr* dans **SQLGetInfo**, ont un type fixe qui dépend de l’option spécifiée. Le pilote part du principe que la mémoire tampon de données est de ce type ; Il incombe à l’application d’allouer une mémoire tampon de ce type. Par exemple, dans l’appel suivant à **SQLGetInfo**, le pilote suppose que la mémoire tampon est un entier 32 bits, car c’est ce que nécessite l’option SQL_STRING_FUNCTIONS :  
  
    ```  
    SQLUINTEGER StringFuncs;  
    SQLGetInfo(hdbc, SQL_STRING_FUNCTIONS, (SQLPOINTER) &StringFuncs, 0,  
                NULL);  
    ```  
  
 Le pilote utilise le type de données C pour interpréter les données dans la mémoire tampon.
