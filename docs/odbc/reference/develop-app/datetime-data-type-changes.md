---
description: Changements dans le type de données datetime
title: Modifications des types de données DateTime | Microsoft Docs
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
ms.openlocfilehash: a36339f275ff03584a3682f9f57eeeb8445faf3b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88424751"
---
# <a name="datetime-data-type-changes"></a>Changements dans le type de données datetime
Dans ODBC *3. x*, les identificateurs pour les types de données SQL date, Time et TIMESTAMP sont modifiés par rapport à SQL_DATE, SQL_TIME et SQL_TIMESTAMP (avec des instances de **#define** dans le fichier d’en-tête 9, 10 et 11) à SQL_TYPE_DATE, SQL_TYPE_TIME et SQL_TYPE_TIMESTAMP (avec des instances de **#define** dans le fichier d’en-tête 91, 92 et 93), respectivement. Les identificateurs de type C correspondants ont été modifiés de SQL_C_DATE, SQL_C_TIME et SQL_C_TIMESTAMP en SQL_C_TYPE_DATE, SQL_C_TYPE_TIME et SQL_C_TYPE_TIMESTAMP, respectivement.  
  
 La taille de colonne et les chiffres décimaux renvoyés pour les types de données DateTime SQL dans ODBC *3. x* sont les mêmes que la précision et l’échelle retournées pour eux dans ODBC *2. x*. Ces valeurs sont différentes de celles des champs de descripteur SQL_DESC_PRECISION et SQL_DESC_SCALE. (Pour plus d’informations, consultez [taille de colonne, chiffres décimaux, longueur d’octet de transfert et taille d’affichage](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md).)  
  
 Ces modifications affectent **SQLDescribeCol**, **SQLDescribeParam**et **SQLColAttribute**; **SQLBindCol**, **SQLBindParameter**et **SQLGetData**; et **SQLColumns**, **SQLGetTypeInfo**, **SQLProcedureColumns**, **SQLStatistics**et **SQLSpecialColumns**.  
  
 Le tableau suivant montre comment le gestionnaire de pilotes ODBC *3. x* effectue le mappage des types de données date, Time et timestamp C entrés dans les arguments *TargetType* de **SQLBindCol** et **SQLGetData** ou dans l’argument *ValueType* de **SQLBindParameter**.  
  
|Type de données<br /><br /> Code entré|application *2. x* à<br /><br /> pilote *2. x*|application *2. x* à<br /><br /> pilote *3. x*|application *3. x* à<br /><br /> pilote *2. x*|application *3. x* à<br /><br /> pilote *3. x*|  
|--------------------------------|-----------------------------------|-----------------------------------|-----------------------------------|-----------------------------------|  
|SQL_C_DATE (9)|Aucun mappage|SQL_C_TYPE_DATE (91)|Aucun mappage [1]|SQL_C_TYPE_DATE (91)|  
|SQL_C_TYPE_DATE (91)|Erreur (de DM)|Erreur (de DM)|SQL_C_DATE (9)|Aucun mappage [2]|  
|SQL_C_TIME (10)|Aucun mappage|SQL_C_TYPE_TIME (92)|Aucun mappage [1]|SQL_C_TYPE_TIME (92)|  
|SQL_C_TYPE_TIME (92)|Erreur (de DM)|Erreur (de DM)|SQL_C_TIME (10)|Aucun mappage [2]|  
|SQL_C_TIMESTAMP (11)|Aucun mappage|SQL_C_TYPE_TIMESTAMP (93)|Aucun mappage [1]|SQL_C_TYPE_TIMESTAMP (93)|  
|SQL_C_TYPE_TIMESTAMP (93)|Erreur (de DM)|Erreur (de DM)|SQL_C_TIMESTAMP (11)|Aucun mappage [2]|  
  
 [1] par conséquent, une application ODBC *3. x* utilisant un pilote ODBC *2. x* peut utiliser les codes de date, d’heure ou d’horodatage renvoyés dans les jeux de résultats qui sont retournés par les fonctions de catalogue.  
  
 [2] à la suite de cela, une application ODBC *3. x* qui utilise un pilote ODBC *3. x* peut utiliser les codes de date, d’heure ou d’horodatage retournés dans les jeux de résultats qui sont retournés par les fonctions de catalogue.  
  
 Le tableau suivant montre comment le gestionnaire de pilotes ODBC *3. x* effectue le mappage des types de données SQL date, Time et timestamp entrés dans l’argument *ParameterType* de **SQLBindParameter** ou dans l’argument *DataType* de **SQLGetTypeInfo**.  
  
|Type de données<br /><br /> Code entré|application *2. x* à<br /><br /> pilote *2. x*|application *2. x* à<br /><br /> pilote *3. x*|application *3. x* à<br /><br /> pilote *2. x*|application *3. x* à<br /><br /> pilote *3. x*|  
|--------------------------------|-----------------------------------|-----------------------------------|-----------------------------------|-----------------------------------|  
|SQL_DATE (9)|Aucun mappage|SQL_TYPE_DATE (91)|Aucun mappage [1]|SQL_TYPE_DATE (91)|  
|SQL_TYPE_DATE (91)|Erreur (de DM)|Erreur (de DM)|SQL_DATE (9)|Aucun mappage [2]|  
|SQL_TIME (10)|Aucun mappage|SQL_TYPE_TIME (92)|Aucun mappage [1]|SQL_TYPE_TIME (92)|  
|SQL_TYPE_TIME (92)|Erreur (de DM)|Erreur (de DM)|SQL_TIME (10)|Aucun mappage [2]|  
|SQL_TIMESTAMP (11)|Aucun mappage|SQL_TYPE_TIMESTAMP (93)|Aucun mappage [1]|SQL_TYPE_TIMESTAMP (93)|  
|SQL_TYPE_TIMESTAMP (93)|Erreur (de DM)|Erreur (de DM)|SQL_TIMESTAMP (11)|Aucun mappage [2]|  
  
 [1] par conséquent, une application ODBC *3. x* utilisant un pilote ODBC *2. x* peut utiliser les codes de date, d’heure ou d’horodatage renvoyés dans les jeux de résultats qui sont retournés par les fonctions de catalogue.  
  
 [2] à la suite de cela, une application ODBC *3. x* qui utilise un pilote ODBC *3. x* peut utiliser les codes de date, d’heure ou d’horodatage retournés dans les jeux de résultats qui sont retournés par les fonctions de catalogue.
