---
title: Élément DatabaseName (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DatabaseName Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.databasename
- http://schemas.microsoft.com/analysisservices/2003/engine#DatabaseName
- urn:schemas-microsoft-com:xml-analysis#DatabaseName
helpviewer_keywords:
- DatabaseName element
ms.assetid: 5cfd9a1f-da53-497a-b677-c51be4641bd0
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c4727f3554b654687484e6bd273a0d88e557215e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48172679"
---
# <a name="databasename-element-xmla"></a>Élément DatabaseName (XMLA)
  Identifie le [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] doit être restaurée par le parent [restaurer](../xml-elements-commands/restore-element-xmla.md) commande.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Restore>  
   ...  
   <DatabaseName>...</DatabaseName>  
   ...  
</Restore>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|String|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Restaurer](../xml-elements-commands/restore-element-xmla.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 L'élément `DatabaseName` identifie la base de données dans laquelle la commande `Restore` restaure un fichier de sauvegarde. Si cet élément n'est pas spécifié ou contient une chaîne vide, le nom de la base de données contenue dans le fichier de sauvegarde est utilisé.  
  
 Si la base de données existe déjà sur l'instance cible, une erreur se produit, sauf si l'élément `AllowOverwrite` de la commande `Restore` parente possède la valeur `True`.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément AllowOverwrite &#40;XMLA&#41;](allowoverwrite-element-xmla.md)   
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
