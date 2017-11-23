---
title: "Élément CalendarLanguage (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: CalendarLanguage Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: CalendarLanguage
helpviewer_keywords: CalendarLanguage element
ms.assetid: e43a0f48-a583-418b-a0a4-d73a40035573
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 40f1350b6d30d7c210f1773a328a5d7b93a0410d
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="calendarlanguage-element-assl"></a>Élément CalendarLanguage (ASSL)
  Définit la langue du calendrier utilisée pour le [TimeBinding](../../../analysis-services/scripting/data-type/timebinding-data-type-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<TimeBinding>  
   ...  
   <CalendarLanguage>...</CalendarLanguage>  
   ...  
</TimeBinding>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Entier|  
|Valeur par défaut|**1033**|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[TimeBinding](../../../analysis-services/scripting/data-type/timebinding-data-type-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 Il s'agit de la langue dans laquelle les noms des membres de dimension sont créés. La langue des légendes doit être définie à l'aide de codes LCID basés sur des entiers. Par exemple, la valeur par défaut représente le LCID anglais américain.  
  
 L’élément qui correspond au parent de **CalendarLanguage** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.TimeBinding>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
