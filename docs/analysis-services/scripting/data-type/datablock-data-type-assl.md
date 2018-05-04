---
title: Type de données DataBlock (ASSL) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DataBlock Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- DataBlock
helpviewer_keywords:
- DataBlock data type
ms.assetid: 4192b388-613a-472b-881c-f9c02215aa81
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 6e6d9e7f21417dc7e435b0b65e10a8dbe928a0c8
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="datablock-data-type-assl"></a>Type de données DataBlock (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Définit un type de données primitif qui représente une collection de blocs de données servant au stockage du contenu binaire d'un élément [ClrAssemblyFile](../../../analysis-services/scripting/data-type/clrassemblyfile-data-type-assl.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<DataBlock>  
   <Blocks>...</Blocks>  
</DataBlock>  
```  
  
## <a name="data-type-characteristics"></a>Caractéristiques du type de données  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Types de données de base|Aucune|  
|Types de données dérivés|Aucune|  
  
## <a name="data-type-relationships"></a>Relations du type de données  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|Aucune|  
|Éléments enfants|[Blocs](../../../analysis-services/scripting/collections/blocks-element-assl.md)|  
|Éléments dérivés|Élément[Data](../../../analysis-services/scripting/objects/data-element-assl.md) de type [ClrAssemblyFile](../../../analysis-services/scripting/data-type/clrassemblyfile-data-type-assl.md) (collection[Files](../../../analysis-services/scripting/collections/files-element-assl.md) de type [ClrAssembly](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md) )|  
  
## <a name="see-also"></a>Voir aussi  
 [Assembly, élément & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/objects/assembly-element-assl.md)   
 [Élément File & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/objects/file-element-assl.md)   
 [Élément de bloc & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/objects/block-element-assl.md)   
 [Analysis Services script des Types de données XML Language & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
