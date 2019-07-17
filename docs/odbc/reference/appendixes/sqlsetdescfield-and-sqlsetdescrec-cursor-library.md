---
title: SQLSetDescField et SQLSetDescRec (bibliothèque de curseurs) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetDescField function [ODBC], Cursor Library
- SQLSetDescRec function [ODBC], Cursor Library
ms.assetid: 4ccff067-85cd-4bfa-a6cd-7f28051fb5b9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5a21af2a2067498a3ec495013554b70d6a86455a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68125574"
---
# <a name="sqlsetdescfield-and-sqlsetdescrec-cursor-library"></a>SQLSetDescField et SQLSetDescRec (bibliothèque de curseurs)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans tout nouveau développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser les fonctionnalités de curseur du pilote.  
  
 Cette rubrique explique comment utiliser le **SQLSetDescField** et **SQLSetDescRec** fonctions dans la bibliothèque de curseurs. Pour obtenir des informations générales sur ces fonctions, consultez [SQLSetDescField, fonction](../../../odbc/reference/syntax/sqlsetdescfield-function.md) et [SQLSetDescRec, fonction](../../../odbc/reference/syntax/sqlsetdescrec-function.md).  
  
 La bibliothèque de curseurs exécute **SQLSetDescField** lorsqu’elle est appelée pour retourner la valeur des champs définie pour les colonnes de signet :  
  
 SQL_DESC_DATA_PTR  
  
 SQL_DESC_INDICATOR_PTR  
  
 SQL_DESC_OCTET_LENGTH_PTR  
  
 SQL_DESC_LENGTH  
  
 SQL_DESC_OCTET_LENGTH  
  
 SQL_DESC_DATETIME_INTERVAL_CODE  
  
 SQL_DESC_SCALE  
  
 SQL_DESC_PRECISION  
  
 SQL_DESC_TYPE  
  
 SQL_DESC_NAME  
  
 SQL_DESC_UNNAMED  
  
 SQL_DESC_NULLABLE  
  
 La bibliothèque de curseurs exécute les appels à **SQLSetDescRec** pour une colonne de signet.  
  
 Lorsque vous travaillez avec une application ODBC *2.x* pilote, la bibliothèque de curseurs retourne SQLSTATE HY090 (longueur de chaîne ou de mémoire tampon non valide) lorsque **SQLSetDescField** ou **SQLSetDescRec** est appelée Pour définir le champ SQL_DESC_OCTET_LENGTH pour l’enregistrement de signet d’un ARD sur une valeur non égale à 4. Lorsque vous travaillez avec une application ODBC *3.x* pilote, la bibliothèque de curseurs permet d’être n’importe quelle taille de la mémoire tampon.  
  
 La bibliothèque de curseurs exécute **SQLSetDescField** lorsqu’elle est appelée pour retourner la valeur du champ SQL_DESC_BIND_OFFSET_PTR, SQL_DESC_BIND_TYPE, SQL_DESC_ROW_ARRAY_SIZE ou SQL_DESC_ROW_STATUS_PTR. Ces champs peuvent être retournées pour n’importe quelle ligne, pas seulement la ligne du signet.  
  
 La bibliothèque de curseurs n’exécute pas **SQLSetDescField** pour modifier n’importe quel champ de descripteur autres que les champs mentionnés précédemment. Si une application appelle **SQLSetDescField** pour définir tout autre champ lors du chargement de la bibliothèque de curseurs, l’appel est passé au pilote.  
  
 La bibliothèque de curseurs prend en charge la modification dynamique des champs SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR et SQL_DESC_OCTET_LENGTH_PTR de n’importe quelle ligne d’un descripteur de ligne d’application (après un appel à **SQLExtendedFetch**, **SQLFetch**, ou **SQLFetchScroll**). Le champ SQL_DESC_OCTET_LENGTH_PTR peut être modifié à un pointeur null uniquement à annuler la liaison de la mémoire tampon de longueur pour une colonne.  
  
 La bibliothèque de curseurs ne prend pas en charge la modification du champ SQL_DESC_BIND_TYPE dans un APD ou le ARD lorsqu’un curseur est ouvert. Le champ SQL_DESC_BIND_TYPE peut être modifié uniquement une fois que le curseur est fermé et avant l’ouverture d’un nouveau curseur. Les seuls champs de descripteur que la bibliothèque de curseurs prend en charge la modification quand le curseur est ouvert sont SQL_DESC_ARRAY_STATUS_PTR, SQL_DESC_BIND_OFFSET_PTR, SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR, SQL_DESC_OCTET_LENGTH_PTR et SQL_DESC_ROWS_PROCESSED_ PTR.  
  
 La bibliothèque de curseurs ne prend pas en charge la modification du champ SQL_DESC_COUNT de la ARD après **SQLExtendedFetch** ou **SQLFetchScroll** a été appelée et avant que le curseur a été fermé.
