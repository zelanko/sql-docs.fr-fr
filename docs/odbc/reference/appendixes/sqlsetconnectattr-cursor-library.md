---
title: SQLSetConnectAttr (Cursor Library) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a87c85d727fb9eb2fc27613b9eecd3fe0ec51b58
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300539"
---
# <a name="sqlsetconnectattr-cursor-library"></a>SQLSetConnectAttr (bibliothèque de curseurs)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans de nouveaux travaux de développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser la fonctionnalité du curseur du conducteur.  
  
 Ce sujet traite de l’utilisation de la fonction **SQLSetConnectAttr** dans la bibliothèque de curseurs. Pour plus d’informations générales sur **SQLSetConnectAttr**, voir [SQLSetConnectAttr Function](../../../odbc/reference/syntax/sqlsetconnectattr-function.md).  
  
 Une application appelle **SQLSetConnectAttr** avec l’attribut SQL_ATTR_ODBC_CURSORS pour spécifier si la bibliothèque de curseurs est toujours utilisée, utilisée si le conducteur ne prend pas en charge les curseurs défilementables, ou jamais utilisé. La bibliothèque de curseurs suppose qu’un conducteur prend en charge les curseurs défilementables s’il retourne SQL_CA1_RELATIVE pour le type d’information SQL_STATIC_CURSOR_ATTRIBUTES1 dans **SQLGetInfo**.  
  
 L’application doit appeler **SQLSetConnectAttr** pour spécifier l’utilisation de la bibliothèque de curseur après avoir appelé **SQLAllocHandle** avec un *HandleType* de SQL_HANDLE_DBC pour allouer la connexion et avant qu’il ne se connecte à la source de données. Si une application appelle **SQLSetConnectAttr** avec l’attribut SQL_ATTR_ODBC_CURSORS pendant que la connexion est toujours active, la bibliothèque de curseur renvoie une erreur.  
  
 Pour définir un attribut de déclaration pris en charge par la bibliothèque de curseurs pour toutes les instructions associées à une connexion, une application doit appeler **SQLSetConnectAttr** pour cet attribut de déclaration après qu’il se connecte à la source de données et avant qu’il ouvre le curseur. Si une application appelle **SQLSetConnectAttr** avec un attribut de relevé et qu’un curseur est ouvert sur une déclaration associée à la connexion, l’attribut de déclaration ne sera pas appliqué à cette déclaration tant que le curseur n’aura pas été fermé et rouvert.
