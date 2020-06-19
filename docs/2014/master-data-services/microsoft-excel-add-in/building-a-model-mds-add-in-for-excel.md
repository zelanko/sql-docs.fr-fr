---
title: Génération d’un modèle (Complément MDS pour Excel) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 8ae26ec3-c5d5-4c4f-a810-2951a7454439
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 74f7e3a13e28b0cd6e9e6e539992e0430f64753f
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84961469"
---
# <a name="building-a-model-mds-add-in-for-excel"></a>Génération d'un modèle (Complément MDS pour Excel)
  Dans le [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], les administrateurs peuvent effectuer un sous-ensemble des fonctions d’administration disponibles dans l’application web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] .  
  
 Les tâches de conception de modèles que les administrateurs peuvent effectuer dans le [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] sont les suivantes :  
  
-   Créer des entités. Pour plus d’informations sur les entités, consultez [Entités &#40;Master Data Services&#41;](../entities-master-data-services.md).  
  
-   Créer des attributs de tous types, notamment des attributs basés sur un domaine. Pour plus d’informations sur les attributs, consultez [Attributs &#40;Master Data Services&#41;](../attributes-master-data-services.md) et [Attributs basés sur un domaine &#40;Master Data Services&#41;](../domain-based-attributes-master-data-services.md).  
  
 En tant qu'administrateur, vous devez créer le modèle à l'aide du service Web ou de l'application Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] . Vous pouvez utiliser [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] pour créer des entités et des attributs dans le modèle. Pour plus d’informations sur les objets de modèle, consultez [Modèles &#40;Master Data Services&#41;](../models-master-data-services.md).  
  
## <a name="related-tasks"></a>Tâches associées  
 La plupart des tâches d'administration doivent toujours être effectuées dans l'application Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] ou à l'aide du service Web. Le tableau suivant montre les outils que les administrateurs peuvent utiliser pour exécuter des tâches dans MDS.  
  
|Description de la tâche|Outil|Rubrique|  
|----------------------|----------|-----------|  
|Créer des modèles.|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Application web ou service web|[Créer un modèle &#40;Master Data Services&#41;](../create-a-model-master-data-services.md)|  
|Créer une entité.|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] application Web, service Web ou le [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]|[Créer une entité &#40;Complément MDS pour Excel&#41;](create-an-entity-mds-add-in-for-excel.md)|  
|Créer un attribut basé sur un domaine.|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] application Web, service Web ou le [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]|[Créer un attribut basé sur un domaine &#40;complément MDS pour Excel&#41;](create-a-domain-based-attribute-mds-add-in-for-excel.md)|  
|Créer des groupes d'attributs.|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Application web ou service web|[Créer un groupe d’attributs &#40;Master Data Services&#41;](../create-an-attribute-group-master-data-services.md)|  
|Créer des règles d'entreprise.|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Application web ou service web|[Créer et publier une règle d’entreprise &#40;Master Data Services&#41;](../create-and-publish-a-business-rule-master-data-services.md)|  
|Créer des vues d'abonnement.|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Application web ou service web|[Créer une vue d’abonnement &#40;Master Data Services&#41;](../create-a-subscription-view-to-export-data-master-data-services.md)|  
|créer des hiérarchies ;|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Application web ou service web|[Créer une hiérarchie dérivée &#40;Master Data Services&#41;](../create-a-derived-hierarchy-master-data-services.md)<br /><br /> [Créer une hiérarchie explicite &#40;Master Data Services&#41;](../create-an-explicit-hierarchy-master-data-services.md)|  
|Créer des collections.|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Application web ou service web|[Créer une collection &#40;Master Data Services&#41;](../create-a-collection-master-data-services.md)|  
|Créer des versions de données.|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Application web ou service web|[Verrouiller une version &#40;Master Data Services&#41;](../lock-a-version-master-data-services.md)|  
|Déployer des modèles.|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Application web, service web ou outil MDSModelDeploy.|[Créer un package de déploiement de modèle à l'aide de MDSModelDeploy](../create-a-model-deployment-package-by-using-mdsmodeldeploy.md)|  
  
## <a name="related-content"></a>Contenu associé  
  
-   [Modèles &#40;Master Data Services&#41;](../models-master-data-services.md)  
  
-   [Entités &#40;Master Data Services&#41;](../entities-master-data-services.md)  
  
-   [Attributs &#40;Master Data Services&#41;](../attributes-master-data-services.md)  
  
-   [Attributs basés sur un domaine &#40;Master Data Services&#41;](../domain-based-attributes-master-data-services.md)  
  
-   [Groupes d’attributs &#40;Master Data Services&#41;](../attribute-groups-master-data-services.md)  
  
-   [Règles d’entreprise &#40;Master Data Services&#41;](../business-rules-master-data-services.md)  
  
-   [Exportation de données &#40;Master Data Services&#41;](../overview-exporting-data-master-data-services.md)  
  
-   [Hiérarchies &#40;Master Data Services&#41;](../hierarchies-master-data-services.md)  
  
-   [Collections &#40;Master Data Services&#41;](../collections-master-data-services.md)  
  
-   [Versions &#40;Master Data Services&#41;](../versions-master-data-services.md)  
  
-   [Sécurité &#40;Master Data Services&#41;](../security-master-data-services.md)  
  
-   [Déploiement de modèles &#40;Master Data Services&#41;](../deploying-models-master-data-services.md)  
  
  
