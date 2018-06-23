---
title: Méthode Discover (XMLA) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Discover Method
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#
- http://schemas.microsoft.com/analysisservices/2003/engine#
- microsoft.xml.analysis.discover
- urn:schemas-microsoft-com:xml-analysis#Discover
- Discover
helpviewer_keywords:
- Discover method
ms.assetid: 0eb52d88-c081-416e-a229-610e4373b0b3
caps.latest.revision: 36
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: ead875bbe88ea71c8741450f8a3127efcf4b313d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36140373"
---
# <a name="discover-method-xmla"></a>Méthode Discover (XMLA)
  Récupère les informations, telles que la liste des bases de données disponibles ou des détails concernant un objet spécifique, à partir d’une instance de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Les données récupérées à l'aide de la méthode `Discover` dépendent des valeurs des paramètres qui lui sont transmis.  
  
 **Espace de noms** urn:schemas-microsoft-com:xml-analysis  
  
 **Action SOAP** « urn : schemas-microsoft-com-analysis : découvrir »  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Discover>  
   <RequestType>...</RequestType>  
   <Restrictions>...</Restrictions>  
   <Properties>...</Properties>  
</Discover>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|None|  
|Éléments enfants|[Propriétés](xml-elements-properties/properties-element-xmla.md), [RequestType](xml-elements-properties/type-element-xmla.md), [Restrictions](xml-elements-properties/restrictions-element-xmla.md)|  
  
## <a name="remarks"></a>Notes  
 La méthode `Discover` demande les métadonnées sur des instances [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] et des objets. Métadonnées sont retournées à l’aide de la XMLA [ensemble de lignes](xml-data-types/rowset-data-type-xmla.md) type de données.  
  
## <a name="example"></a>Exemple  
 Dans l'exemple de code suivant, le client envoie l'appel `Discover` pour demander une liste de cubes de l'exemple [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] de la base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] :  
  
```  
<Discover xmlns="urn:schemas-microsoft-com:xml-analysis">  
   <RequestType>MDSCHEMA_CUBES</RequestType>  
   <Restrictions>  
      <RestrictionList>  
         <CATALOG_NAME>Adventure Works DW Multidimensional 2012</CATALOG_NAME>  
      </RestrictionList>  
   </Restrictions>  
   <Properties>  
      <PropertyList>  
         <DataSourceInfo>Provider=MSOLAP;Data Source=local;</DataSourceInfo>  
         <Catalog>Adventure Works DW Multidimensional 2012</Catalog>  
         <Format>Tabular</Format>  
      </PropertyList>  
   </Properties>  
</Discover>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données XML &#40;XMLA&#41;](xml-data-types/xml-data-types-xmla.md)   
 [Exécuter la méthode &#40;XMLA&#41;](xml-elements-methods-execute.md)   
 [Méthodes &#40;XMLA&#41;](xml-elements-methods.md)   
 [Éléments XML &#40;XMLA&#41;](../dev-guide/xml-elements-xmla.md)   
 [Ensembles de lignes de schéma Analysis Services](../schema-rowsets/analysis-services-schema-rowsets.md)  
  
  