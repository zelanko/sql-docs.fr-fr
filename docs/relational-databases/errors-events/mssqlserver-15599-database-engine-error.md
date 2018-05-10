---
title: MSSQLSERVER_15599 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 15599 (Database Engine error)
ms.assetid: 97e427a9-8587-46ea-954b-974b5df9c223
caps.latest.revision: 8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 01ad3f136b948fc9d62d863a91c9c1b9a571edea
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
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
  
