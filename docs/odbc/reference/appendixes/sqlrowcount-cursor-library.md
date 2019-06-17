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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9b3dcd9c348d83dad1e295e253cb37768fbb0abb
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63473045"
---
# <a name="sqlrowcount-cursor-library"></a>SQLRowCount (bibliothèque de curseurs)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans tout nouveau développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser les fonctionnalités de curseur du pilote.  
  
 Cette rubrique explique comment utiliser le **SQLRowCount** fonction dans la bibliothèque de curseurs. Pour des informations générales sur **SQLRowCount**, consultez [SQLRowCount, fonction](../../../odbc/reference/syntax/sqlrowcount-function.md).  
  
 Lorsqu’une application appelle **SQLRowCount** avec l’instruction associée au curseur, la bibliothèque de curseurs retourne le nombre de lignes de données qu’il a récupéré à partir du pilote.  
  
 Lorsqu’une application appelle **SQLRowCount** avec l’instruction associée à une mise à jour positionnée ou d’une instruction delete, la bibliothèque de curseurs retourne le nombre de lignes affectées par l’instruction.  
  
 Lorsqu’une application appelle **SQLRowCount** après un **sélectionnez** instruction, la bibliothèque de curseurs retourne -1.
