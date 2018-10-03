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
manager: craigg
ms.openlocfilehash: 84710ffd69ea377c979adf94af1394d8436ef10b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47786337"
---
# <a name="data-type-conversions"></a>Conversions de type de données
Données qui peuvent être converties à partir d’un type vers un autre à un des quatre fois : quand données sont transférées à partir de la variable d’une application vers un autre C à C, lorsque les données dans une variable d’application sont envoyées à un paramètre d’instruction (C en SQL), lorsque les données dans une colonne de jeu de résultats sont retournées dans une variable d’application (SQL vers C), et lorsque les données sont transférées à partir de la source de données d’une colonne vers un autre (SQL to SQL).  
  
 Toute conversion se produit lorsque les données sont transférées à partir de la variable d’une application à l’autre est en dehors de la portée de ce document.  
  
 Lorsqu’une application lie une variable à un paramètre de colonne ou une instruction de jeu de résultats, l’application spécifie implicitement une conversion de type de données dans son choix du type de données de la variable d’application. Par exemple, qu'une colonne contient des données de type integer. Si l’application lie une variable entière à la colonne, elle spécifie qu’aucune conversion n’être effectuée ; Si l’application lie une variable de caractère à la colonne, il spécifie que les données être convertie à partir d’entier en caractère.  
  
 ODBC définit comment les données sont converties entre chaque type de données SQL et C. En fait, ODBC prend en charge de toutes les conversions raisonnables, tels que des caractères à l’entier et float et ne prend pas en charge les conversions mal définies, comme float en date. Pilotes sont requis pour prendre en charge toutes les conversions pour chaque type de données SQL qu’ils prennent en charge. Pour obtenir une liste complète des conversions entre types de données SQL et C, consultez [conversion des données à partir de SQL pour les Types de données C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md) et [conversion des données à partir de C en Types de données SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md) annexe d : Types de données.  
  
 ODBC définit également une fonction scalaire pour la conversion des données à partir d’un type de données SQL vers un autre. Le **convertir** fonction scalaire est mappée par le pilote à la fonction scalaire sous-jacent ou des fonctions définies pour effectuer des conversions dans la source de données. Étant donné que cette fonction est mappée à des fonctions spécifiques au SGBD, ODBC ne définit pas le fonctionnement de ces conversions ou les conversions doivent être prises en charge. Une application permet de découvrir quelles conversions sont prises en charge par une source de données et de pilote particulier via les options de SQL_CONVERT **SQLGetInfo**. Pour plus d’informations sur la **convertir** fonction scalaire, consultez [les séquences d’échappement dans ODBC](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md) et [fonction de Conversion de Type de données explicite](../../../odbc/reference/appendixes/explicit-data-type-conversion-function.md).
