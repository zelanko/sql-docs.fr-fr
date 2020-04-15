---
title: SQLSetDescField et SQLSetDescRec (Cursor Library) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b85eb84cdf48a1c2a441b8994076a9023d254f2d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300549"
---
# <a name="sqlsetdescfield-and-sqlsetdescrec-cursor-library"></a>SQLSetDescField et SQLSetDescRec (bibliothèque de curseurs)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans de nouveaux travaux de développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser la fonctionnalité du curseur du conducteur.  
  
 Ce sujet traite de l’utilisation des fonctions **SQLSetDescField** et **SQLSetDescRec** dans la bibliothèque des curseurs. Pour plus d’informations générales sur ces fonctions, voir [SQLSetDescField Function](../../../odbc/reference/syntax/sqlsetdescfield-function.md) et [SQLSetDescRec Function](../../../odbc/reference/syntax/sqlsetdescrec-function.md).  
  
 La bibliothèque de curseurs exécute **SQLSetDescField** lorsqu’elle est appelée à retourner la valeur des champs réglés pour les colonnes de signets :  
  
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
  
 La bibliothèque de curseurs exécute des appels à **SQLSetDescRec** pour une colonne de signets.  
  
 Lorsque vous travaillez avec un conducteur ODBC *2.x,* la bibliothèque de curseurs retourne SQLSTATE HY090 (longueur de ficelle ou tampon invalide) lorsque **SQLSetDescField** ou **SQLSetDescRec** est appelé à définir le champ SQL_DESC_OCTET_LENGTH pour le enregistrement de signets d’une ARD à une valeur pas égale à 4. Lorsque vous travaillez avec un conducteur ODBC *3.x,* la bibliothèque de curseurs permet au tampon d’être n’importe quelle taille.  
  
 La bibliothèque de curseurs exécute **SQLSetDescField** lorsqu’elle est appelée à retourner la valeur du champ SQL_DESC_BIND_OFFSET_PTR, SQL_DESC_BIND_TYPE, SQL_DESC_ROW_ARRAY_SIZE ou SQL_DESC_ROW_STATUS_PTR. Ces champs peuvent être retournés pour n’importe quelle rangée, pas seulement la ligne de signet.  
  
 La bibliothèque de curseurs n’exécute pas **SQLSetDescField** pour changer n’importe quel champ descripteur autre que les champs mentionnés précédemment. Si une demande appelle **SQLSetDescField** pour régler n’importe quel autre champ pendant que la bibliothèque de curseur est chargée, l’appel est transmis au conducteur.  
  
 La bibliothèque de curseurs prend en charge la modification des champs SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR et SQL_DESC_OCTET_LENGTH_PTR de toute rangée d’un descripteur de ligne d’application dynamiquement (après un appel à **SQLExtendedFetch**, **SQLFetch**, ou **SQLFetchScroll**). Le champ SQL_DESC_OCTET_LENGTH_PTR peut être changé en un pointeur nul seulement pour délier le tampon de longueur pour une colonne.  
  
 La bibliothèque de curseurs n’est pas en faveur de la modification du champ SQL_DESC_BIND_TYPE dans une DPA ou une ARD lorsqu’un curseur est ouvert. Le champ SQL_DESC_BIND_TYPE ne peut être modifié qu’après la fermeture du curseur et avant l’ouverture d’un nouveau curseur. Les seuls champs descripteur que la bibliothèque de curseurs prend en charge en changeant lorsqu’un curseur est ouvert sont SQL_DESC_ARRAY_STATUS_PTR, SQL_DESC_BIND_OFFSET_PTR, SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR, SQL_DESC_OCTET_LENGTH_PTR et SQL_DESC_ROWS_PROCESSED_PTR.  
  
 La bibliothèque de curseurs n’est pas en faveur de la modification du champ SQL_DESC_COUNT de l’ARD après **que SQLExtendedFetch ou** **SQLFetchScroll** a été appelé et avant que le curseur n’ait été fermé.
