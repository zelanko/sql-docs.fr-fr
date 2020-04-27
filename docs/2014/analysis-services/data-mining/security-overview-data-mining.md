---
title: Vue d’ensemble de la sécurité (exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- security [Analysis Services - data mining], about security
ms.assetid: 387bde00-bcf3-4612-b27b-f9f608dbf71e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c55224b5590d23008de8b6caef7f120748f232bf
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66082899"
---
# <a name="security-overview-data-mining"></a>Vue d'ensemble de la sécurité (exploration de données)
  Le processus de sécurisation [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] se produit à plusieurs niveaux. Vous devez sécuriser chaque instance d' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] et ses sources de données pour vous assurer que seuls les utilisateurs autorisés disposent d'autorisations de lecture/écriture sur les dimensions, les modèles d'exploration de données et les sources de données sélectionnés. Vous devez également sécuriser les sources de données sous-jacentes pour empêcher les utilisateurs non autorisés de compromettre volontairement les informations professionnelles sensibles. Le processus de sécurisation d’une instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] est décrit dans les rubriques suivantes.  
  
##  <a name="security-architecture"></a><a name="bkmk_Architecture"></a>Architecture de la sécurité  
 Consultez les ressources suivantes pour en savoir plus sur l'architecture de sécurité de base d'une instance d' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], notamment sur la manière dont [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] utilise l'authentification Windows de [!INCLUDE[msCoName](../../includes/msconame-md.md)] pour authentifier l'accès utilisateur.  
  
-   [Rôles de sécurité &#40;Analysis Services - Données multidimensionnelles&#41;](../multidimensional-models/olap-logical/security-roles-analysis-services-multidimensional-data.md)  
  
-   [Propriétés de sécurité](../server-properties/security-properties.md)  
  
-   [Configurer les comptes de service &#40;Analysis Services&#41;](../instances/configure-service-accounts-analysis-services.md)  
  
-   [Autorisation de l’accès à des objets et des opérations &#40;Analysis Services&#41;](../multidimensional-models/authorizing-access-to-objects-and-operations-analysis-services.md)  
  
##  <a name="configuring-the-logon-account-for-analysis-services"></a><a name="bkmk_Logon"></a> Configuration du compte d'ouverture de session d'Analysis Services  
 Vous devez sélectionner un compte d’ouverture de session approprié pour [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] et définir ses autorisations. Vous devez vérifier que le compte d’ouverture de session [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dispose uniquement des autorisations indispensables pour effectuer les tâches nécessaires, notamment les autorisations appropriées sur les sources de données sous-jacentes.  
  
 Dans le cadre de l'exploration de données, le jeu d'autorisations permettant de créer et de traiter des modèles doit être différent de celui permettant de les afficher et de les interroger. L'élaboration de prédictions sur un modèle est une sorte de requête et ne requiert pas d'autorisations d'administration.  
  
##  <a name="securing-an-analysis-services-instance"></a><a name="bkmk_Instance"></a> Sécurisation d'une instance d'Analysis Services  
 Ensuite, vous devez protéger l’ordinateur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , le système d’exploitation Windows de l’ordinateur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] proprement dit et les sources de données utilisées par [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
##  <a name="configuring-access-to-analysis-services"></a><a name="bkmk_Access"></a> Configuration de l'accès à Analysis Services  
 Lorsque vous configurez et définissez les utilisateurs autorisés d'une instance d' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], vous devez déterminer quels utilisateurs sont également autorisés à administrer des objets de base de données spécifiques, ceux qui peuvent afficher la définition d'objets ou parcourir les modèles, et ceux qui ont la possibilité d'accéder directement aux sources de données.  
  
##  <a name="special-considerations-for-data-mining"></a><a name="bkmk_DMspecial"></a> Considérations spéciales relatives à l'exploration de données  
 Pour permettre à un analyste ou un développeur de créer et de tester des modèles d'exploration de données, vous devez lui donner des autorisations administratives sur la base de données dans laquelle les modèles d'exploration de données sont stockés. Par conséquent, l'analyste ou le développeur d'exploration de données peut potentiellement créer ou supprimer d'autres objets qui ne sont pas associés à l'exploration de données, y compris les objets d'exploration de données qui ont été créés et utilisés par d'autres analystes ou développeurs, ou les objets OLAP non inclus dans la solution d'exploration de données.  
  
 De ce fait, lorsque vous créez une solution d'exploration de données, vous devez trouver le juste équilibre entre les besoins de l'analyste ou du développeur pour développer, tester et paramétrer des modèles et ceux des autres utilisateurs, et devez prendre les mesures nécessaire pour protéger les objets de base de données existants. L'une des approches possibles consiste à créer une base de données distincte réservée à l'exploration de données, ou à créer des bases de données différentes pour chaque analyste.  
  
 Même si la création de modèles requiert le niveau d'autorisations le plus élevé, vous pouvez contrôler l'accès de l'utilisateur aux modèles d'exploration de données pour d'autres opérations, telles que le traitement, l'exploration ou l'interrogation, en utilisant la sécurité basée sur les rôles. Lorsque vous créez un rôle, vous définissez des autorisations spécifiques aux objets d'exploration de données. Tout utilisateur membre d'un rôle dispose automatiquement de toutes les autorisations qui lui sont associées.  
  
 En outre, les modèles d'exploration de données référencent souvent des sources de données qui contiennent des informations sensibles. Si le modèle et la structure d'exploration de données ont été configurés pour autoriser l'extraction du modèle vers les données de la structure, vous devez prendre les précautions nécessaires pour masquer les informations sensibles ou limiter le nombre d'utilisateurs qui ont accès aux données sous-jacentes.  
  
 Si vous utilisez des packages Integration Services pour nettoyer des données, pour mettre à jour des modèles d'exploration de données ou pour élaborer des prédictions, vous devez vous assurer que le service Integration Services dispose des autorisations appropriées sur la base de données dans laquelle le modèle est stocké et sur les données sources.  
  
## <a name="see-also"></a>Voir aussi  
 [Rôles et autorisations &#40;Analysis Services&#41;](../multidimensional-models/roles-and-permissions-analysis-services.md)  
  
  
