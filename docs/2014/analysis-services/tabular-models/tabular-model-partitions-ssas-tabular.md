---
title: Partitions de modèle tabulaire (SSAS tabulaire) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.ssms.partitions.partitionmgr.imbi.f1
ms.assetid: 041c269f-a229-4a41-8794-6ba4b014ef83
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: aaa2b608665e50b25b39d78a39a57bb08b55cf31
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66066389"
---
# <a name="tabular-model-partitions-ssas-tabular"></a>Partitions de modèle tabulaire (SSAS Tabulaire)
  Les partitions divisent une table en sections logiques. Chaque partition peut ensuite être traitée (actualisée) indépendamment d'autres partitions. Les partitions définies pour un modèle au cours de la création de modèles sont dupliquées dans un modèle déployé. Une fois le déploiement terminé, vous pouvez gérer ces partitions et créer de nouvelles partitions à l'aide de la boîte de dialogue **Partitions** dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou à l'aide d'un script. Les informations fournies dans cette rubrique décrivent des partitions dans une base de données de modèle tabulaire déployée. Pour plus d’informations sur la création et la gestion des partitions lors de la création de modèles, consultez [Partitions &#40;SSAS Tabulaire&#41;](partitions-ssas-tabular.md).  
  
 Sections de cette rubrique :  
  
-   [Avantages](#bkmk_benefits)  
  
-   [autorisations](#bkmk_permissions)  
  
-   [Traiter les partitions](#bkmk_process_partitions)  
  
-   [Tâches associées](#bkmk_related_tasks)  
  
##  <a name="benefits"></a><a name="bkmk_benefits"></a>Avantageuse  
 La création de modèles efficaces fait appel à des partitions permettant d'éliminer tout traitement inutile et la charge qui en résulte au niveau du processeur sur les serveurs Analysis Services, tout en veillant en même temps à ce que les données soient traitées et actualisées suffisamment souvent pour refléter les données les plus récentes des sources de données.  
  
 Par exemple, un modèle tabulaire peut avoir une table des ventes qui inclut des données de ventes pour l'exercice fiscal 2011 et chacun des exercices précédents. La table Sales du modèle contient les trois partitions suivantes :  
  
|Partition|Données de|  
|---------------|---------------|  
|Sales2011|Exercice fiscal en cours|  
|Sales2010-2001|Exercices fiscaux 2001, 2002, 2003, 2004, 2005, 2006. 2007, 2008, 2009, 2010|  
|SalesOld|Tous les exercices fiscaux antérieurs aux dix dernières années.|  
  
 À mesure que de nouvelles données de ventes sont ajoutées pour l'exercice fiscal actuel 2011, ces données doivent être traitées quotidiennement afin de se refléter exactement dans l'analyse de données de ventes de l'exercice fiscal en cours. Par conséquent, la partition Sales2011 est traitée de nuit.  
  
 Il est inutile de traiter les données de la partition Sales2010-2001 de nuit ; toutefois, étant donné que les chiffres des ventes pour les dix exercices fiscaux précédents peuvent néanmoins occasionnellement changer en raison de retours de produit et d'autres ajustements, ils doivent toujours être traités régulièrement. De ce fait, les données de la partition Sales2010-2001 sont traitées sur une base mensuelle. Les données de la partition SalesOld ne changent jamais ; par conséquent, elles sont traitées une fois par an uniquement.  
  
 Lorsque vous entrez l’année fiscale 2012, une nouvelle partition Sales2012 est ajoutée à la table Sales du mode. La partition Sales2011 peut ensuite être fusionnée avec la partition Sales2010-2001 et renommée en Sales2011-2002. Les données de l'exercice fiscal 2001 sont éliminées de la nouvelle partition Sales2011-2002 et déplacées vers la partition SalesOld. Toutes les partitions sont ensuite traitées pour refléter les modifications.  
  
 La façon dont vous implémentez une stratégie de partition pour les modèles tabulaires de votre organisation dépend en grande partie de vos besoins en matière de traitement des données de modèle et des ressources disponibles.  
  
##  <a name="permissions"></a><a name="bkmk_permissions"></a> Autorisations  
 Pour créer, gérer et traiter des partitions dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], vous devez disposer des autorisations appropriées pour Analysis Services définies dans un rôle de sécurité. Chaque rôle de sécurité dispose d'une des autorisations suivantes :  
  
|Autorisation|Actions|  
|----------------|-------------|  
|Administrateur|Lire, traiter, créer, copier, fusionner, supprimer|  
|Process|Lire, traiter|  
|Lecture seule|Lire|  
  
 Pour en savoir plus sur la création des rôles pendant la création de modèles à l’aide de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], consultez [Rôles &#40;SSAS Tabulaire&#41;](roles-ssas-tabular.md). Pour en savoir plus sur la gestion des membres de rôles de modèles tabulaires déployés à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], consultez [Rôles de modèles tabulaires &#40;SSAS Tabulaire&#41;](tabular-model-roles-ssas-tabular.md).  
  
##  <a name="process-partitions"></a><a name="bkmk_process_partitions"></a>Traiter les partitions  
 Les partitions peuvent être traitées (actualisées) indépendamment d’autres partitions à l’aide de la boîte de dialogue **Partitions** dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] ou à l’aide d’un script. Les options suivantes sont disponibles pour le traitement :  
  
|Mode|Description|  
|----------|-----------------|  
|Traiter par défaut|Détecte l'état de traitement d'un objet de partition et effectue le traitement nécessaire pour faire passer les objets de partition non traités ou traités partiellement dans un état de traitement complet. Les données des partitions et des tables vides sont chargées ; les hiérarchies, les colonnes calculées et les relations sont créées ou reconstruites.|  
|Traiter entièrement|Traite un objet de partition et tous les objets qu'il contient. Lorsque la commande Traiter entièrement est exécutée pour un objet qui a déjà été traité, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] supprime toutes les données de l'objet, puis traite l'objet. Ce type de traitement est obligatoire lorsqu'une modification structurelle a été apportée à un objet.|  
|Traiter les données|Chargez les données dans une partition ou une table sans reconstruire les hiérarchies ou les relations ni recalculer les colonnes calculées et les mesures.|  
|Traiter l'effacement|Supprime toutes les données d'une partition.|  
|Traiter l'ajout|Mise à jour incrémentielle de la partition avec de nouvelles données.|  
  
##  <a name="related-tasks"></a><a name="bkmk_related_tasks"></a> Tâches associées  
  
|Tâche|Description|  
|----------|-----------------|  
|[Créer et gérer des partitions de modèles tabulaires &#40;SSAS Tabulaire&#41;](create-and-manage-tabular-model-partitions-ssas-tabular.md)|Explique comment créer et gérer des partitions dans un modèle tabulaire déployé à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].|  
|[Traiter les partitions de modèles tabulaires &#40;SSAS Tabulaire&#41;](process-tabular-model-partitions-ssas-tabular.md)|Explique comment traiter des partitions dans un modèle tabulaire déployé à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].|  
  
  
