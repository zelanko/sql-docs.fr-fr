---
title: Suppression des composants SQL Server Data Tools | Microsoft Docs
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f8ddb919-661f-4868-8c71-87c96f1f4487
caps.latest.revision: 6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3a3fcb24fc18812b139dfe49376699e83607f16d
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39087541"
---
# <a name="removing-sql-server-data-tools-components"></a>Suppression des composants SQL Server Data Tools
Certains composants SQL Server Data Tools (SSDT) ne sont pas supprimés lorsque vous désinstallez SSDT ou Visual Studio.  
  
Les packages Windows Installer (.msi) suivants ne seront pas supprimés de l'ordinateur lors de la désinstallation de SSDT ou Visual Studio. La suppression de ces composants peut placer les autres versions de Visual Studio dans un état non pris en charge. Si vous choisissez de supprimer ces composants, utilisez la fonction Ajout/Suppression de programmes de Windows :  
  
-   Microsoft SQL Server Data Tools (SSDT.msi)  
  
-   Microsoft SQL Server Data Tools Build Utilities (SSDTBuildUtilities.msi)  
  
-   Prerequisites for SSDT (SSDTDBSvcExternals.msi)  
  
Les composants partagés suivants sont peut-être utilisés par d'autres produits et resteront sur l'ordinateur après la désinstallation de SSDT.  
  
-   SQL Server Data-Tier App Framework (DACFramework.msi)  
  
-   SQL Server Management Objects (SharedManagementObjects.msi)  
  
-   SQL Server Transact\-SQL Language Service (TSqlLanguageService.msi)  
  
-   Microsoft SQL Server System CLR Types for SQL Server (SQLSysClrTypes.msi)  
  
-   SQL Server Transact\-SQL ScriptDom (SQLDom.msi)  
  
-   SQL Server Transact\-SQL Compiler Service (SQLLs.msi)  
  
