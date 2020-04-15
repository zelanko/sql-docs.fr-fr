---
title: SQLGetDescField et SQLGetDescRec (Cursor Library) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetDescField function [ODBC], Cursor Library
- SQLGetDescRec function [ODBC], Cursor Library
ms.assetid: 1a801f22-6fea-48aa-a723-3187a2ad852b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 49ceea6b6180e1b51f2f103f74412c3e2b4cbe02
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307830"
---
# <a name="sqlgetdescfield-and-sqlgetdescrec-cursor-library"></a>SQLGetDescField et SQLGetDescRec (bibliothèque de curseurs)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans de nouveaux travaux de développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser la fonctionnalité du curseur du conducteur.  
  
 Ce sujet traite de l’utilisation des fonctions **SQLGetDescField** et **SQLGetDescRec** dans la bibliothèque des curseurs. Pour plus d’informations générales sur ces fonctions, voir [SQLGetDescField Function](../../../odbc/reference/syntax/sqlgetdescfield-function.md) et [SQLGetDescRec Function](../../../odbc/reference/syntax/sqlgetdescrec-function.md).  
  
 La bibliothèque de curseurs exécute **SQLGetDescRec** pour retourner les métadonnées pour les colonnes de signets. La bibliothèque de curseurs exécute **SQLGetDescField** pour retourner les mêmes champs retournés par **SQLGetDescRec**, qui sont SQL_DESC_NAME, SQL_DESC_TYPE, SQL_DESC_DATETIME_INTERVAL_CODE, SQL_DESC_OCTET_LENGTH, SQL_DESC_PRECISION, SQL_DESC_SCALE et SQL_DESC_NULLABLE. Pour plus de cohérence, **SQLGetDescField** revient également SQL_DESC_UNNAMED.  
  
 La bibliothèque de curseurs exécute **SQLGetDescField** lorsqu’elle est appelée à retourner la valeur des champs suivants qui sont définis pour les colonnes de signets contraignantes : SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR, SQL_DESC_OCTET_LENGTH_PTR et SQL_DESC_LENGTH.  
  
 La bibliothèque de curseurs exécute **SQLGetDescField** lorsqu’elle est appelée à retourner la valeur du champ SQL_DESC_BIND_OFFSET_PTR, SQL_DESC_BIND_TYPE, SQL_DESC_ROW_ARRAY_SIZE ou SQL_DESC_ROW_STATUS_PTR. Ces champs peuvent être retournés pour n’importe quelle rangée, pas seulement la ligne de signet.  
  
 Si une demande appelle **SQLGetDescField** pour retourner la valeur de n’importe quel champ autre que ceux mentionnés précédemment, la bibliothèque de curseur passe l’appel au conducteur.
