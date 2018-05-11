---
title: Élément Password (XMLA) | Documents Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 488b406a6378853ecf34fce5405669e28420bde4
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="password-element-xmla"></a>Élément Password (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Détermine le mot de passe à utiliser par le parent [sauvegarde](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md) ou [restaurer](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md) commande pour chiffrer ou déchiffrer un fichier de sauvegarde.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Backup> <!-- or Restore -->  
   ...  
   <Password>...</Password>  
   ...  
</Backup>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Sauvegarde](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md), [restaurer](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 Pour les commandes **Backup** , si l'élément **Password** n'est pas inclus ou contient une chaîne vide, le fichier de sauvegarde n'est pas chiffré.  
  
 Pour les commandes **Restore** , si l'élément **Password** n'est pas inclus ou contient une chaîne vide en tentant de restaurer un fichier de sauvegarde chiffré, une erreur survient.  
  
 Si des éléments **Location** sont inclus dans une commande **Backup** ou **Restore** , le même élément **Password** est utilisé pour les fichiers de sauvegarde et les fichiers de sauvegarde distants. Pour plus d’informations sur les fichiers de sauvegarde à distance, consultez [sauvegarde, restauration et synchronisation de bases de données de &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Élément location &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md)   
 [Propriétés & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
