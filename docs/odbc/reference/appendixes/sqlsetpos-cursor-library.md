---
title: SQLSetPos (Cursor Library) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetPos function [ODBC], Cursor Library
ms.assetid: 574399c3-2bb2-4d19-829c-7c77bd82858d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4c46ef88075a5adbd96138d7d1f03c26712f7ea1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300509"
---
# <a name="sqlsetpos-cursor-library"></a>SQLSetPos (bibliothèque de curseurs)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans de nouveaux travaux de développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser la fonctionnalité du curseur du conducteur.  
  
 Ce sujet traite de l’utilisation de la fonction **SQLSetPos** dans la bibliothèque de curseurs. Pour plus d’informations générales sur **SQLSetPos**, voir [SQLSetPos Function](../../../odbc/reference/syntax/sqlsetpos-function.md).  
  
 La bibliothèque de curseurs ne soutient l’opération SQL_POSITION que pour *l’argument de l’opération* dans **SQLSetPos**. Il ne supporte la valeur SQL_LOCK_NO_CHANGE que pour l’argument *LockType.*  
  
 Si le conducteur ne prend pas en charge les opérations en vrac, la bibliothèque de curseurs renvoie SQLSTATE HYC00 (conducteur non capable) lorsque **SQLSetPos** est appelé avec *RowNumber* égal à 0. Ce comportement du conducteur n’est pas recommandé.  
  
 La bibliothèque de curseurs n’appuie pas les opérations SQL_UPDATE et SQL_DELETE dans un appel à **SQLSetPos**. La bibliothèque de curseurs implémente une mise à jour positionnée ou supprime la déclaration SQL en créant une mise à jour recherchée ou en supprimant l’instruction avec une clause WHERE qui énumère les valeurs stockées dans son cache pour chaque colonne liée. Pour plus d’informations, voir [Mise à jour positionnée de traitement et supprimer les déclarations](../../../odbc/reference/appendixes/processing-positioned-update-and-delete-statements.md).  
  
 Si le conducteur ne prend pas en charge les curseurs statiques, une application fonctionnant avec la bibliothèque de curseur ne doit appeler **SQLSetPos** que sur un ramset récupéré par **SQLExtendedFetch** ou **SQLFetchScroll**, et non par **SQLFetch**. La bibliothèque de curseurs met en œuvre **SQLExtendedFetch** et **SQLFetchScroll** en faisant des appels répétés de **SQLFetch** (avec une taille de rame de 1) dans le conducteur. La bibliothèque de curseurs transmet les appels à **SQLFetch,** d’autre part, jusqu’au conducteur. Si **SQLSetPos** est appelé sur un ramset multirow récupéré par **SQLFetch** lorsque le conducteur ne prend pas en charge les curseurs statiques, l’appel échouera parce que **SQLSetPos** ne fonctionne pas avec des curseurs avant seulement. Cela se produira même si une application a appelé avec succès **SQLSetStmtAttr** pour régler SQL_ATTR_CURSOR_TYPE à SQL_CURSOR_STATIC, que la bibliothèque de curseur prend en charge même si le conducteur ne prend pas en charge les curseurs statiques.
