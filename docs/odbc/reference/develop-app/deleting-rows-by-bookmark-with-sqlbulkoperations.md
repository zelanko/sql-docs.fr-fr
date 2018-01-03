---
title: Suppression de lignes par le signet avec SQLBulkOperations | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data updates [ODBC], SQLBulkOperations
- SQLBulkOperations function [ODBC], deleting rows
- updating data [ODBC], SQLBulkOperations
ms.assetid: 46139ec9-7095-481a-bf45-20200a2fdc03
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: bb572386d385ea081297bc752a9c0f1dd9a8fd7b
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="deleting-rows-by-bookmark-with-sqlbulkoperations"></a>Suppression de lignes par le signet avec SQLBulkOperations
Lors de la suppression d’une ligne par un signet, **SQLBulkOperations** permet de supprimer une ou plusieurs lignes sélectionnées de la table de la source de données. Les lignes sont identifiées par le signet dans une colonne liée de signet.  
  
 Pour supprimer des lignes par le signet avec **SQLBulkOperations**, l’application effectue les opérations suivantes :  
  
1.  Récupère et met en cache les signets de toutes les lignes à supprimer. S’il existe plusieurs signets et la liaison est utilisée, les signets sont stockés dans un tableau ; s’il existe plusieurs signets et la liaison est utilisée, les signets sont stockés dans un tableau de structures de ligne.  
  
2.  Définit l’attribut d’instruction SQL_ATTR_ROW_ARRAY_SIZE au nombre de signets et lie la mémoire tampon qui contient la valeur du signet, ou le tableau de signets, à la colonne 0.  
  
3.  Appels **SQLBulkOperations** avec *opération* SQL_DELETE_BY_BOOKMARK la valeur.
