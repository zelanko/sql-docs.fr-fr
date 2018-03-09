---
title: "Définir des attributions et autres commandes de Script | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- empty scripts [Analysis Services]
- calculations [Analysis Services], scripts
- MDX [Analysis Services], scripts
- scripts [Analysis Services], calculations
ms.assetid: f28b9b22-3dc7-4a45-b4eb-2d023f2c94b8
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 63f814c8878e1e1151861a8979398a4422d4578a
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2018
---
# <a name="define-assignments-and-other-script-commands"></a>Définir des attributions et d'autres commandes de script
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
Sous l’onglet **Calculs** du Concepteur de cube, cliquez sur l’icône **Nouvelle commande de script** dans la barre d’outils pour créer un script vide. Quand vous créez un script, il s’affiche au départ avec un titre vide dans le volet **Organisateur de script** de l’onglet Calculs. Les caractères que vous tapez dans le volet des expressions de calcul s’affichent en tant que nom de l’élément dans **l’organisateur de script**. Par conséquent, vous pouvez avoir intérêt à taper un nom commenté sur la première ligne pour pouvoir identifier plus facilement le script dans le volet **Organisateur de script** . Pour plus d’informations, consultez [Introduction aux scripts MDX dans Microsoft SQL Server 2005](http://go.microsoft.com/fwlink/?LinkId=81892). Pour plus d’informations sur les problèmes de performances liés aux calculs et aux requêtes MDX, consultez la section du [Guide des performances SQL Server 2005 Analysis Services](http://go.microsoft.com/fwlink/?LinkId=81621)qui explique comment écrire efficacement des requêtes MDX.  
  
> [!IMPORTANT]  
>  Quand vous basculez au départ vers l’onglet **Calculs** du Concepteur de cube, le volet **Organisateur de script** contient un script unique avec une commande CALCULATE. La commande CALCULATE contrôle l'agrégation des cellules dans le cube et ne doit être modifiée que si vous avez l'intention de spécifier manuellement la méthode d'agrégation à utiliser pour le cube.  
  
 Vous pouvez utiliser le volet des expressions de calcul pour créer une expression dans la syntaxe MDX (Multidimensional Expressions). Pendant la création de l’expression, vous pouvez faire glisser ou copier des composants, des fonctions et des modèles de cube du volet **Outils de calcul** vers le volet des expressions de calcul. En procédant ainsi, le script de l'élément est ajouté au volet des expressions de calcul à l'endroit où vous le déposez ou le collez. Remplacez les arguments et leurs délimiteurs (« et ») par les valeurs appropriées.  
  
> [!IMPORTANT]  
>  Lorsque vous rédigez une expression contenant plusieurs instructions à l'aide du volet des expressions de calcul, assurez-vous que toutes les lignes du script MDX, sauf la dernière, se terminent par un point-virgule (;). Les calculs sont concaténés dans un seul script MDX et chaque script est suivi d'un point-virgule pour que le script MDX soit correctement compilé. Si vous ajoutez un point-virgule à la fin de la dernière ligne du script dans le volet des expressions de calcul, le cube sera correctement généré et déployé, mais vous ne pourrez pas exécuter de requêtes avec.  
  
## <a name="see-also"></a>Voir aussi  
 [Calculs dans les modèles multidimensionnels](../../analysis-services/multidimensional-models/calculations-in-multidimensional-models.md)  
  
  
