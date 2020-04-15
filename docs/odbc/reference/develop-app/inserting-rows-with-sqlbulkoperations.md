---
title: Insertion de lignes avec SQLBulkOperations (fr) Microsoft Docs
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
ms.openlocfilehash: a6fa384292f02026b8390aa92525144dce6f549b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300109"
---
# <a name="inserting-rows-with-sqlbulkoperations"></a>Insertion de lignes avec SQLBulkOperations
L’insertion de données avec **SQLBulkOperations** est similaire à la mise à jour des données avec **SQLBulkOperations** parce qu’elle utilise les données des tampons d’application liés.  
  
 De sorte que chaque colonne de la nouvelle ligne a une valeur, toutes les colonnes liées avec une valeur de longueur / indicateur de SQL_COLUMN_IGNORE et toutes les colonnes non liées doivent soit accepter les valeurs NULL ou avoir un défaut.  
  
 Pour insérer des lignes avec **SQLBulkOperations**, l’application fait ce qui suit :  
  
1.  Définit l’attribut SQL_ATTR_ROW_ARRAY_SIZE énoncé au nombre de lignes à insérer et place les nouvelles valeurs de données dans les tampons d’application liés. Pour plus d’informations sur la façon d’envoyer de longues données avec **SQLBulkOperations**, voir [Long Data et SQLSetPos et SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md).  
  
2.  Définit la valeur dans le tampon longueur/indicateur de chaque colonne au besoin. Il s’agit de la longueur d’entrée des données ou SQL_NTS pour les colonnes liées aux tampons de chaîne, la longueur d’or des données pour les colonnes liées aux tampons binaires, et SQL_NULL_DATA pour toutes les colonnes à définir à NULL. L’application définit la valeur dans le tampon longueur/indicateur des colonnes qui doivent être réglées à leur défaut (si cela existe) ou NULL (si elle ne le fait pas) pour SQL_COLUMN_IGNORE.  
  
3.  Appels **SQLBulkOperations** avec *l’argument de l’opération* mis à SQL_ADD.  
  
 Après le retour **de SQLBulkOperations,** la ligne actuelle est inchangée. Si la colonne de signets (colonne 0) est liée, **SQLBulkOperations** renvoie les signets des rangées insérées dans le tampon encastré lié à cette colonne.
