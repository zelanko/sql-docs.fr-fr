---
title: "COMME les Limitations de prédicats | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- LIKE predicate limitations [ODBC]
- ODBC SQL grammar, LIKE predicate limitations
ms.assetid: dbd39099-caf6-4c4c-9ad8-f6c63c1bd5e4
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4cb55109261fee419af8bd0773ed8e85956e8ca9
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="like-predicate-limitations"></a>COMME les Limitations de prédicats
Si les données d’une colonne sont supérieure à 255 caractères, la comparaison LIKE doit reposer uniquement sur les 255 premiers caractères.  
  
 Un type utilisé dans une procédure est pris en charge uniquement avec les modèles de constante. Les pilotes de la base de données Desktop prend en charge SQL-92 comme critères spéciaux.  
  
 Utilisation d’une clause d’échappement dans un prédicat LIKE n’est pas prise en charge.  
  
 Une comparaison LIKE ne doit pas être effectuée sur une colonne contenant les données d’un type de données numériques ou float. Les résultats peuvent être imprévisibles. Pour plus d’informations, consultez la *Guide du programmeur moteur Microsoft Jet de base de données*.
