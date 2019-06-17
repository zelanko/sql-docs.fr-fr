---
title: L’exécution des fonctions de catalogue | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- catalog functions [ODBC], executing
- functions [ODBC], catalog functions
ms.assetid: c59cbda3-e214-4399-9edc-cfac86b378d7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fc53e265ffa25c5ec598187f62505f18436f1c69
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63248343"
---
# <a name="executing-catalog-functions"></a>Exécution de fonctions de catalogue
Comme une fonction de catalogue crée un jeu de résultats, il est équivalent à l’exécution de n’importe quelle instruction SQL de génération de jeu de résultat. En fait, les fonctions de catalogue sont souvent implémentées en exécutant les instructions SQL prédéfinies ou en appelant des procédures prédéfinies qui sont livrés avec le pilote ou le SGBD. Presque tout ce qui s’applique aux instructions SQL qui créent des jeux de résultats s’applique également aux fonctions de catalogue. Par exemple, l’attribut d’instruction SQL_ATTR_MAX_ROWS limite le nombre de lignes retournées par la fonction de catalogue, tout comme il limite le nombre de lignes retournées par une **sélectionnez** instruction.  
  
 Pour exécuter une fonction de catalogue, une application appelle simplement la fonction.  
  
 Pour plus d’informations sur les fonctions de catalogue, consultez [fonctions de catalogue](../../../odbc/reference/develop-app/catalog-functions.md).
