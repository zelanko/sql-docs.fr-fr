---
title: "Leçon 6 : Définition de calculs | Documents Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tutorial
ms.reviewer: 
ms.suite: sql
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to: SQL Server 2016
ms.assetid: e0a1e354-e879-4eb8-bb2b-6c3809e32cb6
caps.latest.revision: "19"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 124ccfaa310ac6bc356cfaf30a7dc5c331b563a0
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="lesson-6-defining-calculations"></a>Leçon 6 : Définition de calculs
Dans cette leçon, vous apprenez à définir des calculs, qui sont des expressions ou des scripts MDX (Multidimensional Expressions). Les calculs vous permettent de définir des membres calculés, des jeux nommés et d'exécuter d'autres commandes de script pour étendre les possibilités d'un cube [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] . Par exemple, vous pouvez exécuter une commande de script pour définir un sous-cube et assigner un calcul aux cellules du sous-cube.  
  
Lorsque vous définissez un nouveau calcul dans le Concepteur de cube, ce calcul est ajouté au volet **Organisateur de script** de l'onglet **Calculs** du Concepteur de cube, et les champs pour ce type de calcul particulier s'affichent dans un formulaire de calcul dans le volet **Expressions de calcul** . Les calculs sont exécutés dans l'ordre où ils apparaissent dans le volet **Organisateur de script** . Vous pouvez changer l’ordre des calculs en cliquant avec le bouton droit sur un calcul particulier, puis en sélectionnant **Monter** ou **Descendre**. Ou bien, vous pouvez cliquer sur un calcul particulier, puis utiliser l’icône **Monter** ou **Descendre** de la barre d’outils de l’onglet **Calculs** .  
  
Sous l'onglet **Calculs** , vous pouvez ajouter de nouveaux calculs et afficher ou modifier des calculs existants dans l'un des deux modes d'affichage du volet **Expressions de calcul** :  
  
-   Mode Formulaire. Ce mode affiche les expressions et les propriétés pour une seule commande dans un format graphique. Lorsque vous modifiez un script MDX, une zone d'expression occupe tout le formulaire.  
  
-   Mode Script. Ce mode affiche tous les scripts de calcul dans un éditeur de code, ce qui vous permet de les modifier facilement. Lorsque le volet **Expressions de calcul** est en mode Script, l' **Organisateur de script** est masqué. Le mode Script offre un codage en couleurs, un appariement des parenthèses, une saisie semi-automatique et des régions de code MDX. Vous pouvez développer ou réduire les régions de code MDX pour faciliter les modifications.  
  
Pour passer d'un mode à l'autre dans le volet **Expressions de calcul** , cliquez sur **Mode Formulaire** ou sur **Mode Script** dans la barre d'outils de l'onglet **Calculs** .  
  
> [!NOTE]  
> Si [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] détecte une erreur de syntaxe dans un calcul, l'affichage en mode Formulaire est impossible tant que l'erreur n'a pas été corrigée en mode Script.  
  
Vous pouvez aussi utiliser l'Assistant Business Intelligence pour ajouter certains calculs à un cube. Par exemple, vous pouvez utiliser cet Assistant pour ajouter l'analyse chronologique automatisée à un cube, ce qui revient à définir des membres calculés pour des calculs liés à la chronologie, par exemple le cumul dans la période jusqu'à ce jour, les moyennes mobiles ou la croissance d'une période à l'autre. Pour plus d’informations, consultez [Définir des calculs Time Intelligence à l’aide de l’Assistant Business Intelligence](../analysis-services/multidimensional-models/define-time-intelligence-calculations-using-the-business-intelligence-wizard.md).  
  
> [!IMPORTANT]  
> Sous l'onglet **Calculs** , le script de calcul commence par la commande CALCULATE. La commande CALCULATE contrôle l'agrégation des cellules du cube et vous ne devez la modifier que si vous comptez spécifier manuellement les modalités de cette agrégation.  
  
Pour plus d’informations, consultez [Calculs](../analysis-services/multidimensional-models-olap-logical-cube-objects/calculations.md), et [Calculs dans les modèles multidimensionnels](../analysis-services/multidimensional-models/calculations-in-multidimensional-models.md).  
  
> [!NOTE]  
> Les projets achevés de toutes les leçons de ce didacticiel sont disponibles en ligne. Vous pouvez sauter des leçons en utilisant le projet achevé de la leçon précédente comme point de départ. [Cliquez ici](http://go.microsoft.com/fwlink/?LinkID=221866) pour télécharger les exemples de projet de ce didacticiel.  
  
Cette leçon contient les tâches suivantes :  
  
[Définition des membres calculés](../analysis-services/lesson-6-1-defining-calculated-members.md)  
Dans cette tâche, vous apprenez à définir des membres calculés.  
  
[Définition de jeux nommés](../analysis-services/lesson-6-2-defining-named-sets.md)  
Dans cette tâche, vous apprenez à définir des jeux nommés.  
  
## <a name="next-lesson"></a>Leçon suivante  
[Leçon 7 : Définition d’indicateurs de performance clés &#40;KPIs&#41;](../analysis-services/lesson-7-defining-key-performance-indicators-kpis.md)  
  
## <a name="see-also"></a>Voir aussi  
[Scénario du didacticiel Analysis Services](../analysis-services/analysis-services-tutorial-scenario.md)  
[Modélisation multidimensionnelle &#40;didacticiel Adventure Works&#41;](../analysis-services/multidimensional-modeling-adventure-works-tutorial.md)  
[Créer des jeux nommés](../analysis-services/multidimensional-models/create-named-sets.md)  
[Créer des membres calculés](../analysis-services/multidimensional-models/create-calculated-members.md)  
  
  
  
