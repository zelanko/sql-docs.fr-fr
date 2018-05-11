---
title: Élément ConnectionStringSecurity (ASSL) | Documents Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 16c4b581d6ca5fd03df090c8fbcc4dca871b9d28
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="connectionstringsecurity-element-assl"></a>Élément ConnectionStringSecurity (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Spécifie si le mot de passe de l'utilisateur est supprimé de la chaîne de connexion à la source de données pour des raisons de sécurité.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<DataSource>  
   ...  
   <ConnectionStringSecurity>...</ConnectionStringSecurity>  
   ...  
</DataSource>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[DataSource](../../../analysis-services/scripting/objects/datasource-element-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes du tableau suivant.  
  
|Valeur| Description|  
|-----------|-----------------|  
|*PasswordRemoved*|Le mot de passe a été supprimé de la chaîne de connexion.|  
|*Non modifié*|La chaîne de connexion n'a pas été modifiée.|  
  
 L’énumération qui correspond aux valeurs autorisées pour **ConnectionStringSecurity** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.ConnectionStringSecurity>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
