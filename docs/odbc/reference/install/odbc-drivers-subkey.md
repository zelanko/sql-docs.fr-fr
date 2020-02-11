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
ms.openlocfilehash: eb54ba7becad42d8d9d2c2870c02db37a3c7d89f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68093983"
---
# <a name="odbc-drivers-subkey"></a>Sous-clé des pilotes ODBC
Les valeurs de la sous-clé pilotes ODBC répertorient les pilotes installés. Le format de ces valeurs est indiqué dans le tableau suivant.  
  
|Name|Type de données|Données|  
|----------|---------------|----------|  
|*Description du pilote*|REG_SZ|**Ordinateur**|  
  
 Le nom *de la description du pilote* est défini par le développeur du pilote. Il s’agit généralement du nom du SGBD associé au pilote.  
  
 Par exemple, supposons que des pilotes ont été installés pour les fichiers texte mis en forme et les SQL Server. Les valeurs sous la sous-clé pilotes ODBC peuvent être :  
  
```  
Text : REG_SZ : Installed  
SQL Server : REG_SZ : Installed  
```
