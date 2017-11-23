---
title: "Appel de procédure | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL grammar [ODBC], procedure invocation
- procedure invocation [ODBC]
ms.assetid: b9ff2c3a-2003-4832-adbe-08dd0f5ad948
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 793209ab716d720266e834fcbbb846dea56950ed
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="procedure-invocation"></a>Appel de procédure
Lorsque le pilote Microsoft Access est utilisé, les procédures peuvent être appelées à partir du pilote à l’aide de la **SQLExecDirect** ou **SQLPrepare** fonction avec la syntaxe suivante : {appeler *-nom de la procédure* [(*paramètre*[,*paramètre*]...)]}. Notez que les expressions ne sont pas prises en charge en tant que paramètres à une procédure appelée.  
  
 Si un nom de procédure comprend un tiret, le nom doit être délimité avec guillemets précédent (').  
  
 Une requête paramétrable peut être appelée à l’aide de l’instruction précédente.
