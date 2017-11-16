---
title: "Création des procédures stockées | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- stored procedures [Analysis Services], designing
- dependent assemblies [Analysis Services]
- assemblies [Analysis Services]
ms.assetid: af4e7bd5-041b-4a40-9942-0ef6a3af46c6
caps.latest.revision: 28
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7ce4810cec6ebfe861150aa24fea322682dc0e8c
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="designing-stored-procedures"></a>Conception des procédures stockées
  Le modèle objet administratif AMO (Analysis Management Objects) et le modèle objet orienté client ([!INCLUDE[msCoName](../../includes/msconame-md.md)] ADO (ActiveX® Data Objects) MD (Multidimensional)) sont disponibles dans les procédures stockées.  
  
 Les procédures stockées doivent être dans la portée (le serveur ou la base de données) afin d'être visibles au niveau MDX (Multidimensional Expressions) pour être appelées. Toutefois, lorsqu'une procédure stockée est appelée, sa portée ne se limite pas aux actions effectuées sous son parent. Une procédure stockée peut effectuer des modifications n'importe où sur le serveur ; elle est juste astreinte à respecter les limites de sécurité du processus utilisateur qui l'appelle ou les limites de la transaction dans laquelle elle fonctionne.  
  
 Les procédures de portée du serveur sont disponibles dans tous les contextes du serveur. Les procédures stockées de portée de base de données sont uniquement visibles dans le contexte de la base de données dans laquelle elles sont définies.  
  
 Comme pour toute fonction MDX, une procédure stockée doit être résolue pour qu'une session MDX puisse continuer ; les procédures stockées bloquent les sessions MDX pendant leur exécution. Sauf si une raison spécifique justifie l'arrêt d'une session MDX dans l'attente d'une intervention de l'utilisateur, il est fortement recommandé d'éviter toute interaction de ce type (telle qu'une boîte de dialogue par exemple).  
  
## <a name="dependent-assemblies"></a>Assemblys dépendants  
 Tous les assemblys dépendants doivent être chargés dans une instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] que le Common Language Runtime (CLR) doit trouver. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] stocke les assemblys dépendants dans le même dossier que l'assembly principal, afin que le CLR résolve automatiquement toutes les références de fonction à des fonctions de ces assemblys.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des assemblys de modèle multidimensionnel](../../analysis-services/multidimensional-models/multidimensional-model-assemblies-management.md)   
 [Définition de procédures stockées](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  

