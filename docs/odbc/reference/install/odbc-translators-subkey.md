---
title: ODBC traducteurs sous-clé | Documents Microsoft
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
- translator subkey [ODBC]
- subkeys [ODBC], translator subkey
- registry entries for components [ODBC], translator subkey
ms.assetid: 6b170f1f-e263-4aac-9d49-8d0ca0470ca2
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ede16122078aa53d3eeb0799678537746e3fcf12
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="odbc-translators-subkey"></a>ODBC traducteurs sous-clé
Les valeurs sous la sous-clé ODBC traducteurs répertorient les convertisseurs installés. Le format de ces valeurs est illustré dans le tableau suivant.  
  
|Nom|Type de données|data|  
|----------|---------------|----------|  
|*traducteur-desc.*|REG_SZ|**Installé**|  
  
 Le *traducteur-desc* nom est défini par le développeur du traducteur.  
  
 Par exemple, supposons qu’un utilisateur a installé le traducteur de Page de Code Microsoft® et un ASCII personnalisé sur le traducteur d’EBCDIC. Les valeurs sous la sous-clé ODBC traducteurs peuvent être comme suit :  
  
```  
MS Code Page Translator: REG_SZ : Installed  
ASCII to EBCDIC: REG_SZ : Installed.  
```
