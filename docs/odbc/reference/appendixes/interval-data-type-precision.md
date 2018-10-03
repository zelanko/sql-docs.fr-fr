---
title: Précision du Type de données d’intervalle | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 98be3b4a7e4db30f394a2834364ecab9a20ef182
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47706427"
---
# <a name="interval-data-type-precision"></a>Précision des types de données d’intervalle
Précision pour un type de données d’intervalle inclut l’intervalle de début de précision, la précision de l’intervalle et la précision en.  
  
 Le champ début d’un intervalle est une valeur numérique signée. Le nombre maximal de chiffres pour le champ de début est déterminé par un nombre appelé *précision, interval* qui fait partie de la déclaration de type de données. Par exemple, la déclaration : intervalle HOUR(5) MINUTE a un intervalle de 5 ; la précision de début le champ d’heure peut prendre les valeurs à partir de –99999 et 99 999. La précision interval est contenue dans le champ SQL_DESC_DATETIME_INTERVAL_PRECISION de l’enregistrement de descripteur.  
  
 La liste des champs de type de données d’intervalle est constitué d’est appelée *précision de l’intervalle*. Il n’est pas une valeur numérique, comme l’implique le terme « précision ». Par exemple, la précision de l’intervalle du type INTERVAL DAY TO SECOND agit de la liste jour, heure, MINUTE, seconde. Il n’existe aucun champ de descripteur qui contient cette valeur ; la précision de l’intervalle peut toujours être déterminée par le type de données d’intervalle.  
  
 N’importe quel type de données d’intervalle qui a un deuxième champ a un *précision à la seconde*. Il s’agit du nombre de chiffres décimaux autorisés dans la partie fractionnaire de la valeur des secondes. Voici différente de celles d’autres types de données, où la précision indique le nombre de chiffres avant la virgule décimale. La précision en secondes d’un type de données d’intervalle est le nombre de chiffres après la virgule décimale. Par exemple, si la précision des secondes est définie sur 6, le nombre 123456 dans le champ de fraction serait interprété comme.123456 et le nombre 1230 seraient interprétées en tant que.001230. Pour les autres types de données, il est appelé mise à l’échelle. Précision de secondes d’intervalle est contenue dans le champ SQL_DESC_PRECISION du descripteur. Si la précision du composant fractions de secondes de la valeur d’intervalle SQL est supérieure à ce que peuvent être conservée dans la structure d’intervalle C, il est définies par le pilote si la valeur de fraction de seconde dans l’intervalle SQL est arrondie ou tronquée lorsque converti en C structure d’intervalle.  
  
 Lorsque le champ SQL_DESC_CONCISE_TYPE est défini pour un type de données d’intervalle, le champ SQL_DESC_TYPE a la valeur SQL_INTERVAL et la valeur SQL_DESC_DATETIME_INTERVAL_CODE est définie sur le code pour le type de données d’intervalle. Le champ SQL_DESC_DATETIME_INTERVAL_PRECISION est automatiquement défini à la précision de début intervalle par défaut de 2, et le SQL_DESC_PRECISION champ est automatiquement défini sur la précision de secondes d’intervalle par défaut de 6. Si une de ces valeurs n’est pas approprié, l’application doit définir explicitement le champ de descripteur via un appel à **SQLSetDescField**.
