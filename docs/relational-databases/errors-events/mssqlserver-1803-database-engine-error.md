---
title: MSSQLSERVER_1803 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 1803 (Database Engine error)
ms.assetid: d4315390-82f1-4c4c-8d1b-1a4989537cca
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 013012ceb495ceb0b5b9e8fc207c9775713a8d5f
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver1803"></a>MSSQLSERVER_1803
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|1803|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|NO_SPACE|  
|Texte du message|Échec de CREATE DATABASE. Le fichier primaire doit être doté d’une capacité minimale de %d Mo pour recevoir une copie de la base de données model.|  
  
## <a name="explanation"></a>Explication  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] crée une base de données en effectuant une copie de la base de données model. Ensuite, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] renomme la copie et agrandit la nouvelle base de données à la taille demandée. Dans le cas présent, l'utilisateur a essayé de créer une base de données plus petite que la base de données model. L'opération a échoué car la copie de la base de données model ne correspondait pas au fichier de données primaire, parce que le fichier était plus petit que la base de données model.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Créez la base de données en utilisant une plus grande taille pour le fichier de base de données. Réduisez ensuite si vous le souhaitez la base de données en utilisant [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou l'instruction DBCC SHRINKDATABASE.  
  
