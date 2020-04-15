---
title: Modifications de type de données date time (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- time data type [ODBC]
- datetime data types [ODBC]
- date data type [ODBC]
- backward compatibility [ODBC], datetime data types
- timestamp data type [ODBC]
- compatibility [ODBC], datetime data types
ms.assetid: c38c79f9-8bb0-4633-ac86-542366c09a95
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4f186047dd31aa2c4b66ec1ce73c8cb9fae31c04
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304642"
---
# <a name="datetime-data-type-changes"></a>Changements dans le type de données datetime
Dans ODBC *3.x*, les identificateurs pour la date, les types de données SQL de temps, et de temps en retard sont passés de SQL_DATE, SQL_TIME et SQL_TIMESTAMP (avec des cas de **#define** dans le fichier d’en-tête de 9, 10 et 11) à SQL_TYPE_DATE, SQL_TYPE_TIME et SQL_TYPE_TIMESTAMP (avec des cas de **#define** dans le fichier d’en-tête de 91, 92 et 93), respectivement. Les identificateurs de type C correspondants sont passés de SQL_C_DATE, SQL_C_TIME et SQL_C_TIMESTAMP à SQL_C_TYPE_DATE, SQL_C_TYPE_TIME et SQL_C_TYPE_TIMESTAMP, respectivement.  
  
 La taille de la colonne et les chiffres décimaux retournés pour les types de données SQL datetime dans ODBC *3.x* sont les mêmes que la précision et l’échelle retournée pour eux dans ODBC *2.x*. Ces valeurs sont différentes des valeurs des champs de SQL_DESC_PRECISION et de SQL_DESC_SCALE descripteur. (Pour plus d’informations, voir [Taille de colonne, chiffres décimaux, Longueur Octet transfert, et taille d’affichage](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md).)  
  
 Ces changements affectent **SQLDescribeCol**, **SQLDescribeParam**, et **SQLColAttribute**; **SQLBindCol**, **SQLBindParameter**, et **SQLGetData**; et **SQLColumns**, **SQLGetTypeInfo**, **SQLProcedureColumns**, **SQLStatistics**, et **SQLSpecialColumns**.  
  
 Le tableau suivant montre comment l’ODBC *3.x* Driver Manager effectue la cartographie de la date, de l’heure et des types de données timetamp C entrés dans les arguments *targetType* de **SQLBindCol** et **SQLGetData** ou dans l’argument *ValueType* de **SQLBindParameter**.  
  
|Type de données<br /><br /> code entré|*2.x* application à<br /><br /> *2.x* conducteur|*2.x* application à<br /><br /> *3.x* conducteur|*application 3.x* à<br /><br /> *2.x* conducteur|*application 3.x* à<br /><br /> *3.x* conducteur|  
|--------------------------------|-----------------------------------|-----------------------------------|-----------------------------------|-----------------------------------|  
|SQL_C_DATE (9)|Pas de cartographie|SQL_C_TYPE_DATE (91)|Pas de cartographie[1]|SQL_C_TYPE_DATE (91)|  
|SQL_C_TYPE_DATE (91)|Erreur (de DM)|Erreur (de DM)|SQL_C_DATE (9)|Pas de cartographie[2]|  
|SQL_C_TIME (10)|Pas de cartographie|SQL_C_TYPE_TIME (92)|Pas de cartographie[1]|SQL_C_TYPE_TIME (92)|  
|SQL_C_TYPE_TIME (92)|Erreur (de DM)|Erreur (de DM)|SQL_C_TIME (10)|Pas de cartographie[2]|  
|SQL_C_TIMESTAMP (11)|Pas de cartographie|SQL_C_TYPE_TIMESTAMP (93)|Pas de cartographie[1]|SQL_C_TYPE_TIMESTAMP (93)|  
|SQL_C_TYPE_TIMESTAMP (93)|Erreur (de DM)|Erreur (de DM)|SQL_C_TIMESTAMP (11)|Pas de cartographie[2]|  
  
 [1] À la suite de cela, une application ODBC *3.x* travaillant avec un pilote ODBC *2.x* peut utiliser les codes de date, d’heure ou de timetamp retournés dans les ensembles de résultat qui sont retournés par les fonctions de catalogue.  
  
 [2] À la suite de cela, une application ODBC *3.x* travaillant avec un pilote ODBC *3.x* peut utiliser les codes de date, d’heure ou de timetamp retournés dans les ensembles de résultat qui sont retournés par les fonctions de catalogue.  
  
 Le tableau suivant montre comment l’ODBC *3.x* Driver Manager effectue la cartographie de la date, de l’heure et des types de données SQL horaires entrés dans *l’argument de ParameterType* de **SQLBindParameter** ou dans l’argument *DataType* de **SQLGetTypeInfo**.  
  
|Type de données<br /><br /> code entré|*2.x* application à<br /><br /> *2.x* conducteur|*2.x* application à<br /><br /> *3.x* conducteur|*application 3.x* à<br /><br /> *2.x* conducteur|*application 3.x* à<br /><br /> *3.x* conducteur|  
|--------------------------------|-----------------------------------|-----------------------------------|-----------------------------------|-----------------------------------|  
|SQL_DATE (9)|Pas de cartographie|SQL_TYPE_DATE (91)|Pas de cartographie[1]|SQL_TYPE_DATE (91)|  
|SQL_TYPE_DATE (91)|Erreur (de DM)|Erreur (de DM)|SQL_DATE (9)|Pas de cartographie[2]|  
|SQL_TIME (10)|Pas de cartographie|SQL_TYPE_TIME (92)|Pas de cartographie[1]|SQL_TYPE_TIME (92)|  
|SQL_TYPE_TIME (92)|Erreur (de DM)|Erreur (de DM)|SQL_TIME (10)|Pas de cartographie[2]|  
|SQL_TIMESTAMP (11)|Pas de cartographie|SQL_TYPE_TIMESTAMP (93)|Pas de cartographie[1]|SQL_TYPE_TIMESTAMP (93)|  
|SQL_TYPE_TIMESTAMP (93)|Erreur (de DM)|Erreur (de DM)|SQL_TIMESTAMP (11)|Pas de cartographie[2]|  
  
 [1] À la suite de cela, une application ODBC *3.x* travaillant avec un pilote ODBC *2.x* peut utiliser les codes de date, d’heure ou de timetamp retournés dans les ensembles de résultat qui sont retournés par les fonctions de catalogue.  
  
 [2] À la suite de cela, une application ODBC *3.x* travaillant avec un pilote ODBC *3.x* peut utiliser les codes de date, d’heure ou de timetamp retournés dans les ensembles de résultat qui sont retournés par les fonctions de catalogue.
