---
title: résultats Element (XMLA) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- results Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.results
- urn:schemas-microsoft-com:xml-analysis#results
- http://schemas.microsoft.com/analysisservices/2003/engine#results
helpviewer_keywords:
- results element
ms.assetid: 3249a17a-7bfa-4753-b605-8f611ba7ae2b
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d59d5be9eaf822b21ea3b5a24e0dacbe9dec56f7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="results-element-xmla"></a>Élément results (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Contient une collection d'éléments [root](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md) retournée par la méthode [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) employée avec la commande [Batch](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md) .  
  
 **espace de noms** `http://schemas.microsoft.com/analysisservices/2003/xmla-multipleresults`  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<return>  
   <results>  
      <root>...</root>  
   </results>  
</return>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Aucune|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[de retour](../../../analysis-services/xmla/xml-elements-properties/return-element-xmla.md)|  
|Éléments enfants|[racine](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)|  
  
## <a name="remarks"></a>Notes  
 Si une commande **Batch** est exécutée par la méthode **Execute** , l'élément **return** contient un élément **results** unique au lieu d'un élément **root** unique. Le contenu de l'élément **results** dépend des paramètres utilisés pour exécuter la commande **Batch** .  
  
 Pour les commandes **Batch** non transactionnelles, l'élément **results** contient un élément **root** pour chacune des commandes exécutées par la commande **Batch** , que ces commandes réussissent ou échouent. Pour les commandes **Batch** transactionnelles, l'élément **results** contient un seul élément **root** contenant les informations d'erreur de la commande qui a échoué dans la commande **Batch** .  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
