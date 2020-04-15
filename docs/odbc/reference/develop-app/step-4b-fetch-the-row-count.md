---
title: 'Étape 4b: Aller chercher le compte de ligne Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- fetches [ODBC], fetching row count
- row count [ODBC]
- application process [ODBC], fetching row count
ms.assetid: 3af481b1-d694-446e-948d-e3a5edcad050
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 31ccbd15ae435165ea007fa9f3c0505c1dcc5aa0
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302960"
---
# <a name="step-4b-fetch-the-row-count"></a>Étape 4b : Extraire le nombre de lignes
L’étape suivante consiste à aller chercher le nombre de rangées, comme le montre l’illustration suivante.  
  
 ![Présente l'extraction du nombre de lignes](../../../odbc/reference/develop-app/media/pr15.gif "pr15")  
  
 Si la déclaration exécutée dans l’étape 3 était une **mise À JOUR**, **SUPPRIMER**, ou **INSERT** déclaration, l’application récupère le nombre de lignes touchées avec **SQLRowCount**. Pour plus d’informations, voir [Déterminer le nombre de lignes touchées](../../../odbc/reference/develop-app/determining-the-number-of-affected-rows.md).  
  
 L’application revient maintenant à l’étape 3 pour exécuter une autre déclaration dans la même transaction ou produit à l’étape 5 pour valider ou annuler la transaction.
