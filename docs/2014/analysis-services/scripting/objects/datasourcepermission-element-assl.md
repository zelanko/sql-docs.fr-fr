---
title: Élément DataSourcePermission (ASSL) | Microsoft Docs
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
- DataSourcePermission Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- DataSourcePermission element
ms.assetid: 6dc6fb13-034e-479a-902e-27f3fb78c33f
caps.latest.revision: 14
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d88f18a752e96e5081462056d831bc968dc605df
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37241359"
---
# <a name="datasourcepermission-element-assl"></a>Élément DataSourcePermission (ASSL)
  Définit les autorisations par défaut dans un [DataSource](../data-type/datasource-data-type-assl.md) type de données pour un spécifique [rôle](role-element-assl.md) élément.  
  
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
|Type de données et longueur|[Autorisation](../data-type/permission-data-type-assl.md)|  
|Valeur par défaut|None|  
|Cardinalité|0-n : élément facultatif susceptible d'apparaître une fois ou plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[DataSourcePermissions](../collections/datasourcepermissions-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Les objets `DataSourcePermission` ne peuvent exister que pour les rôles détenus par la base de données, et seul un objet `DataSourcePermission` peut exister pour un rôle quelconque.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément role &#40;ASSL&#41;](role-element-assl.md)   
 [Objets &#40;ASSL&#41;](objects-assl.md)  
  
  
