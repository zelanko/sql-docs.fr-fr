---
title: ODBC Traducteurs Subkey (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 617416adfcddfbf041c48acbf83cb9589e34ae27
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296219"
---
# <a name="odbc-translators-subkey"></a>Sous-clé de convertisseurs ODBC
Les valeurs sous la sous-liste des traducteurs de l’ODBC répertorient les traducteurs installés. Le format de ces valeurs est affiché dans le tableau suivant.  
  
|Nom|Type de données|Données|  
|----------|---------------|----------|  
|*traducteur-desc*|REG_SZ|**Installé**|  
  
 Le nom *traducteur-desc* est défini par le développeur du traducteur.  
  
 Supposons, par exemple, qu’un utilisateur ait installé le traducteur de page de code Microsoft® et un traducteur ASCII personnalisé pour ebCDIC. Les valeurs sous la sous-clé ODBC Translators pourraient être les suivantes :  
  
```  
MS Code Page Translator: REG_SZ : Installed  
ASCII to EBCDIC: REG_SZ : Installed.  
```
