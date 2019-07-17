---
title: COMME prédicat-Limitations | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- LIKE predicate limitations [ODBC]
- ODBC SQL grammar, LIKE predicate limitations
ms.assetid: dbd39099-caf6-4c4c-9ad8-f6c63c1bd5e4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8cd3cebfcf20df2f8a3a786ea66fd28dd76307c0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68119707"
---
# <a name="like-predicate-limitations"></a>LIKE, prédicat - limitations
Si les données dans une colonne sont supérieure à 255 caractères, la comparaison LIKE doit reposer uniquement sur les 255 premiers caractères.  
  
 Un type utilisé dans une procédure est prise en charge uniquement avec les modèles de constante. Les pilotes de base de données Desktop prend en charge SQL-92 comme critères spéciaux.  
  
 Utilisation d’une clause d’échappement dans un prédicat LIKE n’est pas prise en charge.  
  
 Une comparaison LIKE ne doit pas être effectuée sur une colonne contenant les données d’un type de données numériques ou float. Les résultats peuvent être imprévisibles. Pour plus d’informations, consultez le *-Guide du programmeur moteur Microsoft Jet de base de données*.
