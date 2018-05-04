---
title: Ensemble de lignes DISCOVER_LITERALS | Documents Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DISCOVER_LITERALS
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DISCOVER_LITERALS rowset
ms.assetid: 1bf0a2e2-a419-4c25-b271-37dfa44de2ea
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: dc239de2abb609aa035880c0cf9dd9217343c08c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="discoverliterals-rowset"></a>Ensemble de lignes DISCOVER_LITERALS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Retourne des informations sur les littéraux pris en charge par le fournisseur XMLA (XML for Analysis) [!INCLUDE[msCoName](../../../includes/msconame-md.md)], y compris les types de données et les valeurs.  
  
 Si vous appelez le [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) méthode avec la **DISCOVER_LITERALS** valeur d’énumération dans le [RequestType](../../../analysis-services/xmla/xml-elements-properties/requesttype-element-xmla.md) élément, le **Discover** méthode retourne la **DISCOVER_LITERALS** ensemble de lignes.  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 Le **DISCOVER_LITERALS** ensemble de lignes contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Longueur| Description|  
|-----------------|--------------------|------------|-----------------|  
|**LiteralName**|**DBTYPE_WSTR**||Nom du littéral décrit dans la ligne.<br /><br /> Par exemple : **DBLITERAL_LIKE_PERCENT**|  
|**LiteralValue**|**DBTYPE_WSTR**||Valeur littérale réelle.<br /><br /> Par exemple, si **LiteralName** est **DBLITERAL_LIKE_PERCENT** et le caractère de pourcentage (**%**) correspond à zéro ou plusieurs caractères dans une clause LIKE, la valeur de la **LiteralValue** colonne est «**%**».|  
|**LiteralInvalidChars**|**DBTYPE_WSTR**||Caractères qui ne sont pas valides dans le littéral.<br /><br /> Par exemple, si les noms de table peuvent contenir la valeur de l’autre chose qu’un caractère numérique, cette chaîne est «**0123456789**».|  
|**LiteralInvalidStartingChars**|**DBTYPE_WSTR**||Caractères qui ne sont pas valides comme premier caractère dans le littéral. Si le littéral peut commencer par n’importe quel caractère valide, il s’agit **null**.|  
|**LiteralMaxLength**|**DBTYPE_I4**||Nombre maximal de caractères du littéral. Si la colonne ne possède pas de longueur maximale ou si elle est inconnue, la valeur est -1.|  
|**LiteralNameEnumValue**|**DBTYPE_I4**|||  
  
 Cet ensemble de lignes de schéma n'est pas trié.  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 Le **DISCOVER_LITERALS** ensemble de lignes peut être restreint sur les colonnes dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|**LiteralName**|**DBTYPE_WSTR**|Ce paramètre est facultatif.|  
  
## <a name="see-also"></a>Voir aussi  
 [XML for Analysis ensembles de lignes de schéma](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)   
 [Ensemble de lignes DISCOVER_KEYWORDS & #40 ; XMLA & #41 ;](../../../analysis-services/schema-rowsets/xml/discover-keywords-rowset-xmla.md)  
  
  
