---
title: Référence XML for Analysis (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- XML for Analysis, reference
- XMLA, reference
ms.assetid: 88045e05-ce47-4e28-999b-7f9c74af9faf
caps.latest.revision: 33
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ec0d843ac46cbcf5d032d1f93190869fd5a37cb2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37241279"
---
# <a name="xml-for-analysis--xmla-reference"></a>Référence XML for Analysis (XMLA)
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] utilise le protocole XML for Analysis (XMLA) pour gérer toutes les communications entre les applications clientes et une instance Analysis Services. Au niveau de base, d'autres bibliothèques clientes telles que ADOMD.NET et AMO génèrent des requêtes et décodent les réponses en XMLA, servant d'intermédiaires à une instance d'Analysis Services qui utilise exclusivement XMLA.  
  
 Pour prendre en charge la découverte et la manipulation de données dans des formats multidimensionnelles et tabulaires, la spécification XMLA définit deux méthodes généralement accessibles, [Discover](xml-elements-methods-discover.md) et [Execute](xml-elements-methods-execute.md)et un collection de types d’éléments et les données XML. Du fait que XML autorise l'exploitation d'une architecture client et serveur faiblement couplée, ces deux méthodes gèrent les informations entrantes et sortantes au format XML. Analysis Services est compatible avec la spécification XMLA 1.1, mais l'étend pour inclure la fonction de définition de données et de manipulation implémentée sous la forme d'annotations sur les méthodes `Discover` et `Execute`. La syntaxe XML étendue est désignée par le terme ASSL (Analysis Services Scripting Language). ASSL repose sur la spécification XMLA sans la décomposer. L'interopérabilité basée sur XMLA est garantie si vous utilisez uniquement XMLA ou XMLA et ASSL.  
  
 En tant que programmeur, vous pouvez utiliser XMLA comme interface de programmation si les spécifications de solution spécifient des protocoles standard, tels que XML, SOAP et HTTP. Les programmeurs et les administrateurs peuvent également utiliser XMLA sur une base ad hoc pour récupérer les informations du serveur ou pour exécuter des commandes.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Éléments XML &#40;XMLA&#41;](../dev-guide/xml-elements-xmla.md)|Décrit des éléments dans la spécification XMLA.|  
|[Types de données XML &#40;XMLA&#41;](xml-data-types/xml-data-types-xmla.md)|Décrit des types de données dans la spécification XMLA.|  
|[Conformité XML for Analysis &#40;XMLA&#41;](xml-for-analysis-compliance-xmla.md)|Décrit le niveau de compatibilité avec la spécification XMLA 1.1.|  
  
## <a name="related-sections"></a>Sections connexes  
 [Développement avec Analysis Services Scripting Language &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)  
  
 [Ensembles de lignes de schéma XML for Analysis](../schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
 [Développement avec ADOMD.NET](../multidimensional-models/adomd-net/developing-with-adomd-net.md)  
  
 [Développement avec Analysis Management Objects &#40;AMO&#41;](../multidimensional-models/analysis-management-objects/developing-with-analysis-management-objects-amo.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation de l’architecture Microsoft OLAP](../multidimensional-models/olap-physical/understanding-microsoft-olap-architecture.md)  
  
  
