---
title: 'C à SQL: Intervalles de mois d’année Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from c to SQL types [ODBC], year-month intervals
- intervals [ODBC], converting
- year-month intervals [ODBC]
- data conversions from C to SQL types [ODBC], year-month intervals
ms.assetid: a0eb7b55-9db0-4375-9210-bddec4593880
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2ec7bfda0015883c8470dd453c7ae5de9bfd6cec
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306610"
---
# <a name="c-to-sql-year-month-intervals"></a>C en SQL : Intervalles d’années-mois
Les identificateurs pour l’intervalle d’un mois ODBC C types de données sont les :  
  
 SQL_C_INTERVAL_MONTH SQL_C_INTERVAL_YEAR SQL_C_INTERVAL_YEAR_TO_MONTH  
  
 Le tableau suivant montre les types de données SQL ODBC auxquels les données d’intervalle C peuvent être converties pendant l’année. Pour une explication des colonnes et des termes dans le tableau, voir [convertir les données de C à SQL Data Types](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|Identifiant de type SQL|Test|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR[a]<br /><br /> SQL_VARCHAR[a]<br /><br /> SQL_LONGVARCHAR[a]|Longueur d’ente de colonne >- Longueur d’ente de caractère<br /><br /> Longueur d’ente de colonne < longueur d’ente de caractère[a]<br /><br /> La valeur des données n’est pas un intervalle littéral valide|n/a<br /><br /> 22001<br /><br /> 22015|  
|SQL_WCHAR[a]<br /><br /> SQL_WVARCHAR[a]<br /><br /> SQL_WLONGVARCHAR[a]|Longueur de caractère de colonne >- Longueur de caractère des données<br /><br /> Longueur de caractère de colonne < longueur de caractère des données[a]<br /><br /> La valeur des données n’est pas un intervalle littéral valide|n/a<br /><br /> 22001<br /><br /> 22015|  
|SQL_TINYINT[b]<br /><br /> SQL_SMALLINT[b]<br /><br /> SQL_INTEGER[b]<br /><br /> SQL_BIGINT[b]<br /><br /> SQL_NUMERIC[b]<br /><br /> SQL_DECIMAL[b]|La conversion d’un intervalle d’un seul champ n’a pas entraîné la troncation de chiffres entiers<br /><br /> La conversion a abouti à la troncation de chiffres entiers|n/a<br /><br /> 22003|  
|SQL_INTERVAL_MONTH<br /><br /> SQL_INTERVAL_YEAR<br /><br /> SQL_INTERVAL_YEAR_TO_MONTH|La valeur des données a été convertie sans troncation de champs<br /><br /> Un ou plusieurs champs de valeur de données ont été tronqués lors de la conversion|n/a<br /><br /> 22015|  
  
 [a] Tous les types de données d’intervalle C peuvent être convertis en un type de données de caractère.  
  
 [b] Si le champ de type dans la structure d’intervalle est tel que l’intervalle est un champ unique (SQL_YEAR ou SQL_MONTH), le type d’intervalle C peut être converti en n’importe quel numérique exact (SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, SQL_BIGINT, SQL_DECIMAL, ou SQL_NUMERIC).  
  
 La conversion par défaut d’un type d’intervalle C est du type SQL d’intervalle correspondant d’un mois d’année.  
  
 Le conducteur ignore la valeur de longueur/indicateur lors de la conversion des données à partir du type de données d’intervalle C et suppose que la taille du tampon de données est la taille du type de données d’intervalle C. La durée/valeur de l’indicateur est passée dans *l’argument StrLen_or_Ind* dans **SQLPutData** et dans le tampon spécifié avec *l’argument StrLen_or_IndPtr* dans **SQLBindParameter**. Le tampon de données est spécifié avec l’argument *DataPtr* dans **SQLPutData** et *l’argument De ParameterValuePtr* dans **SQLBindParameter**.
