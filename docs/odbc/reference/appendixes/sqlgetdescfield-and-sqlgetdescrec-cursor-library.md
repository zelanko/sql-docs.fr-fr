---
title: SQLGetDescField et SQLGetDescRec (bibliothèque de curseurs) | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 853a364b61b63d58da93111c75db0d7d723ee49b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68073914"
---
# <a name="sqlgetdescfield-and-sqlgetdescrec-cursor-library"></a>SQLGetDescField et SQLGetDescRec (bibliothèque de curseurs)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans tout nouveau développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser les fonctionnalités de curseur du pilote.  
  
 Cette rubrique explique comment utiliser le **SQLGetDescField** et **SQLGetDescRec** fonctions dans la bibliothèque de curseurs. Pour obtenir des informations générales sur ces fonctions, consultez [SQLGetDescField, fonction](../../../odbc/reference/syntax/sqlgetdescfield-function.md) et [SQLGetDescRec, fonction](../../../odbc/reference/syntax/sqlgetdescrec-function.md).  
  
 La bibliothèque de curseurs exécute **SQLGetDescRec** pour retourner les métadonnées pour les colonnes à signets. La bibliothèque de curseurs exécute **SQLGetDescField** pour retourner les mêmes champs retournés par **SQLGetDescRec**, qui sont SQL_DESC_NAME, SQL_DESC_TYPE, SQL_DESC_DATETIME_INTERVAL_CODE, SQL_DESC_OCTET_ LONGUEUR, SQL_DESC_PRECISION, SQL_DESC_SCALE et SQL_DESC_NULLABLE. Par souci de cohérence, **SQLGetDescField** retourne également la définition de SQL_DESC_UNNAMED.  
  
 La bibliothèque de curseurs exécute **SQLGetDescField** lorsqu’elle est appelée pour retourner les champs de la valeur des éléments suivants sont définis pour la liaison de colonnes à signets : SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR, SQL_DESC_OCTET_LENGTH_PTR et SQL_DESC_LENGTH.  
  
 La bibliothèque de curseurs exécute **SQLGetDescField** lorsqu’elle est appelée pour retourner la valeur du champ SQL_DESC_BIND_OFFSET_PTR, SQL_DESC_BIND_TYPE, SQL_DESC_ROW_ARRAY_SIZE ou SQL_DESC_ROW_STATUS_PTR. Ces champs peuvent être retournées pour n’importe quelle ligne, pas seulement la ligne du signet.  
  
 Si une application appelle **SQLGetDescField** pour retourner la valeur de n’importe quel champ autres que celles mentionnées précédemment, la bibliothèque de curseurs passe l’appel au pilote.
