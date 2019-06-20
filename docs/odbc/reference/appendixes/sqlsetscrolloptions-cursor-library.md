---
title: SQLSetScrollOptions (bibliothèque de curseurs) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetScrollOptions function [ODBC], Cursor Library
ms.assetid: c5c0ac6d-a6c1-4077-8186-1644df1944f8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e1fe6765c0ff8a057aac8e86ea5ad4aa1ac388b4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63297490"
---
# <a name="sqlsetscrolloptions-cursor-library"></a>SQLSetScrollOptions (bibliothèque de curseurs)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans tout nouveau développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser les fonctionnalités de curseur du pilote.  
  
 Cette rubrique explique comment utiliser le **SQLSetScrollOptions** fonction dans la bibliothèque de curseurs. Pour des informations générales sur **SQLSetScrollOptions**, consultez [sqlsetscrolloptions, fonction](../../../odbc/reference/syntax/sqlsetscrolloptions-function.md).  
  
 Prend en charge de la bibliothèque de curseurs **SQLSetScrollOptions** uniquement pour la compatibilité descendante ; applications doivent utiliser les attributs d’instruction SQL_ATTR_CONCURRENCY et SQL_ATTR_ROW_ARRAY_SIZE SQL_ATTR_CURSOR_TYPE à la place.
