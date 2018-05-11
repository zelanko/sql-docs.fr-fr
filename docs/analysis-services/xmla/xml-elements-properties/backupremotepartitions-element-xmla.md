---
title: Élément BackupRemotePartitions (XMLA) | Documents Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 565fc78cc4a0aa0fe04c8d8196689a0c9cacb82b
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="backupremotepartitions-element-xmla"></a>Élément BackupRemotePartitions (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Détermine si le parent [sauvegarde](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md) commande sauvegarde des partitions distantes associées à l’objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Backup>  
   ...  
   <BackupRemotePartitions>...</BackupRemotePartitions>  
   ...  
</Backup>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Booléen|  
|Valeur par défaut|False|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Sauvegarde](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 Si **BackupRemotePartitions** possède la valeur **True**, un élément **Locations** contenant un ou plusieurs éléments **Location** doit être inclus dans la commande **Backup** ou bien une erreur se produit. Pour plus d’informations sur la sauvegarde et restauration des partitions distantes, consultez [sauvegarde, restauration et synchroniser les bases de données & #40 ; XMLA & #41 ; ](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Élément Locations &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/locations-element-xmla.md)   
 [Élément location &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md)   
 [Propriétés & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
