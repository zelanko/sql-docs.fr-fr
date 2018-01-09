---
title: "Architecture logique (Analysis Services - données multidimensionnelles) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- Analysis Services, architecture
- logical architecture [Analysis Services Multidimensional Data]
ms.assetid: 1b9cae0a-8990-4194-af5f-a1ea5f2aff06
caps.latest.revision: "14"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 85b98af5dc33f21da4b54f14e60179594382c934
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="understanding-microsoft-olap-logical-architecture"></a>Présentation de l’Architecture logique Microsoft OLAP
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)][!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] utilise les composants serveur et client pour fournir des fonctionnalités d’exploration de données pour les applications de décisionnel et de traitement analytique en ligne (OLAP) :  
  
-   Le composant serveur d'[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] est implémenté comme un service Microsoft Windows. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] prend en charge plusieurs instances sur le même ordinateur, chaque instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] implémentée comme une instance distincte du service Windows.  
  
-   Les clients communiquent avec [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] à l’aide de la norme publique XMLA (XML for Analysis), un protocole SOAP qui permet d’émettre des commandes et de recevoir des réponses, exposée en tant que service web. Des modèles objet clients sont aussi fournis via XMLA, et sont accessibles soit à l'aide d'un fournisseur managé, notamment ADOMD.NET ou un fournisseur OLE DB natif.  
  
-   Les commandes de requête peuvent être émises à l'aide des langages suivants : SQL, MDX (Multidimensional Expressions), un langage de requête standard orienté analyse ou DMX (Data Mining Extensions), un langage de requête standard orienté exploration de données. Vous pouvez aussi utiliser ASSL (Analysis Services Scripting Language) pour gérer les objets de la base de données [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] .  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] prend également en charge un moteur de cube local qui permet aux applications exécutées sur des clients déconnectés de parcourir les données multidimensionnelles stockées localement. Pour plus d’informations, consultez [Architecture de Client requise pour le développement d’Analysis Services](../../../analysis-services/multidimensional-models/olap-physical/client-architecture-requirements-for-analysis-services-development.md)  
  
## <a name="in-this-section"></a>Dans cette section  
 **Vue d’ensemble de l’Architecture logique**  
 [Vue d’ensemble de l’Architecture logique &#40; Analysis Services - données multidimensionnelles &#41;](../../../analysis-services/multidimensional-models/olap-logical/logical-architecture-overview-analysis-services-multidimensional-data.md)  
  
 **Objets serveur**  
 [Objets de serveur &#40; Analysis Services - données multidimensionnelles &#41;](../../../analysis-services/multidimensional-models/olap-logical/server-objects-analysis-services-multidimensional-data.md)  
  
 **Objets de base de données**  
 [Les objets de base de données &#40; Analysis Services - données multidimensionnelles &#41;](../../../analysis-services/multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md)  
  
 **Objets de dimension**  
 [Objets de dimension &#40; Analysis Services - données multidimensionnelles &#41;](../../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimension-objects-analysis-services-multidimensional-data.md)  
  
 **Objets de cube**  
 [Objets de cube &#40; Analysis Services - données multidimensionnelles &#41;](../../../analysis-services/multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md)  
  
 **Sécurité d’accès utilisateur**  
 [Architecture de sécurité d’accès utilisateur](http://msdn.microsoft.com/library/71b44e10-2bd0-44f7-8de9-7c8f5b7ac082)  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation de l’Architecture Microsoft OLAP](../../../analysis-services/multidimensional-models/olap-physical/understanding-microsoft-olap-architecture.md)   
 [Architecture physique &#40; Analysis Services - données multidimensionnelles &#41;](../../../analysis-services/multidimensional-models/olap-physical/understanding-microsoft-olap-physical-architecture.md)  
  
  
