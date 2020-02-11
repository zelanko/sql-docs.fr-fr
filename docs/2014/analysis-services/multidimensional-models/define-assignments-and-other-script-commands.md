---
title: Définir des affectations et d’autres commandes de script | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- empty scripts [Analysis Services]
- calculations [Analysis Services], scripts
- MDX [Analysis Services], scripts
- scripts [Analysis Services], calculations
ms.assetid: f28b9b22-3dc7-4a45-b4eb-2d023f2c94b8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: caa3b6f49ce778b78f066abf687a3a51b61cc487
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66075822"
---
# <a name="define-assignments-and-other-script-commands"></a>Définir des attributions et d'autres commandes de script
  Sous l’onglet **Calculs** du Concepteur de cube, cliquez sur l’icône **Nouvelle commande de script** dans la barre d’outils pour créer un script vide. Lorsque vous créez un nouveau script, il s’affiche initialement avec un titre vide dans le volet **organisateur de script** de l’onglet calculs. Les caractères que vous tapez dans le volet des expressions de calcul seront visibles en tant que nom de l’élément dans l' **organisateur de script**. Par conséquent, vous pouvez avoir intérêt à taper un nom commenté sur la première ligne pour pouvoir identifier plus facilement le script dans le volet **Organisateur de script** . Pour plus d’informations, consultez [Introduction aux scripts MDX dans Microsoft SQL Server 2005](https://go.microsoft.com/fwlink/?LinkId=81892). Pour plus d’informations sur les problèmes de performances liés aux calculs et requêtes MDX, consultez la section « écriture d’expressions MDX efficaces » dans le [Guide des performances SQL Server 2005 Analysis Services](https://docsbay.net/Microsoft-SQL-Server-2005-Analysis-Services-Performance-Guide).  
  
> [!IMPORTANT]  
>  Quand vous basculez au départ vers l’onglet **Calculs** du Concepteur de cube, le volet **Organisateur de script** contient un script unique avec une commande CALCULATE. La commande CALCULATE contrôle l'agrégation des cellules dans le cube et ne doit être modifiée que si vous avez l'intention de spécifier manuellement la méthode d'agrégation à utiliser pour le cube.  
  
 Vous pouvez utiliser le volet des expressions de calcul pour créer une expression dans la syntaxe MDX (Multidimensional Expressions). Pendant la création de l’expression, vous pouvez faire glisser ou copier des composants, des fonctions et des modèles de cube du volet **Outils de calcul** vers le volet des expressions de calcul. En procédant ainsi, le script de l'élément est ajouté au volet des expressions de calcul à l'endroit où vous le déposez ou le collez. Remplacez les arguments et leurs délimiteurs (« et ») par les valeurs appropriées.  
  
> [!IMPORTANT]  
>  Lorsque vous rédigez une expression contenant plusieurs instructions à l'aide du volet des expressions de calcul, assurez-vous que toutes les lignes du script MDX, sauf la dernière, se terminent par un point-virgule (;). Les calculs sont concaténés dans un seul script MDX et chaque script est suivi d'un point-virgule pour que le script MDX soit correctement compilé. Si vous ajoutez un point-virgule à la fin de la dernière ligne du script dans le volet des expressions de calcul, le cube sera correctement généré et déployé, mais vous ne pourrez pas exécuter de requêtes avec.  
  
## <a name="see-also"></a>Voir aussi  
 [Calculs dans les modèles multidimensionnels](calculations-in-multidimensional-models.md)  
  
  
