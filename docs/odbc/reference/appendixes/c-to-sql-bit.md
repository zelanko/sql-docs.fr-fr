---
title: 'C à SQL: Bit Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from c to SQL types [ODBC], bit
- bit data type [ODBC]
- data conversions from C to SQL types [ODBC], bit
ms.assetid: 267c9fa9-599e-4ee6-b51b-0cae43f09183
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a96982573d83cf01947f82dc2014ee2c470931e3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292042"
---
# <a name="c-to-sql-bit"></a>C en SQL : bit
L’identifiant pour le type de données bit ODBC C est :  
  
 SQL_C_BIT  
  
 Le tableau suivant montre les types de données SQL ODBC auxquels les données C peuvent être converties. Pour une explication des colonnes et des termes dans le tableau, voir [convertir les données de C à SQL Data Types](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|Identifiant de type SQL|Test|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR<br /><br /> SQL_WCHAR SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|None|n/a|  
|SQL_DECIMAL SQL_NUMERIC<br /><br /> SQL_TINYINT SQL_SMALLINT<br /><br /> SQL_INTEGER SQL_BIGINT<br /><br /> SQL_REAL SQL_FLOAT<br /><br /> SQL_DOUBLE|None|n/a|  
|SQL_BIT|None|n/a|  
  
 Le conducteur ignore la valeur de longueur/indicateur lors de la conversion des données à partir du type de données bit C et suppose que la taille du tampon de données est la taille du type de données bit C. La durée/valeur de l’indicateur est passée dans *l’argument StrLen_or_Ind* dans **SQLPutData** et dans le tampon spécifié avec *l’argument StrLen_or_IndPtr* dans **SQLBindParameter**. Le tampon de données est spécifié avec l’argument *DataPtr* dans **SQLPutData** et *l’argument De ParameterValuePtr* dans **SQLBindParameter**.
