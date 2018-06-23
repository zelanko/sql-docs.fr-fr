---
title: Filtrage d’une Table imbriquée dans un modèle d’exploration de données (didacticiel sur l’exploration des données intermédiaires) | Documents Microsoft
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0a3ae0e5-897b-4898-a60d-5455eec3d305
caps.latest.revision: 18
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 9b11971c6e6005c7e1d65a1728e8b8aac818b41c
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312317"
---
# <a name="filtering-a-nested-table-in-a-mining-model-intermediate-data-mining-tutorial"></a>Filtrage d'une table imbriquée dans un modèle d'exploration de données (Didacticiel sur l'exploration de données intermédiaire)
  Après avoir créé et exploré le modèle, vous décidez de vous concentrer sur un sous-ensemble des données des clients. Par exemple, vous pouvez souhaiter analyser uniquement les paniers qui contiennent un article spécifique ou les caractéristiques démographiques des clients qui n'ont rien acheté pendant une certaine période.  
  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] permet de filtrer les données utilisées dans un modèle d'exploration de données. Cette fonctionnalité est utile, car vous n’avez pas besoin d’installer une nouvelle vue de source de données pour utiliser des données différentes. Dans le didacticiel sur l'exploration de données de base, vous avez appris à filtrer des données provenant d'une table plate en appliquant des conditions à la table de cas. Au cours de cette tâche, vous allez créer un filtre qui s'applique à une table imbriquée.  
  
## <a name="filters-on-nested-vs-case-tables"></a>Filtres sur des tables imbriquées ou des tables de cas  
 Si votre vue de source de données contient une table de cas et une table imbriquée, à l'instar de la vue de source de données utilisée dans le modèle Association, vous pouvez effectuer un filtrage sur les valeurs de la table de cas, sur la présence ou l'absence d'une valeur dans la table imbriquée ou sur une combinaison des deux.  
  
 Au cours de cette tâche, vous allez d'abord effectuer une copie du modèle Association, puis ajouter les attributs IncomeGroup et Region au nouveau modèle associé, afin de pouvoir filtrer ces attributs dans la table de cas.  
  
#### <a name="to-create-and-modify-a-copy-of-the-association-model"></a>Pour créer et modifier une copie du modèle Association  
  
1.  Dans le **des modèles d’exploration de données** onglet de [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], avec le bouton droit le `Association` de modèle, puis sélectionnez **nouveau modèle d’exploration de données**.  
  
2.  Pour **Nom_modèle**, type `Association Filtered`. Pour **nom de l’algorithme**, sélectionnez **Microsoft Association Rules**. Cliquez sur **OK**.  
  
3.  Dans la colonne pour le modèle d’Association avec filtre, cliquez sur la ligne IncomeGroup et remplacez la valeur de **ignorer** à **entrée**.  
  
 Ensuite, vous allez créer un filtre sur la table de cas dans le nouveau modèle Association. Le filtre va passer au modèle uniquement les clients inclus dans la région cible ou possédant le niveau de revenu cible. Ensuite, vous allez ajouter un deuxième jeu de conditions de filtre pour spécifier que le modèle utilise uniquement les clients dont les paniers ont contenu au moins un article.  
  
#### <a name="to-add-a-filter-to-a-mining-model"></a>Pour ajouter un filtre à un modèle d'exploration de données  
  
1.  Dans le **des modèles d’exploration de données** , cliquez sur le modèle Association avec filtre et sélectionnez **définir le filtre de modèle**.  
  
2.  Dans la boîte de dialogue **Filtre de modèle** , cliquez sur la ligne supérieure dans la grille, dans la zone de texte **Colonne de la structure d'exploration de données** .  
  
3.  Dans le **colonne de Structure d’exploration de données** zone de texte, sélectionnez IncomeGroup.  
  
     L'icône située à gauche de la zone de texte change pour indiquer que l'élément sélectionné est une colonne.  
  
4.  Cliquez sur le **opérateur** zone de texte, puis sélectionnez le **=** opérateur dans la liste.  
  
5.  Cliquez sur le **valeur** zone de texte, puis tapez `High` dans la zone.  
  
6.  Cliquez sur la ligne suivante dans la grille.  
  
7.  Cliquez sur le **et/ou** zone de texte dans la ligne suivante de la grille et sélectionnez **ou**.  
  
