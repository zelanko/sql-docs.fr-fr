---
title: "Méthode Execute (XMLA) | Documents Microsoft"
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
apiname: Execute Method
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- EXECUTE
- urn:schemas-microsoft-com:xml-analysis#
- http://schemas.microsoft.com/analysisservices/2003/engine#
- microsoft.xml.analysis.execute
- urn:schemas-microsoft-com:xml-analysis#Execute
helpviewer_keywords: Execute method
ms.assetid: 0fff5221-7164-4bbc-ab58-49cf04c52664
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: a2743ccdbe0f2186db5721479c812f61adfcfe92
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="xml-elements---methods---execute"></a>Les éléments XML - méthodes - exécuter
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
|Type de données et longueur|Aucune|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-1 : élément facultatif qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|Aucune|  
|Éléments enfants|[Commande](../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md), [paramètres](../../analysis-services/xmla/xml-elements-properties/parameters-element-xmla.md), [propriétés](../../analysis-services/xmla/xml-elements-properties/properties-element-xmla.md)|  
  
## <a name="remarks"></a>Notes  
 Le **Execute** méthode s’exécute les commandes XMLA fournies dans le **commande** élément et retourne les données obtenues en utilisant le code XMLA [ensemble de lignes](../../analysis-services/xmla/xml-data-types/rowset-data-type-xmla.md) type de données (pour les jeux de résultats tabulaire) ou le code XMLA [MDDataSet](../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md) de type de données (pour les jeux de résultats multidimensionnels.)  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant est un exemple d’une **Execute** appel de méthode qui contient une instruction SELECT MDX (Multidimensional Expressions).  
  
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
 [Types de données XML &#40; XMLA &#41;](../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)   
 [Découvrez la méthode &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-methods-discover.md)   
 [Méthodes &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-methods.md)   
 [Éléments XML &#40; XMLA &#41;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)   
 [Ensembles de lignes de schéma Analysis Services](../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md)  
  
  
