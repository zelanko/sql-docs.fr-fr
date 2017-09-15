---
title: "SQLSetScrollOptions (bibliothèque de curseurs) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLSetScrollOptions function [ODBC], Cursor Library
ms.assetid: c5c0ac6d-a6c1-4077-8186-1644df1944f8
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c029dbb9906c4d7d738e0e705dd02e437b6c1bec
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsetscrolloptions-cursor-library"></a>SQLSetScrollOptions (bibliothèque de curseurs)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans tout nouveau développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser les fonctionnalités de curseur du pilote.  
  
 Cette rubrique décrit l’utilisation de la **SQLSetScrollOptions** fonction dans la bibliothèque de curseurs. Pour des informations générales sur **SQLSetScrollOptions**, consultez [SQLSetScrollOptions fonction](../../../odbc/reference/syntax/sqlsetscrolloptions-function.md).  
  
 Prend en charge de la bibliothèque de curseurs **SQLSetScrollOptions** uniquement pour la compatibilité descendante ; applications doivent utiliser les attributs d’instruction SQL_ATTR_CONCURRENCY et SQL_ATTR_ROW_ARRAY_SIZE SQL_ATTR_CURSOR_TYPE à la place.
