---
title: Déclarations génératrices de résultats et sans résultats (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result-generating statements [ODBC]
- batches [ODBC], result-generating statements
- batches [ODBC], result-free statements
- SQL statements [ODBC], batches
- result-free statements [ODBC]
ms.assetid: 2f3475d1-3999-4dd8-aba2-a6e1299c95f8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fc94aabd7982fba5879519573980db03b1857ef6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300089"
---
# <a name="result-generating-and-result-free-statements"></a>Instructions avec génération de résultats et sans résultats
Les énoncés SQL peuvent être vaguement divisés en les cinq catégories suivantes :  
  
-   **Énoncés générateurs de résultats** Ce sont des énoncés SQL qui génèrent un ensemble de résultats. Par exemple, une déclaration **SELECT.**  
  
-   **Énoncés générateurs de comptes de rangée** Ce sont des énoncés SQL qui génèrent un décompte des lignes touchées. Par exemple, une **déclaration UPDATE** ou **DELETE.**  
  
-   **Énoncés de langage de définition des données (DDL)** Ce sont des énoncés SQL qui modifient la structure de la base de données. Par exemple, **CREATE TABLE** ou **DROP INDEX**.  
  
-   **Énoncés contextuelles** Il s’agit de déclarations SQL qui modifient le contexte d’une base de données. Par exemple, les relevés **USE** et **SET** dans SQL Server.  
  
-   **Déclarations administratives** Il s’agit de relevés SQL utilisés à des fins administratives dans une base de données. Par exemple, **GRANT** et **REVOKE**.  
  
 Les déclarations SQL dans les deux premières catégories sont collectivement connues sous le nom *d’énoncés générateurs de résultats.* Les déclarations SQL dans les trois dernières catégories sont collectivement connues sous le nom *de déclarations sans résultat*. ODBC définit la sémantique des lots qui n’incluent que des énoncés générateurs de résultats. Ces sémantiques varient considérablement et sont donc spécifiques aux données. Par exemple, le conducteur sqL Server ne prend pas en charge la chute d’un objet, puis se référant ou recréant le même objet dans le même lot. Par conséquent, le *terme batch* tel qu’il est utilisé dans ce manuel ne se réfère qu’à des lots d’instructions génératrices de résultats.
