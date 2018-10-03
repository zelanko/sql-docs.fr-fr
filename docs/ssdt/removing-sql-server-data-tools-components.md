---
title: Suppression des composants SQL Server Data Tools | Microsoft Docs
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: f8ddb919-661f-4868-8c71-87c96f1f4487
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6b114b99b816e10bc004cea8d60c56d296053c7c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47685467"
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
  
