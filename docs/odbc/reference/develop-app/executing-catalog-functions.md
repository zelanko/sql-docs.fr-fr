---
title: Exécution des fonctions de catalogue | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6469a5394e232ab9d9135fbbbd56ba7b791ccbcb
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305720"
---
# <a name="executing-catalog-functions"></a>Exécution de fonctions de catalogue
Étant donné qu’une fonction de catalogue crée un jeu de résultats, elle revient à exécuter toute instruction SQL de génération de jeu de résultats. En fait, les fonctions de catalogue sont souvent implémentées en exécutant des instructions SQL prédéfinies ou en appelant des procédures prédéfinies fournies avec le pilote ou le SGBD. Presque tout ce qui s’applique aux instructions SQL qui créent des jeux de résultats s’applique également aux fonctions de catalogue. Par exemple, l’attribut d’instruction SQL_ATTR_MAX_ROWS limite le nombre de lignes retournées par la fonction Catalog, tout comme il limite le nombre de lignes retournées par une instruction **Select** .  
  
 Pour exécuter une fonction de catalogue, une application appelle simplement la fonction.  
  
 Pour plus d’informations sur les fonctions de catalogue, consultez [fonctions de catalogue](../../../odbc/reference/develop-app/catalog-functions.md).
