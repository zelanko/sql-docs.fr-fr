---
title: Aller chercher des rangées avec SQLBulkOperations (fr) Microsoft Docs
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
ms.openlocfilehash: ae0b4c2114059cecaaf8f8825169300f131bd473
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305648"
---
# <a name="fetching-rows-with-sqlbulkoperations"></a>Extraction de lignes avec SQLBulkOperations
Les données peuvent être refoquées dans un jeu de rangées à l’aide de signets par un appel à **SQLBulkOperations.** Les lignes à aller chercher sont identifiées par les signets dans une colonne de signet lié. Les colonnes d’une valeur de SQL_COLUMN_IGNORE ne sont pas récupérées.  
  
 Pour effectuer des allers-y en vrac avec **SQLBulkOperations**, l’application fait ce qui suit:  
  
1.  Récupère et cache les signets de toutes les lignes à mettre à jour. S’il y a plus d’un signet et une reliure de colonne est utilisée, les signets sont stockés dans un tableau ; s’il y a plus d’un signet et que la reliure en ligne est utilisée, les signets sont stockés dans un tableau de structures de rangée.  
  
2.  Définit l’attribut SQL_ATTR_ROW_ARRAY_SIZE énoncé au nombre de lignes à atteindre et lie le tampon contenant la valeur du signet, ou la gamme de signets, à la colonne 0.  
  
3.  Définit la valeur dans le tampon longueur/indicateur de chaque colonne au besoin. Il s’agit de la longueur d’entrée des données ou SQL_NTS pour les colonnes liées aux tampons de chaîne, la longueur d’or des données pour les colonnes liées aux tampons binaires, et SQL_NULL_DATA pour toutes les colonnes à définir à NULL. L’application définit la valeur dans le tampon longueur/indicateur des colonnes qui doivent être réglées à leur défaut (si cela existe) ou NULL (si elle ne le fait pas) pour SQL_COLUMN_IGNORE.  
  
4.  Appels **SQLBulkOperations** avec *l’argument de l’opération* mis à SQL_FETCH_BY_BOOKMARK.  
  
 Il n’est pas nécessaire que l’application utilise le tableau d’opération de la ligne pour empêcher l’opération d’être effectuée sur certaines colonnes. L’application sélectionne les lignes qu’elle veut aller chercher en copiant uniquement les signets de ces lignes dans le tableau de signets lié.
