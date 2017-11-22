---
title: "Fichiers et numéros de Version | Documents Microsoft"
ms.custom: 
ms.date: 08/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: smo
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, versions
- components [SMO]
- files [SMO], components
- SMO [SQL Server], versions
- versions [SMO]
ms.assetid: 510907b6-e7a9-41bd-b892-d6d99a5118e1
caps.latest.revision: "34"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1a81684285e79e8e79ca1eca79ef24310d64502e
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="files-and-version-numbers"></a>Fichiers et numéros de version
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Requis tous les composants de SQL Server Management Object (SMO) sont inclus dans le package NuGet de Microsoft.SqlServer.SqlManagementObjects. SMO est implémenté dans plusieurs assemblys managés. Vous pouvez développer des applications SMO sur un client ou sur un serveur.  

>>[!Important]
La version du fichier des assemblys SMO s’affiche en tant que principaux. **0**. Build.Revision. Mais la version d’assembly incorporée est majeure. **100**. Build.Revision. Pour cela, vous permettant de séparer la version de SMO utilisée dans chaque application afin de mises à jour à un n’affecte pas les autres.
>>
>>Pour cette raison, vous devez **pas** installez ces versions des assemblys au Global Assembly Cache (GAC). Cela peut entraîner des autres applications, telles que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Studio, pour arrêter l’exécution. 
  
|Fichier| Description|  
|-----------|-----------------|  
|Microsoft.SqlServer.ConnectionInfo.dll|Assure la prise en charge de la connexion à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|Microsoft.SqlServer.ServiceBrokerEnum.dll|Assure la prise en charge de la programmation de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Service Broker. Celle-ci n'est requise que dans les programmes qui accèdent au Service Broker.|  
|Microsoft.SqlServer.Smo.dll|Contient la plupart des classes SMO.|  
|Microsoft.SqlServer.SmoExtended.dll<br /><br /> Microsoft.SqlServer.Management.Sdk.Sfc.dll<br /><br /> Microsoft.SqlServer.SqlEnum.dll|Assure la prise en charge des classes SMO.|  
|Microsoft.SqlServer.WmiEnum.dll|Contient les classes du fournisseur WMI (Windows Management Instrumentation). Celles-ci sont uniquement requises pour les programmes qui utilisent les classes du fournisseur WMI.|  
|Microsoft.SqlServer.RegSvrEnum.dll|Contient les classes de serveurs inscrits. Celles-ci sont uniquement requises pour les programmes qui utilisent les classes de serveurs inscrits.|  
  
  
