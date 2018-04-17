---
title: SQLGetFunctions (bibliothèque de curseurs) | Documents Microsoft
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
ms.topic: article
helpviewer_keywords:
- SQLGetFunctions function [ODBC], Cursor Library
ms.assetid: 931acd12-4eb6-4a78-9a77-157a18a9a2d0
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1d1f4c68474c53c369b46737aa3c41c9cf7146c0
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="sqlgetfunctions-cursor-library"></a>SQLGetFunctions (bibliothèque de curseurs)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans tout nouveau développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser les fonctionnalités de curseur du pilote.  
  
 Cette rubrique décrit l’utilisation de la **SQLGetFunctions** fonction dans la bibliothèque de curseurs. Pour des informations générales sur **SQLGetFunctions**, consultez [fonction SQLGetFunctions](../../../odbc/reference/syntax/sqlgetfunctions-function.md).  
  
 Lorsque vous appelez **SQLGetFunctions**, la bibliothèque de curseurs retourne la prise en charge **SQLExtendedFetch**, **SQLFetchScroll**, **SQLSetPos**, et **SQLSetScrollOptions**, outre les fonctions prises en charge par le pilote.
