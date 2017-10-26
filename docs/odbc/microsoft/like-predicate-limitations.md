---
title: "COMME les Limitations de prédicats | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- LIKE predicate limitations [ODBC]
- ODBC SQL grammar, LIKE predicate limitations
ms.assetid: dbd39099-caf6-4c4c-9ad8-f6c63c1bd5e4
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 5668f03e785c0d27133965f16af40ce69c2a2567
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="like-predicate-limitations"></a>COMME les Limitations de prédicats
Si les données d’une colonne sont supérieure à 255 caractères, la comparaison LIKE doit reposer uniquement sur les 255 premiers caractères.  
  
 Un type utilisé dans une procédure est pris en charge uniquement avec les modèles de constante. Les pilotes de la base de données Desktop prend en charge SQL-92 comme critères spéciaux.  
  
 Utilisation d’une clause d’échappement dans un prédicat LIKE n’est pas prise en charge.  
  
 Une comparaison LIKE ne doit pas être effectuée sur une colonne contenant les données d’un type de données numériques ou float. Les résultats peuvent être imprévisibles. Pour plus d’informations, consultez la *Guide du programmeur moteur Microsoft Jet de base de données*.

