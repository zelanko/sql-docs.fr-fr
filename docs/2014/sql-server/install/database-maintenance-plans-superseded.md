---
title: Plans de maintenance de base de données remplacés | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- suspended database maintenance plans
- database maintenance plans [SQL Server Agent]
- maintenance plans [SQL Server Agent]
ms.assetid: efac127c-6c81-4c7a-a6c4-9aae5d15545d
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7d41763582632a92b3a38bdbd67ee55b65f95b6d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66095760"
---
# <a name="database-maintenance-plans-superseded"></a>Les plans de maintenance de la base de données sont obsolètes
    
## <a name="component"></a>Composant  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent  
  
## <a name="description"></a>Description  
 Les plans de maintenance de base de données existants sont mis à niveau et peuvent encore être utilisés. Cependant, vous ne pourrez pas créer de nouveaux plans de maintenance de base de données en utilisant [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Pour afficher les plans de maintenance dans l'Explorateur d'objets, développez Gestion, puis Existant. Vous pouvez migrer des plans de maintenance de base de données existants vers le nouveau format en sélectionnant **migrer** dans le menu contextuel de n’importe quel plan de maintenance de base de données. Certaines fonctionnalités peuvent être perdues après la migration, car la fonction de nouveau plan de maintenance ne remplace pas directement les plans de maintenance de base de données. Étant donné que la migration d'un plan de maintenance de base de données ne supprime pas le plan existant, vous avez la possibilité de tester les fonctionnalités du nouveau plan de maintenance avant de supprimer le plan antérieur.  
  
 Les fonctionnalités suivantes ne sont plus prises en charge dans les plans de maintenance de base de données :  
  
-   Copie des journaux de transaction  
  
-   L’option **tenter de réparer les problèmes mineurs** de la tâche **de vérification de l’intégrité de la base de données**  
  
## <a name="corrective-action"></a>Action corrective  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] empêche que l'envoi des journaux soit inclus dans un plan de maintenance de base de données. Pour plus d'informations, consultez « Copie des journaux de transaction » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
  
