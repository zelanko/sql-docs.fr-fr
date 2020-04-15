---
title: 'C à SQL: Temps Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data conversions from C to SQL types [ODBC], time
- time data type [ODBC]
- converting data from c to SQL types [ODBC], time
ms.assetid: a8da43c9-d9a5-45e5-bd9a-1dd633db2ee0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 264ce7751072b79163923f0c141542680f7b02bb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304761"
---
# <a name="c-to-sql-time"></a>C en SQL : Temps
L’identifiant pour le moment ODBC C type de données est:  
  
 SQL_C_TYPE_TIME  
  
 Le tableau suivant montre les types de données SQL ODBC à l’heure à laquelle les données C peuvent être converties. Pour une explication des colonnes et des termes dans le tableau, voir [convertir les données de C à SQL Data Types](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|Identifiant de type SQL|Test|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|Longueur d’ente de colonne >8<br /><br /> Longueur d’ente de colonne < 8<br /><br /> La valeur des données n’est pas un temps valide|n/a<br /><br /> 22001<br /><br /> 22008|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|Longueur de caractère de colonne >8<br /><br /> Longueur de caractère de colonne < 8<br /><br /> La valeur des données n’est pas un temps valide|n/a<br /><br /> 22001<br /><br /> 22008|  
|SQL_TYPE_TIME|La valeur des données est un temps valide<br /><br /> La valeur des données n’est pas un temps valide|n/a<br /><br /> 22007|  
|SQL_TYPE_TIMESTAMP|La valeur des données est un temps valide[a]<br /><br /> La valeur des données n’est pas un temps valide|n/a<br /><br /> 22007|  
  
 [a] La partie date de l’humidité de temps est fixée à la date actuelle, et la partie fractionnelle secondes de l’humidité de temps est réglée à zéro.  
  
 Pour plus d’informations sur les valeurs qui sont valables dans une structure SQL_C_TYPE_TIME, voir [C Data Types](../../../odbc/reference/appendixes/c-data-types.md), plus tôt dans cette annexe.  
  
 Lorsque les données C de temps sont converties en données SQL de caractère, les données de caractère qui en résultent sont dans le format «*hh*:*mm*:*ss*».  
  
 Le conducteur ignore la valeur de longueur/indicateur lors de la conversion des données à partir du type de données C et suppose que la taille du tampon de données est la taille du type de données de temps C. La durée/valeur de l’indicateur est passée dans *l’argument StrLen_or_Ind* dans **SQLPutData** et dans le tampon spécifié avec *l’argument StrLen_or_IndPtr* dans **SQLBindParameter**. Le tampon de données est spécifié avec l’argument *DataPtr* dans **SQLPutData** et *l’argument De ParameterValuePtr* dans **SQLBindParameter**.
