---
title: Comparaison de signets | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], bookmarks
- comparing bookmarks [ODBC]
- bookmarks [ODBC]
ms.assetid: ea347635-fbe3-41c1-b537-4048b7c0f7da
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 44da652ad1e52934fa48f32b1b2f88b30212ad3b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68083303"
---
# <a name="comparing-bookmarks"></a>Comparaison de signets
Étant donné que les signets sont comparables à l’octet, ils peuvent être comparées pour l’égalité ou d’inégalité. Pour ce faire, une application traite chaque signet comme un tableau d’octets et compare les deux signets octet par octet. Étant donné que les signets sont assurées d’être distinctes uniquement au sein d’un jeu de résultats, il n’a aucun sens pour comparer des signets qui ont été obtenues à partir de jeux de résultats.
