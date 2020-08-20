---
description: Sous-clé ODBC
title: Sous-clé ODBC | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- registry entries for data sources [ODBC], ODBC subkey
- subkeys [ODBC], ODBC subkey
- ODBC subkey [ODBC]
ms.assetid: f9534144-8f42-4946-b0fb-638e9dcde9c8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4ec27b40e196f5277307b9a299dd865a1604dc0e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88499724"
---
# <a name="odbc-subkey"></a>Sous-clé ODBC
Les valeurs sous la sous-clé ODBC spécifient les options de traçage ODBC. Ces options sont définies à l’aide de l’onglet suivi de la boîte de dialogue administrateur de sources de données ODBC affichée par **SQLManageDataSources**. La sous-clé ODBC elle-même est facultative. Le format de ces valeurs est comme indiqué dans le tableau suivant.  
  
|Nom|Type de données|Données|  
|----------|---------------|----------|  
|Trace|REG_SZ|**0** &#124; **1**|  
|TraceFile|REG_SZ|*TraceFile-chemin d’accès*|  
  
 Les valeurs ont les significations décrites dans le tableau suivant.  
  
|Valeur|Signification|  
|-----------|-------------|  
|Trace|Si la valeur de trace est définie sur 1 lorsqu’une application appelle **SQLAllocHandle** avec l’option SQL_HANDLE_ENV, le suivi est activé pour l’application appelante.<br /><br /> Si le mot clé trace est défini sur 0 quand une application appelle **SQLAllocHandle** avec l’option SQL_HANDLE_ENV, le suivi est désactivé pour l’application appelante. Valeur par défaut.<br /><br /> Une application peut activer ou désactiver le suivi avec l’attribut de connexion SQL_ATTR_TRACE. Toutefois, cela ne modifie pas les données de cette valeur.|  
|TraceFile|Si le suivi est activé, le gestionnaire de pilotes écrit dans le fichier de trace spécifié par la valeur de TraceFile.<br /><br /> Si aucun fichier de trace n’est spécifié, le gestionnaire de pilotes écrit dans le fichier SQL. log sur le lecteur actif. Valeur par défaut.<br /><br /> Le suivi doit être utilisé uniquement pour une application unique, ou chaque application doit spécifier un fichier de trace différent. Dans le cas contraire, deux applications ou plus tenteront d’ouvrir le même fichier de trace en même temps, provoquant une erreur.<br /><br /> Une application peut spécifier un nouveau fichier de trace avec l’attribut de connexion SQL_ATTR_TRACEFILE. Toutefois, cela ne modifie pas les données de cette valeur.|  
  
 Supposons, par exemple, que le suivi est activé et que le fichier de trace est C:\Odbc.log. Les valeurs sous la sous-clé ODBC sont les suivantes :  
  
```  
Trace : REG_SZ : 1  
TraceFile : REG_SZ : C:\ODBC.LOG  
  
```
