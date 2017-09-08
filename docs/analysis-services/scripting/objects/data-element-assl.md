---
title: "Élément de données (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Data Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Data
helpviewer_keywords:
- Data element
ms.assetid: e52b1961-7e11-4029-8ab1-84d275845067
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 998978dfbed910b59f9e781c3ec6e9cf60e5e1f3
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="data-element-assl"></a>Éléments Data (ASSL)
  Contient (dans la collection d’enfants [élément de bloc & #40 ; ASSL & #41 ; ](../../../analysis-services/scripting/objects/block-element-assl.md) éléments) le contenu binaire d’un [ClrAssemblyFile](../../../analysis-services/scripting/data-type/clrassemblyfile-data-type-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<File xsi:type="ClrAssemblyFile">  
   ...  
   <Data xsi:type="DataBlock">...</Data>  
   ...  
</ClrAssemblyFile>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|[DataBlock](../../../analysis-services/scripting/data-type/datablock-data-type-assl.md)|  
|Valeur par défaut|Aucune|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Fichier](../../../analysis-services/scripting/objects/file-element-assl.md) de type [ClrAssemblyFile](../../../analysis-services/scripting/data-type/clrassemblyfile-data-type-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 L’élément qui correspond au parent de **données** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.ClrAssemblyFile>.  
  
## <a name="see-also"></a>Voir aussi  
 [Assembly, élément & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/objects/assembly-element-assl.md)   
 [Type de données ClrAssembly & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md)   
 [Élément de fichiers & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/collections/files-element-assl.md)   
 [Élément Blocks & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/collections/blocks-element-assl.md)   
 [Objets & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
