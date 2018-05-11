---
title: Élément ConnectionString (XMLA) | Documents Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0bf1baf18ffff268f4b82dbb24ced5a8107da23a
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="connectionstring-element-xmla"></a>Élément ConnectionString (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Contient une chaîne de connexion utilisée par le parent [emplacement](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md) ou [Source](../../../analysis-services/xmla/xml-elements-properties/source-element-xmla.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Location> <!-- or Source -->  
   ...  
   <ConnectionString>...</ConnectionString>  
   ...  
</Location>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne|  
|Valeur par défaut|Aucune|  
|Cardinalité|Consultez le tableau ci-dessous.|  
  
|Ancêtre ou parent|Cardinalité|  
|------------------------|-----------------|  
|[Emplacement](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md)|1-1 : élément requis qui apparaît une fois et une seule.|  
|[Source](../../../analysis-services/xmla/xml-elements-properties/source-element-xmla.md)|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Emplacement](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md), [Source](../../../analysis-services/xmla/xml-elements-properties/source-element-xmla.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 Pour **emplacement** éléments, le **ConnectionString** élément contient la chaîne de connexion utilisée par le **restaurer** ou **synchroniser** commande Mettre à jour une source de données local ou se connecter à une instance distante.  
  
 Pour **Source** éléments, le **ConnectionString** élément contient la chaîne de connexion utilisée par le **synchroniser** commande pour vous connecter à l’instance source.  
  
 Pour plus d’informations sur la sauvegarde et restauration des objets, consultez [sauvegarde, restauration et synchroniser les bases de données & #40 ; XMLA & #41 ; ](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Restaurer l’élément & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)   
 [Synchroniser, élément & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)   
 [Propriétés & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
