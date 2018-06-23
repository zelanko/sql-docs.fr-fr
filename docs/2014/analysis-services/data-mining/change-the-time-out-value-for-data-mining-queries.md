---
title: Modifiez la valeur de délai d’attente pour les requêtes d’exploration de données | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- time-out
ms.assetid: f1add4bc-e882-440a-a98b-333cfa274c3e
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: a3415b66dd27f708ed5d9b831900d1de7adb8300
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36154066"
---
# <a name="change-the-time-out-value-for-data-mining-queries"></a>Modifier la valeur du délai d'attente pour les requêtes d'exploration de données
  Lorsque vous générez un graphique de courbes d'élévation ou que vous exécutez une requête de prédiction, quelquefois, la génération de toutes les données requises pour la prédiction peut prendre du temps. Pour empêcher l'expiration du délai pour la requête, vous pouvez modifier la valeur qui contrôle le délai d'attente du serveur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] pour achever une requête.  
  
 La valeur par défaut est 15 ; toutefois, si vos modèles sont complexes ou que la source de données est importante, cela risque de ne pas suffire. Le cas échéant, vous pouvez augmenter cette valeur de manière significative, afin de consacrer assez de temps pour le traitement. Si, par exemple, vous définissez **Délai de requête** avec la valeur 600, l'exécution de la requête peut continuer jusqu'à 10 minutes.  
  
 Pour plus d’informations sur les requêtes de prédiction, consultez [Tâches de requête d’exploration de données et procédures](data-mining-query-tasks-and-how-tos.md).  
  
### <a name="configure-the-time-out-value-for-data-mining-queries"></a>Configurer la valeur du délai d'attente pour les requêtes d'exploration de données  
  
1.  Dans le menu [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]Outils **de** , sélectionnez **Options**.  
  
2.  Dans le volet **Options** , développez **Concepteurs Business Intelligence**.  
  
3.  Cliquez sur la zone de texte **Délai de requête** et tapez une valeur pour le nombre de secondes.  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches de requête d’exploration de données et de procédures](data-mining-query-tasks-and-how-tos.md)   
 [Requêtes d’exploration de données](data-mining-queries.md)  
  
  