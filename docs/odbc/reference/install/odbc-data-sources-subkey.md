---
title: Sous-clé des Sources de données ODBC | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- subkeys [ODBC], for data sources
- data sources [ODBC], subkeys
- registry entries for data sources [ODBC], subkeys
ms.assetid: 0a8ccb80-c573-4418-84e5-f04a2b0e2ac1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9867946ce84163a504582c8a9575100c3c9aacd3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47600867"
---
# <a name="odbc-data-sources-subkey"></a>Sous-clé des sources de données ODBC
Les valeurs sous la sous-clé de Sources de données ODBC répertorient les sources de données. Le format de ces valeurs est comme indiqué dans le tableau suivant.  
  
|Nom   |Type de données|data|  
|----------|---------------|----------|  
|*nom de source de données*|REG_SZ|*description du pilote*|  
  
 Le *nom de source de données* valeur est définie par le programme d’administration (qui en général, l’utilisateur pour lui), et *-description du pilote* est défini par le développeur de pilote (il s’agit généralement du nom de la SGBD associées au pilote).  
  
 Par exemple, supposons que trois sources de données ont été définies : inventaire, qui utilise SQL Server ; Traitement des paies, qui utilise dBASE ; et qui utilise de Personnel, mise en forme de fichiers texte. Les valeurs sous la sous-clé de Sources de données ODBC peuvent être comme suit :  
  
```  
Inventory : REG_SZ : SQL Server  
Payroll : REG_SZ : dBASE  
Personnel : REG_SZ : Text  
```
