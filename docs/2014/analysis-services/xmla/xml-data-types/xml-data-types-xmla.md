---
title: Types de données XML (XMLA) | Documents Microsoft
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
topic_type:
- apiref
- apinav
helpviewer_keywords:
- XML data types [XMLA]
- data types [XML for Analysis]
- XMLA, data types
- XML for Analysis, data types
ms.assetid: 979b5384-90d9-4e09-9286-1d1eafdc4864
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: d7a21691474e890ba8614715b18e972d1353b2c6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36053133"
---
# <a name="xml-data-types-xmla"></a>Types de données XML (XMLA)
  Outre les types dérivés primitifs standard définis par la recommandation XML 1.0, la spécification XML for Analysis (XMLA) 1.1 définit des types de données supplémentaires pour la prise en charge de la représentation des données multidimensionnelles et tabulaires.  
  
 XMLA utilise les types de données répertoriés dans le tableau suivant.  
  
|Types de données|Description|  
|----------------|-----------------|  
|Booléen|Type de données `boolean` XML standard.|  
|Décimal|Type de données `decimal` XML standard.|  
|[EmptyResult](emptyresult-data-type-xmla.md)|Espace de noms sur l'élément `root`. Cet espace de noms est retourné lorsqu’une commande XMLA ne retourne un résultat, car la commande XMLA ne retourne généralement pas un résultat ou une erreur s’est produite sur le [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] lors de l’exécution de la commande XMLA.|  
|[EnumString](enumstring-data-type-xmla.md)|Jeu de constantes de chaînes nommées pour un énumérateur donné.|  
|Entier|Type de données `int` XML standard.|  
|[MDDataSet](mddataset-data-type-xmla.md)|Données multidimensionnelles retournées par la *résultat* paramètre de la [Execute](../xml-elements-methods-execute.md) (méthode).|  
|[Jeu de résultats](resultset-data-type-xmla.md)|Jeu de résultats XML autodescriptif retourné par la méthode `Execute`.|  
|[Rowset](rowset-data-type-xmla.md)|Lignes d’une source de données structurées par un schéma XML incorporé retourné par le [Discover](../xml-elements-methods-discover.md) (méthode).|  
|String|Type de données `string` XML.|  
|UnsignedInt|Type de schéma `unsignedInt` XML.|  
  
 Pour obtenir les descriptions complètes des types de données XML standard, consultez la recommandation de langage candidat du WC3 (World Wide Web).  
  
## <a name="see-also"></a>Voir aussi  
 [Éléments XML &#40;XMLA&#41;](../../dev-guide/xml-elements-xmla.md)   
 [XML for Analysis &#40;XMLA&#41; référence](../xml-for-analysis-xmla-reference.md)  
  
  