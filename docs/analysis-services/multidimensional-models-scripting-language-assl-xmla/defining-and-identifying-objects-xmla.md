---
title: "Définition et identification d’objets (XMLA) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
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
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 136679f6596d7e0bf3c33eca51461af13a9fa6d0
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="defining-and-identifying-objects-xmla"></a>Définition et identification d'objets (XMLA)
  Les objets sont identifiés dans les commandes XMLA (XML for Analysis) à l'aide d'identificateurs et de références d'objet, et ils sont définis à l'aide de commandes XMLA contenant des éléments ASSL (Analysis Services Scripting Language).  
  
## <a name="object-identifiers"></a>Identificateurs d'objet  
 Un objet est identifié à l’aide de l’identificateur unique de l’objet tel que défini sur une instance de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Les identificateurs d'objet peuvent être spécifiés explicitement ou déterminés par l'instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] au moment où [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] crée l'objet. Vous pouvez utiliser la [Discover](../../analysis-services/xmla/xml-elements-methods-discover.md) méthode pour récupérer les identificateurs d’objet pour ultérieures **Discover** ou [Execute](../../analysis-services/xmla/xml-elements-methods-execute.md) les appels de méthode.  
  
## <a name="object-references"></a>Références d'objet  
 Plusieurs commandes XMLA, tel que [supprimer](../../analysis-services/xmla/xml-elements-commands/delete-element-xmla.md) ou [processus](../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md), utilisez une référence d’objet pour faire référence à un objet d’une façon non ambiguë. Une référence d'objet contient l'identificateur de l'objet sur lequel une commande est exécutée, ainsi que les identificateurs des ancêtres de cet objet. Par exemple, dans le cas d'une partition, la référence d'objet contient l'identificateur d'objet de la partition, ainsi que les identificateurs d'objet du groupe de mesures parent, du cube et de la base de données de cette partition.  
  
## <a name="object-definitions"></a>Définition d'objets  
 Le [créer](../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md) et [Alter](../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md) commandes XMLA créer ou modifier, respectivement, objets sur un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance. Les définitions de ces objets sont représentées par une [ObjectDefinition](../../analysis-services/xmla/xml-elements-properties/objectdefinition-element-xmla.md) élément qui contient les éléments ASSL. Identificateurs d’objet peuvent être spécifiés explicitement pour les principaux et de nombreux objets secondaires à l’aide de la [ID](../../analysis-services/xmla/xml-elements-properties/id-element-xmla.md) élément. Si le **ID** élément n’est pas utilisé, le [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance fournit un identificateur unique, avec une convention d’affectation de noms qui dépend de l’objet à être identifié. Pour plus d’informations sur l’utilisation de la **créer** et **Alter** commandes pour définir des objets, consultez [création et modification des objets &#40; XMLA &#41; ](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/creating-and-altering-objects-xmla.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Objet, élément &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)   
 [Élément ParentObject &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-properties/parentobject-element-xmla.md)   
 [Élément source &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-properties/source-element-xmla.md)   
 [Élément cible &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-properties/target-element-xmla.md)   
 [Développement avec XMLA dans Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  

