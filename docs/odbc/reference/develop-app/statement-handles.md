---
title: Poignées de déclarations Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- statement handles [ODBC]
- handles [ODBC], statement
ms.assetid: 65d6d78b-a8c8-489a-9dad-f8d127a44882
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1be90fe10d10a0b087d1c9724fed249805eb4dba
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299675"
---
# <a name="statement-handles"></a>Handles d’instruction
Une *déclaration* est plus facilement considérée comme une déclaration SQL, comme **SELECT \* FROM Employee**. Cependant, une déclaration est plus qu’une simple déclaration SQL - il se compose de toutes les informations associées à cette déclaration SQL, tels que tous les ensembles de résultats créés par l’énoncé et les paramètres utilisés dans l’exécution de la déclaration. Une déclaration n’a même pas besoin d’avoir une déclaration SQL définie par la demande. Par exemple, lorsqu’une fonction de catalogue telle que **SQLTables** est exécutée sur une déclaration, il exécute une déclaration SQL prédéfinie qui renvoie une liste de noms de table.  
  
 Chaque relevé est identifié par une poignée de déclaration. Une déclaration est associée à une seule connexion, et il peut y avoir plusieurs déclarations sur cette connexion. Certains conducteurs limitent le nombre d’énoncés actifs qu’ils appuient; l’option SQL_MAX_CONCURRENT_ACTIVITIES dans **SQLGetInfo** précise le nombre de déclarations actives qu’un conducteur prend en charge sur une seule connexion. Une déclaration est définie pour être *active* si elle a des résultats en attente, lorsque les résultats sont soit un ensemble de résultats ou le nombre de lignes affectées par un **INSERT**, **UPDATE**, ou **DÉLÉ,** ou des données sont envoyées avec plusieurs appels à **SQLPutData**.  
  
 Dans un code qui implémente ODBC (le gestionnaire de conducteur ou un pilote), la poignée de déclaration identifie une structure qui contient des informations de déclaration, telles que :  
  
-   L’état de la déclaration  
  
-   Les diagnostics actuels au niveau de l’énoncé  
  
-   Les adresses des variables d’application liées aux paramètres de l’instruction et aux colonnes de jeu de résultats  
  
-   Les paramètres actuels de chaque attribut d’instruction  
  
 Les poignées de relevé sont utilisées dans la plupart des fonctions ODBC. Notamment, ils sont utilisés dans les fonctions pour lier les paramètres et les colonnes de jeu de résultat (**SQLBindParameter** et **SQLBindCol**), préparer et exécuter des déclarations (**SQLPrepare**, **SQLExecute**, et **SQLExecDirect**), récupérer les métadonnées (**SQLColAttribute** et **SQLDescribeCol**), aller chercher des résultats (**SQLFetch**), et récupérer des diagnostics (**SQLGetDiagField** et **SQLGetDiagRec**). Ils sont également utilisés dans les fonctions de catalogue **(SQLColumns**, **SQLTables**, et ainsi de suite) et un certain nombre d’autres fonctions.  
  
 Les poignées de déclaration sont attribuées avec **SQLAllocHandle** et libérées avec **SQLFreeHandle**.
