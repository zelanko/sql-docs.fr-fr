---
title: Sous-clé des pilotes ODBC | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- subkeys [ODBC], drivers subkey
- registry entries for components [ODBC], drivers subkey
- drivers subkey [ODBC]
ms.assetid: 8edbf68f-d05d-4d77-92f6-e9500008f520
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 43be1c5e75998903ff4e64fc5f4230818a873ffc
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63281127"
---
# <a name="odbc-drivers-subkey"></a>Sous-clé des pilotes ODBC
Les valeurs sous la sous-clé de pilotes ODBC répertorient les pilotes installés. Le format de ces valeurs est illustré dans le tableau suivant.  
  
|Nom|Type de données|Données|  
|----------|---------------|----------|  
|*driver-description*|REG_SZ|**Installed**|  
  
 Le *-description du pilote* nom est défini par le développeur de pilote. Il s’agit généralement du nom du SGBD associé au pilote.  
  
 Par exemple, supposons que les pilotes ont été installés pour les fichiers de texte mis en forme et de SQL Server. Les valeurs sous la sous-clé de pilotes ODBC peuvent être :  
  
```  
Text : REG_SZ : Installed  
SQL Server : REG_SZ : Installed  
```
