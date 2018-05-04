---
title: Les curseurs de bloc et de SQLGetData | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- cursors [ODBC], block
- SQLGetData function [ODBC], block cursors
- block cursors [ODBC]
- result sets [ODBC], block cursors
ms.assetid: 12599cdc-7725-4faf-bcae-e163ea0f5851
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8642e5c228bb0e7976099d2151fe36f4db683f27
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="sqlgetdata-and-block-cursors"></a>SQLGetData et les curseurs de bloc
**SQLGetData** opère sur une seule colonne d’une ligne unique et ne peut pas extraire un tableau contenant les données provenant de plusieurs lignes. Il s’agit, car l’utilisation principale de **SQLGetData** consiste à extraire des données de type long dans les composants, et il est peu ou aucune raison de cela pour plusieurs lignes à la fois.  
  
 Pour utiliser **SQLGetData** avec un curseur de bloc, une application appelle d’abord **SQLSetPos** pour positionner le curseur sur une seule ligne. Il appelle ensuite **SQLGetData** pour une colonne de la ligne. Toutefois, ce comportement est facultatif. Pour déterminer si un pilote prend en charge l’utilisation de **SQLGetData** avec les curseurs de bloc, une application appelle **SQLGetInfo** avec l’option SQL_GETDATA_EXTENSIONS.
