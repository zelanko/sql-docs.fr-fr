---
title: Taille de colonne Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], column size
- size of data types [ODBC]
- SQL data types [ODBC], column characteristics
- column size of data types [ODBC]
ms.assetid: 541b83ab-b16d-4714-bcb2-3c3daa9a963b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 07b6151c723cb5e05189791100338e9e343c28aa
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306580"
---
# <a name="column-size"></a>Taille de colonne
La taille de la colonne (ou du paramètre) des types de données numériques est définie comme le nombre maximum de chiffres utilisés par le type de données de la colonne ou du paramètre, ou la précision des données. Pour les types de caractères, c’est la longueur des caractères des données; pour les types de données binaires, la taille de la colonne est définie comme la longueur des octets des données. Pour le temps, timetamp, et tous les types de données d’intervalle, c’est le nombre de caractères dans la représentation des personnages de ces données. La taille de la colonne définie pour chaque type de données SQL concise est indiquée dans le tableau suivant.  
  
|Identifiant de type SQL|Taille de colonne|  
|-------------------------|-----------------|  
|Tous les types de personnages[a],[b]|La taille définie ou maximale de la colonne dans les caractères de la colonne ou du paramètre (comme contenu dans le champ descripteur SQL_DESC_LENGTH). Par exemple, la taille de colonne d’une colonne de caractère unique définie comme CHAR(10) est de 10.|  
|SQL_DECIMAL SQL_NUMERIC|Le nombre défini de chiffres. Par exemple, la précision d’une colonne définie comme NUMERIC(10,3) est de 10.|  
|SQL_BIT[c]|1|  
|SQL_TINYINT[c]|3|  
|SQL_SMALLINT[c]|5|  
|SQL_INTEGER[c]|10|  
|SQL_BIGINT[c]|19 (s’il est signé) ou 20 (s’il n’est pas signé)|  
|SQL_REAL[c]|7|  
|SQL_FLOAT[c]|15|  
|SQL_DOUBLE[c]|15|  
|Tous les types binaires[a],[b]|La longueur définie ou maximale dans les octets de la colonne ou du paramètre. Par exemple, la longueur d’une colonne définie comme BINAIRE(10) est de 10.|  
|SQL_TYPE_DATE[c]|10 (le nombre de caractères dans le format *yyyy-mm-dd).*|  
|SQL_TYPE_TIME[c]|8 (le nombre de caractères dans le format *hh-mm-ss),* ou 9 *s* (le nombre de caractères dans *s* le *format hh:mm:ss*[.fff...]|  
|SQL_TYPE_TIMESTAMP|16 (le nombre de caractères dans le format *yyyy-mm-dd hh:mm)*<br /><br /> 19 (le nombre de caractères dans le *yyyy-mm-dd* *hh:mm:ss* format)<br /><br /> or<br /><br /> 20 *s* (le nombre de caractères dans le *yyyy-mm-dd hh:mm:ss*[.fff...] format, où *s* est la précision secondes).|  
|SQL_INTERVAL_SECOND|Là où *p* est la précision et le s de pointe *d’intervalle* est la précision secondes, *p* (si *s*'0) ou *p*+*s*'1 (si *s*>0). [d]|  
|SQL_INTERVAL_DAY_TO_SECOND|Là où *p* est la précision et le s de pointe *d’intervalle* est la précision des secondes, 9*p* (si *s*'0) ou 10 *'p*+*s* (si *s*>0). [d]|  
|SQL_INTERVAL_HOUR_TO_SECOND|Là où *p* est la précision et le s de pointe *d’intervalle* est la précision des secondes, 6*p* (si *s*'0) ou 7 *'p*+*s* (si *s>* 0). [d]|  
|SQL_INTERVAL_MINUTE_TO_SECOND|Là où *p* est la précision et le s de pointe *d’intervalle* est la précision des secondes, 3*p* (si *s*'0) ou 4 *'p*+*s* (si *s>* 0). [d]|  
|SQL_INTERVAL_YEAR SQL_INTERVAL_MONTH SQL_INTERVAL_DAY SQL_INTERVAL_HOUR SQL_INTERVAL_MINUTE|*p*, où *p* est l’intervalle de précision de tête. [d]|  
|SQL_INTERVAL_YEAR_TO_MONTH SQL_INTERVAL_DAY_TO_HOUR|3*p*, où *p* est la précision de tête d’intervalle. [d]|  
|SQL_INTERVAL_DAY_TO_MINUTE|6*p*, où *p* est la précision de tête d’intervalle. [d]|  
|SQL_INTERVAL_HOUR_TO_MINUTE|3*p*, où *p* est la précision de tête d’intervalle. [d]|  
|SQL_GUID|36 (le nombre de caractères dans le format *aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeeeee)*|  
  
 [a] Pour une application ODBC 1.0 appelant **SQLSetParam** dans un conducteur ODBC 2.0, et pour une application ODBC 2.0 appelant **SQLBindParameter** dans un conducteur ODBC 1.0, lorsque \* *StrLen_or_IndPtr* est SQL_DATA_AT_EXEC pour un type SQL_LONGVARCHAR ou SQL_LONGVARBINARY, *ColumnSize* doit être réglé à la longueur totale des données à envoyer, et non la précision telle que définie dans ce tableau.  
  
 [b] Si le conducteur ne peut pas déterminer la longueur de colonne ou de paramètre pour un type variable, il retourne SQL_NO_TOTAL.  
  
 [c] *L’argument de ColumnSize* de **SQLBindParameter** est ignoré pour ce type de données.  
  
 [d] Pour des règles générales sur la longueur de la colonne dans les types de données [d’intervalle,](../../../odbc/reference/appendixes/interval-data-type-length.md)voir Interval Data Type Length , plus tôt dans cette annexe.  
  
 Les valeurs retournées pour la taille de la colonne (ou du paramètre) ne correspondent pas aux valeurs d’un champ descripteur. Les valeurs peuvent provenir soit du SQL_DESC_PRECISION ou du champ SQL_DESC_LENGTH, selon le type de données, comme indiqué dans le tableau suivant.  
  
|Type SQL|Champ descripteur correspondant à<br /><br /> taille de colonne ou de paramètre|  
|--------------|--------------------------------------------------------------------|  
|Tous les types de caractère et binaires|LENGTH|  
|Tous les types numériques|PRECISION|  
|Tous les types de date et d’intervalle|LENGTH|  
|SQL_BIT|LENGTH|
