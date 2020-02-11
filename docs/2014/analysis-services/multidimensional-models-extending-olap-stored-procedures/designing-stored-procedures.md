---
title: Conception de procédures stockées | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- stored procedures [Analysis Services], designing
- dependent assemblies [Analysis Services]
- assemblies [Analysis Services]
ms.assetid: af4e7bd5-041b-4a40-9942-0ef6a3af46c6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2948b255f6b6cab85ae5dad71cc9b2f59e547b63
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62727658"
---
# <a name="designing-stored-procedures"></a>Conception des procédures stockées
  Le modèle objet administratif AMO (Analysis Management Objects) et le modèle objet orienté client ([!INCLUDE[msCoName](../../includes/msconame-md.md)] ADO (ActiveX® Data Objects) MD (Multidimensional)) sont disponibles dans les procédures stockées.  
  
 Les procédures stockées doivent être dans la portée (le serveur ou la base de données) afin d'être visibles au niveau MDX (Multidimensional Expressions) pour être appelées. Toutefois, lorsqu'une procédure stockée est appelée, sa portée ne se limite pas aux actions effectuées sous son parent. Une procédure stockée peut effectuer des modifications n'importe où sur le serveur ; elle est juste astreinte à respecter les limites de sécurité du processus utilisateur qui l'appelle ou les limites de la transaction dans laquelle elle fonctionne.  
  
 Les procédures de portée du serveur sont disponibles dans tous les contextes du serveur. Les procédures stockées de portée de base de données sont uniquement visibles dans le contexte de la base de données dans laquelle elles sont définies.  
  
 Comme pour toute fonction MDX, une procédure stockée doit être résolue pour qu'une session MDX puisse continuer ; les procédures stockées bloquent les sessions MDX pendant leur exécution. Sauf si une raison spécifique justifie l'arrêt d'une session MDX dans l'attente d'une intervention de l'utilisateur, il est fortement recommandé d'éviter toute interaction de ce type (telle qu'une boîte de dialogue par exemple).  
  
## <a name="dependent-assemblies"></a>Assemblys dépendants  
 Tous les assemblys dépendants doivent être chargés dans une instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] que le Common Language Runtime (CLR) doit trouver. 
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] stocke les assemblys dépendants dans le même dossier que l'assembly principal, afin que le CLR résolve automatiquement toutes les références de fonction à des fonctions de ces assemblys.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des assemblys de modèles multidimensionnels](../multidimensional-models/multidimensional-model-assemblies-management.md)   
 [Définition de procédures stockées](../multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  
