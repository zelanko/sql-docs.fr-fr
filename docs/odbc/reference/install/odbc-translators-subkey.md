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
ms.openlocfilehash: 7d26f2d33d81e08cfe4bddff9b2260bd2f098f00
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68093943"
---
# <a name="odbc-translators-subkey"></a>Sous-clé de convertisseurs ODBC
Les valeurs sous la sous-clé ODBC traducteurs répertorient les convertisseurs installés. Le format de ces valeurs est illustré dans le tableau suivant.  
  
|Name|Type de données|Données|  
|----------|---------------|----------|  
|*translator-desc*|REG_SZ|**installé**|  
  
 Le *translator-desc* nom est défini par le développeur du traducteur.  
  
 Par exemple, qu'un utilisateur a installé le traducteur de Page de Code Microsoft® et un ASCII personnalisé au traducteur de EBCDIC. Les valeurs sous la sous-clé ODBC traducteurs peuvent être comme suit :  
  
```  
MS Code Page Translator: REG_SZ : Installed  
ASCII to EBCDIC: REG_SZ : Installed.  
```
