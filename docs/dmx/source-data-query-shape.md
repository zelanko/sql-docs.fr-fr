---
title: FORME (DMX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SHAPE
dev_langs:
- DMX
helpviewer_keywords:
- SHAPE statement
- multiple data sources
ms.assetid: b9526ec2-40bc-4bf5-b4e5-774f71075065
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: dcd4940769fc52852b1d48feb453f1393c754084
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="ltsource-data-querygt---shape"></a>&lt;requête de source de données&gt; -forme
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Associe les requêtes de plusieurs sources de données à une table hiérarchique unique (c'est-à-dire une table avec des tables imbriquées), qui devient la table de cas du modèle d'exploration de données.  
  
 La syntaxe complète de la **forme** commande est documentée dans le [!INCLUDE[msCoName](../includes/msconame-md.md)] Kit de développement logiciel (SDK) Data Access Components (MDAC).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SHAPE {<master query>}  
APPEND ({ <child table query> }   
     RELATE <master column> TO <child column>)   
          AS <column table name>  
[  
     ({ <child table query> }   
     RELATE <master column> TO <child column>)   
          AS < column table name>  
...  
]       
```  
  
## <a name="arguments"></a>Arguments  
 *requête principale*  
 Requête retournant la table parent.  
  
 *requête de table enfant*  
 Requête retournant la table imbriquée.  
  
 *colonne de référence*  
 Colonne de la table parent permettant d'identifier les lignes enfants dans le résultat d'une requête de table enfant.  
  
 *colonne enfant*  
 Colonne de la table enfant permettant d'identifier la ligne parent dans le résultat d'une requête de table enfant.  
  
 *nom de la table colonne*  
 Nom de la nouvelle colonne dans la table parent de la table imbriquée.  
  
## <a name="remarks"></a>Notes  
 Vous devez ordonner les requêtes par la colonne qui relie la table parent à la table enfant.  
  
## <a name="examples"></a>Exemples  
 Vous pouvez utiliser l’exemple suivant dans un [INSERT INTO &#40; DMX &#41;](../dmx/insert-into-dmx.md) instruction pour former un modèle contenant une table imbriquée. Les deux tables au sein de la **forme** instruction au moyen du **OrderNumber** colonne.  
  
```  
SHAPE {  
    OPENQUERY([Adventure Works DW Multidimensional 2012],'SELECT OrderNumber  
    FROM vAssocSeqOrders ORDER BY OrderNumber')  
} APPEND (  
    {OPENQUERY([Adventure Works DW Multidimensional 2012],'SELECT OrderNumber, model FROM   
    dbo.vAssocSeqLineItems ORDER BY OrderNumber, Model')}  
  RELATE OrderNumber to OrderNumber)   
```  
  
## <a name="see-also"></a>Voir aussi  
 [&#60; requête de source de données &#62;](../dmx/source-data-query.md)   
 [Les Extensions d’exploration de données &#40; DMX &#41; Instructions de définition de données](../dmx/dmx-statements-data-definition.md)   
 [Les Extensions d’exploration de données &#40; DMX &#41; Instructions de Manipulation de données](../dmx/dmx-statements-data-manipulation.md)   
 [Les Extensions d’exploration de données &#40; DMX &#41; Référence des instructions](../dmx/data-mining-extensions-dmx-statements.md)  
  
  

