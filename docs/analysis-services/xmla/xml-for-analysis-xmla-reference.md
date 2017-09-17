---
title: "Référence XML for Analysis (XMLA) | Documents Microsoft"
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
- XML for Analysis, reference
- XMLA, reference
ms.assetid: 88045e05-ce47-4e28-999b-7f9c74af9faf
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c85218c4cf2bdbd20db1f45b46efe9dd677dfea4
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="xml-for-analysis--xmla-reference"></a>Référence XML for Analysis (XMLA)
  [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] utilise le protocole XML for Analysis (XMLA) pour gérer toutes les communications entre les applications clientes et une instance Analysis Services. Au niveau de base, d'autres bibliothèques clientes telles que ADOMD.NET et AMO génèrent des requêtes et décodent les réponses en XMLA, servant d'intermédiaires à une instance d'Analysis Services qui utilise exclusivement XMLA.  
  
 Pour prendre en charge la détection et la manipulation des données multidimensionnelles et tabulaires des formats, la spécification XMLA définit deux méthodes généralement accessibles, [Discover](../../analysis-services/xmla/xml-elements-methods-discover.md) et [Execute](../../analysis-services/xmla/xml-elements-methods-execute.md)et une collection de types d’éléments et les données XML. Du fait que XML autorise l'exploitation d'une architecture client et serveur faiblement couplée, ces deux méthodes gèrent les informations entrantes et sortantes au format XML. Analysis Services est compatible avec la spécification XMLA 1.1, la spécification, mais l’étend pour inclure la fonctionnalité définition et manipulation de données, implémentée sous forme d’annotations sur le **Discover** et **Execute** méthodes. La syntaxe XML étendue est désignée par le terme ASSL (Analysis Services Scripting Language). ASSL repose sur la spécification XMLA sans la décomposer. L'interopérabilité basée sur XMLA est garantie si vous utilisez uniquement XMLA ou XMLA et ASSL.  
  
 En tant que programmeur, vous pouvez utiliser XMLA comme interface de programmation si les spécifications de solution spécifient des protocoles standard, tels que XML, SOAP et HTTP. Les programmeurs et les administrateurs peuvent également utiliser XMLA sur une base ad hoc pour récupérer les informations du serveur ou pour exécuter des commandes.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique| Description|  
|-----------|-----------------|  
|[Éléments XML &#40; XMLA &#41;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)|Décrit des éléments dans la spécification XMLA.|  
|[Types de données XML &#40; XMLA &#41;](../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)|Décrit des types de données dans la spécification XMLA.|  
|[XML for Analysis conformité &#40; XMLA &#41;](../../analysis-services/xmla/xml-for-analysis-compliance-xmla.md)|Décrit le niveau de compatibilité avec la spécification XMLA 1.1.|  
  
## <a name="related-sections"></a>Sections connexes  
 [Développement avec le langage de script Analysis Services &#40;ASSL&#41;](../../analysis-services/multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)  
  
 [XML for Analysis ensembles de lignes de schéma](../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
 [Développement avec ADOMD.NET](../../analysis-services/multidimensional-models/adomd-net/developing-with-adomd-net.md)  
  
 [Développement avec AMO &#40;Analysis Management Objects&#41;](../../analysis-services/multidimensional-models/analysis-management-objects/developing-with-analysis-management-objects-amo.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation de l’Architecture Microsoft OLAP](../../analysis-services/multidimensional-models/olap-physical/understanding-microsoft-olap-architecture.md)  
  
  
