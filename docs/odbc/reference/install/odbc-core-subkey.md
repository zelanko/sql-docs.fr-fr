---
title: Sous-clé ODBC Core | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 98c9380083eb5a0ad796f436af271564676b757d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68094008"
---
# <a name="odbc-core-subkey"></a>Sous-clé des composants principaux ODBC
La valeur de la sous-clé ODBC principale indique le nombre d’utilisations des composants principaux (gestionnaire de pilotes, bibliothèque de curseurs, DLL du programme d’installation, etc.). Le format de cette valeur est indiqué dans le tableau suivant.  
  
|Name|Type de données|Données|  
|----------|---------------|----------|  
|UsageCount|REG_DWORD|*saut*|  
  
 Par exemple, supposons que les composants ODBC Core ont été installés par les programmes d’installation pour trois applications différentes et deux pilotes différents. La valeur sous la sous-clé ODBC Core est la suivante :  
  
```  
UsageCount : REG_DWORD : 0x5  
```
