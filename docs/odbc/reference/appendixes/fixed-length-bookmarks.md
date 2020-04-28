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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f90c5888a68506c056b2a56fce516080148528e7
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306980"
---
# <a name="fixed-length-bookmarks"></a>Signets de longueur fixe
Si un pilote ODBC *3. x* doit fonctionner avec une application ODBC *2. x* qui utilise des signets de longueur fixe, le pilote doit prendre en charge les éléments suivants :  
  
-   SQL_UB_ON comme valeur pour l’option d’instruction SQL_USE_BOOKMARKS. (SQL_UB_ON est déconseillé dans ODBC *3. x*.)  
  
-   Option d’instruction SQL_GET_BOOKMARK.
