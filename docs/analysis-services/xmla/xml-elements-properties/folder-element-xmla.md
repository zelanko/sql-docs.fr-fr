---
title: Élément Folder (XMLA) | Documents Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0a13ac1689c58519a6e8d1ac06cacc8357570b75
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="folder-element-xmla"></a>Élément Folder (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Contient un emplacement de stockage de système de fichiers mettre à jour pour un [emplacement](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md) élément pendant une [restaurer](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md) ou [synchroniser](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md) commande.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Folders>  
   ...  
   <Folder>  
      <Original>...</Original>  
      <New>...</New>  
   </Folder>  
   ...  
</Folders>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Aucune|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Dossiers](../../../analysis-services/xmla/xml-elements-properties/folders-element-xmla.md)|  
|Éléments enfants|[Nouvelle](../../../analysis-services/xmla/xml-elements-properties/new-element-xmla.md), [d’origine](../../../analysis-services/xmla/xml-elements-properties/original-element-xmla.md)|  
  
## <a name="remarks"></a>Notes  
 S'il est spécifié, l'élément **Folder** modifie les emplacements de stockage des objets contenus dans le fichier de sauvegarde (pour les commandes **Restore** ) ou dans la base de données de l'instance source (pour les commandes **Synchronize** ) permettant de faire correspondre la valeur de l'élément **Original** avec celle de l'élément **New** .  
  
 Pour plus d’informations sur la sauvegarde et restauration des objets, consultez [sauvegarde, restauration et synchroniser les bases de données & #40 ; XMLA & #41 ; ](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Élément StorageLocation & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/properties/storagelocation-element-assl.md)   
 [Propriétés & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
