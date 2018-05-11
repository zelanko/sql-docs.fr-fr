---
title: Type de données MDDataSet (XMLA) | Documents Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: bd82c473b768d8359c82bd2cf55c1cf27e76ae3f
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="mddataset-data-type-xmla"></a>Type de données MDDataSet (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Définit un type de données dérivé qui représente les données multidimensionnelles retournées par la [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) (méthode).  
  
 **Namespace** urn : schemas-microsoft-com-analysis : mddataset  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<root xmlns="urn:schemas-microsoft-com:xml-analysis:rowset">  
   <!-- The following elements extend Resultset -->  
   <!-- Optional schema elements -->  
   <OlapInfo>...</OlapInfo>  
   <Axes>...</Axes>  
   <CellData>...</CellData>  
</root>  
```  
  
## <a name="data-type-characteristics"></a>Caractéristiques du type de données  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Types de données de base|[Jeu de résultats](../../../analysis-services/xmla/xml-data-types/resultset-data-type-xmla.md)|  
|Types de données dérivés|Aucune|  
  
## <a name="data-type-relationships"></a>Relations du type de données  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|Aucune|  
|Éléments enfants|[Axes](../../../analysis-services/xmla/xml-elements-properties/axes-element-xmla.md), [CellData](../../../analysis-services/xmla/xml-elements-properties/celldata-element-xmla.md), [OlapInfo](../../../analysis-services/xmla/xml-elements-properties/olapinfo-element-xmla.md)|  
|Éléments dérivés|Aucune|  
  
## <a name="remarks"></a>Notes  
 Le **MDDataSet** type de données fournit les orienté OLAP ensemble de lignes (ou jeu de données) nécessaires pour représenter les données OLAP en XML. Le contenu de cet ensemble de lignes peut varier en fonction des valeurs de la **contenu** et **Format** propriétés fournies dans le [propriétés](../../../analysis-services/xmla/xml-elements-properties/properties-element-xmla.md) collection de la **Execute** (méthode). Pour plus d’informations sur la **contenu** et **Format** propriétés, consultez [pris en charge les propriétés XMLA &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md).  
  
 Pour informations de base à propos des structures de dataset OLE DB pour OLAP, consultez la section « Type de données MDDataSet mappage sur OLE DB » de la spécification XML for Analysis 1.1. Pour obtenir un exemple de langage (XSD XML) définition de schéma XML complète de la **MDDataSet** de type de données, consultez « Appendix D: MDDataSet Example » de la spécification XML for Analysis 1.1.  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données XML &#40;XMLA&#41;](../../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)  
  
  
