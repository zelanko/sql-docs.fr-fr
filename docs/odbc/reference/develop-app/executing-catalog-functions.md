---
title: "L’exécution des fonctions de catalogue | Documents Microsoft"
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
- catalog functions [ODBC], executing
- functions [ODBC], catalog functions
ms.assetid: c59cbda3-e214-4399-9edc-cfac86b378d7
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 489cd057a15e90794c71cfb433931cd9bc687016
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="executing-catalog-functions"></a>L’exécution des fonctions de catalogue
Une fonction de catalogue crée un jeu de résultats, il est équivalent à l’exécution de n’importe quelle instruction SQL de création de jeu de résultats. En fait, les fonctions de catalogue sont souvent implémentées en exécutant les instructions SQL prédéfinies ou en appelant les procédures prédéfinies qui sont livrés avec le pilote ou le SGBD. Presque tout ce qui s’applique aux instructions SQL qui créent des jeux de résultats s’applique également aux fonctions de catalogue. Par exemple, l’attribut d’instruction SQL_ATTR_MAX_ROWS limite le nombre de lignes retournées par la fonction de catalogue, exactement comme elle limite le nombre de lignes retournées par une **sélectionnez** instruction.  
  
 Pour exécuter une fonction de catalogue, une application appelle simplement la fonction.  
  
 Pour plus d’informations sur les fonctions de catalogue, consultez [fonctions de catalogue](../../../odbc/reference/develop-app/catalog-functions.md).

