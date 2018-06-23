---
title: Accorder des autorisations sur les procédures stockées (Analysis Services) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 01793166-a3e5-4856-8302-21b82d494e69
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: c82a2df266f9e6dce2767ecceb3e2af9bd12fc1d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36154305"
---
# <a name="grant-permissions-on-stored-procedures-analysis-services"></a>Accorder des autorisations sur des procédures stockées (Analysis Services)
  Les procédures stockées ou des assemblys, dans [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] sont des routines externes, écrites un [!INCLUDE[msCoName](../includes/msconame-md.md)] langage de programmation .NET, qui étendent les fonctionnalités de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Les assemblys permettent au développeur de tirer parti de l'intégration interlangage, de la gestion des exceptions, ainsi que de la prise en charge du contrôle de version, du déploiement et du débogage.  
  
 Vous devez être administrateur du serveur pour inscrire un assembly. Consultez [accorder des autorisations d’administrateur de serveur &#40;Analysis Services&#41;](instances/grant-server-admin-rights-to-an-analysis-services-instance.md).  
  
## <a name="security-context-for-stored-procedure-execution"></a>Contexte de sécurité pour l'exécution des procédures stockées  
 N'importe quel utilisateur peut appeler une procédure stockée. En fonction la manière dont la procédure stockée a été configurée, elle peut s'exécuter dans le contexte de l'utilisateur qui appelle la procédure ou dans le contexte d'un utilisateur anonyme. Étant donné qu'un utilisateur anonyme n'a pas de contexte de sécurité, utilisez cette fonctionnalité conjointement avec la configuration de l'instance d'[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] pour autoriser les accès anonymes.  
  
 Entre le moment où l'utilisateur appelle une procédure stockée et l'exécution, par [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], de cette dernière, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] évalue les actions incluses dans la procédure stockée. [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] évalue les actions incluses dans la procédure stockée, en se basant sur l'intersection des autorisations accordées à l'utilisateur et du jeu d'autorisations utilisé pour exécuter la procédure. Si la procédure stockée contient une action qui ne peut pas être exécutée par le rôle de base de données de l'utilisateur, l'action n'est pas exécutée.  
  
 Les jeux d'autorisations utilisés pour exécuter les procédures stockées sont répertoriés ci-dessous :  
  
-   **Safe** jeu d’autorisations avec la Safe, une procédure stockée ne peut pas accéder aux ressources protégées dans le [!INCLUDE[msCoName](../includes/msconame-md.md)] .NET Framework. Ce jeu d'autorisations ne permet que les calculs. Il s'agit du jeu d'autorisations le plus sûr ; les informations ne sortent pas d'[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], les autorisations ne peuvent pas être élevées et les risques de falsification des données sont réduits.  
  
-   **Accès externe** jeu d’autorisations avec l’accès externe, une procédure stockée peut accéder aux ressources externes à l’aide de code managé. L'affectation de ce jeu d'autorisations à une procédure stockée ne générera pas d'erreurs de programmation qui pourraient rendre le serveur instable. Toutefois, ce jeu d'autorisations peut entraîner une divulgation d'informations hors du serveur et des risques d'élévation des autorisations et de falsification des données.  
  
-   **Unrestricted** jeu d’autorisations avec la Unrestricted, une procédure stockée peut accéder aux ressources externes à l’aide de n’importe quel code. Avec ce jeu d'autorisations, il n'existe aucune garantie de sécurité ou de fiabilité pour les procédures stockées.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des assemblys de modèle multidimensionnel](multidimensional-models/multidimensional-model-assemblies-management.md)  
  
  