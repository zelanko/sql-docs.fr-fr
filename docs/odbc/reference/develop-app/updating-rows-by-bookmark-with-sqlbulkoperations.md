---
title: Mise à jour des lignes par Signetmark avec SQLBulkOperations (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9c755297e8beadad92b5be81d78ca534bb96ecae
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81283197"
---
# <a name="updating-rows-by-bookmark-with-sqlbulkoperations"></a>Mise à jour de lignes par signet avec SQLBulkOperations
Lors de la mise à jour d’une ligne par signet, **SQLBulkOperations** rend la source de données mettre à jour une ou plusieurs rangées de la table. Les lignes sont identifiées par le signet dans une colonne de signet lié. La ligne est mise à jour à l’aide des données dans les tampons d’application pour chaque colonne liée (sauf lorsque la valeur de la longueur / tampon indicateur pour une colonne est SQL_COLUMN_IGNORE). Les colonnes non liées ne seront pas mises à jour.  
  
 Pour mettre à jour les lignes par signet avec **SQLBulkOperations**, l’application:  
  
1.  Récupère et cache les signets de toutes les lignes à mettre à jour. S’il y a plus d’un signet et une reliure de colonne est utilisée, les signets sont stockés dans un tableau ; s’il y a plus d’un signet et que la reliure en ligne est utilisée, les signets sont stockés dans un tableau de structures de rangée.  
  
2.  Définit l’attribut SQL_ATTR_ROW_ARRAY_SIZE énoncé au nombre de signets et lie le tampon contenant la valeur du signet, ou la gamme de signets, à la colonne 0.  
  
3.  Place les nouvelles valeurs de données dans les tampons rowset. Pour plus d’informations sur la façon d’envoyer de longues données avec **SQLBulkOperations**, voir [Long Data et SQLSetPos et SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md).  
  
4.  Définit la valeur dans le tampon longueur/indicateur de chaque colonne au besoin. Il s’agit de la longueur d’entrée des données ou SQL_NTS pour les colonnes liées aux tampons de chaîne, la longueur d’or des données pour les colonnes liées aux tampons binaires, et SQL_NULL_DATA pour toutes les colonnes à définir à NULL.  
  
5.  Définit la valeur dans le tampon longueur/indicateur des colonnes qui ne doivent pas être mises à jour pour SQL_COLUMN_IGNORE. Bien que l’application puisse sauter cette étape et renvoyer les données existantes, elle est inefficace et risque d’envoyer des valeurs à la source de données qui ont été tronquées lors de leur lecture.  
  
6.  Appels **SQLBulkOperations** avec *l’argument de l’opération* mis à SQL_UPDATE_BY_BOOKMARK.  
  
 Pour chaque ligne qui est envoyée à la source de données comme une mise à jour, les tampons d’application doivent avoir des données de ligne valides. Si les tampons d’application ont été remplis par aller chercher, si un tableau d’état de ligne a été maintenu, et si la valeur de statut pour une rangée est SQL_ROW_DELETED, SQL_ROW_ERROR, ou SQL_ROW_NOROW, des données invalides pourraient par inadvertance être envoyées à la source de données.
