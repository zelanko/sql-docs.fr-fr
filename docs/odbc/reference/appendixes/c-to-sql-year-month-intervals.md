---
title: 'C en SQL : Intervalles d’années-mois | Microsoft Docs'
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d12727f9298eb63fe10b44c48b9d3b7996a839d5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63159282"
---
# <a name="c-to-sql-year-month-intervals"></a>C en SQL : Intervalles d’années-mois
Les identificateurs pour les types de données ODBC C intervalle année-mois sont :  
  
 SQL_C_INTERVAL_MONTH SQL_C_INTERVAL_YEAR SQL_C_INTERVAL_YEAR_TO_MONTH  
  
 Le tableau suivant présente les types de données à partir de quel mois-année des données d’intervalle C peuvent être converties à ODBC SQL. Pour obtenir une explication des colonnes et des termes dans la table, consultez [conversion des données à partir de C en Types de données SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|Identificateur de type SQL|Test|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR[a]<br /><br /> SQL_VARCHAR[a]<br /><br /> SQL_LONGVARCHAR[a]|Longueur d’octet de colonne > = longueur d’octet de caractère<br /><br /> Longueur d’octet de colonne < caractères de longueur d’octet [a]<br /><br /> Valeur de données n’est pas un littéral d’intervalle valide|n/a<br /><br /> 22001<br /><br /> 22015|  
|SQL_WCHAR[a]<br /><br /> SQL_WVARCHAR[a]<br /><br /> SQL_WLONGVARCHAR[a]|Longueur de colonne caractère > = longueur de caractères de données<br /><br /> Longueur de colonne caractère < caractères de longueur des données [a]<br /><br /> Valeur de données n’est pas un littéral d’intervalle valide|n/a<br /><br /> 22001<br /><br /> 22015|  
|SQL_TINYINT[b]<br /><br /> SQL_SMALLINT[b]<br /><br /> SQL_INTEGER[b]<br /><br /> SQL_BIGINT[b]<br /><br /> SQL_NUMERIC[b]<br /><br /> SQL_DECIMAL[b]|Conversion d’un intervalle de champ unique n’a pas abouti à la troncation des chiffres entières<br /><br /> La conversion a provoqué une troncation de chiffres entières|n/a<br /><br /> 22003|  
|SQL_INTERVAL_MONTH<br /><br /> SQL_INTERVAL_YEAR<br /><br /> SQL_INTERVAL_YEAR_TO_MONTH|Valeur de données a été convertie sans troncation de tous les champs<br /><br /> Un ou plusieurs champs de valeur de données ont été tronquées lors de la conversion|n/a<br /><br /> 22015|  
  
 [a] C tous les types d’intervalle peuvent être converti en un type de données caractère.  
  
 [b] si le champ de type dans la structure de l’intervalle est telle que l’intervalle est un champ unique (SQL_YEAR ou SQL_MONTH), le type d’intervalle C peut être converti en n’importe quel type numérique exacte (SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, SQL_BIGINT, SQL_DECIMAL ou SQL_NUMERIC).  
  
 La conversion par défaut d’un intervalle de type C est à l’intervalle d’années-mois type SQL correspondant.  
  
 Le pilote ignore la valeur de longueur/indicateur lors de la conversion des données à partir du type de données d’intervalle C et suppose que la taille du tampon de données est la taille du type de données d’intervalle C. La valeur de longueur / d’indicateur est passée dans le *StrLen_or_Ind* argument dans **SQLPutData** et dans la mémoire tampon spécifiée avec la *StrLen_or_IndPtr* argument dans **SQLBindParameter**. Le tampon de données est spécifié avec la *DataPtr* argument dans **SQLPutData** et *ParameterValuePtr* argument dans **SQLBindParameter**.
