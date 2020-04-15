---
title: SQLSetScrollOptions (Cursor Library) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0099ca5e9bcb3aefdd86e0132f52d110ab64e8a4
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304910"
---
# <a name="sqlsetscrolloptions-cursor-library"></a>SQLSetScrollOptions (bibliothèque de curseurs)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans de nouveaux travaux de développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser la fonctionnalité du curseur du conducteur.  
  
 Ce sujet traite de l’utilisation de la fonction **SQLSetScrollOptions** dans la bibliothèque de curseurs. Pour plus d’informations générales sur **SQLSetScrollOptions**, voir [SQLSetScrollOptions Function](../../../odbc/reference/syntax/sqlsetscrolloptions-function.md).  
  
 La bibliothèque de curseurs ne prend en charge **SQLSetScrollOptions** que pour la compatibilité vers l’arrière; les applications doivent utiliser les attributs SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_TYPE et SQL_ATTR_ROW_ARRAY_SIZE de l’énoncé à la place.
