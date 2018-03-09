---
title: MSSQLSERVER_15599 | Microsoft Docs
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
- 15599 (Database Engine error)
ms.assetid: 97e427a9-8587-46ea-954b-974b5df9c223
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 52017ed6cc9280cb122f84e6ef0b0e884fe5f8ed
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver15599"></a>MSSQLSERVER_15599
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|15599|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|SEC_LOCAL_TEMP_AUDIT_PERMISSIONS|  
|Texte du message|Impossible de définir l'audit et des autorisations sur des objets temporaires locaux.|  
  
## <a name="explanation"></a>Explication  
L'audit et les autorisations n'ont aucun effet une fois définis pour les objets temporaires locaux ou globaux. Les instructions ne provoquent pas une erreur (les opérations réussissent), mais n'ont aucun effet.  
  
Ce comportement n'a pas changé, mais à partir de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], ce message d'information avertit l'utilisateur.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Aucune action n'est nécessaire, mais envisagez de supprimer les instructions qui essaient de définir l'audit ou des autorisations sur les objets temporaires locaux ou globaux.  
  
