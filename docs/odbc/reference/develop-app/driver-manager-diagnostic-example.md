---
title: Exemple de Diagnostic du Gestionnaire de pilotes | Documents Microsoft
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
- driver manager [ODBC], diagnostic messages
- diagnostic information [ODBC], examples
- error messages [ODBC], diagnostic messages
ms.assetid: af8f2d35-d1bf-495c-af25-630654542b7d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 3f373fe012c2b791329fea35ca853021e70274eb
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="driver-manager-diagnostic-example"></a>Exemple de Diagnostic du Gestionnaire de pilotes
Le Gestionnaire de pilotes peut également générer des messages de diagnostic. Par exemple, si une application a transmis une option non valide de direction pour **SQLDataSources**, le Gestionnaire de pilotes peut mettre en forme et renvoyer les valeurs suivantes à partir de **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "HY103"  
Native Error:      0  
Diagnostic Msg:   "[Microsoft][ODBC Driver Manager]Direction option out of range"  
```  
  
 Étant donné que l’erreur s’est produite dans le Gestionnaire de pilotes, ajouté préfixes pour le message de diagnostic pour le fournisseur ([Microsoft]) et de son identificateur ([Gestionnaire de pilotes ODBC]).
