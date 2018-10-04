---
title: Rôles et autorisations (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- security [Analysis Services], about security
- security [Analysis Services - multidimensional data], about security
ms.assetid: bb885447-868b-4686-853c-8241f63d4370
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: bc36b27bea2c546582cb167046affcc0fbd0d5a6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48114111"
---
# <a name="roles-and-permissions-analysis-services"></a>Rôles et autorisations (Analysis Services)
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] fournit un modèle d’autorisation basé sur les rôles qui accorde l’accès aux opérations, aux objets, ainsi qu’aux données. Tous les utilisateurs qui accèdent à une instance ou à une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] doivent effectuer cette opération dans le contexte d’un rôle.  
  
 En tant qu’administrateur système d’ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , vous êtes chargé d’accorder l’appartenance au **rôle d’administrateur de serveur** qui donne un accès sans restrictions aux opérations sur le serveur. Ce rôle comporte des autorisations fixes et ne peut pas être personnalisé. Par défaut, les membres du groupe local Administrateurs sont automatiquement des administrateurs système d'Analysis Services.  
  
 L’accord de l’accès aux utilisateurs non-administrateurs qui interrogent ou traitent des données s’effectue par l’intermédiaire de **rôles de base de données**. Les administrateurs système et les administrateurs de base de données peuvent tous deux créer les rôles qui décrivent les différents niveaux d'accès à une base de données spécifique, puis attribuer l'appartenance à chaque utilisateur qui a besoin de l'accès. Chaque rôle dispose d'un ensemble personnalisé d'autorisations pour l'accès aux objets et aux opérations dans une base de données particulière. Vous pouvez attribuer des autorisations au niveau des bases de données, des objets intérieurs tels que les cubes et les dimensions (mais pas les perspectives) et des lignes.  
  
 Il est courant de créer des rôles et d'affecter l'appartenance en tant qu'opération distincte. Souvent, le concepteur de modèles ajoute des rôles pendant la phase de conception. De cette manière, toutes les définitions de rôles sont reflétées dans les fichiers de projet qui définissent le modèle. L'appartenance au rôle est généralement transférée ultérieurement, quand la base de données entre en production, généralement par les administrateurs de base de données qui créent des scripts pouvant être développés, testés et exécutés comme une opération indépendante.  
  
 Toutes les autorisations sont établies sur une identité d'utilisateur Windows valide. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] utilise l’authentification Windows exclusivement pour authentifier les identités des utilisateurs. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] n’offre aucune méthode d’authentification propriétaire. Consultez [méthodologies d’authentification pris en charge par Analysis Services](../instances/authentication-methodologies-supported-by-analysis-services.md).  
  
> [!IMPORTANT]  
>  Les autorisations s'ajoutent pour chaque utilisateur ou groupe Windows, parmi tous les rôles de la base de données. Si un rôle interdit à un utilisateur ou à un groupe d'exécuter certaines tâches ou d'afficher certaines données, mais qu'un autre rôle lui permet de le faire, l'utilisateur ou le groupe est autorisé à exécuter la tâche ou à afficher les données.  
  
## <a name="in-this-section"></a>Contenu de cette section  
  
-   [Autoriser l’accès aux objets et aux opérations &#40;Analysis Services&#41;](authorizing-access-to-objects-and-operations-analysis-services.md)  
  
-   [Accorder des autorisations de base de données &#40;Analysis Services&#41;](grant-database-permissions-analysis-services.md)  
  
-   [Accorder des autorisations de cube ou modèle &#40;Analysis Services&#41;](grant-cube-or-model-permissions-analysis-services.md)  
  
-   [Accorder des autorisations de processus &#40;Analysis Services&#41;](grant-process-permissions-analysis-services.md)  
  
-   [Octroyer des autorisations de définition des métadonnées de l’objet lire &#40;Analysis Services&#41;](grant-read-definition-permissions-on-object-metadata-analysis-services.md)  
  
-   [Accorder des autorisations sur un objet de source de données &#40;Analysis Services&#41;](grant-permissions-on-a-data-source-object-analysis-services.md)  
  
-   [Accorder des autorisations sur les structures d’exploration de données et modèles &#40;Analysis Services&#41;](grant-permissions-on-data-mining-structures-and-models-analysis-services.md)  
  
-   [Accorder des autorisations sur une dimension &#40;Analysis Services&#41;](grant-permissions-on-a-dimension-analysis-services.md)  
  
-   [Octroyer un accès personnalisé aux données de dimension &#40;Analysis Services&#41;](grant-custom-access-to-dimension-data-analysis-services.md)  
  
-   [Octroyer un accès personnalisé aux données des cellules &#40;Analysis Services&#41;](grant-custom-access-to-cell-data-analysis-services.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Créer et gérer des rôles &#40;SSAS tabulaire&#41;](../tabular-models/roles-ssas-tabular.md)  
  
  
