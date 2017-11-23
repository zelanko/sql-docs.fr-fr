---
title: "Étape 4 b : extraire le nombre de lignes | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- fetches [ODBC], fetching row count
- row count [ODBC]
- application process [ODBC], fetching row count
ms.assetid: 3af481b1-d694-446e-948d-e3a5edcad050
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 712cbde6925188096f2ef3dc4993a763517459f6
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="step-4b-fetch-the-row-count"></a>Étape 4 b : extraire le nombre de lignes
L’étape suivante consiste à extraire le nombre de lignes, comme indiqué dans l’illustration suivante.  
  
 ![Présente l’extraction du nombre de lignes](../../../odbc/reference/develop-app/media/pr15.gif "pr15")  
  
 Si l’instruction d’exécution à l’étape 3 a été un **mise à jour**, **supprimer**, ou **insérer** instruction, l’application récupère le nombre de lignes affectées avec **SQLRowCount**. Pour plus d’informations, consultez [déterminer le nombre de lignes affectées](../../../odbc/reference/develop-app/determining-the-number-of-affected-rows.md).  
  
 Maintenant, l’application retourne à l’étape 3 pour exécuter une autre instruction dans la même transaction ou passe à l’étape 5 pour valider ou annuler la transaction.
