---
title: "Modifiez la valeur de délai d’attente pour les requêtes d’exploration de données | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- time-out
ms.assetid: f1add4bc-e882-440a-a98b-333cfa274c3e
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 51603c1919fae5e164348181412712d4dfc673a0
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="change-the-time-out-value-for-data-mining-queries"></a>Modifier la valeur du délai d'attente pour les requêtes d'exploration de données
  Lorsque vous générez un graphique de courbes d'élévation ou que vous exécutez une requête de prédiction, quelquefois, la génération de toutes les données requises pour la prédiction peut prendre du temps. Pour empêcher l'expiration du délai pour la requête, vous pouvez modifier la valeur qui contrôle le délai d'attente du serveur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] pour achever une requête.  
  
 La valeur par défaut est 15 ; toutefois, si vos modèles sont complexes ou que la source de données est importante, cela risque de ne pas suffire. Le cas échéant, vous pouvez augmenter cette valeur de manière significative, afin de consacrer assez de temps pour le traitement. Si, par exemple, vous définissez **Délai de requête** avec la valeur 600, l'exécution de la requête peut continuer jusqu'à 10 minutes.  
  
 Pour plus d’informations sur les requêtes de prédiction, consultez [Tâches de requête d’exploration de données et procédures](../../analysis-services/data-mining/data-mining-query-tasks-and-how-tos.md).  
  
### <a name="configure-the-time-out-value-for-data-mining-queries"></a>Configurer la valeur du délai d'attente pour les requêtes d'exploration de données  
  
1.  Dans le menu [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]Outils **de** , sélectionnez **Options**.  
  
2.  Dans le volet **Options** , développez **Concepteurs Business Intelligence**.  
  
3.  Cliquez sur la zone de texte **Délai de requête** et tapez une valeur pour le nombre de secondes.  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches de requête d’exploration de données et procédures](../../analysis-services/data-mining/data-mining-query-tasks-and-how-tos.md)   
 [Requêtes d'exploration de données](../../analysis-services/data-mining/data-mining-queries.md)  
  
  

