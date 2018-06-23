---
title: Élément RequestType (XMLA) | Documents Microsoft
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
- RequestType Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#RequestType
- urn:schemas-microsoft-com:xml-analysis#RequestType
- microsoft.xml.analysis.requesttype
helpviewer_keywords:
- RequestType element
ms.assetid: 54270a57-e327-4233-b4b2-d85b44652ac5
caps.latest.revision: 12
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: b1b2bcc4bf6f97659239a9e53d4adac52d7794a4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36151971"
---
# <a name="requesttype-element-xmla"></a>Élément RequestType (XMLA)
  Détermine le type de métadonnées retournées par le [Discover](../xml-elements-methods-discover.md) (méthode).  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Discover>  
   ...  
   <RequestType>...</RequestType>  
   ...  
</Discover>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|None|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Découvrir](../xml-elements-methods-discover.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 L'élément `RequestType` détermine l'ensemble de lignes de schéma à partir duquel la méthode `Discover` retourne des données. Cette énumération est limitée aux noms des ensembles de lignes de schéma pris en charge par [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Pour plus d’informations sur les ensembles de lignes de schéma, consultez [ensembles de lignes de schéma Analysis Services](../../schema-rowsets/analysis-services-schema-rowsets.md).  
  
> [!NOTE]  
>  L'élément `RequestType` n'énumère que des noms d'ensemble de lignes de schéma. Une erreur se produit si le GUID de l'ensemble de lignes de schéma est utilisé.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  