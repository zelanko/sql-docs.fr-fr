---
title: La mise à jour de lignes par signet avec SQLBulkOperations | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data updates [ODBC], bookmarks
- SQLBulkOperations function [ODBC], updating rows
- data updates [ODBC], SQLBulkOperations
- bookmarks [ODBC]
- updating data [ODBC], bookmarks
- updating data [ODBC], SQLBulkOperations
ms.assetid: c9ad82b7-8dba-45b0-bdb9-f4668b37c0d6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e9f0c59324542793301965c7d3555cf35ad40f5d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63194400"
---
# <a name="updating-rows-by-bookmark-with-sqlbulkoperations"></a>Mise à jour de lignes par signet avec SQLBulkOperations
Lors de la mise à jour d’une ligne par signet, **SQLBulkOperations** rend la source de données à mettre à jour une ou plusieurs lignes de la table. Les lignes sont identifiées par le signet dans une colonne liée de signet. La ligne est mise à jour à l’aide des données dans les mémoires tampons d’application pour chaque colonne dépendante (sauf si la valeur dans la mémoire tampon de longueur / d’indicateur pour une colonne est SQL_COLUMN_IGNORE). Des colonnes indépendantes ne seront pas mis à jour.  
  
 Pour mettre à jour des lignes par signet avec **SQLBulkOperations**, l’application :  
  
1.  Récupère et met en cache les signets de toutes les lignes à mettre à jour. S’il existe plus d’un signet et la liaison est utilisée, les signets sont stockés dans un tableau. s’il existe plus d’un signet et la liaison est utilisée, les signets sont stockés dans un tableau de structures de ligne.  
  
2.  Définit l’attribut d’instruction SQL_ATTR_ROW_ARRAY_SIZE au nombre de signets et lie la mémoire tampon contenant la valeur du signet, ou le tableau de signets, à la colonne 0.  
  
3.  Place les nouvelles valeurs de données dans les mémoires tampons d’ensemble de lignes. Pour plus d’informations sur l’envoi des données de type long avec **SQLBulkOperations**, consultez [données de type Long et SQLSetPos et SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md).  
  
4.  Définit la valeur dans la mémoire tampon de longueur / d’indicateur de chaque colonne en fonction des besoins. Il s’agit de la longueur d’octet des données ou SQL_NTS pour les colonnes liées aux mémoires tampons de chaîne, la longueur d’octet des données pour les colonnes liées à la mémoire tampon binaire et SQL_NULL_DATA pour toutes les colonnes à la valeur NULL.  
  
5.  Définit la valeur dans la mémoire tampon de longueur / d’indicateur de ces colonnes ne doivent ne pas être mis à jour vers SQL_COLUMN_IGNORE. Bien que l’application peut ignorer cette étape et renvoyer les données existantes, cela est inefficace et risque d’envoyer des valeurs dans la source de données qui ont été tronquées lors de leur lecture.  
  
6.  Appels **SQLBulkOperations** avec la *opération* argument a la valeur SQL_UPDATE_BY_BOOKMARK.  
  
 Pour chaque ligne est envoyée à la source de données comme une mise à jour, les mémoires tampons d’application doivent avoir des données de ligne valide. Si les mémoires tampons d’application ont été remplies par extraction, si un tableau d’état de ligne a été maintenu, et si la valeur d’état pour une ligne est SQL_ROW_DELETED, SQL_ROW_ERROR ou SQL_ROW_NOROW, données non valides pourraient être envoyées par inadvertance à la source de données.
