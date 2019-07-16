---
title: Instructions avec génération de résultats et sans résultats | Microsoft Docs
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68020604"
---
# <a name="result-generating-and-result-free-statements"></a>Instructions avec génération de résultats et sans résultats
Instructions SQL peuvent être faiblement divisées en cinq catégories :  
  
-   **Instructions de génération de jeu de résultat** il s’agit d’instructions SQL qui génèrent un jeu de résultats. Par exemple, un **sélectionnez** instruction.  
  
-   **Instructions de génération de nombre de lignes** il s’agit d’instructions SQL qui génèrent un nombre de lignes affectées. Par exemple, un **mise à jour** ou **supprimer** instruction.  
  
-   **Instructions de langage de définition (DDL) de données** il s’agit d’instructions SQL qui modifient la structure de la base de données. Par exemple, **CREATE TABLE** ou **DROP INDEX**.  
  
-   **Instructions de modification de contexte** il s’agit d’instructions SQL qui modifient le contexte d’une base de données. Par exemple, le **utilisation** et **définir** instructions dans SQL Server.  
  
-   **Instructions d’administration** il s’agit d’instructions SQL utilisées pour des raisons administratives dans une base de données. Par exemple, **GRANT** et **RÉVOQUER**.  
  
 Les instructions SQL dans les deux premières catégories sont collectivement regroupés sous *instructions avec génération de résultats*. Instructions SQL dans les trois dernières catégories sont collectivement regroupés sous *sans résultats instructions*. ODBC définit les sémantiques de lots contenant des instructions uniquement avec génération de résultats. Ces sémantiques peuvent varier et sont donc spécifiques à la source de données. Par exemple, le pilote SQL Server ne prend pas en charge la suppression d’un objet puis faisant référence à ou recréer le même objet dans le même lot. Par conséquent, le terme *batch* dans ce manuel se réfère à des lots de générer des résultats instructions.
