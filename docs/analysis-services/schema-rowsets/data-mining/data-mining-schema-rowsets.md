---
title: "Ensembles de lignes de schéma d’exploration de données | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- schema rowsets [Analysis Services], data mining
- schema rowsets [Analysis Services]
- rowsets [Analysis Services], data mining
- data mining [Analysis Services], schema rowsets
ms.assetid: bd7d5df5-500b-4159-8467-880e141bc043
caps.latest.revision: "44"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: fcde375ccb8186f0ef5d38dca2c7f88aefaaf4b7
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2017
---
# <a name="data-mining-schema-rowsets"></a>Data Mining Schema Rowsets
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Un serveur qui est en cours d’exécution [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] prend en charge les ensembles de lignes de schéma d’exploration de données suivantes. Pour vérifier si un fournisseur XML/A particulier prend en charge un ensemble de lignes spécifique, utilisez la [DISCOVER_ENUMERATORS](../../../analysis-services/schema-rowsets/xml/discover-enumerators-rowset.md) ensemble de lignes avec le [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) (méthode).  
  
 Dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], les ensembles de lignes de schéma d'exploration de données sont également exposés en tant que tables en langage Transact-SQL, dans le schéma $SYSTEM. Par exemple, la requête suivante sur une instance Analysis Services retourne la liste des schémas disponibles sur l'instance actuelle.  
  
```  
SELECT * FROM [$system].[DBSCHEMA_TABLES]  
```  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Ensemble de lignes de schéma| Description|  
|-------------------|-----------------|  
|[DMSCHEMA_MINING_COLUMNS, ensemble de lignes](../../../analysis-services/schema-rowsets/data-mining/dmschema-mining-columns-rowset.md)|Décrit les colonnes de tous les modèles d'exploration de données définis qui sont déployés sur le serveur.|  
|[DMSCHEMA_MINING_FUNCTIONS, ensemble de lignes](../../../analysis-services/schema-rowsets/data-mining/dmschema-mining-functions-rowset.md)|Décrit les fonctions de prédiction et les fonctions d'exploration qui peuvent être utilisées avec chaque algorithme d'exploration de données installé sur le serveur.|  
|[DMSCHEMA_MINING_MODEL_CONTENT, ensemble de lignes](../../../analysis-services/schema-rowsets/data-mining/dmschema-mining-model-content-rowset.md)|Permet à l'application cliente de parcourir le contenu d'un modèle d'exploration de données dont l'apprentissage a été effectué.|  
|[DMSCHEMA_MINING_MODEL_CONTENT_PMML, ensemble de lignes](../../../analysis-services/schema-rowsets/data-mining/dmschema-mining-model-content-pmml-rowset.md)|Retourne la représentation XML (PMML 2.1) du contenu du modèle d'exploration de données.|  
|[DMSCHEMA_MINING_MODEL_XML, ensemble de lignes](../../../analysis-services/schema-rowsets/data-mining/dmschema-mining-model-xml-rowset.md)|Retourne la structure XML (PMML 2.1) du modèle d'exploration de données. Il s'agit du même schéma que DMSCHEMA_MINING_MODEL_PMML, lequel est conservé à des fins de compatibilité descendante.|  
|[DMSCHEMA_MINING_MODELS, ensemble de lignes](../../../analysis-services/schema-rowsets/data-mining/dmschema-mining-models-rowset.md)|Énumère les modèles d'exploration de données déployés sur le serveur.|  
|[DMSCHEMA_MINING_SERVICE_PARAMETERS, ensemble de lignes](../../../analysis-services/schema-rowsets/data-mining/dmschema-mining-service-parameters-rowset.md)|Fournit la liste des paramètres pouvant être utilisés pour configurer le comportement de chaque algorithme d'exploration de données installé sur le serveur.|  
|[DMSCHEMA_MINING_SERVICES, ensemble de lignes](../../../analysis-services/schema-rowsets/data-mining/dmschema-mining-services-rowset.md)|Fournit la description de chaque algorithme d'exploration de données disponible sur le serveur.|  
|[DMSCHEMA_MINING_STRUCTURE_COLUMNS, ensemble de lignes](../../../analysis-services/schema-rowsets/data-mining/dmschema-mining-structure-columns-rowset.md)|Décrit les colonnes de toutes les structures d'exploration de données qui sont déployées sur le serveur.|  
|[DMSCHEMA_MINING_STRUCTURES, ensemble de lignes](../../../analysis-services/schema-rowsets/data-mining/dmschema-mining-structures-rowset.md)|Fournit des informations sur les structures d'exploration de données.|  
  
 Tous les ensembles de lignes schéma répertoriés ici sont pris en charge par le serveur est en cours d’exécution [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma de Analysis Services](../../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md)   
 [Ensembles de lignes de schéma de données d’exploration de données &#40; SSAs &#41;](../../../analysis-services/data-mining/data-mining-schema-rowsets-ssas.md)  
  
  
