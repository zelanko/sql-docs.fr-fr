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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 55b2ff4d428f02b59883b675fde95531366f0b4d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68020604"
---
# <a name="result-generating-and-result-free-statements"></a>Instructions avec génération de résultats et sans résultats
Les instructions SQL peuvent être réparties librement dans les cinq catégories suivantes :  
  
-   **Instructions de génération de jeu de résultats** Il s’agit d’instructions SQL qui génèrent un jeu de résultats. Par exemple, une instruction **Select** .  
  
-   **Instructions de génération de nombre de lignes** Il s’agit d’instructions SQL qui génèrent un nombre de lignes affectées. Par exemple, une instruction **Update** ou **Delete** .  
  
-   **Instructions DDL (Data Definition Language)** Il s’agit d’instructions SQL qui modifient la structure de la base de données. Par exemple, **Create table** ou **Drop index**.  
  
-   **Instructions de modification de contexte** Il s’agit d’instructions SQL qui modifient le contexte d’une base de données. Par exemple, les instructions **use** et **Set** dans SQL Server.  
  
-   **Instructions administratives** Il s’agit d’instructions SQL utilisées à des fins administratives dans une base de données. Par exemple, **Grant** et **Revoke**.  
  
 Les instructions SQL dans les deux premières catégories sont collectivement appelées *instructions de génération de résultats*. Les instructions SQL dans les trois dernières catégories sont collectivement appelées des *instructions sans résultat*. ODBC définit la sémantique des lots qui incluent uniquement les instructions de génération de résultats. Ces sémantiques varient considérablement et sont donc spécifiques à la source de données. Par exemple, le pilote SQL Server ne prend pas en charge la suppression d’un objet, puis la référence ou la recréation du même objet dans le même lot. Par conséquent, le terme *lot* utilisé dans ce manuel fait uniquement référence à des lots d’instructions générant des résultats.
