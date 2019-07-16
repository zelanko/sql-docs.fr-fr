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
ms.openlocfilehash: 2a1d0c506c4a4b33d7138378032947821d4e9f3e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68093991"
---
# <a name="odbc-data-sources-subkey"></a>Sous-clé des sources de données ODBC
Les valeurs sous la sous-clé de Sources de données ODBC répertorient les sources de données. Le format de ces valeurs est comme indiqué dans le tableau suivant.  
  
|Nom|Type de données|Données|  
|----------|---------------|----------|  
|*data-source-name*|REG_SZ|*driver-description*|  
  
 Le *nom de source de données* valeur est définie par le programme d’administration (qui en général, l’utilisateur pour lui), et *-description du pilote* est défini par le développeur de pilote (il s’agit généralement du nom de la SGBD associées au pilote).  
  
 Par exemple, supposons que trois des données sources ont été définies : Inventaire, qui utilise SQL Server ; Traitement des paies, qui utilise dBASE ; et qui utilise de Personnel, mise en forme de fichiers texte. Les valeurs sous la sous-clé de Sources de données ODBC peuvent être comme suit :  
  
```  
Inventory : REG_SZ : SQL Server  
Payroll : REG_SZ : dBASE  
Personnel : REG_SZ : Text  
```
