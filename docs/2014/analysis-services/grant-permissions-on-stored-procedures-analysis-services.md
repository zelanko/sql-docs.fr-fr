---
title: Accorder des autorisations sur des procédures stockées (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 01793166-a3e5-4856-8302-21b82d494e69
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9a363336af1bee8c3f84ff620f667c7c0d510b73
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66080729"
---
# <a name="grant-permissions-on-stored-procedures-analysis-services"></a>Accorder des autorisations sur des procédures stockées (Analysis Services)
  Dans [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], les procédures stockées, ou assemblys, sont des routines externes écrites dans un langage de programmation [!INCLUDE[msCoName](../includes/msconame-md.md)] .NET, qui étendent les possibilités d'[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Les assemblys permettent au développeur de tirer parti de l'intégration interlangage, de la gestion des exceptions, ainsi que de la prise en charge du contrôle de version, du déploiement et du débogage.  
  
 Vous devez être administrateur du serveur pour inscrire un assembly. Consultez [accorder des autorisations d’administrateur de serveur &#40;Analysis Services&#41;](instances/grant-server-admin-rights-to-an-analysis-services-instance.md).  
  
## <a name="security-context-for-stored-procedure-execution"></a>Contexte de sécurité pour l'exécution des procédures stockées  
 N'importe quel utilisateur peut appeler une procédure stockée. En fonction la manière dont la procédure stockée a été configurée, elle peut s'exécuter dans le contexte de l'utilisateur qui appelle la procédure ou dans le contexte d'un utilisateur anonyme. Étant donné qu'un utilisateur anonyme n'a pas de contexte de sécurité, utilisez cette fonctionnalité conjointement avec la configuration de l'instance d'[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] pour autoriser les accès anonymes.  
  
 Entre le moment où l'utilisateur appelle une procédure stockée et l'exécution, par [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], de cette dernière, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] évalue les actions incluses dans la procédure stockée. 
  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] évalue les actions incluses dans la procédure stockée, en se basant sur l'intersection des autorisations accordées à l'utilisateur et du jeu d'autorisations utilisé pour exécuter la procédure. Si la procédure stockée contient une action qui ne peut pas être exécutée par le rôle de base de données de l'utilisateur, l'action n'est pas exécutée.  
  
 Les jeux d'autorisations utilisés pour exécuter les procédures stockées sont répertoriés ci-dessous :  
  
-   **Sécurité** Avec le jeu d’autorisations SAFE, une procédure stockée ne peut pas accéder aux [!INCLUDE[msCoName](../includes/msconame-md.md)] ressources protégées dans le .NET Framework. Ce jeu d'autorisations ne permet que les calculs. Il s'agit du jeu d'autorisations le plus sûr ; les informations ne sortent pas d'[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], les autorisations ne peuvent pas être élevées et les risques de falsification des données sont réduits.  
  
-   **Accès externe** Avec le jeu d’autorisations d’accès externe, une procédure stockée peut accéder à des ressources externes à l’aide de code managé. L'affectation de ce jeu d'autorisations à une procédure stockée ne générera pas d'erreurs de programmation qui pourraient rendre le serveur instable. Toutefois, ce jeu d'autorisations peut entraîner une divulgation d'informations hors du serveur et des risques d'élévation des autorisations et de falsification des données.  
  
-   Non **restreint** Avec le jeu d’autorisations non restreint, une procédure stockée peut accéder à des ressources externes à l’aide de n’importe quel code. Avec ce jeu d'autorisations, il n'existe aucune garantie de sécurité ou de fiabilité pour les procédures stockées.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des assemblys de modèles multidimensionnels](multidimensional-models/multidimensional-model-assemblies-management.md)  
  
  
