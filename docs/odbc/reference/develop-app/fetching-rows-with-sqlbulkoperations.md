---
title: Extraction de lignes avec SQLBulkOperations | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a99592210ff315db026d60b8743d4a3bca13c969
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63061627"
---
# <a name="fetching-rows-with-sqlbulkoperations"></a>Extraction de lignes avec SQLBulkOperations
Peuvent récupérer des données dans un ensemble de lignes à l’aide de signets par un appel à **SQLBulkOperations.** Les lignes à extraire sont identifiés par les signets dans une colonne liée de signet. Colonnes avec la valeur SQL_COLUMN_IGNORE ne sont pas extraits.  
  
 Pour effectuer des extractions en bloc avec **SQLBulkOperations**, l’application effectue les opérations suivantes :  
  
1.  Récupère et met en cache les signets de toutes les lignes à mettre à jour. S’il existe plus d’un signet et la liaison est utilisée, les signets sont stockés dans un tableau. s’il existe plus d’un signet et la liaison est utilisée, les signets sont stockés dans un tableau de structures de ligne.  
  
2.  Définit l’attribut d’instruction SQL_ATTR_ROW_ARRAY_SIZE au nombre de lignes à extraire et lie la mémoire tampon contenant la valeur du signet, ou le tableau de signets, à la colonne 0.  
  
3.  Définit la valeur dans la mémoire tampon de longueur / d’indicateur de chaque colonne en fonction des besoins. Il s’agit de la longueur d’octet des données ou SQL_NTS pour les colonnes liées aux mémoires tampons de chaîne, la longueur d’octet des données pour les colonnes liées à la mémoire tampon binaire et SQL_NULL_DATA pour toutes les colonnes à la valeur NULL. L’application définit la valeur dans la mémoire tampon de longueur / d’indicateur de ces colonnes doivent être définies sur leur valeur par défaut (le cas échéant) ou NULL (si ce choix n’est pas le cas) à SQL_COLUMN_IGNORE.  
  
4.  Appels **SQLBulkOperations** avec la *opération* argument a la valeur SQL_FETCH_BY_BOOKMARK.  
  
 Il n’est pas nécessaire pour l’application pour utiliser le tableau d’opération de ligne pour empêcher l’opération à effectuer sur certaines colonnes. L’application sélectionne les lignes qu’elle souhaite extraire en copiant uniquement les signets pour les lignes dans le tableau de signet lié.
