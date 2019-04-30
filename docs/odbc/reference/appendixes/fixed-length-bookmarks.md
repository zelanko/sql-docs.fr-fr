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
ms.openlocfilehash: e40947dc4dbad0830444870ea7e2d0c663490b25
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63188971"
---
# <a name="fixed-length-bookmarks"></a>Signets de longueur fixe
Si un ODBC 3 *.x* pilote doit fonctionner avec une API ODBC 2. *x* application que les signets de longueur fixe utilise, le pilote doivent prendre en charge les éléments suivants :  
  
-   SQL_UB_ON en tant que valeur pour l’option d’instruction SQL_USE_BOOKMARKS. (SQL_UB_ON est déconseillée dans ODBC 3 *.x*.)  
  
-   L’option d’instruction SQL_GET_BOOKMARK.
