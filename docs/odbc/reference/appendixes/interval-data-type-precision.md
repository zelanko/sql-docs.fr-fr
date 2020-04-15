---
title: Précision de type de données d’intervalle (en anglais) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 746293c545c47917abd084ec3eb105051fc2fbcf
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81290739"
---
# <a name="interval-data-type-precision"></a>Précision des types de données d’intervalle
La précision pour un type de données d’intervalle inclut la précision de tête d’intervalle, la précision d’intervalle, et la précision de secondes.  
  
 Le champ de tête d’un intervalle est un numérique signé. Le nombre maximum de chiffres pour le champ de tête est déterminé par une quantité appelée *précision de tête d’intervalle,* qui fait partie de la déclaration de type de données. Par exemple, la déclaration: INTERVAL HOUR(5) TO MINUTE a un intervalle de précision de 5; le champ HOUR peut prendre des valeurs de -99999 à 99999. La précision de tête d’intervalle est contenue dans le champ SQL_DESC_DATETIME_INTERVAL_PRECISION de l’enregistrement descripteur.  
  
 La liste des champs dont un type de données d’intervalle est composé est appelée *précision d’intervalle.* Il ne s’agit pas d’une valeur numérique, comme le terme « précision » pourrait l’impliquer. Par exemple, la précision d’intervalle du type INTERVAL DAY TO SECOND est la liste DAY, HOUR, MINUTE, SECOND. Il n’y a pas de champ descripteur qui détient cette valeur; la précision d’intervalle peut toujours être déterminée par le type de données d’intervalle.  
  
 Tout type de données d’intervalle qui a un champ SECOND a une *précision secondes*. C’est le nombre de chiffres décimaux autorisés dans la partie fractionnaire de la valeur des secondes. Ceci est différent de celui d’autres types de données, où la précision indique le nombre de chiffres avant le point décimal. La précision secondes d’un type de données d’intervalle est le nombre de chiffres après le point décimal. Par exemple, si la précision des secondes est réglée à 6, le nombre 123456 dans le champ fractionnaire serait interprété comme .123456 et le nombre 1230 serait interprété comme .001230. Pour d’autres types de données, c’est ce qu’on appelle l’échelle. La précision des secondes d’intervalle est contenue dans le champ SQL_DESC_PRECISION du descripteur. Si la précision du composant fractionnaire des secondes de la valeur d’intervalle SQL est supérieure à ce qui peut être maintenu dans la structure d’intervalle C, il est défini par le conducteur si la valeur fractionnelle des secondes dans l’intervalle SQL est arrondie ou tronquée lorsqu’elle est convertie en structure d’intervalle C.  
  
 Lorsque le champ SQL_DESC_CONCISE_TYPE est réglé sur un type de données d’intervalle, le champ SQL_DESC_TYPE est réglé pour SQL_INTERVAL et le SQL_DESC_DATETIME_INTERVAL_CODE est réglé sur le code pour le type de données d’intervalle. Le champ SQL_DESC_DATETIME_INTERVAL_PRECISION est automatiquement réglé à l’intervalle par défaut menant la précision de 2, et le champ SQL_DESC_PRECISION est automatiquement réglé à la précision des secondes d’intervalle par défaut de 6. Si l’une ou l’autre de ces valeurs n’est pas appropriée, l’application doit explicitement définir le champ descripteur par un appel à **SQLSetDescField**.
