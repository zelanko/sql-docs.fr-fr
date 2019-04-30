---
title: SQLSetEnvAttr et la bibliothèque de curseurs | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetEnvAttr function [ODBC], Cursor Library
ms.assetid: 59cc8eae-09ae-4796-869a-c5806488ae83
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 74e57f98b7d5e3e1508a960b342521ea5d315a3d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63297533"
---
# <a name="sqlsetenvattr-and-the-cursor-library"></a>SQLSetEnvAttr et la bibliothèque de curseurs
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans tout nouveau développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser les fonctionnalités de curseur du pilote.  
  
 Cette rubrique explique comment utiliser le **SQLSetEnvAttr** fonction avec la bibliothèque de curseurs. Pour des informations générales sur **SQLSetEnvAttr**, consultez [SQLSetEnvAttr, fonction](../../../odbc/reference/syntax/sqlsetenvattr-function.md).  
  
 La bibliothèque de curseurs n’est pas affectée par le paramètre de l’attribut d’environnement SQL_ATTR_ODBC_VERSION, quelle que soit la version du pilote ou une version de l’application.
