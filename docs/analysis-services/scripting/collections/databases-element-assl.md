---
title: "Élément (ASSL) des bases de données | Documents Microsoft"
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
apiname: Databases Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: Databases
helpviewer_keywords: Databases element
ms.assetid: 2806a074-d47e-4434-9599-04888783770f
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: eaef838e6cfe0f2821f1fe722426b6f11eb9d2ad
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="databases-element-assl"></a>Élément Databases (ASSL)
  Contient la collection de [base de données](../../../analysis-services/scripting/objects/database-element-assl.md) éléments associés à un [Server](../../../analysis-services/scripting/objects/server-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Server>  
      ...  
   <Databases>  
      <Database>...</Database>  
      </Databases>  
   ...  
</Server>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Aucune|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Server](../../../analysis-services/scripting/objects/server-element-assl.md)|  
|Éléments enfants|[Base de données](../../../analysis-services/scripting/objects/database-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.DatabaseCollection>.  
  
## <a name="see-also"></a>Voir aussi  
 [Collections de &#40; ASSL &#41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
