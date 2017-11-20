---
title: "SQLSetEnvAttr et la bibliothèque de curseurs | Documents Microsoft"
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
- SQLSetEnvAttr function [ODBC], Cursor Library
ms.assetid: 59cc8eae-09ae-4796-869a-c5806488ae83
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c08fab3b713e1f1a57d7a81f53ed29b1678893cd
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsetenvattr-and-the-cursor-library"></a>SQLSetEnvAttr et la bibliothèque de curseurs
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans tout nouveau développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser les fonctionnalités de curseur du pilote.  
  
 Cette rubrique décrit l’utilisation de la **SQLSetEnvAttr** fonction avec la bibliothèque de curseurs. Pour des informations générales sur **SQLSetEnvAttr**, consultez [fonction SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md).  
  
 La bibliothèque de curseurs n’est pas affectée par le paramètre de l’attribut d’environnement SQL_ATTR_ODBC_VERSION, quelle que soit la version du pilote ou une version de l’application.

