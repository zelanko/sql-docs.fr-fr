---
description: Insertion de lignes avec SQLBulkOperations
title: Insertion de lignes à l’aide de SQLBulkOperations | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLBulkOperations function [ODBC], inserting rows
- data updates [ODBC], SQLBulkOperations
- updating data [ODBC], SQLBulkOperations
ms.assetid: ed585ea7-4d56-4df9-8dc3-53ca82382450
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 36f04a393d2053389f823c33a55050f24dd87020
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88424631"
---
# <a name="inserting-rows-with-sqlbulkoperations"></a>Insertion de lignes avec SQLBulkOperations
L’insertion de données avec **SQLBulkOperations** est semblable à la mise à jour des données avec **SQLBulkOperations** , car elle utilise les données des mémoires tampons d’application liées.  
  
 Pour que chaque colonne de la nouvelle ligne ait une valeur, toutes les colonnes liées avec une valeur longueur/indicateur de SQL_COLUMN_IGNORE et toutes les colonnes indépendantes doivent accepter les valeurs NULL ou avoir une valeur par défaut.  
  
 Pour insérer des lignes avec **SQLBulkOperations**, l’application effectue les opérations suivantes :  
  
1.  Définit l’attribut d’instruction SQL_ATTR_ROW_ARRAY_SIZE sur le nombre de lignes à insérer et place les nouvelles valeurs de données dans les mémoires tampons de l’application liée. Pour plus d’informations sur l’envoi de données de type long avec **SQLBulkOperations**, consultez [long Data et SQLSetPos et SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md).  
  
2.  Définit la valeur de la mémoire tampon de longueur/d’indicateur de chaque colonne si nécessaire. Il s’agit de la longueur en octets des données ou SQL_NTS pour les colonnes liées aux mémoires tampons de chaîne, la longueur en octets des données pour les colonnes liées aux mémoires tampons binaires, et SQL_NULL_DATA pour toutes les colonnes dont la valeur est NULL. L’application définit la valeur dans la mémoire tampon de longueur/d’indicateur des colonnes qui doivent être définies sur leur valeur par défaut (le cas échéant) ou NULL (le cas échéant) pour SQL_COLUMN_IGNORE.  
  
3.  Appelle **SQLBulkOperations** avec l’argument *Operation* défini sur SQL_ADD.  
  
 Une fois **SQLBulkOperations** retourné, la ligne actuelle est inchangée. Si la colonne de signets (colonne 0) est liée, **SQLBulkOperations** retourne les signets des lignes insérées dans la mémoire tampon de l’ensemble de lignes liée à cette colonne.
