---
title: FORME (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: c928d4c96917479f8c37415d5ebe2db9b7f9eb98
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67938116"
---
# <a name="ltsource-data-querygt---shape"></a>&lt;requête de source de données&gt; -forme
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
 *requête maître*  
 Requête retournant la table parent.  
  
 *requête de table enfant*  
 Requête retournant la table imbriquée.  
  
 *colonne maître*  
 Colonne de la table parent permettant d'identifier les lignes enfants dans le résultat d'une requête de table enfant.  
  
 *colonne enfant*  
 Colonne de la table enfant permettant d'identifier la ligne parent dans le résultat d'une requête de table enfant.  
  
 *nom de la table colonne*  
 Nom de la nouvelle colonne dans la table parent de la table imbriquée.  
  
## <a name="remarks"></a>Notes  
 Vous devez ordonner les requêtes par la colonne qui relie la table parent à la table enfant.  
  
## <a name="examples"></a>Exemples  
 Vous pouvez utiliser l’exemple suivant dans un [INSERT INTO &#40;DMX&#41; ](../dmx/insert-into-dmx.md) instruction pour former un modèle contenant une table imbriquée. Les deux tables au sein de la **forme** instruction associées par le biais du **OrderNumber** colonne.  
  
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
 [&#60;requête de source de données&#62;](../dmx/source-data-query.md)   
 [Data Mining Extensions &#40;DMX&#41; les instructions de définition de données](../dmx/dmx-statements-data-definition.md)   
 [Data Mining Extensions &#40;DMX&#41; les instructions de Manipulation de données](../dmx/dmx-statements-data-manipulation.md)   
 [Guide de référence des instructions DMX &#40;Data Mining Extensions&#41;](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
