---
title: sysssispackagefolders (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysdtspackagefolders90
- sysdtspackagefolders90_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysssispackagefolders system table
ms.assetid: ddc4833f-27bf-4610-b739-d257961d17ac
author: douglasl
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5166d82d0212c3974cbc7f95b071765ef25afdb6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47740587"
---
# <a name="sysssispackagefolders-transact-sql"></a>sysssispackagefolders (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient une ligne pour chaque dossier logique dans l’arborescence des dossiers qui [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] utilise. Ces dossiers sont répertoriés dans l'Explorateur d'objets de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] lorsque vous vous connectez à [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Un dossier répertorie les packages qui sont enregistrés dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou dans le système de fichiers.  
  
 Le **parentfolderid** colonne décrit l’arborescence des dossiers. Le dossier en haut de la hiérarchie de dossiers contient une valeur null dans **parentfolderid**.  
  
 Le **NomDossier** colonne contient le nom des dossiers qui apparaissent dans l’Explorateur d’objets.  
  
 Cette table est stockée dans le **msdb** base de données.  

  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**folderId**|**uniqueidentifier**|GUID du dossier.|  
|**parentfolderid**|**uniqueidentifier**|GUID du dossier qui est le dossier parent.|  
|**nom du dossier**|**sysname**|Nom du dossier. Ce nom apparaît dans l'arborescence des dossiers de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].|  
  
  
