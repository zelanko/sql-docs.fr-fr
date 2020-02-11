---
title: Précision du type de données Interval | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], interval data types
- precision [ODBC], interval data types
- seconds precision [ODBC]
- interval data type [ODBC], precision
- precision [ODBC]
- interval leading precision [ODBC]
- interval precision [ODBC]
ms.assetid: eb73bd77-2e7e-4498-a266-4d7c990a0d56
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3424c58d25be69d2ddc42a3088aa457ebddf1d4b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67947600"
---
# <a name="interval-data-type-precision"></a>Précision des types de données d’intervalle
La précision d’un type de données Interval comprend la précision d’intervalle, la précision de l’intervalle et la précision en secondes.  
  
 Le champ de début d’un intervalle est un nombre signé. Le nombre maximal de chiffres pour le champ de début est déterminé par une quantité appelée *précision de début d’intervalle,* qui fait partie de la déclaration de type de données. Par exemple, la déclaration : intervalle heure (5) à MINUTE a une précision d’intervalle de 5 ; le champ heure peut prendre des valeurs comprises entre-99999 et 99999. La précision de début de l’intervalle est contenue dans le champ SQL_DESC_DATETIME_INTERVAL_PRECISION de l’enregistrement du descripteur.  
  
 La liste des champs dont le type de données interval est composé est appelée précision de l' *intervalle*. Il ne s’agit pas d’une valeur numérique, comme le terme « précision » peut impliquer. Par exemple, la précision de l’intervalle de type jour à seconde est le jour de la liste, l’heure, la MINUTE, la seconde. Il n’existe aucun champ de descripteur qui contient cette valeur ; la précision de l’intervalle peut toujours être déterminée par le type de données Interval.  
  
 Tout type de données Interval ayant un deuxième champ a une *précision de secondes*. Il s’agit du nombre de chiffres décimaux autorisés dans la partie fractionnaire de la valeur des secondes. Cela est différent pour les autres types de données, où la précision indique le nombre de chiffres avant la virgule décimale. La précision en secondes d’un type de données interval est le nombre de chiffres après la virgule décimale. Par exemple, si la précision en secondes est définie sur 6, le nombre 123456 dans le champ fraction est interprété comme. 123456 et le nombre 1230 est interprété comme. 001230. Pour les autres types de données, il s’agit de l’échelle. La précision de l’intervalle en secondes est contenue dans le champ SQL_DESC_PRECISION du descripteur. Si la précision du composant fractions de seconde de la valeur de l’intervalle SQL est supérieure à celle qui peut être conservée dans la structure de l’intervalle C, elle est définie par le pilote, que la valeur fractions de seconde de l’intervalle SQL soit arrondie ou tronquée lorsqu’elle est convertie en C structure d’intervalle.  
  
 Lorsque le champ SQL_DESC_CONCISE_TYPE est défini sur un type de données Interval, le champ SQL_DESC_TYPE a la valeur SQL_INTERVAL et le SQL_DESC_DATETIME_INTERVAL_CODE est défini sur le code pour le type de données Interval. Le champ SQL_DESC_DATETIME_INTERVAL_PRECISION est automatiquement défini sur la précision d’intervalle par défaut de 2 et le champ SQL_DESC_PRECISION est automatiquement défini sur la précision par défaut de l’intervalle en secondes de 6. Si l’une de ces valeurs n’est pas appropriée, l’application doit définir explicitement le champ descripteur via un appel à **SQLSetDescField**.
