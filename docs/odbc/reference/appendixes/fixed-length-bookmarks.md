---
title: Signets de longueur fixe | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- backward compatibility [ODBC], bookmarks
- bookmarks [ODBC]
- compatibility [ODBC], bookmarks
- fixed-length bookmarks [ODBC]
ms.assetid: cbd8185e-fb03-408f-b80b-1a2e164534fd
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 21af6ef1be21e000d25582151650f274fe3561a4
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67793372"
---
# <a name="fixed-length-bookmarks"></a>Signets de longueur fixe
Si une application ODBC *3.x* pilote doit fonctionner avec une application ODBC *2.x* application que les signets de longueur fixe utilise, le pilote doivent prendre en charge les éléments suivants :  
  
-   SQL_UB_ON en tant que valeur pour l’option d’instruction SQL_USE_BOOKMARKS. (SQL_UB_ON est déconseillée dans ODBC *3.x*.)  
  
-   L’option d’instruction SQL_GET_BOOKMARK.
