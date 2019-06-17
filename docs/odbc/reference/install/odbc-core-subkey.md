---
title: Sous-clé des composants principaux ODBC | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 5c95c4e28a5f32131307daeaa61e214af887b577
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63069697"
---
# <a name="odbc-core-subkey"></a>Sous-clé des composants principaux ODBC
La valeur sous la sous-clé ODBC Core donne le décompte d’utilisation pour les composants principaux (Gestionnaire de pilotes, bibliothèque de curseurs, DLL d’installation et ainsi de suite). Le format de cette valeur est illustré dans le tableau suivant.  
  
|Nom|Type de données|Données|  
|----------|---------------|----------|  
|UsageCount|REG_DWORD|*nombre*|  
  
 Par exemple, supposons que les composants de niveau principal ODBC ont été installés par les programmes d’installation pour les trois applications différentes et deux pilotes différents. La valeur sous la sous-clé ODBC Core serait :  
  
```  
UsageCount : REG_DWORD : 0x5  
```
