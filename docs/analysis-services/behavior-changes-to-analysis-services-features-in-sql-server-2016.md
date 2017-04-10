---
title: "Modifications du comportement des fonctionnalit&#233;s d’Analysis Services dans SQL Server 2016 | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 92ebd5cb-afb6-4b62-968f-39f5574a452b
caps.latest.revision: 17
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 17
---
# Modifications du comportement des fonctionnalit&#233;s d’Analysis Services dans SQL Server 2016
  Une *modifications de comportement* affecte le mode de fonctionnement ou d’interaction des fonctionnalités de la version actuelle de SQL Server par rapport aux versions précédentes.  
  
 Une révision des valeurs par défaut, une configuration manuelle requise pour une mise à niveau ou une restauration, ou une nouvelle implémentation d’une fonction existante sont toutes des exemples de modification de comportement dans le produit.  
  
 Les comportements de fonctionnalité modifiés dans cette version, mais qui restent opérationnels après la mise à niveau d’un modèle ou d’un code, sont répertoriés ici.  
  
> [!NOTE]  
>  Contrairement à une *modification de comportement*, une *modification avec rupture* empêche un modèle de données ou une application intégrée dans [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] de s’exécuter après la mise à niveau d’un serveur, d’un outil client ou d’un modèle. Pour voir la liste, visitez la page [Modifications avec rupture dans les fonctionnalités Analysis Services de SQL Server 2016](../analysis-services/breaking-changes-to-analysis-services-features-in-sql-server-2016.md).  
  
## Analysis Services en mode SharePoint  
 L’exécution de l’Assistant de configuration de PowerPivot en tant que tâche de post-installation n’est plus nécessaire. Cela est vrai pour toutes les versions prises en charge de SharePoint qui chargent les modèles à partir de la version [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] actuelle d’[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
## Mode DirectQuery dans les modèles tabulaires  
 *DirectQuery* est un mode d’accès aux données des modèles tabulaires, où la requête s’exécute sur une base de données relationnelle principale, extrayant le jeu de résultats en temps réel. Il est souvent utilisé pour les jeux de données trop volumineux pour la mémoire ou lorsque les données sont volatiles et que vous souhaitez recevoir les données les plus récentes suite aux requêtes exécutées sur un modèle tabulaire.  
  
 Dans plusieurs versions précédentes, DirectQuery existait sous la forme d’un mode d’accès aux données. Dans [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)], l’implémentation a été légèrement modifiée, en supposant que le modèle tabulaire soit au niveau de compatibilité 1200. DirectQuery a moins de restrictions qu’auparavant. Il propose également d’autres propriétés de base de données.  
  
 Si vous utilisez DirectQuery dans un modèle tabulaire existant, vous pouvez conserver ce dernier à son niveau de compatibilité actuel (1100 ou 1103) et continuer de l’utiliser tel qu’il est mis en œuvre à ces niveaux. Vous pouvez également passer au niveau de compatibilité 1200 pour tirer parti des améliorations apportées à DirectQuery dans cette version de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 Il n’existe aucune mise à niveau in situ d’un modèle DirectQuery, car les paramètres des niveaux de compatibilité plus anciens n’ont pas d’équivalents exacts dans le niveau de compatibilité 1200. Si votre modèle tabulaire s’exécute en mode DirectQuery, vous devez l’ouvrir dans SQL Server Data Tools, désactiver DirectQuery, régler le paramètre **Niveau de compatibilité** sur 1200, puis reconfigurer les propriétés de DirectQuery pour les modèles tabulaires 1200. Pour plus d’informations, consultez [Mode DirectQuery &#40;SSAS Tabulaire&#41;](../analysis-services/tabular-models/directquery-mode-ssas-tabular.md).  
  
## Voir aussi  
 [Compatibilité descendante_supprimé](../Topic/Backward%20Compatibility_deleted.md)   
 [Modifications avec rupture dans les fonctionnalités Analysis Services de SQL Server 2016](../analysis-services/breaking-changes-to-analysis-services-features-in-sql-server-2016.md)   
 [Niveau de compatibilité pour les modèles tabulaires dans Analysis Services](../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)   
 [Télécharger SQL Server Data Tools](https://msdn.microsoft.com/en-us/library/mt204009.aspx)  
  
  