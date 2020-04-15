---
title: 'C à SQL: Numeric Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- numeric data type [ODBC], converting
- data conversions from C to SQL types [ODBC], numeric
- converting data from c to SQL types [ODBC], numeric
ms.assetid: af4095ff-06c3-4b04-83bf-19f9ee098dc2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bbc0a994ef95f2deca29c8a4cbb06f3167b0433f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304730"
---
# <a name="c-to-sql-numeric"></a>C en SQL : Numérique
Les identificateurs pour les types de données numériques ODBC C sont les :  
  
 SQL_C_STINYINT  
  
 SQL_C_SLONG  
  
 SQL_C_UTINYINT  
  
 SQL_C_ULONG  
  
 SQL_C_TINYINT  
  
 SQL_C_LONG  
  
 SQL_C_SSHORT  
  
 SQL_C_FLOAT  
  
 SQL_C_USHORT  
  
 SQL_C_DOUBLE  
  
 SQL_C_SHORT  
  
 SQL_C_NUMERIC  
  
 SQL_C_SBIGINT  
  
 SQL_C_UBIGINT  
  
 Le tableau suivant montre les types de données SQL ODBC auxquels les données numériques C peuvent être converties. Pour une explication des colonnes et des termes dans le tableau, voir [convertir les données de C à SQL Data Types](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|Identifiant de type SQL|Test|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|Nombre de chiffres <' Longueur d’byte de colonne<br /><br /> Nombre de chiffres > longueur d’ente de colonne|n/a<br /><br /> 22001|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|Nombre de caractères <' Longueur de caractère de colonne<br /><br /> Nombre de caractères > longueur de caractère de colonne|n/a<br /><br /> 22001|  
|SQL_DECIMAL[b]<br /><br /> SQL_NUMERIC[b]<br /><br /> SQL_TINYINT[b]<br /><br /> SQL_SMALLINT[b]<br /><br /> SQL_INTEGER[b]<br /><br /> SQL_BIGINT[b]|Données converties sans troncation ou tronquées de chiffres fractionnaires<br /><br /> Données converties avec troncation de chiffres entiers|n/a<br /><br /> 22003|  
|SQL_REAL<br /><br /> SQL_FLOAT<br /><br /> SQL_DOUBLE|Les données se situent dans la plage du type de données auquel le nombre est converti<br /><br /> Les données sont en dehors de la plage du type de données à laquelle le nombre est converti|n/a<br /><br /> 22003|  
|SQL_BIT|Les données sont de 0 ou 1<br /><br /> Les données sont supérieures à 0, moins de 2, et n’égalent pas 1<br /><br /> Les données sont inférieures à 0 ou plus ou égales à 2|n/a<br /><br /> 22001<br /><br /> 22003|  
|SQL_INTERVAL_YEAR[a]<br /><br /> SQL_INTERVAL_MONTH[a]<br /><br /> SQL_INTERVAL_DAY[a]<br /><br /> SQL_INTERVAL_HOUR[a]<br /><br /> SQL_INTERVAL_MINUTE[a]<br /><br /> SQL_INTERVAL_SECOND[a]|Données non tronquées.<br /><br /> Données tronquées.|n/a<br /><br /> 22015|  
  
 [a] Ces conversions ne sont prises en charge que pour les types exacts de données numériques (SQL_C_STINYINT, SQL_C_UTINYINT, SQL_C_SSHORT, SQL_C_USHORT, SQL_C_SLONG, SQL_C_ULONG ou SQL_C_NUMERIC). Ils ne sont pas pris en charge pour les types de données numériques approximatives (SQL_C_FLOAT ou SQL_C_DOUBLE). Les types de données numériques C exactes ne peuvent pas être convertis en un type SQL d’intervalle dont la précision d’intervalle n’est pas un seul champ.  
  
 [b] Pour le cas « n/a », un conducteur peut retourner d’option SQL_SUCCESS_WITH_INFO et 01S07 lorsqu’il y a une troncation fractionnaire.  
  
 Le conducteur ignore la valeur de longueur/indicateur lors de la conversion des données à partir des types de données numériques C et suppose que la taille du tampon de données est la taille du type de données numérique C. La durée/valeur de l’indicateur est passée dans *l’argument StrLen_or_Ind* dans **SQLPutData** et dans le tampon spécifié avec *l’argument StrLen_or_IndPtr* dans **SQLBindParameter**. Le tampon de données est spécifié avec l’argument *DataPtr* dans **SQLPutData** et *l’argument De ParameterValuePtr* dans **SQLBindParameter**.
