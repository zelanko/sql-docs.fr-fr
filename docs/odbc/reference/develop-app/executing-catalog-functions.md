---
title: Exécution des fonctions de catalogue (fr) Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305720"
---
# <a name="executing-catalog-functions"></a>Exécution de fonctions de catalogue
Étant donné qu’une fonction de catalogue crée un ensemble de résultats, elle équivaut à l’exécution de toute déclaration SQL génératrice de résultats. En fait, les fonctions de catalogue sont souvent mises en œuvre en exécutant des relevés SQL prédéfinis ou en appelant des procédures prédéfinies qui sont expédiées avec le conducteur ou DBMS. Presque tout ce qui s’applique aux énoncés SQL qui créent des ensembles de résultats s’applique également aux fonctions de catalogue. Par exemple, l’attribut de l’SQL_ATTR_MAX_ROWS’énoncé limite le nombre de lignes retournées par la fonction catalogue, tout comme elle limite le nombre de lignes retournées par une instruction **SELECT.**  
  
 Pour exécuter une fonction de catalogue, une application appelle simplement la fonction.  
  
 Pour plus d’informations sur les fonctions du catalogue, voir [Catalog Functions](../../../odbc/reference/develop-app/catalog-functions.md).
