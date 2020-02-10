---
title: Création d’une structure et d’un modèle de réseau neuronal (Didacticiel intermédiaire sur l’exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- discretization [Analysis Services]
- DISCRETIZED column
- DiscretizationBuckets property
- DiscretizationMethod property
- EQUAL_AREAS method
ms.assetid: 3f16215c-531e-4ecf-a11f-ee7c6a764463
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 6787db165770f944838a312ecd3e0386d161da38
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62856330"
---
# <a name="creating-a-neural-network-structure-and-model-intermediate-data-mining-tutorial"></a>Création d'une structure et d'un modèle de réseau neuronal (Didacticiel sur l'exploration de données intermédiaire)
  Pour créer un modèle d'exploration de données, vous devez d'abord utiliser l'Assistant Exploration de données pour créer une nouvelle structure d'exploration de données basée sur la nouvelle vue de source de données. Au cours de cette tâche, vous allez utiliser cet Assistant pour créer une structure d'exploration de données ainsi qu'un modèle d'exploration de données associé basé sur l'algorithme MNN ([!INCLUDE[msCoName](../includes/msconame-md.md)] Neural Network).  
  
 Les réseaux neuronaux sont extrêmement flexibles et peuvent analyser de nombreuses combinaisons d'entrées et de sorties ; vous devez donc essayer plusieurs façons de traiter les données pour obtenir des résultats optimaux. Par exemple, vous pouvez personnaliser la façon dont la cible numérique pour la qualité de service est *Binned (*, ou regroupée, pour cibler des besoins spécifiques de l’entreprise. Pour ce faire, vous allez ajouter une nouvelle colonne à la structure d'exploration de données qui regroupe les données numériques de façon différente, puis vous allez créer un modèle qui utilise la nouvelle colonne. Vous allez utiliser ces modèles d'exploration de données pour effectuer une exploration de données.  
  
 Enfin, lorsque vous aurez appris à partir du modèle de réseau neuronal quels sont les facteurs ayant l'impact le plus important pour votre question pratique, vous pourrez générer un modèle distinct de prédiction et de calcul de score. Vous utiliserez l'algorithme MLR ([!INCLUDE[msCoName](../includes/msconame-md.md)]) qui se base sur le modèle de réseaux neuronaux mais qui est optimisé pour la recherche d'une solution axée sur des entrées spécifiques.  
  
 **Étapes**  
  
 [Créer la structure et le modèle d'exploration de données par défaut](#bkmk_defaul)  
  
 [Utiliser la discrétisation pour placer la colonne prédictible dans un conteneur](#bkmk_ColumnCopy)  
  
 [Copier la colonne et modifier la méthode de discrétisation pour un autre modèle](#bkmk_Alias)  
  
 [Créer un alias pour la colonne prédictible afin que vous puissiez comparer les modèles](#bkmk_Alias2)  
  
 [Traiter tous les modèles](#bkmk_SeedProcess)  
  
## Créer la structure de centre d’appels par défaut<a name="bkmk_defaul"></a>  
  
1.  Dans Explorateur de solutions dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], cliquez avec le bouton droit sur **structures d’exploration de données** et sélectionnez **nouvelle structure d’exploration de données**.  
  
2.  Dans la page **Assistant Exploration de données** , cliquez sur **Suivant**.  
  
3.  Sur la page **Sélectionner la méthode de définition** , vérifiez que **à partir de la base de données relationnelle ou de l’entrepôt de données existant** est sélectionné, puis cliquez sur **suivant**.  
  
4.  Dans la page **créer la structure d’exploration de données** , vérifiez que l’option **créer une structure d’exploration de données avec un modèle d’exploration** de données est sélectionnée.  
  
5.  Cliquez sur la liste déroulante de l’option **quelle technique d’exploration de données voulez-vous utiliser ?**, puis sélectionnez **réseaux neuronaux Microsoft**.  
  
     Les modèles de régression logistique étant basés sur les réseaux neuronaux, vous pouvez réutiliser la même structure et ajouter un nouveau modèle d'exploration de données.  
  
6.  Cliquez sur **Suivant**.  
  
     La page **Sélectionner une vue de source de données** s’affiche.  
  
7.  Sous **vues de sources de données disponibles**, sélectionnez `Call Center`, puis cliquez sur **suivant**.  
  
8.  Dans la page **spécifier les types des tables** , activez la case à cocher **cas** en regard de la table **FactCallCenter** . Ne sélectionnez rien pour **DimDate**. Cliquez sur **Suivant**.  
  
9. Dans la page **spécifier les données d’apprentissage** , sélectionnez **clé** en regard de la colonne **FactCallCenterID.**  
  
10. Activez les `Predict` cases à cocher et **d’entrée** .  
  
11. Sélectionnez la **clé**, l' **entrée**et `Predict` les cases à cocher comme indiqué dans le tableau suivant :  
  
    |Tables/Colonnes|Clé/Entrée/Prédire|  
    |---------------------|-------------------------|  
    |AutomaticResponses|Entrée|  
    |AverageTimePerIssue|Entrée/Prédire|  
    |Calls|Entrée|  
    |DateKey|Ne pas utiliser|  
    |DayOfWeek|Entrée|  
    |FactCallCenterID|Clé|  
    |IssuesRaised|Entrée|  
    |LevelOneOperators|Entrée/Prédire|  
    |LevelTwoOperators|Entrée|  
    |Commandes|Entrée/Prédire|  
    |ServiceGrade|Entrée/Prédire|  
    |Shift|Entrée|  
    |TotalOperators|Ne pas utiliser|  
    |WageType|Entrée|  
  
     Notez que plusieurs colonnes prédictibles ont été sélectionnées. L'une des forces de l'algorithme de réseau neuronal réside dans sa possibilité à analyser toutes les combinaisons possibles des attributs d'entrée et de sortie. Vous ne souhaitez pas effectuer cette opération pour un jeu de données volumineux, car cela peut augmenter de façon exponentielle le temps de traitement.  
  
12. Dans la page **spécifier le type de contenu et de données des colonnes** , vérifiez que la grille contient les colonnes, les types de contenu et les types de données, comme indiqué dans le tableau suivant, puis cliquez sur **suivant**.  
  
    |Colonnes|Type de contenu|Types de données|  
    |-------------|------------------|----------------|  
    |AutomaticResponses|Continue|Long|  
    |AverageTimePerIssue|Continue|Long|  
    |Calls|Continue|Long|  
    |DayOfWeek|Discret|Texte|  
    |FactCallCenterID|Clé|Long|  
    |IssuesRaised|Continue|Long|  
    |LevelOneOperators|Continue|Long|  
    |LevelTwoOperators|Continue|Long|  
    |Commandes|Continue|Long|  
    |ServiceGrade|Continue|Double|  
    |Shift|Discret|Texte|  
    |WageType|Discret|Texte|  
  
13. Sur la page **créer un jeu de test** , désactivez la zone de texte correspondant à l’option, **pourcentage de données à tester**. Cliquez sur **Suivant**.  
  
14. Dans la page **fin de l’Assistant** , pour **nom**de la structure d' `Call Center`exploration de données, tapez.  
  
15. Pour le **nom du modèle**d’exploration `Call Center Default NN`de données, tapez, puis cliquez sur **Terminer**.  
  
     La zone **autoriser l’extraction** est désactivée, car vous ne pouvez pas extraire des données avec des modèles de réseau neuronal.  
  
16. Dans Explorateur de solutions, cliquez avec le bouton droit sur le nom de la structure d’exploration de données que vous venez de créer, puis sélectionnez **traiter**.  
  
## <a name="use-discretization-to-bin-the-target-column"></a>Utiliser la discrétisation pour placer la colonne cible dans un conteneur  
 Par défaut, lorsque vous créez un modèle de réseau neuronal qui a un attribut prédictible numérique, l'algorithme MNN (Microsoft Neural Network) traite cet attribut comme un nombre continu. Par exemple, l'attribut ServiceGrade est un nombre qui, théoriquement, est compris entre 0.00 (tous les appels font l'objet d'une réponse) et 1.00 (tous les appelants raccrochent). Dans ce jeu de données, les valeurs sont distribuées de la façon suivante :  
  
 ![distribution de valeurs de niveau de service](../../2014/tutorials/media/skt-service-grade-valuesc.gif "distribution de valeurs de niveau de service")  
  
 En conséquence, lorsque vous traitez le modèle, les sorties peuvent ne pas être regroupées comme vous le souhaitez. Par exemple, si vous utilisez le clustering pour identifier les meilleurs groupes de valeurs, l’algorithme divise les valeurs de ServiceGrade en plages telles que celle-ci : 0,0748051948-0.09716216215. Bien que ce regroupement soit mathématiquement exact, il est possible que ce type de plage ne soit pas aussi explicite pour les utilisateurs professionnels.  
  
 Dans cette étape, pour rendre le résultat plus intuitif, vous regroupez les valeurs numériques différemment, en créant des copies de la colonne de données numériques.  
  
### <a name="how-discretization-works"></a>Fonctionnement de la discrétisation  
 Analysis Services fournit plusieurs méthodes pour le traitement des données numériques ou leur placement dans un conteneur. Le tableau suivant illustre les différences qui existent entre les résultats lorsque l'attribut de sortie ServiceGrade est traité de trois manières différentes :  
  
-   en le traitant comme un nombre continu ;  
  
-   en ayant le clustering d'utilisation d'algorithme pour identifier le meilleur arrangement des valeurs ;  
  
-   en spécifiant que les nombres doivent être placés dans un conteneur par la méthode EQUAL_AREAS (zones équivalentes).  
  
 Modèle par défaut (continu)  
  
|VALEUR|SUPPORT|  
|-----------|-------------|  
|Manquant|0|  
|0,09875|120|  
  
 Placement dans un conteneur par clustering  
  
|VALEUR|SUPPORT|  
|-----------|-------------|  
|\<0,0748051948|34|  
|0,0748051948-0.09716216215|27|  
|0.09716216215-0.13297297295|39|  
|0.13297297295 - 0.167499999975|10|  
|>= 0.167499999975|10|  
  
 Placement dans un conteneur par zones équivalentes  
  
|VALEUR|SUPPORT|  
|-----------|-------------|  
|\<0,07|26|  
|0,07-0,00|22|  
|0,09-0,11|36|  
|>= 0,12|36|  
  
> [!NOTE]  
>  Vous pouvez obtenir ces statistiques à partir du nœud des statistiques marginales du modèle, une fois que toutes les données ont été traitées. Pour plus d’informations sur le nœud de statistiques marginales, consultez [Mining Model Content for Neuron Network models &#40;Analysis Services-data mining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-neural-network-models-analysis-services-data-mining.md).  
  
 Dans cette table, la colonne VALUE montre la manière dont le nombre de ServiceGrade a été traité. La colonne SUPPORT indique le nombre de cas ayant eu cette valeur, ou qui sont tombés dans cette plage.  
  
-   **Utilisez les nombres continus (valeur par défaut)**  
  
     Si vous avez utilisé la méthode par défaut, l'algorithme calcule des résultats pour 120 valeurs distinctes, dont la valeur moyenne est 0,09875. Vous pouvez également consulter le nombre de valeurs manquantes.  
  
-   **Emplacement par clustering**  
  
     Lorsque vous laissez l'algorithme de clustering Microsoft déterminer le regroupement facultatif des valeurs, l'algorithme regrouperait les valeurs de ServiceGrade en cinq (5) plages. Le nombre de cas dans chaque plage n'est pas distribué uniformément, comme vous pouvez voir dans la colonne Support.  
  
-   **Emplacement par zone égale**  
  
     Lorsque vous choisissez cette méthode, l'algorithme force les valeurs dans des compartiments de taille égale qui modifie tour à tour les limites supérieure et inférieure de chaque plage. Vous pouvez spécifier le nombre de compartiments, mais vous éviterez d'avoir deux valeurs manquantes dans chaque compartiment.  
  
 Pour plus d’informations sur les options compartimentage, consultez [méthodes de discrétisation &#40;&#41;d’exploration de données ](../../2014/analysis-services/data-mining/discretization-methods-data-mining.md).  
  
 Au lieu d’utiliser les valeurs numériques, vous pouvez également ajouter une colonne dérivée distincte qui classifie les notes de service en plages cibles prédéfinies, telles que **Best** ( \<ServiceGrade = 0,05), **Acceptable** (0,10 > ServiceGrade > 0,05) et **médiocre** (ServiceGrade >= 0,10).  
  
###  <a name="bkmk_newColumn"></a>Créer une copie d’une colonne et modifier la méthode de discrétisation  
 Vous allez effectuer une copie de la colonne d’exploration de données qui contient l’attribut cible, ServiceGrade et modifier la façon dont les nombres sont regroupés. Vous pouvez créer plusieurs copies d'une colonne d'une structure d'exploration de données, y compris de l'attribut prédictible.  
  
 Pour ce didacticiel, vous allez utiliser la méthode EQUAL_AREAS de discrétisation et spécifier quatre compartiments. Les regroupements qui résultent de cette méthode sont très proches des valeurs cibles présentant un intérêt pour les utilisateurs professionnels.  
  
####  <a name="bkmk_ColumnCopy"></a>Pour créer une copie personnalisée d’une colonne dans la structure d’exploration de données  
  
1.  Dans l'Explorateur de solutions, double-cliquez sur la structure d'exploration de données que vous venez de créer.  
  
2.  Sous l’onglet structure d’exploration de données, cliquez sur **Ajouter une colonne de structure d’exploration de données**.  
  
3.  Dans la boîte de dialogue **Sélectionner la colonne** , sélectionnez ServiceGrade dans la liste de la **colonne source**, puis cliquez sur **OK**.  
  
     Une nouvelle colonne est ajoutée à la liste des colonnes de structure d'exploration de données. Par défaut, la nouvelle colonne d'exploration de données porte le même nom que la colonne existante, avec une valeur numérique finale en plus : par exemple, ServiceGrade 1. Vous pouvez modifier le nom de cette colonne afin de le rendre plus descriptif.  
  
     Vous devez également spécifier la méthode de discrétisation.  
  
4.  Cliquez avec le bouton droit sur ServiceGrade 1, puis sélectionnez **Propriétés**.  
  
5.  Dans la fenêtre **Propriétés** , recherchez la propriété **Name** , puis remplacez le nom par **service grade Binned (** .  
  
6.  Une boîte de dialogue s'affiche en vous demandant si vous souhaitez apporter la même modification au nom de toutes les colonnes de modèle d'exploration de données connexe. Cliquez sur **Non**.  
  
7.  Dans la fenêtre **Propriétés** , recherchez la section **type de données** et développez-la si nécessaire.  
  
8.  Remplacez la valeur `Content` de la propriété `Continuous` par `Discretized`.  
  
     Les propriétés suivantes sont maintenant disponibles. Modifiez les valeurs des propriétés comme indiqué dans le tableau suivant :  
  
    |Propriété|Valeur par défaut|Nouvelle valeur|  
    |--------------|-------------------|---------------|  
    |`DiscretizationMethod`|`Continuous`|`EqualAreas`|  
    |`DiscretizationBucketCount`|Aucune valeur|4|  
  
    > [!NOTE]  
    >  La valeur par défaut de <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> est en fait 0, ce qui signifie que l'algorithme détermine automatiquement le nombre optimal de compartiments. Par conséquent, si vous voulez réinitialiser la valeur par défaut de cette propriété, tapez 0.  
  
9. Dans le concepteur d’exploration de données, cliquez sur l’onglet **modèles d’exploration** de données.  
  
     Notez que lorsque vous ajoutez une copie d'une colonne de structure d'exploration de données, l'indicateur d'utilisation de la copie a automatiquement la valeur `Ignore`. En règle générale, lorsque vous ajoutez une copie d'une colonne à une structure d'exploration de données, vous ne devez pas utiliser la copie conjointement avec la colonne d'origine à des fins d'analyse ; sinon, l'algorithme trouvera une forte corrélation entre les deux colonnes, ce qui risque de masquer d'autres relations.  
  
##  <a name="bkmk_NewModel"></a>Ajouter un nouveau modèle d’exploration de données à la structure d’exploration de données  
 À présent que vous avez créé un regroupement pour l'attribut cible, vous devez ajouter un nouveau modèle d'exploration de données qui utilise la colonne discrétisée. Une fois que vous aurez terminé, la structure d'exploration de données CallCenter disposera de deux modèles d'exploration de données :  
  
-   Le modèle d'exploration de données, Call Center Default NN (Centre d'appels par défaut NN), gère les valeurs ServiceGrade sous forme de plage continue.  
  
-   Vous allez créer un nouveau modèle d’exploration de données, le centre d’appels Binned (NN, qui utilise comme cible pour les valeurs de la colonne ServiceGrade, distribuées en quatre compartiments de taille égale.  
  
#### <a name="to-add-a-mining-model-based-on-the-new-discretized-column"></a>Pour ajouter un modèle d'exploration de données basé sur la nouvelle colonne discrétisée  
  
1.  Dans Explorateur de solutions, cliquez avec le bouton droit sur la structure d’exploration de données que vous venez de créer, puis sélectionnez **ouvrir**.  
  
2.  Cliquez sur l'onglet **Modèles d'exploration de données** .  
  
3.  Cliquez sur **créer un modèle d’exploration de données connexe**.  
  
4.  Dans la boîte de dialogue **nouveau modèle d’exploration de données** , pour `Call Center Binned NN`nom du **modèle**, tapez. Dans la liste déroulante nom de l' **algorithme** , sélectionnez **Microsoft neuronal Network**.  
  
5.  Dans la liste des colonnes contenues dans le nouveau modèle d'exploration de données, localisez ServiceGrade, puis remplacez l'indicateur d'utilisation `Predict` par `Ignore`.  
  
6.  De même, localisez ServiceGrade Binned (ServiceGrade placé dans un conteneur), puis remplacez l'indicateur d'utilisation `Ignore` par `Predict`.  
  
##  <a name="bkmk_Alias2"></a>Créer un alias pour la colonne cible  
 D'ordinaire, vous ne pouvez pas comparer des modèles d'exploration de données qui utilisent des attributs prédictibles différents. Toutefois, vous pouvez créer un alias pour une colonne de modèle d'exploration de données. Autrement dit, vous pouvez renommer la colonne ServiceGrade Binned (dans le modèle d’exploration de données afin qu’elle porte le même nom que la colonne d’origine. Vous pouvez ensuite comparer directement ces deux modèles dans un graphique d'analyse de précision, même si les données sont discrétisées de manière différente.  
  
###  <a name="bkmk_Alias"></a>Pour ajouter un alias pour une colonne de structure d’exploration de données dans un modèle d’exploration de données  
  
1.  Sous l’onglet **modèles d’exploration de données** , sous **structure**, sélectionnez ServiceGrade Binned (.  
  
     Notez que la fenêtre **Propriétés** affiche les propriétés de l’objet ScalarMiningStructureColumn colonne.  
  
2.  Sous la colonne du modèle d'exploration de données, ServiceGrade Binned NN (ServiceGrade placé dans un conteneur NN), cliquez sur la cellule correspondant à la colonne ServiceGrade Binned (ServiceGrade placé dans un conteneur).  
  
     Notez que, à présent, la fenêtre **Propriétés** affiche les propriétés de l’objet, MiningModelColumn.  
  
3.  Recherchez la propriété **Name** et remplacez la valeur par `ServiceGrade`.  
  
4.  Recherchez la propriété **Description** et tapez **alias de colonne temporaire**.  
  
     La fenêtre **Propriétés** doit contenir les informations suivantes :  
  
    |Propriété|Valeur|  
    |--------------|-----------|  
    |**Description**|Temporary column alias (Alias de colonne temporaire)|  
    |**IDENTIFI**|ServiceGrade Binned (|  
    |**Indicateurs de modélisation**||  
    |**Nom**|Service Grade (Niveau de service)|  
    |**ID SourceColumn**|Service Grade 1 (Niveau de service 1)|  
    |**Utilisation**|Prédire|  
  
5.  Cliquez n’importe où dans l’onglet **modèle d’exploration de données** .  
  
     La grille est mise à jour pour afficher le nouvel alias de `ServiceGrade`colonne temporaire,, en regard de l’utilisation de la colonne. La grille contenant la structure d'exploration de données et deux modèles d'exploration de données doit ressembler à ce qui suit :  
  
    |Structure|Call Center Default NN|Call Center Binned NN (Centre d'appels placé dans un conteneur NN)|  
    |---------------|----------------------------|---------------------------|  
    ||Microsoft Neural Network|Microsoft Neural Network|  
    |AutomaticResponses|Entrée|Entrée|  
    |AverageTimePerIssue|Prédire|Prédire|  
    |Calls|Entrée|Entrée|  
    |DayOfWeek|Entrée|Entrée|  
    |FactCallCenterID|Clé|Clé|  
    |IssuesRaised|Entrée|Entrée|  
    |LevelOneOperators|Entrée|Entrée|  
    |LevelTwoOperators|Entrée|Entrée|  
    |Commandes|Entrée|Entrée|  
    |ServiceGrade Binned (ServiceGrade placé dans un conteneur)|Ignorer|Prédire (ServiceGrade)|  
    |ServiceGrade|Prédire|Ignorer|  
    |Shift|Entrée|Entrée|  
    |TotalOperators|Entrée|Entrée|  
    |WageType|Entrée|Entrée|  
  
## <a name="process-all-models"></a>Traiter tous les modèles  
 Pour terminer, afin de vous assurer que les modèles créés sont facilement comparables, vous devez définir le paramètre de valeur initiale pour le modèle par défaut et le modèle placé dans un conteneur. La définition d'une valeur initiale permet de garantir que chaque modèle débutera le traitement des données à partir du même point.  
  
> [!NOTE]  
>  Si vous ne spécifiez pas de valeur numérique pour le paramètre de valeur initiale, SQL Server Analysis Services générera une valeur initiale basée sur le nom du modèle. Puisque les modèles ont toujours des noms différents, vous devez définir une valeur initiale afin de garantir qu'ils traitent les données dans le même ordre.  
  
###  <a name="bkmk_SeedProcess"></a>Pour spécifier la valeur initiale et traiter les modèles  
  
1.  Dans l’onglet **modèle d’exploration de données** , cliquez avec le bouton droit sur la colonne du modèle nommé Call Center-LR, puis sélectionnez définir les paramètres d' **algorithme**.  
  
2.  Dans la ligne correspondant au paramètre HOLDOUT_SEED, cliquez sur la cellule vide sous **valeur**, puis `1`tapez. Cliquez sur **OK**. Répétez cette étape pour chaque modèle associé à la structure.  
  
    > [!NOTE]  
    >  La valeur que vous choisissez comme valeur initiale n'a pas d'importance tant que vous utilisez la même valeur initiale pour tous les modèles associés.  
  
3.  Dans le menu **modèles d’exploration de données** , sélectionnez traiter l' **exploration de données et tous les modèles**. Cliquez sur **Oui** pour déployer le projet d’exploration de données mis à jour sur le serveur.  
  
4.  Dans la boîte de dialogue **traiter le modèle d’exploration de données** , cliquez sur **exécuter**.  
  
5.  Cliquez sur **Fermer** pour fermer la boîte de dialogue **État d’avancement du traitement** , puis cliquez de nouveau sur **Fermer** dans la boîte de dialogue traiter le modèle d' **exploration de données** .  
  
 Une fois que vous avez créé les deux modèles d'exploration de données connexes, vous devez explorer les données pour identifier les relations qui existent entre ces dernières.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Exploration du modèle de centre d’appels &#40;didacticiel sur l’exploration de données intermédiaire&#41;](../../2014/tutorials/exploring-the-call-center-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Structures d’exploration de données &#40;Analysis Services d’exploration de données&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)  
  
  
