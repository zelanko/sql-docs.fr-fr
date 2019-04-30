---
title: 'C en SQL : Binary | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- binary data type [ODBC]
- data conversions from C to SQL types [ODBC], binary
- binary data transfers [ODBC]
- converting data from c to SQL types [ODBC], binary
ms.assetid: 3e9083f3-357b-41aa-833c-2c8aac2226cd
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 76c2e4673d9b561aeb5af3e61e1e4dc8532195d6
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63201593"
---
# <a name="c-to-sql-binary"></a>C en SQL : Binaire
L’identificateur pour le type de données ODBC C binaire est :  
  
 SQL_C_BINARY  
  
 Le tableau suivant présente les types de données à laquelle les données de C binaires peuvent être converties à ODBC SQL. Pour obtenir une explication des colonnes et des termes dans la table, consultez [conversion des données à partir de C en Types de données SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|Identificateur de type SQL|Test|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|Longueur d’octet de données < = longueur d’octet de colonne<br /><br /> Longueur d’octet de données > longueur d’octet de colonne|n/a<br /><br /> 22001|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|Longueur des données de caractère < = longueur de caractère de colonne<br /><br /> Longueur des données de caractères > longueur de caractère de colonne|n/a<br /><br /> 22001|  
|SQL_DECIMAL<br /><br /> SQL_NUMERIC<br /><br /> SQL_TINYINT<br /><br /> SQL_SMALLINT<br /><br /> SQL_INTEGER<br /><br /> SQL_BIGINT<br /><br /> SQL_REAL<br /><br /> SQL_FLOAT<br /><br /> SQL_DOUBLE<br /><br /> SQL_BIT SQL_TYPE_DATE<br /><br /> SQL_TYPE_TIME<br /><br /> SQL_TYPE_TIMESTAMP|Longueur d’octet de données = longueur de données SQL<br /><br /> Longueur d’octet de longueur de données données <> SQL|n/a<br /><br /> 22003|  
|SQL_BINARY<br /><br /> SQL_VARBINARY<br /><br /> SQL_LONGVARBINARY|Longueur des données < = longueur de colonne<br /><br /> Longueur des données > longueur de colonne|n/a<br /><br /> 22001|
