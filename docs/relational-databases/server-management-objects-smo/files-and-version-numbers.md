---
description: Fichiers et numéros de version
title: Fichiers et numéros de version | Microsoft Docs
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, versions
- components [SMO]
- files [SMO], components
- SMO [SQL Server], versions
- versions [SMO]
ms.assetid: 510907b6-e7a9-41bd-b892-d6d99a5118e1
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 850268d303106e8c07a19915f9284b6c4dc3f7d2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88420273"
---
# <a name="files-and-version-numbers"></a>Fichiers et numéros de version
[!INCLUDE [SQL Server ASDB, ASDBMI, ASDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa.md)]

  Tous les composants SMO (SQL Server Management Objects) requis sont inclus dans le package NuGet Microsoft. SqlServer. SqlManagementObjects. SMO est implémenté dans plusieurs assemblys managés. Vous pouvez développer des applications SMO sur un client ou sur un serveur.  

> > [!Important]
> > La version de fichier des assemblys SMO est affichée comme majeure. **0**. Build. révision. Mais la version de l’assembly incorporé est majeure. **100**. Build. révision. Cette opération permet de conserver la version de SMO utilisée dans chaque application, de sorte que les mises à jour apportées à l’une d’elles n’affectent pas les autres.
> > 
> > Pour cette raison, vous **ne devez pas** installer ces versions des assemblys dans le global assembly cache (GAC). Cela peut entraîner l’arrêt d’autres applications, telles que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Studio. 
  
|Fichier|Description|  
|-----------|-----------------|  
|Microsoft.SqlServer.ConnectionInfo.dll|Assure la prise en charge de la connexion à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|Microsoft.SqlServer.ServiceBrokerEnum.dll|Assure la prise en charge de la programmation de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Service Broker. Celle-ci n'est requise que dans les programmes qui accèdent au Service Broker.|  
|Microsoft.SqlServer.Smo.dll|Contient la plupart des classes SMO.|  
|Microsoft.SqlServer.SmoExtended.dll<br /><br /> Microsoft.SqlServer.Management.Sdk.Sfc.dll<br /><br /> Microsoft.SqlServer.SqlEnum.dll|Assure la prise en charge des classes SMO.|  
|Microsoft.SqlServer.WmiEnum.dll|Contient les classes du fournisseur WMI (Windows Management Instrumentation). Celles-ci sont uniquement requises pour les programmes qui utilisent les classes du fournisseur WMI.|  
|Microsoft.SqlServer.RegSvrEnum.dll|Contient les classes de serveurs inscrits. Celles-ci sont uniquement requises pour les programmes qui utilisent les classes de serveurs inscrits.|  
  
  
