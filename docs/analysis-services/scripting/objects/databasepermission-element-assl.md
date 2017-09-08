---
title: "Élément DatabasePermission (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- DatabasePermission Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- DatabasePermission
helpviewer_keywords:
- DatabasePermission element
ms.assetid: 6dcb9136-a40d-42e3-ad3b-b8ce8c7ca78c
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b33711fc326cf8256cc9c641c047c90a1686505a
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="databasepermission-element-assl"></a>Élément DatabasePermission (ASSL)
  Définit les autorisations par défaut dans un [base de données](../../../analysis-services/scripting/objects/database-element-assl.md) élément pour un spécifique [rôle](../../../analysis-services/scripting/objects/role-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<DatabasePermissions>  
      <DatabasePermission xsi:type="Permission">  
      <!-- The following elements extend Permission -->  
      <Administer>...</Administer>  
...</DatabasePermission>  
</DatabasePermissions>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|[Autorisation](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)|  
|Valeur par défaut|False|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[DatabasePermissions](../../../analysis-services/scripting/collections/databasepermissions-element-assl.md)|  
|Éléments enfants|[Administrer](../../../analysis-services/scripting/properties/administer-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 Les objets**DatabasePermission** ne peuvent exister que pour les rôles détenus par la base de données, et seul un objet **DatabasePermission** peut exister pour un rôle quelconque.  
  
 Cet élément a les validations suivantes sous la valeur 2 de DeploymentMode (modèles tabulaires).  
  
-   La valeur par défaut de l'attribut*Administer* est définie sur **False**, sauf si l'utilisateur a des privilèges d'administrateur. Pour les utilisateurs avec des privilèges d'administrateur, la valeur d'attribut est définie sur **True**.  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.DatabasePermission>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément role &#40; ASSL &#41;](../../../analysis-services/scripting/objects/role-element-assl.md)   
 [Objets &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
