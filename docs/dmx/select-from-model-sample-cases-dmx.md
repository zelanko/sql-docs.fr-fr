---
title: "SELECT FROM &lt;modèle&gt;. SAMPLE_CASES (DMX) | Documents Microsoft"
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
- SAMPLE_CASES
- SELECT
- FROM
dev_langs:
- DMX
helpviewer_keywords:
- SELECT FROM <model>.SAMPLE_CASES statement
- mining models [Analysis Services], sample cases
- sample cases [DMX]
- training mining models
ms.assetid: e7a34b9b-3562-4503-bfa7-dd9b12db480a
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 3c1e90c2d4fd6b7dab565550bc4b08a4a33192ee
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="select-from-ltmodelgtsamplecases-dmx"></a>SELECT FROM &lt;modèle&gt;. SAMPLE_CASES (DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne les exemples de cas qui sont représentatifs des cas utilisés pour l'apprentissage du modèle d'exploration de données.  
  
 Pour utiliser cette instruction, vous devez activer l'extraction lorsque vous créez le modèle d'exploration de données. Pour plus d’informations sur l’activation de l’extraction, consultez [créer un modèle d’exploration de données &#40; DMX &#41;](../dmx/create-mining-model-dmx.md), [SELECT INTO &#40; DMX &#41;](../dmx/select-into-dmx.md), et [modifier la STRUCTURE d’exploration de données &#40; DMX &#41;](../dmx/alter-mining-structure-dmx.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SELECT [FLATTENED] [TOP <n>] <expression list> FROM <model>.SAMPLE_CASES  
[WHERE <condition list>] ORDER BY <expression> [DESC|ASC]]  
```  
  
## <a name="arguments"></a>Arguments  
 *n*  
 Ce paramètre est facultatif. Entier qui spécifie le nombre de lignes à retourner.  
  
 *liste d’expressions*  
 Liste séparée par des virgules des identificateurs des colonnes associées.  
  
 *model*  
 Identificateur du modèle  
  
 *liste des conditions*  
 Ce paramètre est facultatif. Conditions pour restreindre les valeurs retournées de la liste des colonnes.  
  
 *expression*  
 Ce paramètre est facultatif. Expression qui retourne une valeur scalaire.  
  
## <a name="remarks"></a>Notes  
 Les exemples de cas peuvent être générés et ne pas réellement exister dans les données d'apprentissage. Le cas retourné est représentatif du nœud de contenu spécifié.  
  
 Bien que le [!INCLUDE[msCoName](../includes/msconame-md.md)] algorithme Sequence Clustering est le seul [!INCLUDE[msCoName](../includes/msconame-md.md)] algorithme prenant en charge à l’aide de SELECT FROM \<modèle >. SAMPLE_CASES, les algorithmes tiers peuvent également en charge.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant retourne les exemples de cas utilisés pour l'apprentissage du modèle d'exploration de données Target Mail (Courrier cible). À l’aide de la [IsInNode &#40; DMX &#41;](../dmx/isinnode-dmx.md) de fonction dans le **où** clause retourne uniquement les cas qui sont associées au nœud « 000000003 ». La chaîne de nœud peut être trouvée dans la colonne NODE_UNIQUE_NAME de l'ensemble de lignes du schéma.  
  
```  
Select * from [Sequence Clustering].SAMPLE_Cases  
WHERE IsInNode('000000003')  
```  
  
## <a name="see-also"></a>Voir aussi  
 [SÉLECTIONNEZ &#40; DMX &#41;](../dmx/select-dmx.md)   
 [Les Extensions d’exploration de données &#40; DMX &#41; Instructions de définition de données](../dmx/dmx-statements-data-definition.md)   
 [Les Extensions d’exploration de données &#40; DMX &#41; Instructions de Manipulation de données](../dmx/dmx-statements-data-manipulation.md)   
 [Les Extensions d’exploration de données &#40; DMX &#41; Référence des instructions](../dmx/data-mining-extensions-dmx-statements.md)  
  
  

