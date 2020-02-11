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
ms.openlocfilehash: 5877a6cb7a99803f854338321e333c87037c2e90
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67913584"
---
# <a name="fixed-length-bookmarks"></a>Signets de longueur fixe
Si un pilote ODBC *3. x* doit fonctionner avec une application ODBC *2. x* qui utilise des signets de longueur fixe, le pilote doit prendre en charge les éléments suivants :  
  
-   SQL_UB_ON comme valeur pour l’option d’instruction SQL_USE_BOOKMARKS. (SQL_UB_ON est déconseillé dans ODBC *3. x*.)  
  
-   Option d’instruction SQL_GET_BOOKMARK.
