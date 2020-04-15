---
title: Chiffres décimaux - France Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- size of data types [ODBC]
- decimal digits of data types [ODBC]
- data types [ODBC], decimal digits
- SQL data types [ODBC], column characteristics
ms.assetid: 07f3d1fc-b4ee-4693-b342-330b2231b6d0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4921a6162b6d711e657f223b5be5783dfa37bca8
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285159"
---
# <a name="decimal-digits"></a>Nombres décimaux
Les *chiffres décimaux* des types décimaux et numériques de données sont définis comme le nombre maximal de chiffres à droite du point décimal, ou l’échelle des données. Pour les colonnes ou paramètres de nombres flottants approximatifs, l’échelle n’est pas définie parce que le nombre de chiffres à droite du point décimal n’est pas fixé. Pour les données de date ou d’intervalle qui contiennent un composant de secondes, les chiffres décimaux sont définis comme le nombre de chiffres à droite du point décimal dans le composant secondes des données.  
  
 Pour les types de données SQL_DECIMAL et SQL_NUMERIC, l’échelle maximale est généralement la même que la précision maximale. Toutefois, certaines sources de données imposent une limite distincte à l’échelle maximale. Pour déterminer les échelles minimales et maximales autorisées pour un type de données, une application appelle **SQLGetTypeInfo**.  
  
 Les chiffres décimaux définis pour chaque type de données SQL concis sont indiqués dans le tableau suivant.  
  
|Type SQL|des chiffres décimaux|  
|--------------|--------------------|  
|Tous les caractères et les types binaires[a]|n/a|  
|SQL_DECIMAL<br />SQL_NUMERIC|Le nombre défini de chiffres à droite du point décimal. Par exemple, l’échelle d’une colonne définie comme NUMERIC(10,3) est de 3. Cela peut être un nombre négatif pour soutenir le stockage de très grand nombre sans utiliser la notation exponentielle; par exemple, "12000" pourrait être stocké comme "12" avec une échelle de -3.|  
|Tous les types numériques exacts autres que les SQL_DECIMAL et SQL_NUMERIC[a]|0|  
|Tous les types de données approximatives[a]|n/a|  
|SQL_TYPE_DATE, et tous les types d’intervalle sans composant secondes[a]|n/a|  
|Tous les types de datetime, sauf SQL_TYPE_DATE, et tous les types d’intervalle avec un composant de secondes|Le nombre de chiffres à droite du point décimal dans la partie secondes de la valeur (fractions de secondes). Ce nombre ne peut pas être négatif.|  
|SQL_GUID|n/a|  
  
 [a] *L’argument DecimalDigits* de **SQLBindParameter** est ignoré pour ce type de données.  
  
 Les valeurs retournées pour les chiffres décimaux ne correspondent pas aux valeurs dans un domaine descripteur. Les valeurs peuvent provenir soit du SQL_DESC_SCALE ou du champ SQL_DESC_PRECISION, selon le type de données, comme indiqué dans le tableau suivant.  
  
|Type SQL|Champ descripteur correspondant à<br /><br /> Décimaux|  
|--------------|----------------------------------------------------------|  
|Tous les types de caractère et binaires|n/a|  
|Tous les types numériques exacts|SCALE|  
|SQL_BIT|n/a|  
|Tous les types numériques approximatifs|n/a|  
|Tous les types de date time|PRECISION|  
|Tous les types d’intervalle avec un composant de secondes|PRECISION|  
|Tous les types d’intervalle sans composant de secondes|n/a|
