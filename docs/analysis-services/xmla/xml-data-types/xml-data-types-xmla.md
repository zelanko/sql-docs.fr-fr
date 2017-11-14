---
title: "Types de données XML (XMLA) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: xmla
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- XML data types [XMLA]
- data types [XML for Analysis]
- XMLA, data types
- XML for Analysis, data types
ms.assetid: 979b5384-90d9-4e09-9286-1d1eafdc4864
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 60a10edf09c041b563f15bf5fec83cd1b5ec4ec7
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="xml-data-types-xmla"></a>Types de données XML (XMLA)
  Outre les types dérivés primitifs standard définis par la recommandation XML 1.0, la spécification XML for Analysis (XMLA) 1.1 définit des types de données supplémentaires pour la prise en charge de la représentation des données multidimensionnelles et tabulaires.  
  
 XMLA utilise les types de données répertoriés dans le tableau suivant.  
  
|Types de données|Description|  
|----------------|-----------------|  
|Booléen|Type de données **boolean** XML standard.|  
|Decimal|Type de données **decimal** XML standard.|  
|[EmptyResult](../../../analysis-services/xmla/xml-data-types/emptyresult-data-type-xmla.md)|Espace de noms sur l'élément **root** . Cet espace de noms est retourné lorsqu’une commande XMLA ne retourne un résultat, car la commande XMLA ne retourne généralement pas un résultat ou une erreur s’est produite sur le [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] lors de l’exécution de la commande XMLA.|  
|[EnumString](../../../analysis-services/xmla/xml-data-types/enumstring-data-type-xmla.md)|Jeu de constantes de chaînes nommées pour un énumérateur donné.|  
|Entier|Type de données **int** XML standard.|  
|[MDDataSet](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md)|Données multidimensionnelles retournées par la *résultat* paramètre de la [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) (méthode).|  
|[Jeu de résultats](../../../analysis-services/xmla/xml-data-types/resultset-data-type-xmla.md)|Jeu de résultats XML autodescriptif retourné par la méthode **Execute** .|  
|[Ensemble de lignes](../../../analysis-services/xmla/xml-data-types/rowset-data-type-xmla.md)|Lignes d’une source de données structurées par un schéma XML incorporé retourné par le [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) (méthode).|  
|Chaîne|Type de données **string** XML.|  
|UnsignedInt|Type de schéma **unsignedInt** XML.|  
  
 Pour obtenir les descriptions complètes des types de données XML standard, consultez la recommandation de langage candidat du WC3 (World Wide Web).  
  
## <a name="see-also"></a>Voir aussi  
 [Éléments XML &#40; XMLA &#41;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)   
 [XML for Analysis &#40; XMLA &#41; Référence](../../../analysis-services/xmla/xml-for-analysis-xmla-reference.md)  
  
  