8.  Dans le **colonne de Structure d’exploration de données** zone de texte, sélectionnez IncomeGroup. Dans le **valeur** zone de texte, tapez `Moderate`.  
  
     La condition de filtre que vous avez créé est automatiquement ajoutée à la **Expression** zone de texte et doit apparaître comme suit :  
  
     `[IncomeGroup] = 'High' OR [IncomeGroup] = 'Moderate'`  
  
9. Cliquez sur la ligne suivante dans la grille, en laissant l’opérateur en tant que la valeur par défaut, **AND**.  
  
10. Pour **opérateur**, laissez la valeur par défaut, **contient**. Cliquez sur le **valeur** zone de texte.  
  
11. Dans le **filtre** boîte de dialogue, dans la première ligne sous **colonne de Structure d’exploration de données**, sélectionnez `Model`.  
  
12. Pour **opérateur**, sélectionnez **IS NOT NULL**. Laissez le **valeur** zone de texte vide. Cliquez sur **OK**.  
  
     La condition de filtre dans le **Expression** zone de texte de la **filtre de modèle** boîte de dialogue est automatiquement mis à jour pour inclure la nouvelle condition sur la table imbriquée. L'expression complétée se présente comme suit :  
  
     `[IncomeGroup] = 'High' OR [IncomeGroup] = 'Moderate' AND EXISTS SELECT * FROM [vAssocSeqLineItems] WHERE [Model] <> NULL).`  
  
13. [!INCLUDE[clickOK](../includes/clickok-md.md)] ``  
  
#### <a name="to-enable-drillthrough-and-to-process-the-filtered-model"></a>Pour activer l'extraction et traiter le modèle filtré  
  
1.  Dans le **des modèles d’exploration de données** onglet, cliquez sur le `Association Filtered` de modèle, puis sélectionnez **propriétés**.  
  
2.  Modifier la **AllowDrillThrough** propriété **True**.  
  
3.  Cliquez sur le `Association Filtered` modèle d’exploration de données, puis sélectionnez **modèle de processus**.  
  
4.  Cliquez sur **Oui** dans le message d’erreur pour déployer le nouveau modèle pour le [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] base de données.  
  
5.  Dans le **traiter la Structure d’exploration de données** boîte de dialogue, cliquez sur **exécuter**.  
  
6.  Lorsque le traitement est terminé cliquez sur **fermer** pour quitter le **progression du processus** boîte de dialogue, puis cliquez sur **fermer** pour quitter le **traiter la Structure d’exploration de données**  boîte de dialogue.  
  
 Vous pouvez vérifier que le modèle filtré contient moins de cas que le modèle d'origine en utilisant la visionneuse de l'arborescence de contenu générique Microsoft et en recherchant la valeur de NODE_SUPPORT.  
  
## <a name="remarks"></a>Notes  
 Le filtre de table imbriquée que vous venez de créer recherche uniquement la présence d'au moins une ligne dans la table imbriquée ; toutefois, vous pouvez également créer des conditions de filtre qui permettent de rechercher la présence de produits spécifiques.  Par exemple, vous pouvez créer le filtre suivant :  
  
```  
[IncomeGroup] = 'High' AND  
 EXISTS (SELECT * FROM [<nested table name>] WHERE [Model] = 'Water Bottle' )   
```  
  
 Cette instruction signifie que vous restreignez les clients figurant dans la table de cas à uniquement ceux qui ont acheté une bouteille d'eau. Toutefois, puisque le nombre d'attributs de table imbriquée est potentiellement illimité, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ne fournit pas de liste de valeurs possibles à sélectionner. Vous devez alors taper la valeur exacte.  
  
 Vous pouvez cliquer sur **modifier la requête** pour modifier manuellement l’expression de filtre. Toutefois, si vous modifiez manuellement quelque partie que ce soit d'une expression de filtre, la grille est alors désactivée et vous devez utiliser l'expression de filtre en mode édition de texte uniquement. Pour restaurer le mode de modification de grille, vous devez effacer l'expression de filtre et recommencer.  
  
> [!WARNING]  
>  Vous ne pouvez pas utiliser l'opérateur LIKE dans un filtre de table imbriquée.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Prédiction d’Associations &#40;intermédiaire Didacticiel d’exploration de données&#41;](../../2014/tutorials/predicting-associations-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Syntaxe de filtre et des exemples de modèle &#40;Analysis Services - Exploration de données&#41;](../../2014/analysis-services/data-mining/model-filter-syntax-and-examples-analysis-services-data-mining.md)   
 [Filtres pour les modèles d’exploration de données &#40;Analysis Services - Exploration de données&#41;](../../2014/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)  
  
  