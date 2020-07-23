---
title: FORME (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 4d5d93d4236b3cf86719c416ba87517401e4b4f5
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "86970299"
---
# <a name="ltsource-data-querygt---shape"></a>&lt;requête de données source &gt; -forme
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Associe les requêtes de plusieurs sources de données à une table hiérarchique unique (c'est-à-dire une table avec des tables imbriquées), qui devient la table de cas du modèle d'exploration de données.  
  
 La syntaxe complète de la commande **Shape** est documentée dans le [!INCLUDE[msCoName](../includes/msconame-md.md)] Kit de développement logiciel (SDK) de Data Access Components (MDAC).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SHAPE {<primary query>}  
APPEND ({ <child table query> }   
     RELATE <primary column> TO <child column>)   
          AS <column table name>  
[  
     ({ <child table query> }   
     RELATE <primary column> TO <child column>)   
          AS < column table name>  
...  
]       
```  
  
## <a name="arguments"></a>Arguments  
 *requête principale*  
 Requête retournant la table parent.  
  
 *requête de table enfant*  
 Requête retournant la table imbriquée.  
  
 *colonne principale*  
 Colonne de la table parent permettant d'identifier les lignes enfants dans le résultat d'une requête de table enfant.  
  
 *colonne enfant*  
 Colonne de la table enfant qui permet d’identifier la ligne parente à partir du résultat d’une requête principale.  
  
 *nom de la table de colonnes*  
 Nom de la nouvelle colonne dans la table parent de la table imbriquée.  
  
## <a name="remarks"></a>Remarques  
 Vous devez ordonner les requêtes par la colonne qui relie la table parent à la table enfant.  
  
## <a name="examples"></a>Exemples  
 Vous pouvez utiliser l’exemple suivant dans une instruction [INSERT INTO &#40;DMX&#41;](../dmx/insert-into-dmx.md) pour effectuer l’apprentissage d’un modèle contenant une table imbriquée. Les deux tables de l’instruction **Shape** sont liées par le biais de la colonne **OrderNumber** .  
  
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
 [&#60;&#62;de requête de données source](../dmx/source-data-query.md)   
 [Instructions de définition de données DMX&#41; Data Mining Extensions &#40;](../dmx/dmx-statements-data-definition.md)   
 [Data Mining Extensions &#40;les instructions de manipulation de données DMX&#41;](../dmx/dmx-statements-data-manipulation.md)   
 [Guide de référence des instructions DMX &#40;Data Mining Extensions&#41;](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
