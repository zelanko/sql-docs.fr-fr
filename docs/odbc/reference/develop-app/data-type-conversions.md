---
title: Conversions de type de données (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], conversions
- SQL data types [ODBC], conversions
- converting data [ODBC]
- converting data types [ODBC]
- C data types [ODBC], conversions
ms.assetid: d311fe1c-d882-4136-9fa5-220a4121e04c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cd888fe32692494e2b0ceadc1ed872dd96e244a9
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305211"
---
# <a name="data-type-conversions"></a>Conversions de type de données
Les données peuvent être converties d’un type à l’autre à l’une des quatre fois : lorsque les données sont transférées d’une variable d’application à une autre (C à C), lorsque les données d’une variable d’application sont envoyées à un paramètre d’instruction (C à SQL), lorsque les données dans une colonne d’ensemble de résultats sont retournées dans une variable d’application (SQL à C), et lorsque les données sont transférées d’une colonne de source de données à une autre (SQL à SQL).  
  
 Toute conversion qui se produit lorsque les données sont transférées d’une variable d’application à une autre est en dehors de la portée de ce document.  
  
 Lorsqu’une application lie une variable à un paramètre de colonne ou d’énoncé de résultat, l’application spécifie implicitement une conversion de type de données dans son choix du type de données de la variable d’application. Supposons, par exemple, qu’une colonne contienne des données integer. Si l’application lie une variable d’intégrerie à la colonne, elle précise qu’aucune conversion n’est effectuée; si l’application lie une variable de caractère à la colonne, elle spécifie que les données sont converties de l’intégrant au caractère.  
  
 ODBC définit la façon dont les données sont converties entre chaque type de données SQL et C. Fondamentalement, ODBC prend en charge toutes les conversions raisonnables, telles que le caractère d’intégrer et d’intégrer à flotter, et ne prend pas en charge les conversions mal définies, telles que le flotteur à ce jour. Les conducteurs sont tenus de prendre en charge toutes les conversions pour chaque type de données SQL qu’ils prennent en charge. Pour une liste complète des conversions entre les types de données SQL et C, voir [convertir les données de SQL à C Data Types](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md) et convertir les données de C à [SQL Data Types](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md) dans l’annexe D : Data Types.  
  
 ODBC définit également une fonction scalaire pour convertir les données d’un type de données SQL à une autre. La fonction scalaire **CONVERT** est cartographiée par le conducteur à la fonction ou fonctions scalaires sous-jacentes définies pour effectuer des conversions dans la source de données. Étant donné que cette fonction est cartographiée selon des fonctions spécifiques à DBMS, ODBC ne définit pas comment ces conversions fonctionnent ni quelles conversions doivent être prises en charge. Une application découvre quelles conversions sont prises en charge par un conducteur particulier et une source de données grâce aux options SQL_CONVERT dans **SQLGetInfo**. Pour plus d’informations sur la fonction scalaire **CONVERT,** voir [Séquences d’évasion dans ODBC](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md) et [Explicit Data Type Conversion Function](../../../odbc/reference/appendixes/explicit-data-type-conversion-function.md).
