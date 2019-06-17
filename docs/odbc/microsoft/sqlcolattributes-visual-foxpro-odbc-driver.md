---
title: SQLColAttributes (pilote ODBC de Visual FoxPro) | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e34929315d3a3548799bc605dbb8f3c4a2f665d0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62928164"
---
# <a name="sqlcolattributes-visual-foxpro-odbc-driver"></a>SQLColAttributes (pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Cette rubrique contient des informations spécifiques au pilote ODBC Visual FoxPro. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Prise en charge : Complète  
  
 Conformité d’API ODBC : Niveau principal  
  
 Retourne des informations de descripteur pour une colonne dans un jeu de résultats. Informations de descripteur sont retournées comme une chaîne de caractères, une valeur de descripteur dépendant de 32 bits ou une valeur entière.  
  
> [!NOTE]  
>  **SQLColAttributes** ne peut pas être utilisé pour retourner des informations sur la signet colonne (0).  
  
 Le pilote ODBC Visual FoxPro prend en charge tous les *fDescType* valeurs. Le tableau suivant inclut des commentaires sur l’implémentation du pilote de valeurs sélectionnées.  
  
|*fDescType*|Commentaire|  
|-----------------|-------------|  
|SQL_COLUMN_AUTO_INCREMENT|Retourne la valeur FALSE : Visual FoxPro comporte aucun champ de compteur.|  
|SQL_COLUMN_CASE_SENSITIVE|Retourne toujours la valeur TRUE si le type de colonne est le caractère.|  
|SQL_COLUMN_LABEL|Retourne le nom de colonne, qui est également renvoyé par SQL_COLUMN_NAME.|  
|SQL_COLUMN_MONEY|Retourne la valeur TRUE si le type de colonne est monétaire (représenté par un « Y » dans le langage Visual FoxPro).|  
|SQL_COLUMN_OWNER_NAME|Retourne toujours une chaîne vide.|  
|SQL_COLUMN_QUALIFIER_NAME|Retourne toujours une chaîne vide.|  
|SQL_COLUMN_SEARCHABLE|Retourne SQL_UNSEARCHABLE pour les colonnes de type général ; ces colonnes ne peut pas être utilisés dans une clause WHERE.<br /><br /> Retourne SQL_SEARCHABLE pour les colonnes de type caractère ou Mémo avec NOCPTRANS pas définies. ces colonnes peuvent être utilisées dans une clause WHERE avec tout opérateur de comparaison.<br /><br /> Retourne SQL_ALL_EXCEPT_LIKE pour tous les autres types de colonne ; ces colonnes peuvent être utilisées dans une clause WHERE avec tous les opérateurs de comparaison à l’exception de type.|  
|SQL_COLUMN_TABLE_NAME|Retourne toujours une chaîne vide.|  
  
 Pour plus d’informations, consultez [SQLColAttributes](../../odbc/reference/syntax/sqlcolattributes-function.md) dans le *de référence du programmeur ODBC*.
