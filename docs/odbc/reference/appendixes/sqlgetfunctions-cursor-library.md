---
title: SQLGetFunctions (bibliothèque de curseurs) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetFunctions function [ODBC], Cursor Library
ms.assetid: 931acd12-4eb6-4a78-9a77-157a18a9a2d0
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1497a7d2ec5951feedb36831ab541413e57152f4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68073936"
---
# <a name="sqlgetfunctions-cursor-library"></a>SQLGetFunctions (bibliothèque de curseurs)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans de nouveaux travaux de développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande l’utilisation de la fonctionnalité de curseur du pilote.  
  
 Cette rubrique traite de l’utilisation de la fonction **SQLGetFunctions** dans la bibliothèque de curseurs. Pour obtenir des informations générales sur **SQLGetFunctions**, consultez [fonction SQLGetFunctions](../../../odbc/reference/syntax/sqlgetfunctions-function.md).  
  
 Lorsque vous appelez **SQLGetFunctions**, la bibliothèque de curseurs retourne la prise en charge de **SQLExtendedFetch**, **SQLFetchScroll**, **SQLSetPos**et **SQLSetScrollOptions**, en plus des fonctions prises en charge par le pilote.
