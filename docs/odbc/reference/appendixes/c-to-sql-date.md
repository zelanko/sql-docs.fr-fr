---
title: 'C à SQL: Date Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- date data type [ODBC]
- converting data from c to SQL types [ODBC], date
- data conversions from C to SQL types [ODBC], date
ms.assetid: bea087d3-911f-418b-b483-d2b5b334da19
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fa3df8aaee03472076b3241cb9bb60e2a307e28b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298847"
---
# <a name="c-to-sql-date"></a>C en SQL : Date
L’identifiant pour la date ODBC C type de données est:  
  
 SQL_C_TYPE_DATE  
  
 Le tableau suivant montre les types de données SQL ODBC à quelle date les données C peuvent être converties. Pour une explication des colonnes et des termes dans le tableau, voir [convertir les données de C à SQL Data Types](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|Identifiant de type SQL|Test|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|Longueur d’ente de colonne >10<br /><br /> Longueur d’ente de colonne < 10<br /><br /> La valeur des données n’est pas une date valide|n/a<br /><br /> 22001<br /><br /> 22008|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|Longueur de caractère de colonne >10<br /><br /> Longueur de caractère de colonne < 10<br /><br /> La valeur des données n’est pas une date valide|n/a<br /><br /> 22001<br /><br /> 22008|  
|SQL_TYPE_DATE|La valeur des données est une date valide<br /><br /> La valeur des données n’est pas une date valide|n/a<br /><br /> 22007|  
|SQL_TYPE_TIMESTAMP|La valeur des données est une date valide[a]<br /><br /> La valeur des données n’est pas une date valide|n/a<br /><br /> 22007|  
  
 [a] La partie temporelle de l’humidité du temps est réglée à zéro.  
  
 Pour plus d’informations sur les valeurs qui sont valables dans une structure SQL_C_TYPE_DATE, voir [C Data Types](../../../odbc/reference/appendixes/c-data-types.md), plus tôt dans cette annexe.  
  
 Lorsque les données de la date C sont converties en données SQL de caractère, les données de caractère qui en résultent sont dans le format «*yyyy*-*mm*-*dd*».  
  
 Le conducteur ignore la durée/la valeur de l’indicateur lors de la conversion des données à partir du type de données de la date C et suppose que la taille du tampon de données est la taille du type de données de la date C. La durée/valeur de l’indicateur est passée dans *l’argument StrLen_or_Ind* dans **SQLPutData** et dans le tampon spécifié avec *l’argument StrLen_or_IndPtr* dans **SQLBindParameter**. Le tampon de données est spécifié avec l’argument *DataPtr* dans **SQLPutData** et *l’argument De ParameterValuePtr* dans **SQLBindParameter**.
