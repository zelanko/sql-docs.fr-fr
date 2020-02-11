---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ec9eacef6f0bd63eb0aaeac36dc97938297d1f16
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68135635"
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
