---
description: Mise à jour de lignes par signet avec SQLBulkOperations
title: Mise à jour de lignes par signet avec SQLBulkOperations | Microsoft Docs
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
ms.openlocfilehash: 9981136d546d53b131cff0d71edcdeab5b2e650c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88482872"
---
# <a name="updating-rows-by-bookmark-with-sqlbulkoperations"></a>Mise à jour de lignes par signet avec SQLBulkOperations
Lors de la mise à jour d’une ligne par signet, **SQLBulkOperations** permet à la source de données de mettre à jour une ou plusieurs lignes de la table. Les lignes sont identifiées par le signet dans une colonne de signets liée. La ligne est mise à jour à l’aide des données des mémoires tampons d’application pour chaque colonne liée (sauf lorsque la valeur de la mémoire tampon de longueur/d’indicateur d’une colonne est SQL_COLUMN_IGNORE). Les colonnes indépendantes ne seront pas mises à jour.  
  
 Pour mettre à jour des lignes par signet avec **SQLBulkOperations**, l’application :  
  
1.  Récupère et met en cache les signets de toutes les lignes à mettre à jour. Si plusieurs liaisons de signet et de colonne sont utilisées, les signets sont stockés dans un tableau ; s’il y a plus d’un signet et que la liaison selon les lignes est utilisée, les signets sont stockés dans un tableau de structures de lignes.  
  
2.  Définit l’attribut d’instruction SQL_ATTR_ROW_ARRAY_SIZE sur le nombre de signets et lie la mémoire tampon contenant la valeur de signet, ou le tableau de signets, à la colonne 0.  
  
3.  Place les nouvelles valeurs de données dans les mémoires tampons de l’ensemble de lignes. Pour plus d’informations sur l’envoi de données de type long avec **SQLBulkOperations**, consultez [long Data et SQLSetPos et SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md).  
  
4.  Définit la valeur de la mémoire tampon de longueur/d’indicateur de chaque colonne si nécessaire. Il s’agit de la longueur en octets des données ou SQL_NTS pour les colonnes liées aux mémoires tampons de chaîne, la longueur en octets des données pour les colonnes liées aux mémoires tampons binaires, et SQL_NULL_DATA pour toutes les colonnes dont la valeur est NULL.  
  
5.  Définit la valeur dans la mémoire tampon de longueur/d’indicateur des colonnes qui ne doivent pas être mises à jour pour SQL_COLUMN_IGNORE. Bien que l’application puisse ignorer cette étape et renvoyer les données existantes, cela est inefficace et risque d’envoyer des valeurs à la source de données qui ont été tronquées lors de leur lecture.  
  
6.  Appelle **SQLBulkOperations** avec l’argument *Operation* défini sur SQL_UPDATE_BY_BOOKMARK.  
  
 Pour chaque ligne envoyée à la source de données sous forme de mise à jour, les mémoires tampons de l’application doivent avoir des données de ligne valides. Si les mémoires tampons de l’application ont été remplies par l’extraction, si un tableau d’état de ligne a été conservé et si la valeur d’état d’une ligne est SQL_ROW_DELETED, SQL_ROW_ERROR ou SQL_ROW_NOROW, les données non valides peuvent être envoyées par inadvertance à la source de données.
