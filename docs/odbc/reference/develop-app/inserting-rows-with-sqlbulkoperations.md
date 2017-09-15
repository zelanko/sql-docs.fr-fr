---
title: Insertion de lignes avec SQLBulkOperations | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLBulkOperations function [ODBC], inserting rows
- data updates [ODBC], SQLBulkOperations
- updating data [ODBC], SQLBulkOperations
ms.assetid: ed585ea7-4d56-4df9-8dc3-53ca82382450
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: bd79255e4cda68d1fd4d425544702e589f44336b
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="inserting-rows-with-sqlbulkoperations"></a>Insertion de lignes avec SQLBulkOperations
Insertion de données avec **SQLBulkOperations** est similaire à la mise à jour des données avec **SQLBulkOperations** , car elle utilise les données du tampon de l’application liée.  
  
 Afin que chaque colonne dans la nouvelle ligne a une valeur, tous les lié des colonnes avec une valeur de l’indicateur/longueur de SQL_COLUMN_IGNORE et toutes les colonnes indépendantes doivent accepter des valeurs NULL ou une valeur par défaut.  
  
 Pour insérer des lignes avec **SQLBulkOperations**, l’application effectue les opérations suivantes :  
  
1.  Définit l’attribut d’instruction SQL_ATTR_ROW_ARRAY_SIZE au nombre de lignes à insérer et place les nouvelles valeurs de données dans les mémoires tampons d’application liée. Pour plus d’informations sur l’envoi des données de type long avec **SQLBulkOperations**, consultez [données de type Long et SQLSetPos et SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md).  
  
2.  Définit la valeur dans la mémoire tampon de longueur / d’indicateur de chaque colonne si nécessaire. Il s’agit de la longueur d’octet des données ou SQL_NTS pour les colonnes liées aux mémoires tampons de chaîne, la longueur en octets des données pour les colonnes liées aux mémoires tampons de binaire et SQL_NULL_DATA pour toutes les colonnes à la valeur NULL. L’application définit la valeur dans la mémoire tampon de longueur / d’indicateur de ces colonnes doivent être définies sur leur valeur par défaut (le cas échéant) ou NULL (si une n’est pas le cas) pour SQL_COLUMN_IGNORE.  
  
3.  Appels **SQLBulkOperations** avec la *opération* argument a la valeur SQL_ADD.  
  
 Après avoir **SQLBulkOperations** est retournée, la ligne actuelle est inchangée. Si la signet colonne (0) est liée, **SQLBulkOperations** retourne les signets des lignes insérées dans la mémoire tampon d’ensemble de lignes est liées à cette colonne.
