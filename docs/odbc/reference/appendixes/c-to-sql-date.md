---
title: 'C en SQL : Date | Microsoft Docs'
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
manager: craigg
ms.openlocfilehash: 8edb075be1bf64dad8f4ef18924a6396b7c64e80
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47796127"
---
# <a name="c-to-sql-date"></a>C en SQL : date
L’identificateur pour le type de données ODBC C date est :  
  
 SQL_C_TYPE_DATE  
  
 Le tableau suivant présente les types de données à laquelle les données C de date peut-être être convertie à ODBC SQL. Pour obtenir une explication des colonnes et des termes dans la table, consultez [conversion des données à partir de C en Types de données SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|Identificateur de type SQL|Test|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|Longueur d’octet de colonne > = 10<br /><br /> Colonne de longueur d’octet < 10<br /><br /> Valeur de données n’est pas une date valide|n/a<br /><br /> 22001<br /><br /> 22008|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|Longueur de colonne caractère > = 10<br /><br /> Colonne de longueur < 10 caractères<br /><br /> Valeur de données n’est pas une date valide|n/a<br /><br /> 22001<br /><br /> 22008|  
|SQL_TYPE_DATE|Valeur de données est une date valide<br /><br /> Valeur de données n’est pas une date valide|n/a<br /><br /> 22007|  
|SQL_TYPE_TIMESTAMP|Valeur de données est une date valide [a]<br /><br /> Valeur de données n’est pas une date valide|n/a<br /><br /> 22007|  
  
 [a] la partie heure de l’horodatage est définie à zéro.  
  
 Pour plus d’informations sur les valeurs qui sont valides dans une structure SQL_C_TYPE_DATE, consultez [les Types de données C](../../../odbc/reference/appendixes/c-data-types.md), plus haut dans cette annexe.  
  
 Lorsque les données de date C sont converties en données de caractères SQL, les données de caractères résultant sont dans la «*aaaa*-*mm*-*jj*« format.  
  
 Le pilote ignore la valeur de longueur/indicateur lors de la conversion des données à partir du type de données date C et suppose que la taille du tampon de données est la taille du type de données date C. La valeur de longueur / d’indicateur est passée dans le *StrLen_or_Ind* argument dans **SQLPutData** et dans la mémoire tampon spécifiée avec la *StrLen_or_IndPtr* argument dans **SQLBindParameter**. Le tampon de données est spécifié avec la *DataPtr* argument dans **SQLPutData** et *ParameterValuePtr* argument dans **SQLBindParameter**.
