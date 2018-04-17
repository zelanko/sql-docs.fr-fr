---
title: Sources de données ODBC sous-clé | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- subkeys [ODBC], for data sources
- data sources [ODBC], subkeys
- registry entries for data sources [ODBC], subkeys
ms.assetid: 0a8ccb80-c573-4418-84e5-f04a2b0e2ac1
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bbe6d0e7e424f2bea8d90eb4e9c5993f50370848
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
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
