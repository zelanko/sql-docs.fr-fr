---
title: Fonctions XQuery sur le type de données XML | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- XQuery, functions
- xml data type [SQL Server], XQuery
- functions [SQL Server], XQuery
ms.assetid: 8df0877d-a03f-4ca9-b84e-908c4bb42b5e
author: rothja
ms.author: jroth
ms.openlocfilehash: e885b537fbc86f3b70a8142c5513dbf16cb1c158
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67945996"
---
# <a name="xquery-functions-against-the-xml-data-type"></a>Fonctions XQuery impliquant le type de données xml
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Cette rubrique et ses sous-rubriques décrivent les fonctions que vous pouvez utiliser lors de la spécification de XQuery par rapport au type de données **XML** . Pour les spécifications du W3C, [http://www.w3.org/TR/2004/WD-xpath-functions-20040723](https://go.microsoft.com/fwlink/?LinkId=4873)consultez.  
  
 Les fonctions XQuery appartiennent à l' http://www.w3.org/2004/07/xpath-functions espace de noms. Les spécifications W3C utilisent le préfixe d'espace de noms « fn: » pour décrire ces fonctions. Vous n'avez pas besoin de spécifier ce préfixe explicitement lorsque vous utilisez les fonctions. Par conséquent, et dans un souci de lisibilité, les préfixes d'espace de noms ne sont généralement pas utilisés dans cette documentation.  
  
 Le tableau suivant répertorie les fonctions XQuery prises en charge par rapport au type de données **XML**.  
  
|Category|Nom de fonction|  
|--------------|-------------------|  
|[Fonctions sur des valeurs numériques](https://msdn.microsoft.com/library/d5740a32-b174-43b9-b64d-1cc6edc50cff)|[plafond](../xquery/numeric-values-functions-ceiling.md)|  
||[Floor](../xquery/numeric-values-functions-floor.md)|  
||[Round](../xquery/numeric-values-functions-round.md)|  
|[Fonctions XQuery sur des valeurs de chaîne](https://msdn.microsoft.com/library/2dccefef-5d90-4f56-bda7-4c1954d8a730)|[concat](../xquery/functions-on-string-values-concat.md)|  
||[contains](../xquery/functions-on-string-values-contains.md)|  
||[substring](../xquery/functions-on-string-values-substring.md)|  
||[Fonction en minuscules &#40;XQuery&#41;](../xquery/functions-on-string-values-lower-case.md)|  
||[chaîne-longueur](../xquery/functions-on-string-values-string-length.md)|  
||[Fonction majuscule &#40;XQuery&#41;](../xquery/functions-on-string-values-upper-case.md)|  
|Fonctions sur les valeurs booléennes|[not](../xquery/functions-on-boolean-values-not-function.md)|  
|[Fonctions sur les nœuds](https://msdn.microsoft.com/library/09a8affa-3341-4f50-aebc-fdf529e00c08)|[number](../xquery/functions-on-nodes-number.md)|  
||[Fonction local-name (XQuery)](../xquery/functions-on-nodes-local-name.md)|  
||[Fonction namespace-uri (XQuery)](../xquery/functions-on-nodes-namespace-uri.md)|  
|[Fonctions de contexte](https://msdn.microsoft.com/library/f7d8af33-9de9-450c-a667-23dee3129b5f)|[last](../xquery/context-functions-last-xquery.md)|  
||[endroit](../xquery/context-functions-position-xquery.md)|  
|[Fonctions sur les séquences](https://msdn.microsoft.com/library/672d2795-53ab-49c2-bf24-bc81a47ecd3f)|[empty](../xquery/functions-on-sequences-empty.md)|  
||[distinct-values](../xquery/functions-on-sequences-distinct-values.md)|  
||[Fonction id (XQuery)](../xquery/functions-on-sequences-id.md)|  
|[Fonctions d’agrégation &#40;XQuery&#41;](https://msdn.microsoft.com/library/be647ef1-291e-4a5d-ab18-07c759efe176)|[count](../xquery/aggregate-functions-count.md)|  
||[AVG](../xquery/aggregate-functions-avg.md)|  
||[min](../xquery/aggregate-functions-min.md)|  
||[max](../xquery/aggregate-functions-max.md)|  
||[checksum](../xquery/aggregate-functions-sum.md)|  
|[Fonctions de constructeur &#40;XQuery&#41;](../xquery/constructor-functions-xquery.md)|[Fonctions constructeur](../xquery/constructor-functions-xquery.md)|  
|[Fonctions d'accesseurs de données](../xquery/data-accessor-functions.md)|[string](../xquery/data-accessor-functions-string-xquery.md)|  
||[data](../xquery/data-accessor-functions-data-xquery.md)|  
|[Fonctions de constructeur booléen &#40;XQuery&#41;](https://msdn.microsoft.com/library/fa907f39-d4b7-4495-b829-c788928e0f64)|[Fonction true (XQuery)](../xquery/boolean-constructor-functions-true-xquery.md)|  
||[Fonction false (XQuery)](../xquery/boolean-constructor-functions-false-xquery.md)|  
|[Fonctions liées à QNames &#40;XQuery&#41;](https://msdn.microsoft.com/library/7e07eb26-f551-4b63-ab77-861684faff71)|[expanded-QName (XQuery)](../xquery/functions-related-to-qnames-expanded-qname.md)|  
||[local-name-from-QName (XQuery)](../xquery/functions-related-to-qnames-local-name-from-qname.md)|  
||[namespace-uri-from-QName (XQuery)](../xquery/functions-related-to-qnames-namespace-uri-from-qname.md)|  
|[Fonctions d'extension SQL Server XQuery](https://msdn.microsoft.com/library/4bc5d499-5fec-4c3f-b11e-5ab5ef9d8f97)|[fonction SQL : Column () (XQuery)](../xquery/xquery-extension-functions-sql-column.md)|  
||[Fonction sql:variable() (XQuery)](../xquery/xquery-extension-functions-sql-variable.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes de type de données XML](../t-sql/xml/xml-data-type-methods.md)   
 [Référence du langage XQuery &#40;SQL Server&#41;](../xquery/xquery-language-reference-sql-server.md)   
 [Données XML &#40;SQL Server&#41;](../relational-databases/xml/xml-data-sql-server.md)  
  
  
