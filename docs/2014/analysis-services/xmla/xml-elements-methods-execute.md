---
title: Méthode Execute (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Execute Method
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- EXECUTE
- urn:schemas-microsoft-com:xml-analysis#
- http://schemas.microsoft.com/analysisservices/2003/engine#
- microsoft.xml.analysis.execute
- urn:schemas-microsoft-com:xml-analysis#Execute
helpviewer_keywords:
- Execute method
ms.assetid: 0fff5221-7164-4bbc-ab58-49cf04c52664
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6d1c3e842c8f859802be1193ca615933877faa1b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48155680"
---
# <a name="execute-method-xmla"></a>Méthode Execute (XMLA)
  Envoie le code XML pour les commandes Analysis (XMLA) à une instance de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Ceci inclut des demandes qui impliquent un transfert de données (par exemple, la récupération ou la mise à jour de données sur le serveur).  
  
 **Espace de noms** urn:schemas-microsoft-com:xml-analysis  
  
 **Action SOAP** « urn : schemas-microsoft-com-analysis : Execute »  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<Execute>  
   <Command>...</Command>  
   <Properties>...</Properties>  
   <Parameters>...</Parameters>  
</Execute>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|None|  
|Éléments enfants|[Commande](xml-elements-properties/command-element-xmla.md), [paramètres](xml-elements-properties/parameters-element-xmla.md), [propriétés](xml-elements-properties/properties-element-xmla.md)|  
  
## <a name="remarks"></a>Notes  
 Le `Execute` méthode exécute les commandes XMLA fournies dans le `Command` élément et retourne les données obtenues à l’aide de XMLA [ensemble de lignes](xml-data-types/rowset-data-type-xmla.md) type de données (pour les jeux de résultats tabulaire) ou le code XMLA [MDDataSet](xml-data-types/mddataset-data-type-xmla.md) type de données (pour les jeux de résultats multidimensionnels.)  
  
## <a name="example"></a>Exemple  
 L'exemple de code suivant montre un appel de méthode `Execute` qui contient une instruction MDX (Multidimensional Expressions) SELECT.  
  
```  
<Execute xmlns="urn:schemas-microsoft-com:xml-analysis">  
   <Command>  
      <Statement>  
         SELECT [Measures].MEMBERS ON COLUMNS FROM [Adventure Works]  
      </Statement>  
   </Command>  
   <Properties>  
      <PropertyList>  
         <DataSourceInfo>Provider=MSOLAP;Data Source=local;</DataSourceInfo>  
         <Catalog>Adventure Works DW Multidimensional 2012</Catalog>  
         <Format>Multidimensional</Format>  
         <AxisFormat>ClusterFormat</AxisFormat>  
      </PropertyList>  
   </Properties>  
</Execute>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données XML &#40;XMLA&#41;](xml-data-types/xml-data-types-xmla.md)   
 [Méthode Discover &#40;XMLA&#41;](xml-elements-methods-discover.md)   
 [Méthodes &#40;XMLA&#41;](xml-elements-methods.md)   
 [Éléments XML &#40;XMLA&#41;](../dev-guide/xml-elements-xmla.md)   
 [Ensembles de lignes de schéma Analysis Services](../schema-rowsets/analysis-services-schema-rowsets.md)  
  
  
