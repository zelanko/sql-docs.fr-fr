---
title: Signets à longueur fixe Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f90c5888a68506c056b2a56fce516080148528e7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306980"
---
# <a name="fixed-length-bookmarks"></a>Signets de longueur fixe
Si un conducteur ODBC *3.x* doit travailler avec une application ODBC *2.x* qui utilise des signets de longueur fixe, le conducteur doit prendre en charge ce qui suit :  
  
-   SQL_UB_ON comme valeur pour l’option SQL_USE_BOOKMARKS déclaration. (SQL_UB_ON est dépréciée dans ODBC *3.x*.)  
  
-   L’option SQL_GET_BOOKMARK déclaration.
