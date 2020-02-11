---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8aad5171b98c54aa0c4adbde1a5678e4fd953640
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68093965"
---
# <a name="odbc-subkey"></a>Sous-clé ODBC
Les valeurs sous la sous-clé ODBC spécifient les options de traçage ODBC. Ces options sont définies à l’aide de l’onglet suivi de la boîte de dialogue administrateur de sources de données ODBC affichée par **SQLManageDataSources**. La sous-clé ODBC elle-même est facultative. Le format de ces valeurs est comme indiqué dans le tableau suivant.  
  
|Name|Type de données|Données|  
|----------|---------------|----------|  
|Trace|REG_SZ|**0** &#124; **1**|  
|TraceFile|REG_SZ|*TraceFile-chemin d’accès*|  
  
 Les valeurs ont les significations décrites dans le tableau suivant.  
  
|Valeur|Signification|  
|-----------|-------------|  
|Trace|Si la valeur de trace est définie sur 1 lorsqu’une application appelle **SQLAllocHandle** avec l’option SQL_HANDLE_ENV, le suivi est activé pour l’application appelante.<br /><br /> Si le mot clé trace est défini sur 0 quand une application appelle **SQLAllocHandle** avec l’option SQL_HANDLE_ENV, le suivi est désactivé pour l’application appelante. Il s’agit de la valeur par défaut.<br /><br /> Une application peut activer ou désactiver le suivi avec l’attribut de connexion SQL_ATTR_TRACE. Toutefois, cela ne modifie pas les données de cette valeur.|  
|TraceFile|Si le suivi est activé, le gestionnaire de pilotes écrit dans le fichier de trace spécifié par la valeur de TraceFile.<br /><br /> Si aucun fichier de trace n’est spécifié, le gestionnaire de pilotes écrit dans le fichier SQL. log sur le lecteur actif. Il s’agit de la valeur par défaut.<br /><br /> Le suivi doit être utilisé uniquement pour une application unique, ou chaque application doit spécifier un fichier de trace différent. Dans le cas contraire, deux applications ou plus tenteront d’ouvrir le même fichier de trace en même temps, provoquant une erreur.<br /><br /> Une application peut spécifier un nouveau fichier de trace avec l’attribut de connexion SQL_ATTR_TRACEFILE. Toutefois, cela ne modifie pas les données de cette valeur.|  
  
 Supposons, par exemple, que le suivi est activé et que le fichier de trace est C:\Odbc.log. Les valeurs sous la sous-clé ODBC sont les suivantes :  
  
```  
Trace : REG_SZ : 1  
TraceFile : REG_SZ : C:\ODBC.LOG  
  
```
