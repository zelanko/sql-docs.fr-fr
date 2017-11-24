---
title: "Exemple de Source de données | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: data sources [ODBC], examples
ms.assetid: cbf15f32-0550-4c74-8088-8f7ac3855469
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 16217ebf7c229a47263b330e395a777716907797
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="data-source-example"></a>Exemple de Source de données
Sur les ordinateurs exécutant Microsoft® Windows NT® Server et Windows 2000 Server, Microsoft Windows NT Workstation et Windows 2000 Professionnel ou Microsoft Windows® 95/98, les données des ordinateurs, les informations source sont stockées dans le Registre. En fonction de Registre clés que les informations sont stockées sous, la source de données est appelée un *source de données utilisateur* ou un *source de données système*. Sources de données utilisateur sont stockés sous la clé HKEY_CURRENT_USER et sont disponibles uniquement pour l’utilisateur actuel. Sources de données système sont stockés sous la clé HKEY_LOCAL_MACHINE et peuvent être utilisées par plusieurs utilisateurs sur un ordinateur. Ils peuvent également être utilisés par les services du système, qui peuvent alors accéder à la source de données même si aucun utilisateur n’est connecté à l’ordinateur. Pour plus d’informations sur les sources de données système et utilisateur, consultez [SQLManageDataSources](../../odbc/reference/syntax/sqlmanagedatasources.md).  
  
 Supposons qu’un utilisateur a trois sources de données utilisateur : Personnel et inventaire, qui utilisent un SGBD Oracle ; et paie, qui utilise un système SGBD de Microsoft SQL Server. Les valeurs de Registre pour les sources de données peuvent être :  
  
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
  
 et les valeurs de Registre pour la source de données de paie peuvent être :  
  
```  
HKEY_CURRENT_USER  
     SOFTWARE  
          ODBC  
               Odbc.ini  
                    Payroll  
                         Driver : REG_SZ : C:\WINDOWS\SYSTEM\Sqlsrvr.dll  
                         Description : REG_SZ : Payroll database  
                         Server : REG_SZ : PYRLL1  
                         FastConnectOption : REG_SZ : No                          UseProcForPrepare : REG_SZ : Yes  
                         OEMTOANSI : REG_SZ : No  
                         LastUser : REG_SZ : smithjo  
                         Database : REG_SZ : Payroll  
                         Language : REG_SZ :  
```
