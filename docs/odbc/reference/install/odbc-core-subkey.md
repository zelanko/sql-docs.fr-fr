---
title: ODBC Core Subkey - France Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- subkeys [ODBC], core subkey
- registry entries for components [ODBC], core subkey
- core subkey [ODBC]
ms.assetid: 055b31fc-f96c-450b-a596-d4570079fbf2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9e6bfcf3c1efa87076e6d3e27a438cde6f794157
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304053"
---
# <a name="odbc-core-subkey"></a>Sous-clé des composants principaux ODBC
La valeur sous le sous-marin ODBC Core donne le compte d’utilisation pour les composants de base (Driver Manager, cursor library, installateur DLL, et ainsi de suite). Le format de cette valeur est affiché dans le tableau suivant.  
  
|Nom|Type de données|Données|  
|----------|---------------|----------|  
|UtilisationCompte|REG_DWORD|*count*|  
  
 Supposons, par exemple, que les composants ODBC Core aient été installés par les programmes d’installation pour trois applications différentes et deux pilotes différents. La valeur en vertu de la sous-clé ODBC Core serait :  
  
```  
UsageCount : REG_DWORD : 0x5  
```
