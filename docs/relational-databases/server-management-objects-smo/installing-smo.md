---
title: Installation de SMO | Documents Microsoft
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.prod_service: database-engine
ms.component: smo
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- installing SMO
- SMO [SQL Server], installing
- SQL Server Management Objects, installing
ms.assetid: 140e9971-4940-4866-89b9-5cec938e2a16
caps.latest.revision: 46
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: f7c6e834fc29304a92548a5c51776825b88687c1
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
#<a name="installing-smo"></a>Installation de SMO

[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

Cette page fournit des informations sur l’installation de SMO pour une utilisation par les applications et la configuration système requise pour utiliser SMO.

## <a name="smo-nuget-package"></a>Package NuGet SMO

À partir de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2017 SMO est distribué en tant que le [Microsoft.SqlServer.SqlManagementObjects](https://www.nuget.org/packages/Microsoft.SqlServer.SqlManagementObjects) package NuGet permettant aux utilisateurs de développer des applications avec SMO.

Il s’agit d’un remplacement pour SharedManagementObjects.msi, ce qui a été précédemment publiée en tant que partie du Feature Pack SQL pour chaque version de SQL Server. Les applications qui utilisent SMO doivent être mis à jour pour utiliser le package NuGet à la place et seront chargées de s’assurant que les fichiers binaires sont installés avec l’application en cours de développement.

>>[!Important]
>>Comme indiqué sur la [les numéros de Version et les fichiers](files-and-version-numbers.md) page, vous ne devez pas installer les assemblys SMO dans le GAC. Cela peut entraîner des problèmes avec d’autres applications qui utilisent également de ces versions de SMO (telles que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Studio).

##<a name="installing-the-package"></a>Installation du Package

Consultez [NuGet Quick Start - utilisez un Package](https://docs.microsoft.com/en-us/nuget/quickstart/use-a-package) pour obtenir des instructions et des exemples d’installation et à l’aide d’un package NuGet. 
  
## <a name="system-requirements"></a>Configuration système requise
  
 SMO requiert [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 4.0 à exécuter, les applications qui l’utilisent doivent donc vous assurer que les ordinateurs clients ont cette version ou une version ultérieure.
  
