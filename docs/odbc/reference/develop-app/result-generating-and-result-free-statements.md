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
manager: craigg
ms.openlocfilehash: e38e17ac469ec0685f11d7dfde587f36073fb970
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47706907"
---
# <a name="result-generating-and-result-free-statements"></a>Instructions avec génération de résultats et sans résultats
Instructions SQL peuvent être faiblement divisées en cinq catégories :  
  
-   **Instructions de génération de jeu de résultat** il s’agit d’instructions SQL qui génèrent un jeu de résultats. Par exemple, un **sélectionnez** instruction.  
  
-   **Instructions de génération de nombre de lignes** il s’agit d’instructions SQL qui génèrent un nombre de lignes affectées. Par exemple, un **mise à jour** ou **supprimer** instruction.  
  
-   **Instructions de langage de définition (DDL) de données** il s’agit d’instructions SQL qui modifient la structure de la base de données. Par exemple, **CREATE TABLE** ou **DROP INDEX**.  
  
-   **Instructions de modification de contexte** il s’agit d’instructions SQL qui modifient le contexte d’une base de données. Par exemple, le **utilisation** et **définir** instructions dans SQL Server.  
  
-   **Instructions d’administration** il s’agit d’instructions SQL utilisées pour des raisons administratives dans une base de données. Par exemple, **GRANT** et **RÉVOQUER**.  
  
 Les instructions SQL dans les deux premières catégories sont collectivement regroupés sous *instructions avec génération de résultats*. Instructions SQL dans les trois dernières catégories sont collectivement regroupés sous *sans résultats instructions*. ODBC définit les sémantiques de lots contenant des instructions uniquement avec génération de résultats. Ces sémantiques peuvent varier et sont donc spécifique à la source de données. Par exemple, le pilote SQL Server ne prend pas en charge la suppression d’un objet puis faisant référence à ou recréer le même objet dans le même lot. Par conséquent, le terme *batch* dans ce manuel se réfère à des lots de générer des résultats instructions.
