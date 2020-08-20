---
description: 'Étape 4b : Extraire le nombre de lignes'
title: 'Étape 4b : extraire le nombre de lignes | Microsoft Docs'
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
ms.openlocfilehash: 1eab5e1e1bf7eba70e2d84b36349e2f982a0b14c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88494602"
---
# <a name="step-4b-fetch-the-row-count"></a>Étape 4b : Extraire le nombre de lignes
L’étape suivante consiste à extraire le nombre de lignes, comme indiqué dans l’illustration suivante.  
  
 ![Présente l'extraction du nombre de lignes](../../../odbc/reference/develop-app/media/pr15.gif "pr15")  
  
 Si l’instruction exécutée à l’étape 3 était une instruction **Update**, **Delete**ou **Insert** , l’application récupère le nombre de lignes affectées avec **SQLRowCount**. Pour plus d’informations, consultez [détermination du nombre de lignes affectées](../../../odbc/reference/develop-app/determining-the-number-of-affected-rows.md).  
  
 L’application retourne maintenant à l’étape 3 pour exécuter une autre instruction dans la même transaction ou passe à l’étape 5 pour valider ou restaurer la transaction.
