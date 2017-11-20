---
title: "SQLSetConnectAttr (bibliothèque de curseurs) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLSetConnectAttr function [ODBC], Cursor Library
ms.assetid: 6f70bbd0-a057-49ef-8b05-4c80b58fc6e6
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: bf6a14b8215f981e5e0e9c0ca6e9b2e1a2269f65
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsetconnectattr-cursor-library"></a>SQLSetConnectAttr (bibliothèque de curseurs)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans tout nouveau développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser les fonctionnalités de curseur du pilote.  
  
 Cette rubrique décrit l’utilisation de la **SQLSetConnectAttr** fonction dans la bibliothèque de curseurs. Pour des informations générales sur **SQLSetConnectAttr**, consultez [fonction SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md).  
  
 Une application appelle **SQLSetConnectAttr** avec l’attribut SQL_ATTR_ODBC_CURSORS pour spécifier si la bibliothèque de curseurs est toujours utilisée, utilisée si le pilote ne prend pas en charge les curseurs de défilement ou jamais utilisée. La bibliothèque de curseurs suppose qu’un pilote prend en charge les curseurs de défilement si elle retourne SQL_CA1_RELATIVE SQL_STATIC_CURSOR_ATTRIBUTES1 type d’informations dans **SQLGetInfo**.  
  
 L’application doit appeler **SQLSetConnectAttr** pour spécifier l’utilisation de la bibliothèque curseur après l’appel **SQLAllocHandle** avec un *HandleType* de SQL_HANDLE_DBC pour allouer la connexion et avant de se connecter à la source de données. Si une application appelle **SQLSetConnectAttr** avec l’attribut SQL_ATTR_ODBC_CURSORS pendant que la connexion est toujours active, la bibliothèque de curseurs retourne une erreur.  
  
 Pour définir un attribut d’instruction pris en charge par la bibliothèque de curseurs pour toutes les instructions associées à une connexion, une application doit appeler **SQLSetConnectAttr** pour cet attribut d’instruction une fois la connexion à la source de données et avant d’ouvrir le curseur. Si une application appelle **SQLSetConnectAttr** avec une instruction attribut et un curseur est ouvert dans une instruction associée à la connexion, l’attribut d’instruction ne sera pas appliqué à cette instruction jusqu'à ce que le curseur est fermé et rouvert.

