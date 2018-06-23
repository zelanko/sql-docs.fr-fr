---
title: Type de données EnumString (XMLA) | Documents Microsoft
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
- EnumString Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- EnumString
- urn:schemas-microsoft-com:xml-analysis#EnumString
- http://schemas.microsoft.com/analysisservices/2003/engine#EnumString
helpviewer_keywords:
- EnumString data type
ms.assetid: 9214195e-4539-419b-95ec-b7aa75e033ab
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 034ebe0218a8effece3aee526f9920850a7df536
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36141875"
---
# <a name="enumstring-data-type-xmla"></a>Type de données EnumString (XMLA)
  Définit un type de données dérivé qui représente un jeu de constantes nommées pour un énumérateur donné.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<EnumString>...</EnumString>  
```  
  
## <a name="data-type-characteristics"></a>Caractéristiques du type de données  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Types de données de base|`string`|  
|Types de données dérivés|None|  
  
## <a name="data-type-relationships"></a>Relations du type de données  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|None|  
|Éléments enfants|None|  
|Éléments dérivés|None|  
  
## <a name="remarks"></a>Notes  
 XML for Analysis (XMLA) utilise des énumérations pour limiter les valeurs de chaîne à un ensemble de paramètres vérifiables. `EnumString` utilise le type de données XML `string` standard. Les valeurs propres à chacune des constantes nommées sont spécifiées avec la définition de l'énumérateur. Les énumérateurs sont définies en les ajoutant à la [DISCOVER_ENUMERATORS](../../schema-rowsets/xml/discover-enumerators-rowset.md) de lignes du schéma et peut être récupéré à l’aide de la [Discover](../xml-elements-methods-discover.md) type de demande de méthode avec le DISCOVER_ENUMERATORS.  
  
 Le tableau suivant décrit les énumérateurs pris en charge par une instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
|Énumérateur|Description|  
|----------------|-----------------|  
|ProviderType|Prend en charge de la colonne ProviderType dans le [DISCOVER_DATASOURCES](../../schema-rowsets/xml/discover-datasources-rowset.md) de lignes du schéma, qui détermine le type de données qui peuvent être retournées par une [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance.<br /><br /> Cette énumération prend en charge également la propriété XMLA, `ProviderType` qui détermine les types de fournisseur a pris en charge par une instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Cette énumération est également utilisée dans l'ensemble de lignes du schéma DISCOVER_DATASOURCES.<br /><br /> Pour plus d’informations sur `ProviderType`, consultez [pris en charge les propriétés XMLA &#40;XMLA&#41;](../xml-elements-properties/propertylist-element-supported-xmla-properties.md).|  
|AuthenticationMode|Prend en charge la colonne AuthenticationMode dans l'ensemble de lignes du schéma DISCOVER_DATASOURCES qui détermine les informations d'identification de sécurité à transmettre pour accéder à une instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|PropertyAccessType|Prend en charge de la colonne PropertyAccessType dans le [DISCOVER_PROPERTIES](../../schema-rowsets/xml/discover-properties-rowset.md) de lignes du schéma, qui détermine le type d’accès disponibles pour une propriété XMLA.|  
|StateSupport|Prend en charge la propriété XMLA `StateSupport` qui détermine le niveau d'état pris en charge par une instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].<br /><br /> Pour plus d’informations sur `StateSupport`, consultez [pris en charge les propriétés XMLA &#40;XMLA&#41;](../xml-elements-properties/propertylist-element-supported-xmla-properties.md).|  
|StateActionVerb|Contient une liste de verbes pris en charge par XMLA dans les en-têtes SOAP et utilisés pour démarrer, identifier et achever une session.<br /><br /> Pour plus d’informations sur les sessions, consultez [gestion des connexions et Sessions &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md).|  
|ResultsetFormat|Prend en charge la propriété XMLA `Format`, qui détermine le type de données retournées dans un [racine](../xml-elements-properties/root-element-xmla.md) élément.<br /><br /> Pour plus d’informations sur `Format`, consultez [pris en charge les propriétés XMLA &#40;XMLA&#41;](../xml-elements-properties/propertylist-element-supported-xmla-properties.md).|  
|ResultsetAxisFormat|Prend en charge la propriété XMLA `AxisFormat` qui détermine le format des informations d'axe que retourne un élément `root` contenant des données multidimensionnelles.<br /><br /> Pour plus d’informations sur `AxisFormat`, consultez [pris en charge les propriétés XMLA &#40;XMLA&#41;](../xml-elements-properties/propertylist-element-supported-xmla-properties.md).|  
|ResultsetContents|Prend en charge la propriété XMLA `Content` qui détermine si les données ou les métadonnées sont retournées dans un élément `root`.<br /><br /> Pour plus d’informations sur `Content`, consultez [pris en charge les propriétés XMLA &#40;XMLA&#41;](../xml-elements-properties/propertylist-element-supported-xmla-properties.md).|  
|MDXSupportLevel|Prend en charge la propriété XMLA `MDXSupport` qui indique le niveau de prise en charge MDX (Multidimensional Expressions) disponible sur une instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].<br /><br /> Pour plus d’informations sur `MDXSupport`, consultez [pris en charge les propriétés XMLA &#40;XMLA&#41;](../xml-elements-properties/propertylist-element-supported-xmla-properties.md).|  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données XML &#40;XMLA&#41;](xml-data-types-xmla.md)  
  
  