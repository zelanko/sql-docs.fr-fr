---
title: SQLSetConnectAttr (bibliothèque de curseurs) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetConnectAttr function [ODBC], Cursor Library
ms.assetid: 6f70bbd0-a057-49ef-8b05-4c80b58fc6e6
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 73d1369a2bce0327ac3367d33f0894bdcfab8205
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68125582"
---
# <a name="sqlsetconnectattr-cursor-library"></a>SQLSetConnectAttr (bibliothèque de curseurs)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans tout nouveau développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser les fonctionnalités de curseur du pilote.  
  
 Cette rubrique explique comment utiliser le **SQLSetConnectAttr** fonction dans la bibliothèque de curseurs. Pour des informations générales sur **SQLSetConnectAttr**, consultez [fonction SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md).  
  
 Une application appelle **SQLSetConnectAttr** avec l’attribut SQL_ATTR_ODBC_CURSORS pour spécifier si la bibliothèque de curseurs est toujours utilisée, utilisée si le pilote ne prend pas en charge les curseurs avec défilement ou jamais utilisée. La bibliothèque de curseurs suppose qu’un pilote prend en charge les curseurs avec défilement si elle retourne SQL_CA1_RELATIVE pour le type d’informations SQL_STATIC_CURSOR_ATTRIBUTES1 dans **SQLGetInfo**.  
  
 L’application doit appeler **SQLSetConnectAttr** pour spécifier l’utilisation de la bibliothèque curseur après l’appel **SQLAllocHandle** avec un *HandleType* de SQL_HANDLE_DBC pour allouer la connexion et avant de se connecter à la source de données. Si une application appelle **SQLSetConnectAttr** avec l’attribut SQL_ATTR_ODBC_CURSORS pendant que la connexion est toujours active, la bibliothèque de curseurs retourne une erreur.  
  
 Pour définir un attribut d’instruction pris en charge par la bibliothèque de curseurs pour toutes les instructions associées à une connexion, une application doit appeler **SQLSetConnectAttr** pour cet attribut d’instruction une fois la connexion à la source de données et avant qu’elle Ouvre le curseur. Si une application appelle **SQLSetConnectAttr** avec une instruction attribut et un curseur est ouvert sur une instruction associée à la connexion, l’attribut d’instruction ne sera pas appliqué à cette instruction jusqu'à ce que le curseur est fermé et rouvert.
