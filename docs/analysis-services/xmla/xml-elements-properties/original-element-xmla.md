---
title: "Élément original (XMLA) | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
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
apiname: Original Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.original
- http://schemas.microsoft.com/analysisservices/2003/engine#Original
- urn:schemas-microsoft-com:xml-analysis#Original
helpviewer_keywords: Original element
ms.assetid: c98a3700-ac19-4341-85d9-5afedf662601
caps.latest.revision: "11"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 352a4fd4e4be62a666acdc384379ce45c90ee915
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="original-element-xmla"></a>Élément Original (XMLA)
  Contient l’emplacement de stockage d’origine du système de fichiers utilisé par un [dossier](../../../analysis-services/xmla/xml-elements-properties/folder-element-xmla.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Folder>  
   ...  
   <Original>...</Original>  
   ...  
</Folder>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne|  
|Valeur par défaut|Aucune|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Dossier](../../../analysis-services/xmla/xml-elements-properties/folder-element-xmla.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 Le **d’origine** élément contient un chemin d’accès UNC à remplacer par la valeur de la [nouveau](../../../analysis-services/xmla/xml-elements-properties/new-element-xmla.md) élément contenu dans le parent **dossier** élément pour tous les objets restaurés ou synchronisés, respectivement, pendant un [restaurer](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md) ou [synchroniser](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md) commande. La valeur de cet élément est comparée à la valeur de la [StorageLocation](../../../analysis-services/scripting/properties/storagelocation-element-assl.md) , élément pour chaque cube, groupe de mesures ou partition et, si une correspondance est trouvée, la valeur de la **nouveau** élément est utilisé pour mettre à jour le **%{storagelocation/}** de l’objet pendant la restauration ou la synchronisation.  
  
 Pour plus d’informations sur la sauvegarde et restauration des objets, consultez [sauvegarde, restauration et synchroniser les bases de données &#40; XMLA &#41; ](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
