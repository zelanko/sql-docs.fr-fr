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
manager: craigg
ms.openlocfilehash: ee7cf624e7c118a5d9ef36738c810aecc4ec5684
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47711537"
---
# <a name="odbc-subkey"></a>Sous-clé ODBC
Les valeurs sous la sous-clé ODBC spécifient des options de suivi de ODBC. Ces options sont définies via l’onglet suivi de la boîte de dialogue Administrateur de sources de données ODBC affichée par **SQLManageDataSources**. La sous-clé ODBC lui-même est facultative. Le format de ces valeurs est comme indiqué dans le tableau suivant.  
  
|Nom   |Type de données|data|  
|----------|---------------|----------|  
|Trace|REG_SZ|**0** &#124; **1**|  
|TraceFile|REG_SZ|*chemin d’accès de fichier de trace*|  
  
 Les valeurs ont les significations décrites dans le tableau suivant.  
  
|Valeur|Signification|  
|-----------|-------------|  
|Trace|Si la valeur de la Trace est définie à 1 lorsque une application appelle **SQLAllocHandle** avec l’option SQL_HANDLE_ENV, le traçage est activé pour l’application appelante.<br /><br /> Si le mot clé de Trace est défini sur 0, lorsqu’une application appelle **SQLAllocHandle** avec l’option SQL_HANDLE_ENV, le suivi est désactivé pour l’application appelante. Il s'agit de la valeur par défaut.<br /><br /> Une application peut activer ou désactiver le suivi avec l’attribut de connexion SQL_ATTR_TRACE. Toutefois, cela par conséquent, ne modifie pas les données de cette valeur.|  
|TraceFile|Si le traçage est activé, le Gestionnaire de pilotes est écrit dans le fichier de trace spécifié par la valeur du fichier de trace.<br /><br /> Si aucun fichier de trace n’est spécifié, le Gestionnaire de pilotes est écrit dans le fichier de Sql.log sur le lecteur actif. Il s'agit de la valeur par défaut.<br /><br /> Le suivi doit être utilisé uniquement pour une application unique, ou chaque application doit spécifier un fichier de trace différents. Sinon, deux ou plusieurs applications tente d’ouvrir le même fichier de trace en même temps, à l’origine d’une erreur.<br /><br /> Une application peut spécifier un nouveau fichier de trace avec l’attribut de connexion SQL_ATTR_TRACEFILE. Toutefois, cela par conséquent, ne modifie pas les données de cette valeur.|  
  
 Par exemple, supposons que le traçage est activé et que le fichier de trace est C:\Odbc.log. Les valeurs sous la sous-clé ODBC se présente comme suit :  
  
```  
Trace : REG_SZ : 1  
TraceFile : REG_SZ : C:\ODBC.LOG  
  
```
