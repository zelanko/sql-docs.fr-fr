---
title: Diagnostics (en anglais) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a09f46d3fd6aa2f9b9c7310af6d3ddc90f78389f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305150"
---
# <a name="diagnostics"></a>Diagnostics
Les fonctions dans ODBC retournent l’information diagnostique de deux façons. Le code de retour indique le succès ou l’échec global de la fonction, tandis que les dossiers diagnostiques fournissent des informations détaillées sur la fonction. Au moins un enregistrement diagnostique - l’enregistrement d’en-tête - est retourné même si la fonction réussit.  
  
 L’information diagnostique est utilisée au moment du développement pour attraper les erreurs de programmation telles que les poignées invalides et les erreurs de syntaxe dans les déclarations SQL codées en dur. Il est utilisé au moment de l’exécution pour attraper les erreurs de temps d’exécution et les avertissements tels que la troncation de données, les violations d’accès, et les erreurs de syntaxe dans les déclarations SQL saisies par l’utilisateur.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Codes de retour](../../../odbc/reference/develop-app/return-codes-odbc.md)  
  
-   [Enregistrements de diagnostic](../../../odbc/reference/develop-app/diagnostic-records.md)  
  
-   [Utilisation de SQLGetDiagRec et de SQLGetDiagField](../../../odbc/reference/develop-app/using-sqlgetdiagrec-and-sqlgetdiagfield.md)  
  
-   [Implémentation de SQLGetDiagRec et de SQLGetDiagField](../../../odbc/reference/develop-app/implementing-sqlgetdiagrec-and-sqlgetdiagfield.md)  
  
-   [Exemples de gestion des diagnostics](../../../odbc/reference/develop-app/diagnostic-handling-examples.md)
