---
title: "SQLRowCount (bibliothèque de curseurs) | Documents Microsoft"
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
- SQLRowCount function [ODBC], Cursor Library
ms.assetid: 781cf5a5-325e-4523-8633-d96d9e98277c
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9460f4f4bbc522fc421b7e40b261fe17a8410a09
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="sqlrowcount-cursor-library"></a>SQLRowCount (bibliothèque de curseurs)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans tout nouveau développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser les fonctionnalités de curseur du pilote.  
  
 Cette rubrique décrit l’utilisation de la **SQLRowCount** fonction dans la bibliothèque de curseurs. Pour des informations générales sur **SQLRowCount**, consultez [SQLRowCount, fonction](../../../odbc/reference/syntax/sqlrowcount-function.md).  
  
 Lorsqu’une application appelle **SQLRowCount** avec l’instruction associée au curseur, la bibliothèque de curseurs retourne le nombre de lignes de données qu’il a récupéré à partir du pilote.  
  
 Lorsqu’une application appelle **SQLRowCount** avec l’instruction associée à une mise à jour positionnée ou d’une instruction delete, la bibliothèque de curseurs retourne le nombre de lignes affectées par l’instruction.  
  
 Lorsqu’une application appelle **SQLRowCount** après un **sélectionnez** instruction, la bibliothèque de curseurs retourne -1.
