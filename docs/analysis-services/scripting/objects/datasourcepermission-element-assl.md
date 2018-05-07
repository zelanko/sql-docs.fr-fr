---
title: Élément DataSourcePermission (ASSL) | Documents Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b7110adcbcdf4d5c346de756c6df6beccebd18eb
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="datasourcepermission-element-assl"></a>Élément DataSourcePermission (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Définit les autorisations par défaut dans un [DataSource](../../../analysis-services/scripting/data-type/datasource-data-type-assl.md) type de données pour un spécifique [rôle](../../../analysis-services/scripting/objects/role-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<DataSourcePermissions>  
   <DataSourcePermission xsi:type="Permission">  
      <!-- No child elements other than those from Permission are defined -->  
...</DataSourcePermission>  
</DataSourcePermissions>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|[Autorisation](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-n : élément facultatif susceptible d'apparaître une fois ou plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[DataSourcePermissions](../../../analysis-services/scripting/collections/datasourcepermissions-element-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 Les objets**DataSourcePermission** ne peuvent exister que pour les rôles détenus par la base de données, et seul un objet **DataSourcePermission** peut exister pour un rôle quelconque.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément role & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/objects/role-element-assl.md)   
 [Objets & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
