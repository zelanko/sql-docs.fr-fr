---
title: SQLExtendedFetch (Cursor Library) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLExtendedFetch function [ODBC], Cursor Library
ms.assetid: 06fbf06f-127b-475c-b636-7b784918475d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fe39b2d2cbbaf72ce3844c35187040589d1dac58
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302060"
---
# <a name="sqlextendedfetch-cursor-library"></a>SQLExtendedFetch (bibliothèque de curseurs)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans de nouveaux travaux de développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser la fonctionnalité du curseur du conducteur.  
  
 Ce sujet traite de l’utilisation de la fonction **SQLExtendedFetch** dans la bibliothèque de curseurs. Pour plus d’informations sur **SQLExtendedFetch**, voir [SQLExtendedFetch Function](../../../odbc/reference/syntax/sqlextendedfetch-function.md).  
  
 La bibliothèque de curseurs met en œuvre **SQLExtendedFetch** en appelant à plusieurs reprises **SQLFetch** dans le conducteur.  
  
 La bibliothèque de curseurs prend en charge **l’appel SQLExtendedFetch** avec une *fetchOrientation* de SQL_FETCH_BOOKMARK.  
  
 Lorsque la bibliothèque de curseurs est utilisée, les appels à **SQLExtendedFetch** ne peuvent pas être mélangés avec des appels à **SQLFetchScroll** ou **SQLFetch**.
