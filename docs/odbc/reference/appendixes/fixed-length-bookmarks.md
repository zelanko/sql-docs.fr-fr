---
title: Les signets de longueur fixe | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- backward compatibility [ODBC], bookmarks
- bookmarks [ODBC]
- compatibility [ODBC], bookmarks
- fixed-length bookmarks [ODBC]
ms.assetid: cbd8185e-fb03-408f-b80b-1a2e164534fd
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 279b6a3c1f8eb2f1eea5bba35ee10f0a6643fb49
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="fixed-length-bookmarks"></a>Signets de longueur fixe
Si un ODBC 3*.x* pilote doit fonctionner avec une API ODBC 2.* x* application qu’utilise signets de longueur fixe, le pilote doivent prendre en charge les éléments suivants :  
  
-   SQL_UB_ON en tant que valeur pour l’option d’instruction SQL_USE_BOOKMARKS. (SQL_UB_ON est déconseillé dans ODBC 3*.x*.)  
  
-   L’option d’instruction SQL_GET_BOOKMARK.

