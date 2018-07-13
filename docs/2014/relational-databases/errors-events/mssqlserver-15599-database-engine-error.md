---
title: MSSQLSERVER_15599 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 15599 (Database Engine error)
ms.assetid: 97e427a9-8587-46ea-954b-974b5df9c223
caps.latest.revision: 8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 34e0a2cce62986b5e39b96f2afab96f5e27db59f
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37416548"
---
# <a name="mssqlserver15599"></a>MSSQLSERVER_15599
    
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
  
  
