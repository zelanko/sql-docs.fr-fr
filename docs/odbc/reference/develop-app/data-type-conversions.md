---
title: Conversions de types de données | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 590bd488ae87e8e871837c3055a3225794850d00
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68077016"
---
# <a name="data-type-conversions"></a>Conversions de type de données
Les données peuvent être converties d’un type à un autre à quatre moments : lorsque les données sont transférées d’une variable d’application à une autre (C vers C), lorsque les données d’une variable d’application sont envoyées à un paramètre d’instruction (C to SQL), lorsque les données d’une colonne de l’ensemble de résultats sont retournées dans une variable d’application (SQL à C), et lorsque les données sont transférées d’une colonne source de données à une autre (SQL vers SQL).  
  
 Toute conversion qui se produit lorsque les données sont transférées d’une variable d’application à l’autre n’est pas comprise dans le cadre de ce document.  
  
 Quand une application lie une variable à une colonne de jeu de résultats ou un paramètre d’instruction, l’application spécifie implicitement une conversion de type de données dans son choix du type de données de la variable d’application. Par exemple, supposons qu’une colonne contienne des données de type entier. Si l’application lie une variable de type entier à la colonne, elle spécifie qu’aucune conversion n’est effectuée ; Si l’application lie une variable de type caractère à la colonne, elle spécifie que les données sont converties d’un entier en caractère.  
  
 ODBC définit la manière dont les données sont converties entre chaque type de données SQL et C. En fait, ODBC prend en charge toutes les conversions raisonnables, telles que le caractère à l’entier et l’entier à float, et ne prend pas en charge les conversions mal définies, telles que float jusqu’à date. Les pilotes sont requis pour prendre en charge toutes les conversions pour chaque type de données SQL qu’ils prennent en charge. Pour obtenir la liste complète des conversions entre les types de données SQL et C, consultez [conversion de données SQL en types](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md) de données c et [conversion de données de](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md) types de données c en SQL en annexe D : types de données.  
  
 ODBC définit également une fonction scalaire pour la conversion de données d’un type de données SQL vers un autre. La fonction scalaire **Convert** est mappée par le pilote à la fonction scalaire sous-jacente ou aux fonctions définies pour effectuer des conversions dans la source de données. Étant donné que cette fonction est mappée à des fonctions propres au SGBD, ODBC ne définit pas le mode de fonctionnement de ces conversions ou les conversions qui doivent être prises en charge. Une application Découvre les conversions prises en charge par un pilote et une source de données spécifiques par le biais des options de SQL_CONVERT dans **SQLGetInfo**. Pour plus d’informations sur la fonction scalaire **Convert** , consultez [séquences d’échappement dans ODBC](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md) et fonction de conversion de type de [données explicite](../../../odbc/reference/appendixes/explicit-data-type-conversion-function.md).
