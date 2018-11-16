---
title: Fonctions d’accesseur de données | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- data-accessor functions [XQuery]
ms.assetid: 31bad04f-7c74-4773-9f83-612704fdd21c
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: ca466042ba90915076b0be47f867d74c3ab86e68
ms.sourcegitcommit: 0f7cf9b7ab23df15624d27c129ab3a539e8b6457
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51292065"
---
# <a name="data-accessor-functions"></a>Fonctions d'accesseurs de données
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Les rubriques de cette section présentent les fonctions d'accès aux données et les illustrent avec des exemples de code.  
  
## <a name="understanding-fndata-fnstring-and-text"></a>Fonctionnement de fn:data(), fn:string () et text()  
 XQuery fournit une fonction **fn :Data()** pour extraire des valeurs scalaires, typés à partir des nœuds, un test de nœud **text()** pour retourner les nœuds de texte et la fonction **fn :String()** qui retourne le valeur de chaîne d’un nœud. Leur utilisation peut prêter à confusion. Vous trouverez ci-après des instructions relatives à leur bonne utilisation dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. L’instance XML \<age > 12 \< /age > est utilisé à titre d’illustration.  
  
-   XML non typé : l'expression de chemin d'accès /age/text() retourne le nœud de texte "12". Les fonctions fn:data(/age) et fn:string(/age) retournent la valeur de chaîne "12".  
  
-   XML typé : L’expression /age/text() renvoie une erreur statique pour n’importe quel simple typé \<âge > élément. En revanche, la fonction fn:data (/age) retourne l'entier 12. La fonction fn:string(/age) produit la chaîne "12".  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Fonction String &#40;XQuery&#41;](../xquery/data-accessor-functions-string-xquery.md)  
  
-   [Fonction Data &#40;XQuery&#41;](../xquery/data-accessor-functions-data-xquery.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Expressions de chemin &#40;XQuery&#41;](../xquery/path-expressions-xquery.md)  
  
  
