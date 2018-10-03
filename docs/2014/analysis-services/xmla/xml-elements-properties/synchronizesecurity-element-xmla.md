---
title: Élément SynchronizeSecurity (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- SynchronizeSecurity Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.synchronizesecurity
- http://schemas.microsoft.com/analysisservices/2003/engine#SynchronizeSecurity
- urn:schemas-microsoft-com:xml-analysis#SynchronizeSecurity
helpviewer_keywords:
- SynchronizeSecurity element
ms.assetid: d37dbb95-f4a4-44ac-8eb9-f661d5bb5018
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 95e43831854720e8a2525edae06165334443dad3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48224541"
---
# <a name="synchronizesecurity-element-xmla"></a>Élément SynchronizeSecurity (XMLA)
  Indique comment synchroniser des définitions de sécurité, notamment les rôles et autorisations, pendant un [synchroniser](../xml-elements-commands/synchronize-element-xmla.md) commande.  
  
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
|Valeur par défaut|*skipMembership*|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Synchroniser](../xml-elements-commands/synchronize-element-xmla.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Le `Security` élément détermine si les définitions de sécurité, notamment les rôles et autorisations, définies sur un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] base de données sont synchronisées pendant un `Synchronize` commande. Cet élément détermine également si les comptes et les groupes d'utilisateurs Windows définis en tant que membres des définitions de sécurité sont inclus dans le cadre de la commande `Synchronize`.  
  
 La valeur de cet élément est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*skipMembership*|Inclut les définitions de sécurité mais exclut les informations d'appartenance au cours d'une commande `Synchronize`.|  
|*CopyAll*|Inclut les définitions de sécurité et les informations d'appartenance au cours d'une commande `Synchronize`.|  
|*IgnoreSecurity*|Exclut les définitions de sécurité au cours d'une commande `Synchronize`.|  
  
## <a name="see-also"></a>Voir aussi  
 [Élément de sécurité &#40;XMLA&#41;](security-element-xmla.md)   
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
