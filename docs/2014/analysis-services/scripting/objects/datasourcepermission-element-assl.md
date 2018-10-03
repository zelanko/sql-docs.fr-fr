---
title: Élément DataSourcePermission (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d4130cd2a0eb83b32c8bcdf703d10ca6305af619
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48087619"
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
  
  
