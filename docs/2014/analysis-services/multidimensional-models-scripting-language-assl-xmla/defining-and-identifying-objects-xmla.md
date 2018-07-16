---
title: Définition et identification d’objets (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- objects [XML for Analysis]
- identifying objects [XML for Analysis]
- XML for Analysis, objects
- object references [XML for Analysis]
- object identifiers [XML for Analysis]
- object definitions [XML for Analysis]
- XMLA, objects
ms.assetid: 43b65f6d-0123-4556-81f0-c7a0b84361e5
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c788129026d4dffe5c81efc82492fa8a5566de2a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37303039"
---
# <a name="defining-and-identifying-objects-xmla"></a>Définition et identification d'objets (XMLA)
  Les objets sont identifiés dans les commandes XMLA (XML for Analysis) à l'aide d'identificateurs et de références d'objet, et ils sont définis à l'aide de commandes XMLA contenant des éléments ASSL (Analysis Services Scripting Language).  
  
## <a name="object-identifiers"></a>Identificateurs d'objet  
 Un objet est identifié à l’aide de l’identificateur unique de l’objet tel que défini sur une instance de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Les identificateurs d'objet peuvent être spécifiés explicitement ou déterminés par l'instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] au moment où [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] crée l'objet. Vous pouvez utiliser la [Discover](../xmla/xml-elements-methods-discover.md) méthode pour récupérer les identificateurs d’objet pour suivantes `Discover` ou [Execute](../xmla/xml-elements-methods-execute.md) appels de méthode.  
  
## <a name="object-references"></a>Références d'objet  
 Plusieurs commandes XMLA, tel que [supprimer](../xmla/xml-elements-commands/delete-element-xmla.md) ou [processus](../xmla/xml-elements-commands/process-element-xmla.md), utilisez une référence d’objet pour faire référence à un objet de façon non équivoque. Une référence d'objet contient l'identificateur de l'objet sur lequel une commande est exécutée, ainsi que les identificateurs des ancêtres de cet objet. Par exemple, dans le cas d'une partition, la référence d'objet contient l'identificateur d'objet de la partition, ainsi que les identificateurs d'objet du groupe de mesures parent, du cube et de la base de données de cette partition.  
  
## <a name="object-definitions"></a>Définition d'objets  
 Le [créer](../xmla/xml-elements-commands/create-element-xmla.md) et [Alter](../xmla/xml-elements-commands/alter-element-xmla.md) commandes XMLA créer ou modifier, respectivement, objets sur un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance. Les définitions de ces objets sont représentées par une [ObjectDefinition](../xmla/xml-elements-properties/objectdefinition-element-xmla.md) élément qui contient les éléments ASSL. Identificateurs d’objet peuvent être spécifiés explicitement pour les principaux et de nombreux objets secondaires à l’aide de la [ID](../xmla/xml-elements-properties/id-element-xmla.md) élément. Si l'élément `ID` n'est pas utilisé, l'instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] fournit un identificateur unique, avec une convention d'affectation des noms qui dépend de l'objet à identifier. Pour plus d’informations sur l’utilisation de la `Create` et `Alter` commandes pour définir des objets, consultez [création et modification des objets &#40;XMLA&#41;](../xmla/xml-elements-objects.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Élément objet &#40;XMLA&#41;](../xmla/xml-elements-properties/object-element-xmla.md)   
 [Élément ParentObject &#40;XMLA&#41;](../xmla/xml-elements-properties/parentobject-element-xmla.md)   
 [Élément source &#40;XMLA&#41;](../xmla/xml-elements-properties/source-element-xmla.md)   
 [Élément Target &#40;XMLA&#41;](../xmla/xml-elements-properties/target-element-xmla.md)   
 [Développement avec XMLA dans Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  
