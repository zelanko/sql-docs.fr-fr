---
title: Diagnostics | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC]
- functions [ODBC], diagnostic information
- diagnostic information [ODBC], about diagnostic information
ms.assetid: 450abd88-90a1-4fbc-b417-8efbdd8e1dea
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bd6640c0dc06d9e957176717ef26aa3e444ffa9f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68022522"
---
# <a name="diagnostics"></a>Diagnostics
Dans ODBC, les fonctions renvoient des informations de diagnostic de deux manières. Le code de retour indique le succès ou l’échec global de la fonction, tandis que les enregistrements de diagnostic fournissent des informations détaillées sur la fonction. Au moins un enregistrement de diagnostic-l’enregistrement d’en-tête-est retourné même si la fonction réussit.  
  
 Les informations de diagnostic sont utilisées au moment du développement pour intercepter les erreurs de programmation telles que les handles non valides et les erreurs de syntaxe dans les instructions SQL codées en dur. Il est utilisé au moment de l’exécution pour intercepter les erreurs d’exécution et les avertissements tels que la troncation des données, les violations d’accès et les erreurs de syntaxe dans les instructions SQL entrées par l’utilisateur.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Codes de retour](../../../odbc/reference/develop-app/return-codes-odbc.md)  
  
-   [Enregistrements de diagnostic](../../../odbc/reference/develop-app/diagnostic-records.md)  
  
-   [Utilisation de SQLGetDiagRec et de SQLGetDiagField](../../../odbc/reference/develop-app/using-sqlgetdiagrec-and-sqlgetdiagfield.md)  
  
-   [Implémentation de SQLGetDiagRec et de SQLGetDiagField](../../../odbc/reference/develop-app/implementing-sqlgetdiagrec-and-sqlgetdiagfield.md)  
  
-   [Exemples de gestion des diagnostics](../../../odbc/reference/develop-app/diagnostic-handling-examples.md)
