---
title: Insertion de lignes avec SQLBulkOperations | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 05b8f71d6f4c885c7dc64887dd92b1f600005ca7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68138924"
---
# <a name="inserting-rows-with-sqlbulkoperations"></a>Insertion de lignes avec SQLBulkOperations
Insertion de données avec **SQLBulkOperations** est similaire à la mise à jour des données avec **SQLBulkOperations** , car elle utilise les données du tampon de l’application liée.  
  
 Afin que chaque colonne dans la nouvelle ligne a une valeur, toutes les colonnes avec une valeur de longueur / d’indicateur de SQL_COLUMN_IGNORE liées et toutes les colonnes indépendantes doivent accepter les valeurs NULL ou avoir une valeur par défaut.  
  
 Pour insérer des lignes avec **SQLBulkOperations**, l’application effectue les opérations suivantes :  
  
1.  Définit l’attribut d’instruction SQL_ATTR_ROW_ARRAY_SIZE au nombre de lignes à insérer et place les nouvelles valeurs de données dans les mémoires tampons d’application liée. Pour plus d’informations sur l’envoi des données de type long avec **SQLBulkOperations**, consultez [données de type Long et SQLSetPos et SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md).  
  
2.  Définit la valeur dans la mémoire tampon de longueur / d’indicateur de chaque colonne en fonction des besoins. Il s’agit de la longueur d’octet des données ou SQL_NTS pour les colonnes liées aux mémoires tampons de chaîne, la longueur d’octet des données pour les colonnes liées à la mémoire tampon binaire et SQL_NULL_DATA pour toutes les colonnes à la valeur NULL. L’application définit la valeur dans la mémoire tampon de longueur / d’indicateur de ces colonnes doivent être définies sur leur valeur par défaut (le cas échéant) ou NULL (si ce choix n’est pas le cas) à SQL_COLUMN_IGNORE.  
  
3.  Appels **SQLBulkOperations** avec la *opération* argument a la valeur SQL_ADD.  
  
 Après avoir **SQLBulkOperations** est retournée, la ligne actuelle est inchangée. Si la signet colonne (0) est liée, **SQLBulkOperations** retourne les signets des lignes insérées dans la mémoire tampon d’ensemble de lignes est liées à cette colonne.
