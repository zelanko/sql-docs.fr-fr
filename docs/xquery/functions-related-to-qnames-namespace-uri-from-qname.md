---
title: "espace de noms uri à partir de QName (XQuery) | Documents Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
dev_langs:
- XML
helpviewer_keywords:
- fn:namespace-uri-from-QName function
- namespace-uri-from-QName function
ms.assetid: 4ab3f003-2a3b-4268-9e88-b615e35701b2
caps.latest.revision: 13
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: be3af81f884ff54ff6bea5f07f97d31cf0ad2342
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="functions-related-to-qnames---namespace-uri-from-qname"></a>Fonctions relatives aux QName - espace de noms uri à partir de QName
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Retourne une chaîne qui représente l’uri d’espace de noms du QName spécifié par *$arg*. Le résultat est la séquence vide si *$arg* est la séquence vide.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
namespace-uri-from-QName($arg as xs:QName?) as xs:string?  
```  
  
## <a name="arguments"></a>Arguments  
 *$arg*  
 est le QName d'où est renvoyé l'URI d'espace de noms.  
  
## <a name="examples"></a>Exemples  
 Cette rubrique fournit des exemples de XQuery relatifs à des instances XML stockés dans différentes **xml** colonnes de type dans la base de données AdventureWorks.  
  
### <a name="a-retrieve-the-namespace-uri-from-a-qname"></a>A. Récupération d'un URI d'espace de noms à partir d'un QName  
 Pour obtenir un exemple fonctionnel, consultez [nom local de QName &#40; XQuery &#41; ](../xquery/functions-related-to-qnames-local-name-from-qname.md).  
  
### <a name="implementation-limitations"></a>Limites de mise en œuvre  
 Les limitations suivantes s'appliquent :  
  
-   Le **namespace-uri-from-QName()** fonction retourne des instances de xs : String au lieu de xs : anyURI.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions relatives aux QName &#40; XQuery &#41;](http://msdn.microsoft.com/library/7e07eb26-f551-4b63-ab77-861684faff71)  
  
  
