---
title: Types de données XML (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: dba93ca0c4b066498455efeac7470a65d291941a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48191201"
---
# <a name="xml-data-types-xmla"></a>Types de données XML (XMLA)
  Outre les types dérivés primitifs standard définis par la recommandation XML 1.0, la spécification XML for Analysis (XMLA) 1.1 définit des types de données supplémentaires pour la prise en charge de la représentation des données multidimensionnelles et tabulaires.  
  
 XMLA utilise les types de données répertoriés dans le tableau suivant.  
  
|Types de données|Description|  
|----------------|-----------------|  
|Booléen|Type de données `boolean` XML standard.|  
|Décimal|Type de données `decimal` XML standard.|  
|[EmptyResult](emptyresult-data-type-xmla.md)|Espace de noms sur l'élément `root`. Cet espace de noms est retourné lorsqu’une commande XMLA ne retourne un résultat, car la commande XMLA ne retourne généralement pas un résultat ou une erreur s’est produite sur le [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance lors de l’exécution de la commande XMLA.|  
|[EnumString](enumstring-data-type-xmla.md)|Jeu de constantes de chaînes nommées pour un énumérateur donné.|  
|Entier|Type de données `int` XML standard.|  
|[MDDataSet](mddataset-data-type-xmla.md)|Données multidimensionnelles retournées par la *résultat* paramètre de la [Execute](../xml-elements-methods-execute.md) (méthode).|  
|[Jeu de résultats](resultset-data-type-xmla.md)|Jeu de résultats XML autodescriptif retourné par la méthode `Execute`.|  
|[Rowset](rowset-data-type-xmla.md)|Lignes d’une source de données structurées par un schéma XML incorporé retourné par la [Discover](../xml-elements-methods-discover.md) (méthode).|  
|String|Type de données `string` XML.|  
|UnsignedInt|Type de schéma `unsignedInt` XML.|  
  
 Pour obtenir les descriptions complètes des types de données XML standard, consultez la recommandation de langage candidat du WC3 (World Wide Web).  
  
## <a name="see-also"></a>Voir aussi  
 [Éléments XML &#40;XMLA&#41;](../../dev-guide/xml-elements-xmla.md)   
 [XML for Analysis &#40;XMLA&#41; référence](../xml-for-analysis-xmla-reference.md)  
  
  
