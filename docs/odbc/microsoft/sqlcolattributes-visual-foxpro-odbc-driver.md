---
title: SQLColAttributes (pilote ODBC Visual FoxPro) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLColAttribute function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: d403dfa0-c26d-47d4-91d9-2f29aa387399
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9508fa7b9ada8273e1250d7584e577892acf5c51
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81307910"
---
# <a name="sqlcolattributes-visual-foxpro-odbc-driver"></a>SQLColAttributes (pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Cette rubrique contient des informations spécifiques au pilote ODBC Visual FoxPro. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous référence de l' [API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Prise en charge : complète  
  
 Conformité de l’API ODBC : niveau principal  
  
 Retourne les informations de descripteur pour une colonne dans un jeu de résultats. Les informations de descripteur sont retournées sous la forme d’une chaîne de caractères, d’une valeur dépendante du descripteur 32 bits ou d’une valeur entière.  
  
> [!NOTE]  
>  **SQLColAttributes** ne peut pas être utilisé pour retourner des informations sur la colonne de signet (colonne 0).  
  
 Le pilote ODBC Visual FoxPro prend en charge toutes les valeurs *fDescType* . Le tableau suivant contient des commentaires sur l’implémentation des valeurs sélectionnées par le pilote.  
  
|*fDescType*|Comment|  
|-----------------|-------------|  
|SQL_COLUMN_AUTO_INCREMENT|Retourne FALSe : Visual FoxPro n’a pas de champs de compteur.|  
|SQL_COLUMN_CASE_SENSITIVE|Retourne toujours TRUE si le type de colonne est caractère.|  
|SQL_COLUMN_LABEL|Retourne le nom de la colonne, qui est également retournée par SQL_COLUMN_NAME.|  
|SQL_COLUMN_MONEY|Retourne la valeur TRUE si le type de colonne est Currency (représenté par un « Y » dans le langage Visual FoxPro).|  
|SQL_COLUMN_OWNER_NAME|Retourne toujours une chaîne vide.|  
|SQL_COLUMN_QUALIFIER_NAME|Retourne toujours une chaîne vide.|  
|SQL_COLUMN_SEARCHABLE|Retourne SQL_UNSEARCHABLE pour les colonnes de type général ; ces colonnes ne peuvent pas être utilisées dans une clause WHERE.<br /><br /> Retourne SQL_SEARCHABLE pour les colonnes de type caractère ou Mémo avec NOCPTRANS non défini ; ces colonnes peuvent être utilisées dans une clause WHERE avec n’importe quel opérateur de comparaison.<br /><br /> Retourne SQL_ALL_EXCEPT_LIKE pour tous les autres types de colonnes ; ces colonnes peuvent être utilisées dans une clause WHERE avec tous les opérateurs de comparaison, sauf LIKE.|  
|SQL_COLUMN_TABLE_NAME|Retourne toujours une chaîne vide.|  
  
 Pour plus d’informations, consultez [SQLColAttributes](../../odbc/reference/syntax/sqlcolattributes-function.md) dans le *Guide de référence du programmeur ODBC*.
