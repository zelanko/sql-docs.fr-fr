---
title: "ODBC Core sous-clé | Documents Microsoft"
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
- subkeys [ODBC], core subkey
- registry entries for components [ODBC], core subkey
- core subkey [ODBC]
ms.assetid: 055b31fc-f96c-450b-a596-d4570079fbf2
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ad7a45f0f3272e1e2d7ae799ab1ca86bfb90b9be
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="odbc-core-subkey"></a>ODBC Core sous-clé
La valeur sous la sous-clé ODBC Core donne le nombre d’utilisations pour les composants principaux (Gestionnaire de pilotes, bibliothèque de curseurs, programme d’installation DLL et ainsi de suite). Le format de cette valeur est illustré dans le tableau suivant.  
  
|Nom|Type de données|data|  
|----------|---------------|----------|  
|UsageCount|REG_DWORD|*nombre*|  
  
 Par exemple, supposons que les composants de niveau principal ODBC ont été installés par les programmes d’installation pour les trois applications différentes et deux différents pilotes. La valeur sous la sous-clé ODBC Core serait :  
  
```  
UsageCount : REG_DWORD : 0x5  
```

