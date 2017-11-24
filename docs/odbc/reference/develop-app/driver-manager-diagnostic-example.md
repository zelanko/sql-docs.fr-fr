---
title: Exemple de Diagnostic du Gestionnaire de pilotes | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- driver manager [ODBC], diagnostic messages
- diagnostic information [ODBC], examples
- error messages [ODBC], diagnostic messages
ms.assetid: af8f2d35-d1bf-495c-af25-630654542b7d
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d51a5318c1b331a99ff1b108a3a56010a5e83a5b
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="driver-manager-diagnostic-example"></a>Exemple de Diagnostic du Gestionnaire de pilotes
Le Gestionnaire de pilotes peut également générer des messages de diagnostic. Par exemple, si une application a transmis une option non valide de direction pour **SQLDataSources**, le Gestionnaire de pilotes peut mettre en forme et renvoyer les valeurs suivantes à partir de **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "HY103"  
Native Error:      0  
Diagnostic Msg:   "[Microsoft][ODBC Driver Manager]Direction option out of range"  
```  
  
 Étant donné que l’erreur s’est produite dans le Gestionnaire de pilotes, ajouté préfixes pour le message de diagnostic pour le fournisseur ([Microsoft]) et de son identificateur ([Gestionnaire de pilotes ODBC]).
