---
title: Élément DatabasePermission (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DatabasePermission Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DatabasePermission
helpviewer_keywords:
- DatabasePermission element
ms.assetid: 6dcb9136-a40d-42e3-ad3b-b8ce8c7ca78c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a904f12b86d6449c11f354a790503dc1bd93ffbe
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48106659"
---
# <a name="databasepermission-element-assl"></a>Élément DatabasePermission (ASSL)
  Définit les autorisations par défaut dans un [base de données](database-element-assl.md) élément pour un spécifique [rôle](role-element-assl.md) élément.  
  
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
|Type de données et longueur|[Autorisation](../data-type/permission-data-type-assl.md)|  
|Valeur par défaut|False|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[DatabasePermissions](../collections/databasepermissions-element-assl.md)|  
|Éléments enfants|[Administrer](../properties/administer-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 Les objets `DatabasePermission` ne peuvent exister que pour les rôles détenus par la base de données, et seul un objet `DatabasePermission` peut exister pour un rôle quelconque.  
  
 Cet élément a les validations suivantes sous la valeur 2 de DeploymentMode (modèles tabulaires).  
  
-   *Administrer* attribut par défaut a la valeur `False`, sauf si l’utilisateur a des privilèges d’administrateur. Pour les utilisateurs avec des privilèges d'administrateur, la valeur d'attribut est définie sur `True`.  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.DatabasePermission>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément role &#40;ASSL&#41;](role-element-assl.md)   
 [Objets &#40;ASSL&#41;](objects-assl.md)  
  
  
