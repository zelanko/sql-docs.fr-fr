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
manager: craigg
ms.openlocfilehash: 8035eed9e0aaff1f914f386b6d4bc9f2d65f9a0f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47652972"
---
# <a name="like-predicate-limitations"></a>LIKE, prédicat - limitations
Si les données dans une colonne sont supérieure à 255 caractères, la comparaison LIKE doit reposer uniquement sur les 255 premiers caractères.  
  
 Un type utilisé dans une procédure est prise en charge uniquement avec les modèles de constante. Les pilotes de base de données Desktop prend en charge SQL-92 comme critères spéciaux.  
  
 Utilisation d’une clause d’échappement dans un prédicat LIKE n’est pas prise en charge.  
  
 Une comparaison LIKE ne doit pas être effectuée sur une colonne contenant les données d’un type de données numériques ou float. Les résultats peuvent être imprévisibles. Pour plus d’informations, consultez le *-Guide du programmeur moteur Microsoft Jet de base de données*.
