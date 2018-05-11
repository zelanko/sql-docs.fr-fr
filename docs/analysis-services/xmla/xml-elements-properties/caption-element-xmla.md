---
title: Caption, élément (XMLA) | Documents Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7b6ccdb8c8fa95725764cc3e94961d6a177e448c
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="caption-element-xmla"></a>Élément Caption (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Contient des informations sur la légende du parent [HierarchyInfo](../../../analysis-services/xmla/xml-elements-properties/hierarchyinfo-element-xmla.md) ou [membre](../../../analysis-services/xmla/xml-elements-properties/member-element-xmla.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<HierarchyInfo> <!-- or Member -->  
   ...  
   <Caption>...</Caption>  
   ...  
</HierarchyInfo>  
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
|Éléments parents|[HierarchyInfo](../../../analysis-services/xmla/xml-elements-properties/hierarchyinfo-element-xmla.md), [Member](../../../analysis-services/xmla/xml-elements-properties/member-element-xmla.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 Pour **HierarchyInfo** éléments, le **légende** élément contient le nom de la propriété qui fournit des légendes de la hiérarchie du membre. Sa valeur est équivalente à la propriété MEMBER_CAPTION définie pour les ensembles de lignes d'axe dans la spécification OLE DB pour OLAP.  
  
 Pour **membre** éléments, le **légende** élément contient la légende du parent **membre** élément dans la langue spécifiée pour le code XML pour la session Analysis (XMLA). Si aucune légende n'est disponible, cet élément contient le nom unique du membre.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
