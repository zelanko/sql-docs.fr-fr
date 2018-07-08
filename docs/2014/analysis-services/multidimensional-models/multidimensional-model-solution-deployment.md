---
title: Déploiement de solutions de modèle multidimensionnel | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services deployments, planning
- deploying [Analysis Services]
- deploying [Analysis Services], planning
ms.assetid: 7259c201-ff54-43e8-bda5-a6d51474e0e6
caps.latest.revision: 38
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 781bbeed98772266d4ea9c228c42426df424fe1c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37222219"
---
# <a name="multidimensional-model-solution-deployment"></a>Déploiement d'une solution de modèle multidimensionnel
  Une fois le développement d’un projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] terminé, vous pouvez déployer la base de données sur un serveur Analysis Services. Analysis Services fournit six méthodes de déploiement possibles qui peuvent être utilisées pour déplacer la base de données vers un serveur de production ou de test. Les méthodes sont énumérées ici dans l'ordre de leur avantage : automatisation AMO (Analysis Management Objects), XMLA, Assistant Déploiement, Utilitaire de déploiement, Assistant Synchronisation, Sauvegarde et Restauration.  
  
 Cette rubrique comprend les sections suivantes :  
  
 [Méthodes de déploiement](#bkmk_meth)  
  
 [Points à prendre en considération pour le déploiement](#bkmk_considerations)  
  
 [Tâches associées](#bkmk_rel)  
  
##  <a name="bkmk_meth"></a> Méthodes de déploiement  
  
|Méthode|Description|Lien|  
|------------|-----------------|----------|  
|**Automatisation AMO (Analysis Management Objects)**|AMO fournit une interface de programmation à l'ensemble de commandes complet pour [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], y compris les commandes qui peuvent être utilisées pour le déploiement de solutions. En tant qu'approche au déploiement de solutions, l'automatisation AMO constitue la méthode la plus souple, mais elle nécessite également un effort de programmation.  Le principal avantage de l'utilisation d'AMO est que vous pouvez utiliser l'Agent SQL Server avec votre application AMO pour exécuter le déploiement selon une planification prédéfinie.|[Développement avec Analysis Management Objects &#40;AMO&#41;](analysis-management-objects/developing-with-analysis-management-objects-amo.md)|  
|**XMLA**|Utilisez [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour générer un script XMLA des métadonnées d'une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] existante, puis exécutez le script sur un autre serveur pour recréer la base de données initiale. Les scripts XMLA sont aisément formés dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] en définissant le processus de déploiement, puis en le codifiant et en l'enregistrant dans un script XMLA. Une fois que le script XMLA est dans un fichier sauvegardé, vous pouvez aisément l'exécuter le script conformément au calendrier ou l'incorporer dans une application qui se connecte directement à une instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].<br /><br /> Vous pouvez également exécuter des scripts XMLA sur une base prédéfinie à l'aide de l'Agent SQL Server, mais la flexibilité n'est pas aussi grande que celle offerte par AMO. AMO fournit un large éventail de fonctionnalités en hébergeant tout le spectre des commandes administratives.|[Déployer des solutions de modèle à l’aide de XMLA](deploy-model-solutions-using-xmla.md)|  
|**Assistant Déploiement**|Utilisez l'Assistant Déploiement pour utiliser les fichiers de sortie XMLA générés par un projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] pour déployer les métadonnées du projet sur un serveur de destination. Avec l'Assistant Déploiement, vous pouvez effectuer directement le déploiement à partir du fichier [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , tel que créé dans le répertoire de sortie par la génération du projet.<br /><br /> Le principal avantage de l'utilisation de l'assistant Déploiement [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] est son aspect pratique. Tout comme vous pouvez enregistrer un script XMLA en vue d'une utilisation ultérieure dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], vous pouvez enregistrer les scripts de l'assistant Déploiement. L'Assistant Déploiement peut être exécuté de façon interactive et à partir de l'invite de commandes via l'Utilitaire de déploiement.|[Déployer des solutions de modèle à l’aide de l’Assistant Déploiement](deploy-model-solutions-using-the-deployment-wizard.md)|  
|**Utilitaire de déploiement**|L'utilitaire de déploiement permet de démarrer le moteur de déploiement Analysis Services à partir d'une invite de commandes.|[Déployer des solutions de modèle avec l’utilitaire de déploiement](deploy-model-solutions-with-the-deployment-utility.md)|  
|**Assistant Synchronisation de base de données**|Utilisez l'Assistant Synchronisation de base de données pour synchroniser les métadonnées et les données entre deux bases de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .<br /><br /> L'Assistant Synchronisation peut être utilisé pour copier des données et des métadonnées d'un serveur source vers un serveur de destination. Si le serveur de destination n'a pas de copie de la base de données que vous souhaitez déployer, une nouvelle base de données est copiée sur le serveur de destination. Si le serveur de destination dispose déjà d'une copie de la même base de données, la base de données sur le serveur de destination est mise à jour afin d'utiliser les métadonnées et les données de la base de données source.|[Synchroniser des bases de données Analysis Services](synchronize-analysis-services-databases.md)|  
|**Sauvegarde et restauration**|La sauvegarde offre la méthode la plus simple permettant de transférer des bases de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Dans la boîte de dialogue **Sauvegarde** , vous pouvez définir la configuration des options, puis exécuter la sauvegarde à partir de cette même boîte de dialogue. Vous pouvez également créer un script qui peut être enregistré et exécuté aussi souvent que nécessaire.<br /><br /> La sauvegarde et la restauration ne sont pas utilisées aussi souvent que les autres méthodes de déploiement, mais elles permettent de terminer rapidement un déploiement avec une infrastructure minimale.|[Sauvegarde et restauration de bases de données Analysis Services](backup-and-restore-of-analysis-services-databases.md)|  
  
##  <a name="bkmk_considerations"></a> Points à prendre en considération pour le déploiement  
 Avant de déployer un projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , prenez en considération les questions qui s’appliquent à votre solution, puis passez en revue le lien associé pour savoir comment résoudre le problème :  
  
|Considération|Lien vers des informations  supplémentaires|  
|-------------------|------------------------------|  
|Quelles ressources matérielles et logicielles sont nécessaires pour cette solution ?|[Configuration requise et considérations relatives au déploiement d’Analysis Services](requirements-and-considerations-for-analysis-services-deployment.md)|  
|Comment allez-vous déployer les objets connexes qui se trouvent en dehors de l’étendue du projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , par exemple les packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , les rapports ou les schémas de base de données relationnelle ?||  
|Comment allez-vous charger et mettre à jour les données dans la base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] déployée ?<br /><br /> Comment allez-vous mettre à jour les métadonnées (par exemple les calculs) dans la base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] déployée ?|[Méthodes de déploiement](#bkmk_meth) dans cette rubrique.|  
|Souhaitez-vous autoriser des utilisateurs à accéder aux données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] à travers Internet ?|[Configurer l’accès HTTP à Analysis Services sur Internet Information Services &#40;IIS&#41; 8.0](../instances/configure-http-access-to-analysis-services-on-iis-8-0.md)|  
|Souhaitez-vous fournir un accès par requête continu aux données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ?|[Configuration requise et considérations relatives au déploiement d’Analysis Services](requirements-and-considerations-for-analysis-services-deployment.md)|  
|Souhaitez-vous déployer des objets dans un environnement distribué en utilisant des objets liés ou des partitions distantes ?|[Créer et gérer une partition locale &#40;Analysis Services&#41;](create-and-manage-a-local-partition-analysis-services.md), [Créer et gérer une partition distante &#40;Analysis Services&#41;](create-and-manage-a-remote-partition-analysis-services.md) et [Groupes de mesures liés](linked-measure-groups.md).|  
|Comment allez-vous sécuriser les données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ?|[Autoriser l’accès aux objets et aux opérations &#40;Analysis Services&#41;](authorizing-access-to-objects-and-operations-analysis-services.md)|  
  
##  <a name="bkmk_rel"></a> Tâches associées  
 [Configuration requise et considérations relatives au déploiement d’Analysis Services](requirements-and-considerations-for-analysis-services-deployment.md)  
  
 [Déployer des solutions de modèle à l’aide de XMLA](deploy-model-solutions-using-xmla.md)  
  
 [Déployer des solutions de modèle à l’aide de l’Assistant Déploiement](deploy-model-solutions-using-the-deployment-wizard.md)  
  
 [Déployer des solutions de modèle avec l’utilitaire de déploiement](deploy-model-solutions-with-the-deployment-utility.md)  
  
  
