---
title: Exemple de source de données Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], examples
ms.assetid: cbf15f32-0550-4c74-8088-8f7ac3855469
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 48c87f0d9f0a48b7d216151178c15bb019c0cbaa
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306520"
---
# <a name="data-source-example"></a>Exemple de source de données
Sur les ordinateurs exécutant Microsoft® Windows NT® Server/Windows 2000 Server, Microsoft Windows NT Workstation/Windows 2000 Professional, ou Microsoft Windows® 95/98, les informations source de données machines sont stockées dans le registre. Selon la clé de registre sous laquelle les informations sont stockées, la source de données est connue sous le nom de *source de données utilisateur* ou de source de données *système*. Les sources de données utilisateur sont stockées sous la clé HKEY_CURRENT_USER et ne sont disponibles que pour l’utilisateur actuel. Les sources de données système sont stockées sous la clé HKEY_LOCAL_MACHINE et peuvent être utilisées par plus d’un utilisateur sur une machine. Ils peuvent également être utilisés par les services à l’échelle du système, qui peuvent ensuite accéder à la source de données, même si aucun utilisateur n’est connecté à la machine. Pour plus d’informations sur les sources de données utilisateur et système, voir [SQLManageDataSources](../../odbc/reference/syntax/sqlmanagedatasources.md).  
  
 Supposons qu’un utilisateur dispose de trois sources de données utilisateur : personnel et inventaire, qui utilisent un DBMS Oracle ; et Payroll, qui utilise un serveur Microsoft SQL DBMS. Les valeurs de registre des sources de données peuvent être les suivante :  
  
```  
HKEY_CURRENT_USER  
SOFTWARE  
          ODBC  
               Odbc.ini  
                    ODBC Data Sources  
                    Personnel : REG_SZ : Oracle  
                    Inventory : REG_SZ : Oracle  
                    Payroll : REG_SZ : SQL Server  
```  
  
 et les valeurs du registre de la source de données sur la paie peuvent être les suivante :  
  
```  
HKEY_CURRENT_USER  
     SOFTWARE  
          ODBC  
               Odbc.ini  
                    Payroll  
                         Driver : REG_SZ : C:\WINDOWS\SYSTEM\Sqlsrvr.dll  
                         Description : REG_SZ : Payroll database  
                         Server : REG_SZ : PYRLL1  
                         FastConnectOption : REG_SZ : No                          UseProcForPrepare : REG_SZ : Yes  
                         OEMTOANSI : REG_SZ : No  
                         LastUser : REG_SZ : smithjo  
                         Database : REG_SZ : Payroll  
                         Language : REG_SZ :  
```
