---
description: Tables Integration Services (Transact-SQL)
title: Tables Integration Services (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- SQL Server Integration Services system tables
- system tables [SQL Server], Integration Services
- system tables [Integration Services]
- SSIS, system tables
ms.assetid: 683b181b-0091-4a9c-86db-bc577af43cec
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 05f7e319dbaec37761eb5488f9d9a33cce09f3a4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88473244"
---
# <a name="integration-services-tables-transact-sql"></a>Tables Integration Services (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Les rubriques de cette section décrivent les tables système de la base de données msdb qui stockent les informations utilisées par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
## <a name="in-this-section"></a>Dans cette section  
 [sysssislog](../../relational-databases/system-tables/sysssislog-transact-sql.md)  
 Contient une ligne pour chaque entrée de journal générée par un package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] au moment de l'exécution.  
  
 Cette table ne sert que lorsque des packages utilisent le module fournisseur d'informations [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [sysssispackagefolders](../../relational-databases/system-tables/sysssispackagefolders-transact-sql.md)  
 Contient une ligne pour chaque dossier logique dont se sert le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] pour organiser les packages. Les valeurs de colonne définissent les relations parent/enfant entre les dossiers imbriqués.  
  
> [!NOTE]  
>  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] affiche les packages stockés dans une vue hiérarchique lorsque vous vous connectez au service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [sysssispackages](../../relational-databases/system-tables/sysssispackages-transact-sql.md)  
 Contient une ligne pour chaque package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 Cette table est utilisée uniquement lorsque vous stockez des packages dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
  
