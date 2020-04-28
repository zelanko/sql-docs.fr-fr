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
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: d2ff4537f5db246dd9bcdc114b02005402f8745f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68029594"
---
# <a name="sysssispackagefolders-transact-sql"></a>sysssispackagefolders (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient une ligne pour chaque dossier logique dans l’arborescence des dossiers [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] qui utilise. Ces dossiers sont répertoriés dans l'Explorateur d'objets de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] lorsque vous vous connectez à [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Un dossier répertorie les packages qui sont enregistrés dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou dans le système de fichiers.  
  
 La colonne **ParentFolderId** décrit l’arborescence des dossiers. Le dossier en haut de l’arborescence des dossiers contient une valeur null dans **ParentFolderId**.  
  
 La colonne **NomDossier** contient le nom des dossiers qui s’affichent dans l’Explorateur d’objets.  
  
 Cette table est stockée dans la base de données **msdb** .  

  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**FolderId**|**uniqueidentifier**|GUID du dossier.|  
|**ParentFolderId**|**uniqueidentifier**|GUID du dossier qui est le dossier parent.|  
|**NomDossier**|**sysname**|Nom du dossier. Ce nom apparaît dans l'arborescence des dossiers de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].|  
  
  
