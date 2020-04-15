---
title: SQLRowCount (Cursor Library) Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300589"
---
# <a name="sqlrowcount-cursor-library"></a>SQLRowCount (bibliothèque de curseurs)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans de nouveaux travaux de développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser la fonctionnalité du curseur du conducteur.  
  
 Ce sujet traite de l’utilisation de la fonction **SQLRowCount** dans la bibliothèque de curseurs. Pour plus d’informations sur **SQLRowCount**, voir [SQLRowCount Function](../../../odbc/reference/syntax/sqlrowcount-function.md).  
  
 Lorsqu’une demande appelle **SQLRowCount** avec l’instruction associée au curseur, la bibliothèque de curseur renvoie le nombre de rangées de données qu’elle a récupérées au conducteur.  
  
 Lorsqu’une application appelle **SQLRowCount** avec l’instruction associée à une mise à jour ou à une déclaration de suppression positionnée, la bibliothèque de curseur renvoie le nombre de lignes touchées par l’énoncé.  
  
 Lorsqu’une demande appelle **SQLRowCount** après une déclaration **SELECT,** la bibliothèque de curseurs renvoie -1.
