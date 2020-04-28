---
title: SQLRowCount (bibliothèque de curseurs) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLRowCount function [ODBC], Cursor Library
ms.assetid: 781cf5a5-325e-4523-8633-d96d9e98277c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bf9fe597f54ecb4bc82439251e2228ac5fdc4ea3
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300589"
---
# <a name="sqlrowcount-cursor-library"></a>SQLRowCount (bibliothèque de curseurs)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans de nouveaux travaux de développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande l’utilisation de la fonctionnalité de curseur du pilote.  
  
 Cette rubrique traite de l’utilisation de la fonction **SQLRowCount** dans la bibliothèque de curseurs. Pour obtenir des informations générales sur **SQLRowCount**, consultez [fonction SQLRowCount](../../../odbc/reference/syntax/sqlrowcount-function.md).  
  
 Quand une application appelle **SQLRowCount** avec l’instruction associée au curseur, la bibliothèque de curseurs retourne le nombre de lignes de données qu’elle a récupérées à partir du pilote.  
  
 Quand une application appelle **SQLRowCount** avec l’instruction associée à une instruction UPDATE ou DELETE positionnée, la bibliothèque de curseurs retourne le nombre de lignes affectées par l’instruction.  
  
 Quand une application appelle **SQLRowCount** après une instruction **Select** , la bibliothèque de curseurs retourne-1.
