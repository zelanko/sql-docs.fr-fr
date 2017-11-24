---
title: "SQLExtendedFetch (bibliothèque de curseurs) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SQLExtendedFetch function [ODBC], Cursor Library
ms.assetid: 06fbf06f-127b-475c-b636-7b784918475d
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3c900dd244199051ef8c35baf5ae84a328cb3fb2
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="sqlextendedfetch-cursor-library"></a>SQLExtendedFetch (bibliothèque de curseurs)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans tout nouveau développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser les fonctionnalités de curseur du pilote.  
  
 Cette rubrique décrit l’utilisation de la **SQLExtendedFetch** fonction dans la bibliothèque de curseurs. Pour des informations générales sur **SQLExtendedFetch**, consultez [SQLExtendedFetch fonction](../../../odbc/reference/syntax/sqlextendedfetch-function.md).  
  
 La bibliothèque de curseurs implémente **SQLExtendedFetch** en appelant à plusieurs reprises **SQLFetch** dans le pilote.  
  
 La bibliothèque de curseurs prend en charge l’appel **SQLExtendedFetch** avec un *FetchOrientation* de SQL_FETCH_BOOKMARK.  
  
 Lorsque la bibliothèque de curseurs est utilisée, les appels à **SQLExtendedFetch** ne peut pas être combiné avec des appels vers **SQLFetchScroll** ou **SQLFetch**.
