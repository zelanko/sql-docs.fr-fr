---
title: Instructions de génération de résultats et de résultat | Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300089"
---
# <a name="result-generating-and-result-free-statements"></a>Instructions avec génération de résultats et sans résultats
Les instructions SQL peuvent être réparties librement dans les cinq catégories suivantes :  
  
-   **Instructions de génération de jeu de résultats** Il s’agit d’instructions SQL qui génèrent un jeu de résultats. Par exemple, une instruction **Select** .  
  
-   **Instructions de génération de nombre de lignes** Il s’agit d’instructions SQL qui génèrent un nombre de lignes affectées. Par exemple, une instruction **Update** ou **Delete** .  
  
-   **Instructions DDL (Data Definition Language)** Il s’agit d’instructions SQL qui modifient la structure de la base de données. Par exemple, **Create table** ou **Drop index**.  
  
-   **Instructions de modification de contexte** Il s’agit d’instructions SQL qui modifient le contexte d’une base de données. Par exemple, les instructions **use** et **Set** dans SQL Server.  
  
-   **Instructions administratives** Il s’agit d’instructions SQL utilisées à des fins administratives dans une base de données. Par exemple, **Grant** et **Revoke**.  
  
 Les instructions SQL dans les deux premières catégories sont collectivement appelées *instructions de génération de résultats*. Les instructions SQL dans les trois dernières catégories sont collectivement appelées des *instructions sans résultat*. ODBC définit la sémantique des lots qui incluent uniquement les instructions de génération de résultats. Ces sémantiques varient considérablement et sont donc spécifiques à la source de données. Par exemple, le pilote SQL Server ne prend pas en charge la suppression d’un objet, puis la référence ou la recréation du même objet dans le même lot. Par conséquent, le terme *lot* utilisé dans ce manuel fait uniquement référence à des lots d’instructions générant des résultats.
