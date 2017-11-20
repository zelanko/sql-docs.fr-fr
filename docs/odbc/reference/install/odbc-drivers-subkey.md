---
title: "Sous-clé de pilotes ODBC | Documents Microsoft"
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
- subkeys [ODBC], drivers subkey
- registry entries for components [ODBC], drivers subkey
- drivers subkey [ODBC]
ms.assetid: 8edbf68f-d05d-4d77-92f6-e9500008f520
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 21b151256f93d77cd0efecedfa8eef2ddcd6482b
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="odbc-drivers-subkey"></a>Sous-clé de pilotes ODBC
Les valeurs sous la sous-clé de pilotes ODBC répertorient les pilotes installés. Le format de ces valeurs est illustré dans le tableau suivant.  
  
|Nom|Type de données|data|  
|----------|---------------|----------|  
|*description du pilote*|REG_SZ|**Installé**|  
  
 Le *description du pilote* nom est défini par le développeur. Il s’agit généralement du nom du SGBD associé au pilote.  
  
 Par exemple, supposons que les pilotes ont été installés pour les fichiers de texte mis en forme et de SQL Server. Les valeurs sous la sous-clé de pilotes ODBC peuvent être :  
  
```  
Text : REG_SZ : Installed  
SQL Server : REG_SZ : Installed  
```

