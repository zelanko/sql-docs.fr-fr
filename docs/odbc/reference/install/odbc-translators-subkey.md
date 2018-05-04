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
ms.topic: conceptual
helpviewer_keywords:
- translator subkey [ODBC]
- subkeys [ODBC], translator subkey
- registry entries for components [ODBC], translator subkey
ms.assetid: 6b170f1f-e263-4aac-9d49-8d0ca0470ca2
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1a6c59901d3e784f1ab845da595c84a4e74a0129
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
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
