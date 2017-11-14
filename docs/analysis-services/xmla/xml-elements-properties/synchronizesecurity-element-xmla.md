---
title: "Élément SynchronizeSecurity (XMLA) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: xmla
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- SynchronizeSecurity Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.synchronizesecurity
- http://schemas.microsoft.com/analysisservices/2003/engine#SynchronizeSecurity
- urn:schemas-microsoft-com:xml-analysis#SynchronizeSecurity
helpviewer_keywords:
- SynchronizeSecurity element
ms.assetid: d37dbb95-f4a4-44ac-8eb9-f661d5bb5018
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 94f58bf16e0127b1686e83a0e81ba754c3cf0066
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="synchronizesecurity-element-xmla"></a>Élément SynchronizeSecurity (XMLA)
  Indique comment synchroniser les définitions de sécurité, notamment les rôles et autorisations, pendant un [synchroniser](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md) commande.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Synchronize>  
   ...  
   <SynchronizeSecurity>...</SynchronizeSecurity>  
   ...  
</Synchronize>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|*SkipMembership*|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Synchroniser](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 Le **sécurité** élément détermine si les définitions de sécurité, notamment les rôles et autorisations, définies sur une [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] base de données sont synchronisées pendant un **synchroniser** commande. Cet élément détermine également si les comptes et les groupes d'utilisateurs Windows définis en tant que membres des définitions de sécurité sont inclus dans le cadre de la commande **Synchronize** .  
  
 La valeur de cet élément est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur| Description|  
|-----------|-----------------|  
|*SkipMembership*|Inclut les définitions de sécurité mais exclut les informations d'appartenance au cours d'une commande **Synchronize** .|  
|*CopyAll*|Inclut les définitions de sécurité et les informations d'appartenance au cours d'une commande **Synchronize** .|  
|*IgnoreSecurity*|Exclut les définitions de sécurité au cours d'une commande **Synchronize** .|  
  
## <a name="see-also"></a>Voir aussi  
 [Élément de sécurité &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/security-element-xmla.md)   
 [Propriétés &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

