---
title: Sous-clé de convertisseurs ODBC | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- translator subkey [ODBC]
- subkeys [ODBC], translator subkey
- registry entries for components [ODBC], translator subkey
ms.assetid: 6b170f1f-e263-4aac-9d49-8d0ca0470ca2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9e7109a6f1b88cf7639b2fc823ce0c5f14d05002
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63280793"
---
# <a name="odbc-translators-subkey"></a>Sous-clé de convertisseurs ODBC
Les valeurs sous la sous-clé ODBC traducteurs répertorient les convertisseurs installés. Le format de ces valeurs est illustré dans le tableau suivant.  
  
|Créer une vue d’abonnement|Type de données|Données|  
|----------|---------------|----------|  
|*translator-desc*|REG_SZ|**Installed**|  
  
 Le *translator-desc* nom est défini par le développeur du traducteur.  
  
 Par exemple, qu'un utilisateur a installé le traducteur de Page de Code Microsoft® et un ASCII personnalisé au traducteur de EBCDIC. Les valeurs sous la sous-clé ODBC traducteurs peuvent être comme suit :  
  
```  
MS Code Page Translator: REG_SZ : Installed  
ASCII to EBCDIC: REG_SZ : Installed.  
```
