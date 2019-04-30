---
title: Remplacé des plans de maintenance de base de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- suspended database maintenance plans
- database maintenance plans [SQL Server Agent]
- maintenance plans [SQL Server Agent]
ms.assetid: efac127c-6c81-4c7a-a6c4-9aae5d15545d
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 769bc3ad8b330afd81b14aed1340a67c1d7812ef
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63137592"
---
# <a name="database-maintenance-plans-superseded"></a>Les plans de maintenance de la base de données sont obsolètes
    
## <a name="component"></a>Composant  
 Agent [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
## <a name="description"></a>Description  
 Les plans de maintenance de base de données existants sont mis à niveau et peuvent encore être utilisés. Cependant, vous ne pourrez pas créer de nouveaux plans de maintenance de base de données en utilisant [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Pour afficher les plans de maintenance dans l'Explorateur d'objets, développez Gestion, puis Existant. Vous pouvez migrer des plans de maintenance de base de données existants vers le nouveau format en sélectionnant **Migrate** dans le menu contextuel pour n’importe quel plan de maintenance de base de données. Certaines fonctionnalités peuvent être perdues après la migration, car la fonction de nouveau plan de maintenance ne remplace pas directement les plans de maintenance de base de données. Étant donné que la migration d'un plan de maintenance de base de données ne supprime pas le plan existant, vous avez la possibilité de tester les fonctionnalités du nouveau plan de maintenance avant de supprimer le plan antérieur.  
  
 Les fonctionnalités suivantes ne sont plus prises en charge dans les plans de maintenance de base de données :  
  
-   Envoi des journaux de transaction  
  
-   Le **tenter de réparer tout problème mineur** possibilité du **contrôle d’intégrité de base de données** tâche  
  
## <a name="corrective-action"></a>Action corrective  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] empêche que l'envoi des journaux soit inclus dans un plan de maintenance de base de données. Pour plus d'informations, consultez « Copie des journaux de transaction » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
  
