---
title: Suppression des lignes par Bookmark avec SQLBulkOperations (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data updates [ODBC], SQLBulkOperations
- SQLBulkOperations function [ODBC], deleting rows
- updating data [ODBC], SQLBulkOperations
ms.assetid: 46139ec9-7095-481a-bf45-20200a2fdc03
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6b6a4c1b24ee276c86175392eb45ac5ce0aa45e5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305960"
---
# <a name="deleting-rows-by-bookmark-with-sqlbulkoperations"></a>Suppression de lignes par signet avec SQLBulkOperations
Lors de la suppression d’une ligne par signet, **SQLBulkOperations** fait la source de données supprimer une ou plusieurs rangées sélectionnées de la table. Les lignes sont identifiées par le signet dans une colonne de signet lié.  
  
 Pour supprimer les lignes par signet avec **SQLBulkOperations**, l’application fait ce qui suit :  
  
1.  Récupère et cache les signets de toutes les lignes à supprimer. S’il y a plus d’un signet et une reliure de colonne est utilisée, les signets sont stockés dans un tableau ; s’il y a plus d’un signet et que la reliure en ligne est utilisée, les signets sont stockés dans un tableau de structures de rangée.  
  
2.  Définit l’attribut SQL_ATTR_ROW_ARRAY_SIZE énoncé au nombre de signets et lie le tampon contenant la valeur du signet, ou la gamme de signets, à la colonne 0.  
  
3.  Appels **SQLBulkOperations** avec *Opération* réglée à SQL_DELETE_BY_BOOKMARK.
