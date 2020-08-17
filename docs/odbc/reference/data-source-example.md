---
description: Exemple de source de données
title: Exemple de source de données | Microsoft Docs
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
ms.openlocfilehash: f0d165279dc0b2f4b056d2e214461c7ef019956b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88386045"
---
# <a name="data-source-example"></a>Exemple de source de données
Sur les ordinateurs exécutant Microsoft® Windows NT® Server/Windows 2000 Server, Microsoft Windows NT Workstation/Windows 2000 Professional ou Microsoft Windows® 95/98, les informations relatives à la source de données de l’ordinateur sont stockées dans le registre. Selon la clé de Registre dans laquelle les informations sont stockées, la source de données est appelée *source de données utilisateur* ou *source de données système*. Les sources de données utilisateur sont stockées sous la clé de HKEY_CURRENT_USER et sont disponibles uniquement pour l’utilisateur actuel. Les sources de données système sont stockées sous la clé de HKEY_LOCAL_MACHINE et peuvent être utilisées par plusieurs utilisateurs sur un même ordinateur. Elles peuvent également être utilisées par les services du système, qui peuvent alors accéder à la source de données même si aucun utilisateur n’est connecté à la machine. Pour plus d’informations sur les sources de données utilisateur et système, consultez [SQLManageDataSources](../../odbc/reference/syntax/sqlmanagedatasources.md).  
  
 Supposons qu’un utilisateur possède trois sources de données utilisateur : le personnel et l’inventaire, qui utilisent un SGBD Oracle. et Payroll, qui utilise un SGBD Microsoft SQL Server. Les valeurs de Registre pour les sources de données peuvent être :  
  
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
  
 et les valeurs de registre de la source de données de la paie peuvent être :  
  
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
