---
title: Architecture logique (Analysis Services-données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- Analysis Services, architecture
- logical architecture [Analysis Services Multidimensional Data]
ms.assetid: 1b9cae0a-8990-4194-af5f-a1ea5f2aff06
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 074659d42e1960c5f24cf4afa20668a3d8c823b0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62725483"
---
# <a name="logical-architecture-analysis-services---multidimensional-data"></a>Architecture logique (Analysis Services - Données multidimensionnelles)
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilise des composants serveur et client pour fournir des fonctionnalités de traitement analytique en ligne (OLAP) et d’exploration de données pour les applications décisionnelles [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] :  
  
-   Le composant serveur d'[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] est implémenté comme un service Microsoft Windows. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] prend en charge plusieurs instances sur le même ordinateur, chaque instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] de étant implémentée en tant qu’instance distincte du service Windows.  
  
-   Les clients communiquent avec [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] à l’aide de la norme publique XMLA (XML for Analysis), un protocole SOAP qui permet d’émettre des commandes et de recevoir des réponses, exposée en tant que service web. Des modèles objet clients sont aussi fournis via XMLA, et sont accessibles soit à l'aide d'un fournisseur managé, notamment ADOMD.NET ou un fournisseur OLE DB natif.  
  
-   Les commandes de requête peuvent être émises à l'aide des langages suivants : SQL, MDX (Multidimensional Expressions), un langage de requête standard orienté analyse ou DMX (Data Mining Extensions), un langage de requête standard orienté exploration de données. Vous pouvez aussi utiliser ASSL (Analysis Services Scripting Language) pour gérer les objets de la base de données [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] .  
  
 
  [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] prend également en charge un moteur de cube local qui permet aux applications exécutées sur des clients déconnectés de parcourir les données multidimensionnelles stockées localement. Pour plus d’informations, consultez [Configuration requise de l’architecture client pour le développement de Analysis Services](../olap-physical/client-architecture-requirements-for-analysis-services-development.md)  
  
## <a name="in-this-section"></a>Dans cette section  
 **Vue d'ensemble de l'architecture logique**  
 [Vue d’ensemble de l’architecture logique &#40;Analysis Services-données multidimensionnelles&#41;](logical-architecture-overview-analysis-services-multidimensional-data.md)  
  
 **Objets Server**  
 [Objets serveur &#40;Analysis Services-données multidimensionnelles&#41;](server-objects-analysis-services-multidimensional-data.md)  
  
 **Objets de base de données**  
 [Objets de base de données &#40;Analysis Services-données multidimensionnelles&#41;](database-objects-analysis-services-multidimensional-data.md)  
  
 **Objets Dimension**  
 [Objets de dimension &#40;Analysis Services-données multidimensionnelles&#41;](../../multidimensional-models-olap-logical-dimension-objects/dimension-objects-analysis-services-multidimensional-data.md)  
  
 **Objets de cube**  
 [Objets de cube &#40;Analysis Services-données multidimensionnelles&#41;](../../multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md)  
  
 **Sécurité de l'accès utilisateur**  
 [Architecture de sécurité de l'accès utilisateur](understanding-microsoft-olap-logical-architecture.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Compréhension de l’architecture Microsoft OLAP](../olap-physical/understanding-microsoft-olap-architecture.md)   
 [Architecture physique &#40;Analysis Services-données multidimensionnelles&#41;](../olap-physical/understanding-microsoft-olap-physical-architecture.md)  
  
  
