---
title: SQLColAttributes (Visual FoxPro ODBC Driver) Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307910"
---
# <a name="sqlcolattributes-visual-foxpro-odbc-driver"></a>SQLColAttributes (pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Ce sujet contient des informations visuelles spécifiques à FoxPro ODBC Driver. Pour plus d’informations générales sur cette fonction, voir le sujet approprié sous [ODBC API Référence](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Soutien: Complet  
  
 Conformité API ODBC : Niveau de base  
  
 Renvoie les informations descripteur pour une colonne dans un ensemble de résultats. Les informations descripteur sont retournées comme une chaîne de caractère, une valeur descripteur-dépendante de 32 bits, ou une valeur d’intégrateur.  
  
> [!NOTE]  
>  **SQLColAttributes** ne peut pas être utilisé pour retourner des informations sur la colonne de signets (colonne 0).  
  
 Le Visual FoxPro ODBC Driver prend en charge toutes les valeurs *fDescType.* Le tableau suivant comprend des commentaires sur la mise en œuvre par le conducteur de valeurs sélectionnées.  
  
|*fDescType*|Commentaire|  
|-----------------|-------------|  
|SQL_COLUMN_AUTO_INCREMENT|Retours FALSE: Visual FoxPro n’a pas de champs de compteur.|  
|SQL_COLUMN_CASE_SENSITIVE|Retourne toujours VRAI si le type de colonne est Caractère.|  
|SQL_COLUMN_LABEL|Retourne le nom de colonne, qui est également retourné par SQL_COLUMN_NAME.|  
|SQL_COLUMN_MONEY|Retourne VRAI si le type de colonne est Monnaie (représenté par un "Y" dans la langue Visuelle FoxPro).|  
|SQL_COLUMN_OWNER_NAME|Retourne toujours une chaîne vide.|  
|SQL_COLUMN_QUALIFIER_NAME|Retourne toujours une chaîne vide.|  
|SQL_COLUMN_SEARCHABLE|Retours SQL_UNSEARCHABLE pour les colonnes de type général; ces colonnes ne peuvent pas être utilisées dans une clause WHERE.<br /><br /> Retourne SQL_SEARCHABLE pour les colonnes de type Caractère ou Memo avec NOCPTRANS non défini; ces colonnes peuvent être utilisées dans une clause WHERE avec n’importe quel opérateur de comparaison.<br /><br /> Retours SQL_ALL_EXCEPT_LIKE pour tous les autres types de colonnes; ces colonnes peuvent être utilisées dans une clause WHERE avec tous les opérateurs de comparaison, sauf LIKE.|  
|SQL_COLUMN_TABLE_NAME|Retourne toujours une chaîne vide.|  
  
 Pour plus d’informations, voir [SQLColAttributes](../../odbc/reference/syntax/sqlcolattributes-function.md) dans la *référence du programmeur ODBC*.
