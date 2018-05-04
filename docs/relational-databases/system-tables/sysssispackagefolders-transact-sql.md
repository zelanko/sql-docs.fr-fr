---
title: sysssispackagefolders (Transact-SQL) | Documents Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sysdtspackagefolders90
- sysdtspackagefolders90_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysssispackagefolders system table
ms.assetid: ddc4833f-27bf-4610-b739-d257961d17ac
caps.latest.revision: 22
author: douglasl
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b4c3a4106a16be5c2f223ec253fcd9e5c8491daf
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="sysssispackagefolders-transact-sql"></a>sysssispackagefolders (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient une ligne pour chaque dossier logique dans l’arborescence des dossiers qui [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] utilise. Ces dossiers sont répertoriés dans l'Explorateur d'objets de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] lorsque vous vous connectez à [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Un dossier répertorie les packages qui sont enregistrés dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou dans le système de fichiers.  
  
 Le **parentfolderid** colonne décrit l’arborescence des dossiers. Le dossier en haut de la hiérarchie de dossiers contient une valeur null dans **parentfolderid**.  
  
 Le **NomDossier** colonne contient le nom des dossiers qui s’affichent dans l’Explorateur d’objets.  
  
 Cette table est stockée dans le **msdb** base de données.  

  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**folderId**|**uniqueidentifier**|GUID du dossier.|  
|**parentfolderid**|**uniqueidentifier**|GUID du dossier qui est le dossier parent.|  
|**nom de dossier**|**sysname**|Nom du dossier. Ce nom apparaît dans l'arborescence des dossiers de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].|  
  
  
