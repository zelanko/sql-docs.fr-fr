---
title: Les curseurs de bloc et de SQLGetData | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cursors [ODBC], block
- SQLGetData function [ODBC], block cursors
- block cursors [ODBC]
- result sets [ODBC], block cursors
ms.assetid: 12599cdc-7725-4faf-bcae-e163ea0f5851
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 12b3c2dc5693f141f24b9209a12923b18a9859e5
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="sqlgetdata-and-block-cursors"></a>SQLGetData et les curseurs de bloc
**SQLGetData** opère sur une seule colonne d’une ligne unique et ne peut pas extraire un tableau contenant les données provenant de plusieurs lignes. Il s’agit, car l’utilisation principale de **SQLGetData** consiste à extraire des données de type long dans les composants, et il est peu ou aucune raison de cela pour plusieurs lignes à la fois.  
  
 Pour utiliser **SQLGetData** avec un curseur de bloc, une application appelle d’abord **SQLSetPos** pour positionner le curseur sur une seule ligne. Il appelle ensuite **SQLGetData** pour une colonne de la ligne. Toutefois, ce comportement est facultatif. Pour déterminer si un pilote prend en charge l’utilisation de **SQLGetData** avec les curseurs de bloc, une application appelle **SQLGetInfo** avec l’option SQL_GETDATA_EXTENSIONS.
