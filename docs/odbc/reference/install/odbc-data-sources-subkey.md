---
title: "Sources de données ODBC sous-clé | Documents Microsoft"
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
- subkeys [ODBC], for data sources
- data sources [ODBC], subkeys
- registry entries for data sources [ODBC], subkeys
ms.assetid: 0a8ccb80-c573-4418-84e5-f04a2b0e2ac1
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 445cb41e239a0c2e8f3cf83b3ebbf2ca319fd9bb
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="odbc-data-sources-subkey"></a>Sous-clé de Sources de données ODBC
Les valeurs sous la sous-clé de Sources de données ODBC répertorient les sources de données. Le format de ces valeurs est tel qu’indiqué dans le tableau suivant.  
  
|Nom|Type de données|data|  
|----------|---------------|----------|  
|*nom de source de données*|REG_SZ|*description du pilote*|  
  
 Le *nom de source de données* valeur est définie par le programme d’administration (qui demande généralement à l’utilisateur pour lui), et *description du pilote* est défini par le développeur de pilote (il est généralement le nom du SGBD associé au pilote).  
  
 Par exemple, supposons que trois sources de données ont été définies : l’inventaire, qui utilise SQL Server ; Gestion de la paie, qui utilise dBASE ; et qui utilise Personnel, mise en forme des fichiers texte. Les valeurs sous la sous-clé de Sources de données ODBC peuvent être comme suit :  
  
```  
Inventory : REG_SZ : SQL Server  
Payroll : REG_SZ : dBASE  
Personnel : REG_SZ : Text  
```

