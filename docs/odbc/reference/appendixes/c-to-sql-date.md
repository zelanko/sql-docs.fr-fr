---
title: 'C en SQL : date | Microsoft Docs'
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 02ee7c1fb396dc1c9c0708cf6c0e7a52ff1c11ec
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68019411"
---
# <a name="c-to-sql-date"></a>C en SQL : date
L’identificateur pour le type de données de la date ODBC C est le suivant :  
  
 SQL_C_TYPE_DATE  
  
 Le tableau suivant présente les types de données SQL ODBC dans lesquels les données de date peuvent être converties. Pour obtenir une explication des colonnes et des termes du tableau, consultez [conversion de données de C en types de données SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|Identificateur de type SQL|Test|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|Longueur d’octet de colonne >= 10<br /><br /> Longueur d’octet de colonne < 10<br /><br /> La valeur des données n’est pas une date valide|n/a<br /><br /> 22001<br /><br /> 22008|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|Longueur des caractères de la colonne >= 10<br /><br /> Longueur des caractères de la colonne < 10<br /><br /> La valeur des données n’est pas une date valide|n/a<br /><br /> 22001<br /><br /> 22008|  
|SQL_TYPE_DATE|La valeur des données est une date valide<br /><br /> La valeur des données n’est pas une date valide|n/a<br /><br /> 22007|  
|SQL_TYPE_TIMESTAMP|La valeur des données est une date valide [a]<br /><br /> La valeur des données n’est pas une date valide|n/a<br /><br /> 22007|  
  
 [a] la partie heure de l’horodatage est définie à zéro.  
  
 Pour plus d’informations sur les valeurs qui sont valides dans une structure SQL_C_TYPE_DATE, consultez [types de données C](../../../odbc/reference/appendixes/c-data-types.md), plus haut dans cette annexe.  
  
 Lorsque les données de date C sont converties en données SQL de caractères, les données de caractères résultantes sont au format «*yyyy*-*mm*-*JJ*».  
  
 Le pilote ignore la valeur de longueur/indicateur lors de la conversion de données à partir du type de données de date C et suppose que la taille de la mémoire tampon de données est égale à la taille du type de données C. La valeur de longueur/indicateur est passée dans l’argument *StrLen_Or_Ind* dans **SQLPutData** et dans la mémoire tampon spécifiée avec l’argument *StrLen_or_IndPtr* dans **SQLBindParameter**. La mémoire tampon de données est spécifiée avec l’argument *DataPtr* dans **SQLPutData** et l’argument *ParameterValuePtr* dans **SQLBindParameter**.
