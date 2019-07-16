---
title: Chiffres décimaux | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6e58551ae3c6edda3cd865817223fd8052d03ec5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68130054"
---
# <a name="decimal-digits"></a>Nombres décimaux
Le *chiffres décimaux* de données decimal et numeric types est défini comme le nombre maximal de chiffres à droite de la virgule décimale, ou à l’échelle des données. Pour les colonnes de nombres à virgule flottante approximatifs ou de paramètres, l’échelle est non définie, car le nombre de chiffres à droite de la virgule décimale n’est pas fixe. Pour les données datetime ou interval qui contient un composant « secondes », les chiffres décimaux est défini comme le nombre de chiffres à droite de la virgule décimale dans le composant « secondes » des données.  
  
 Pour les types de données SQL_DECIMAL et SQL_NUMERIC, l’échelle maximale est généralement identique à la précision maximale. Toutefois, certaines sources de données imposent une limite distincte sur l’échelle maximale. Pour déterminer les échelles minimales et maximales autorisées pour un type de données, une application appelle **SQLGetTypeInfo**.  
  
 Les chiffres décimaux définis pour chaque type de données SQL concis est indiqué dans le tableau suivant.  
  
|Type SQL|Chiffres décimaux|  
|--------------|--------------------|  
|Tous les types caractères et binaires [a]|N/A|  
|SQL_DECIMAL<br />SQL_NUMERIC|Le nombre défini de chiffres à droite de la virgule décimale. Par exemple, l’échelle d’une colonne définie en tant que NUMERIC(10,3) est 3. Cela peut être un nombre négatif pour prendre en charge le stockage de très grands nombres sans utiliser de notation exponentielle ; par exemple, « 12000 » peuvent être stockées en tant que « 12 » avec une échelle de -3.|  
|Tous les types numériques exacts autres que SQL_DECIMAL et SQL_NUMERIC [a]|0|  
|Tous les types de données approximatifs [a]|N/A|  
|SQL_TYPE_DATE et tous les types d’intervalle avec aucun composant « secondes » [a]|N/A|  
|Tous les types de date/heure sauf SQL_TYPE_DATE et tous les types d’intervalle avec un composant « secondes »|Le nombre de chiffres à droite de la virgule décimale dans la partie secondes de la valeur (en fractions de seconde). Ce nombre ne peut pas être négatif.|  
|SQL_GUID|N/A|  
  
 [a] le *DecimalDigits* argument de **SQLBindParameter** est ignorée pour ce type de données.  
  
 Les valeurs retournées pour les chiffres décimaux ne correspondent pas aux valeurs dans n’importe quel champ de descripteur un. Les valeurs peuvent provenir de la SQL_DESC_SCALE ou le champ SQL_DESC_PRECISION, selon le type de données, comme indiqué dans le tableau suivant.  
  
|Type SQL|Champ de descripteur correspondant à<br /><br /> Chiffres décimaux|  
|--------------|----------------------------------------------------------|  
|Tous les types caractères et binaires|N/A|  
|Tous les types numériques exacts|SCALE|  
|SQL_BIT|N/A|  
|Tous les types numériques approximatifs|N/A|  
|Tous les types de date/heure|PRECISION|  
|Tous les types d’intervalle avec un composant « secondes »|PRECISION|  
|Tous les types d’intervalle avec aucun composant « secondes »|N/A|
