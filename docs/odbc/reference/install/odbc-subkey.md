---
title: ODBC Subkey - France Microsoft Docs
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
ms.openlocfilehash: 96e9a5f4c3cdac5097686528d3c089d9ec5826f7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81287439"
---
# <a name="odbc-subkey"></a>Sous-clé ODBC
Les valeurs sous le sous-clé ODBC spécifient les options de traçage ODBC. Ces options sont définies à travers l’onglet Tracing de la boîte de dialogue ODBC Data Source Administrator affichée par **SQLManageDataSources**. Le sous-clé ODBC lui-même est facultatif. Le format de ces valeurs est tel que indiqué dans le tableau suivant.  
  
|Nom|Type de données|Données|  
|----------|---------------|----------|  
|Trace|REG_SZ|**0** &#124; **1**|  
|TraceFile|REG_SZ|*tracefile-chemin*|  
  
 Les valeurs ont les significations décrites dans le tableau suivant.  
  
|Value|Signification|  
|-----------|-------------|  
|Trace|Si la valeur Trace est réglée à 1 lorsqu’une application appelle **SQLAllocHandle** avec l’option SQL_HANDLE_ENV, le traçage est activé pour l’application d’appel.<br /><br /> Si le mot clé Trace est réglé à 0 lorsqu’une application appelle **SQLAllocHandle** avec l’option SQL_HANDLE_ENV, le traçage est désactivé pour l’application d’appel. Il s’agit de la valeur par défaut.<br /><br /> Une application peut activer ou désactiver le traçage avec l’attribut de connexion SQL_ATTR_TRACE. Toutefois, cela ne modifie pas les données pour cette valeur.|  
|TraceFile|Si le traçage est activé, le gestionnaire de conducteur écrit au fichier de traçage spécifié par la valeur TraceFile.<br /><br /> Si aucun fichier de trace n’est spécifié, le gestionnaire de conducteur écrit au fichier Sql.log sur le disque actuel. Il s’agit de la valeur par défaut.<br /><br /> Le traçage ne doit être utilisé que pour une seule application, ou chaque application doit spécifier un fichier de traces différent. Dans le cas contraire, deux applications ou plus tenteront d’ouvrir le même fichier de traçabilité en même temps, provoquant une erreur.<br /><br /> Une application peut spécifier un nouveau fichier de traçabilité avec l’attribut de connexion SQL_ATTR_TRACEFILE. Toutefois, cela ne modifie pas les données pour cette valeur.|  
  
 Supposons, par exemple, que le traçage est activé et que le fichier de trace est C : Odbc.log. Les valeurs sous la sous-clé de l’ODBC seraient les suivantes :  
  
```  
Trace : REG_SZ : 1  
TraceFile : REG_SZ : C:\ODBC.LOG  
  
```
