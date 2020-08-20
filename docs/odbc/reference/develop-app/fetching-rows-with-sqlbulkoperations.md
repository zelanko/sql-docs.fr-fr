---
description: Extraction de lignes avec SQLBulkOperations
title: Extraction de lignes à l’aide de SQLBulkOperations | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data updates [ODBC], bookmarks
- SQLBulkOperations function [ODBC], fetching rows
- data updates [ODBC], SQLBulkOperations
- bookmarks [ODBC]
- updating data [ODBC], bookmarks
- updating data [ODBC], SQLBulkOperations
ms.assetid: 0efee2d6-ce94-411e-9976-97ba28b8da37
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e4c3cb6a38e3ef9c42f4e853b8c406579b5c0236
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88499869"
---
# <a name="fetching-rows-with-sqlbulkoperations"></a>Extraction de lignes avec SQLBulkOperations
Les données peuvent être réextraites dans un ensemble de lignes à l’aide de signets par un appel à **SQLBulkOperations.** Les lignes à extraire sont identifiées par les signets dans une colonne de signets liés. Les colonnes ayant la valeur SQL_COLUMN_IGNORE ne sont pas extraites.  
  
 Pour effectuer des extractions en bloc avec **SQLBulkOperations**, l’application effectue les opérations suivantes :  
  
1.  Récupère et met en cache les signets de toutes les lignes à mettre à jour. Si plusieurs liaisons de signet et de colonne sont utilisées, les signets sont stockés dans un tableau ; s’il y a plus d’un signet et que la liaison selon les lignes est utilisée, les signets sont stockés dans un tableau de structures de lignes.  
  
2.  Définit l’attribut d’instruction SQL_ATTR_ROW_ARRAY_SIZE sur le nombre de lignes à extraire et lie la mémoire tampon contenant la valeur de signet, ou le tableau de signets, à la colonne 0.  
  
3.  Définit la valeur de la mémoire tampon de longueur/d’indicateur de chaque colonne si nécessaire. Il s’agit de la longueur en octets des données ou SQL_NTS pour les colonnes liées aux mémoires tampons de chaîne, la longueur en octets des données pour les colonnes liées aux mémoires tampons binaires, et SQL_NULL_DATA pour toutes les colonnes dont la valeur est NULL. L’application définit la valeur dans la mémoire tampon de longueur/d’indicateur des colonnes qui doivent être définies sur leur valeur par défaut (le cas échéant) ou NULL (le cas échéant) pour SQL_COLUMN_IGNORE.  
  
4.  Appelle **SQLBulkOperations** avec l’argument *Operation* défini sur SQL_FETCH_BY_BOOKMARK.  
  
 L’application n’a pas besoin d’utiliser le tableau d’opérations de ligne pour empêcher l’exécution de l’opération sur certaines colonnes. L’application sélectionne les lignes qu’elle souhaite extraire en copiant uniquement les signets pour ces lignes dans le tableau de signets lié.
