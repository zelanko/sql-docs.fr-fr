---
title: SQLGetData et curseurs de bloc | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- cursors [ODBC], block
- SQLGetData function [ODBC], block cursors
- block cursors [ODBC]
- result sets [ODBC], block cursors
ms.assetid: 12599cdc-7725-4faf-bcae-e163ea0f5851
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a14c98f045fd974b404209cc998496dc5fa7193e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63149066"
---
# <a name="sqlgetdata-and-block-cursors"></a>SQLGetData et curseurs de bloc
**SQLGetData** opère sur une seule colonne d’une ligne unique et ne peut pas extraire un tableau contenant les données provenant de plusieurs lignes. Il s’agit, car l’utilisation principale de **SQLGetData** consiste à extraire des données de type long dans les parties, et il est peu ou aucune raison pour plus d’une ligne à la fois.  
  
 Pour utiliser **SQLGetData** avec un curseur de bloc, une application appelle d’abord **SQLSetPos** pour positionner le curseur sur une seule ligne. Il appelle ensuite **SQLGetData** pour une colonne de cette ligne. Toutefois, ce comportement est facultatif. Pour déterminer si un pilote prend en charge l’utilisation de **SQLGetData** avec les curseurs de bloc, une application appelle **SQLGetInfo** avec l’option SQL_GETDATA_EXTENSIONS.
