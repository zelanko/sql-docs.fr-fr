---
title: Créer des requêtes d’extraction à l’aide de DMX | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 42c896ee-e5ee-4017-b66e-31d1fe66d369
caps.latest.revision: 5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 72c540463b5bf2b1dff262731fddbc5d258a1de6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37151700"
---
# <a name="create-drillthrough-queries-using-dmx"></a>Créer des requêtes d'extraction à l'aide de DMX
  Pour tous les modèles qui prennent en charge l'extraction, vous pouvez récupérer les données de cas et les données de structure en créant une requête DMX dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou dans tout autre client qui prend en charge DMX.  
  
> [!WARNING]  
>  Pour afficher les données, l'extraction doit avoir été activée, et vous devez disposer des autorisations nécessaires.  
  
## <a name="specifying-drillthrough-options"></a>Spécification des options d'extraction  
 La syntaxe générale pour extraire les cas de modèles et les cas de structure est la suivante :  
  
```  
SELECT <model column list>, StructureColumn('<structure column name') FROM <modelname>.CASES  
```  
  
 Pour plus d’informations sur l’utilisation de requêtes DMX pour retourner des données de cas, consultez [SELECT FROM &#60;modèle&#62;.CASES &#40;DMX&#41;](/sql/dmx/select-from-model-content-dmx) et [SELECT FROM &#60;structure&#62;.CASES](/sql/dmx/select-from-structure-cases).  
  
## <a name="examples"></a>Exemples  
 La requête DMX suivante retourne les données de cas pour une série de produit spécifique, à partir d'un modèle de série chronologique. La requête retourne également la colonne `Amount`, qui n'a pas été utilisée dans le modèle, mais qui est disponible dans la structure d'exploration de données.  
  
```  
SELECT [DateSeries], [Model Region], Quantity, StructureColumn('Amount') AS [M200 Pacific Amount]  
FROM Forecasting.CASES  
WHERE [Model Region] = 'M200 Pacific'  
```  
  
 Notez que, dans cet exemple, un alias a été utilisé pour renommer la colonne de structure. Si vous n'assignez pas d'alias à la colonne de structure, la colonne est retournée avec le nom 'Expression'. Il s'agit du comportement par défaut pour toutes les colonnes sans nom.  
  
## <a name="see-also"></a>Voir aussi  
 [Requêtes d’extraction &#40;exploration de données&#41;](drillthrough-queries-data-mining.md)   
 [Extraction sur des structures d’exploration de données](drillthrough-on-mining-structures.md)  
  
  
