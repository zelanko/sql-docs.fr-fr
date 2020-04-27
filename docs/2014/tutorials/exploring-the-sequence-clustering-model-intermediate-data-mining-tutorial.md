---
title: Exploration du modèle Sequence Clustering (Didacticiel intermédiaire sur l’exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: f8a485d5-47ed-4dd5-bb66-ef4d6d463845
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: e0904239933361b80727700c94b03e379751251f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63164056"
---
# <a name="exploring-the-sequence-clustering-model-intermediate-data-mining-tutorial"></a>Exploration du modèle Sequence Clustering (Didacticiel intermédiaire sur l'exploration de données)
  Maintenant que vous avez créé la **séquence de mise en clusters avec** le modèle Region, vous pouvez l' [!INCLUDE[msCoName](../includes/msconame-md.md)] Explorer à l’aide de la visionneuse Sequence Clustering dans l’onglet **visionneuse de modèle d’exploration** de données du concepteur d’exploration de données. La [!INCLUDE[msCoName](../includes/msconame-md.md)] visionneuse Sequence cluster contient cinq onglets : **diagramme de cluster**, **profils de cluster**, **caractéristiques du cluster**, **ClusterDiscrimination**et **transitions d’État**. Pour plus d’informations sur l’utilisation de cette visionneuse, consultez [Parcourir un modèle à l’aide de Microsoft Sequence Cluster Viewer](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md).  
  
-   [Onglet diagramme de cluster](#bkmk_CDiagram)  
  
-   [Onglet Profils du cluster](#bkmk_CProfiles)  
  
-   [Onglet caractéristiques du cluster](#bkmk_CChars)  
  
-   [Onglet discrimination de cluster](#bkmk_CDiscrim2)  
  
-   [Onglet Transitions d'état](#bkmk_StateTran)  
  
-   [Vue de contenu générique](#bkmk_Generic)  
  
##  <a name="cluster-diagram-tab"></a><a name="bkmk_CDiagram"></a>Onglet diagramme de cluster  
 L’onglet **diagramme de cluster** affiche graphiquement les clusters découverts par l’algorithme dans la base de données. La disposition du diagramme représente les relations entre les clusters. Dans cette présentation, les clusters similaires sont regroupés. Par défaut, la nuance de chaque nœud représente la densité de tous les cas présents dans le cluster : plus le nœud est foncé, plus le nombre de cas qu'il contient est élevé. Vous pouvez changer la signification de la nuance des nœuds afin qu'elle représente la prise en charge, dans chaque nœud, d'un attribut et d'un état.  
  
 Vous pouvez renommer également les clusters pour simplifier l'identification et l'utilisation des clusters cibles. Pour ce didacticiel, vous renommerez le cluster qui a le pourcentage le plus élevé de clients de la région Pacific, et le cluster qui a le plus de cas en général.  
  
> [!NOTE]  
>  Les cas assignés à des clusters spécifiques peuvent changer lorsque vous retraitez le modèle, en fonction des données et des paramètres du modèle. De plus, si vous renommez des clusters, les noms seront perdus lorsque vous retraitez le modèle d'exploration de données.  
  
#### <a name="to-change-the-attribute-used-for-highlighting-clusters"></a>Pour modifier l'attribut utilisé pour mettre en surbrillance des clusters  
  
1.  Dans la liste **variable d’ombrage** , sélectionnez **modèle**.  
  
2.  Sélectionnez **extrémité de cycle** dans la liste **État** .  
  
     Le diagramme est mis à jour pour afficher la concentration du produit sélectionné dans chacun des clusters. Le cluster le plus foncé contient la plus grande densité de casquettes de cyclisme. Vous pouvez modifier la variable d’ombrage pour utiliser n’importe quel état de n’importe quelle colonne d’entrée.  
  
3.  Dans la liste **variable d’ombrage** , sélectionnez **remplissage**.  
  
     Lorsque vous remplacez la variable d'ombrage par remplissage, le diagramme est mis à jour pour comparer les clusters par taille. Le cluster dont l'ombrage est le plus sombre contient davantage de cas que les autres clusters.  
  
#### <a name="to-rename-nodes-in-the-model"></a>Pour renommer des nœuds dans le modèle  
  
1.  Remplacez la **variable** d’ombrage `Region`par, et définissez **State** sur **Pacific**.  
  
2.  Mettez en surbrillance le nœud le plus sombre dans le graphique.  
  
3.  Cliquez avec le bouton droit sur ce cluster et sélectionnez **Renommer le cluster.**  
  
4.  Tapez le nom**Pacific cluster.**  
  
5.  Remplacez la valeur de **variable d’ombrage** par **remplissage**.  
  
6.  Dans le graphique mis à jour, localisez le cluster le plus sombre, qui doit être le plus grand cluster. Si vous ne pouvez pas déterminer en fonction de l'ombrage quel cluster est le plus grand, placez la souris sur chaque cluster et consultez l'info-bulle, puis choisissez le cluster qui contient le plus de cas.  
  
7.  Cliquez avec le bouton droit sur ce cluster et sélectionnez **Renommer le cluster**. Tapez le nouveau nom, `Largest Cluster`.  
  
 Vous pouvez extraire du nœud qui représente le cluster pour consulter le détail des cas qui sont dans chaque cluster. Cela peut être utile si vous souhaitez agir sur les résultats de votre analyse en envoyant par exemple un message électronique à un client. Vous pouvez parcourir également les autres attributs des cas que vous avez inclus dans la structure mais que vous n'avez pas utilisés dans le modèle, tels que Region et IncomeGroup. Pour plus d’informations sur l’extraction des modèles d’exploration de données vers les cas sous-jacents, consultez [requêtes d’extraction &#40;&#41;d’exploration de données ](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md).  
  
#### <a name="to-drill-through-to-details-from-the-cluster-diagram"></a>Pour extraire des détails dans le diagramme Cluster  
  
1.  Cliquez avec le `Pacific Cluster`bouton droit sur, sélectionnez **extraire**, puis sélectionnez **colonnes de structure et de modèle**.  
  
     La boîte de dialogue **extraire** s’ouvre. Les colonnes qui ne sont pas utilisées dans le modèle mais qui sont disponibles pour l’interrogation sont précédées de la **structure**.  
  
     Vous constatez que ce cluster contient principalement des clients de la région Pacific, et seulement quelques clients issus d'autres régions.  
  
2.  Cliquez sur le signe plus dans la colonne imbriquée v Assoc Seq Line Items pour consulter la séquence d'éléments dans une commande particulière.  
  
3.  Fermez la boîte de dialogue **extraire** .  
  
    > [!NOTE]  
    >  Le bouton de **lecture** vous permet de relancer une requête sur les données ; Toutefois, la rerequête ne modifie pas les données affichées, à moins que le modèle ait été mis à jour dynamiquement en arrière-plan par un autre processus.  
  
 [Retour au début](#bkmk_CDiagram)  
  
##  <a name="cluster-profiles-tab"></a><a name="bkmk_CProfiles"></a>Onglet Profils du cluster  
 L’onglet **profils du cluster** affiche les séquences qui se trouvent dans chaque cluster. Les clusters sont répertoriés dans des colonnes individuelles à droite de la colonne **États** .  
  
 Dans la visionneuse, la ligne de **modèle** décrit la distribution globale des éléments d’un cluster, et la ligne **Model. Samples** contient les séquences des éléments. Chaque ligne des séquences de couleurs dans chaque cellule de la ligne **Model. Samples** représente le comportement d’un utilisateur sélectionné de façon aléatoire dans le cluster.  
  
 Chaque couleur dans un histogramme de séquences individuelles représente le modèle d'un produit. La légende d'exploration de données vous montre les séquences de produits à l'aide des codes de couleur et des noms de modèle de produit. Si vous avez ajouté d'autres colonnes au modèle pour le clustering, telles que Region ou Income Group, la visionneuse contiendra une ligne supplémentaire pour chaque colonne qui affiche la distribution de ces valeurs dans chaque cluster.  
  
#### <a name="to-view-the-sequences-that-are-most-common-in-a-cluster"></a>Pour consulter les séquences les plus courantes dans un cluster  
  
1.  Cliquez avec le bouton droit sur la ligne de **modèle** dans la `Largest Cluster`colonne du cluster, puis sélectionnez **afficher la légende**.  
  
     La colonne **couleur** contient une barre ombrée qui indique la fréquence des éléments trouvés dans les séquences. Chaque élément est représenté par une couleur différente. La colonne **signification** répertorie les noms de modèle de produit pour chaque couleur. La colonne **distribution** indique le pourcentage de cas qui contenaient cet élément dans une séquence.  
  
2.  Fermez la **légende d’exploration de données**.  
  
3.  Cliquez avec le bouton droit sur la ligne **Model. Samples** de la colonne avec l’en-tête, **population,** puis sélectionnez **afficher la légende**.  
  
4.  Analyser la liste des séquences dans le modèle global`.`  
  
     La légende d'exploration de données répertorie en premier les séquences les plus courantes, vous pouvez ainsi constater que Mountain Tire Tube est le premier élément dans de nombreuses séquences. Cela signifie qu'un client a de fortes chances d'ajouter Mountain Tire Tube en premier dans son panier.  
  
#### <a name="to-drill-through-to-cases-from-the-cluster-viewer"></a>Pour extraire les cas de la visionneuse de clusters  
  
1.  Faites défiler le volet attribut jusqu’à ce que vous trouviez la ligne de l' `Region` attribut.  
  
     La ligne contient un histogramme pour chaque cluster du modèle, plus un histogramme supplémentaire pour le **remplissage**, ce qui signifie l’ensemble des cas utilisés dans le modèle. Un histogramme est une barre contenant des couleurs différentes, où chaque couleur représente un attribut, et la taille de la section colorée pour cet attribut représente le pourcentage de cas ayant cet attribut.  
  
2.  Comparez les histogrammes pour les clusters que vous avez renommés `Pacific Cluster` et. `Largest Cluster` Chaque cluster apparaît dans une colonne différente.  
  
     Ils présentent tous les deux des couleurs unies, mais les couleurs sont différentes.  
  
3.  Sur la `Region` ligne, placez la souris sur l’histogramme de couleur `Largest Cluster`pour.  
  
     L'info-bulle affiche des valeurs qui affichent les pourcentages réels de cas de chaque région.  
  
4.  Cliquez avec le bouton droit sur l’histogramme `Region` de couleur `Pacific Cluster`de la ligne pour, sélectionnez **extraire**, puis sélectionnez **colonnes de modèle uniquement**.  
  
5.  Déplacez la barre de défilement pour examiner tous les clients dans ce cluster.  
  
     Là encore, l'extraction des détails vous permet de constater que le cluster contient principalement des commandes de la région Pacific, mais également certaines des régions North America et Europe.  
  
6.  Fermez la boîte de dialogue **extraire** .  
  
 [Retour au début](#bkmk_CDiagram)  
  
##  <a name="cluster-characteristics-tab"></a><a name="bkmk_CChars"></a>Onglet caractéristiques du cluster  
 L’onglet **caractéristiques du cluster** résume les transitions entre les États d’un cluster en affichant des barres qui représentent visuellement l’importance de la valeur de l’attribut pour le cluster sélectionné. La colonne **variables** indique ce que le modèle a jugé important pour le cluster ou le remplissage sélectionnés : une valeur particulière ou la relation entre les valeurs, appelée *transition*. La colonne **valeurs** fournit plus de détails sur la valeur ou la transition, et la colonne **probabilité** représente visuellement le poids de cet attribut ou de cette transition.  
  
#### <a name="to-view-the-important-attributes-for-a-cluster"></a>Pour consulter les attributs importants pour un cluster  
  
1.  Dans la **Cluster** liste déroulante cluster `Pacific Cluster`, sélectionnez.  
  
     La liste est mise à jour pour afficher les caractéristiques du cluster que vous avez renommé `Pacific Cluster`. Dans ce cluster, la caractéristique la plus importante `Region`est.  
  
2.  Placez le pointeur de la souris sur la barre ombrée de `Region`la ligne pour.  
  
     La probabilité que la valeur soit Pacific est très élevée. Pour plus d’informations sur la façon d’interpréter ces valeurs, consultez informations techniques de référence sur l' [algorithme Microsoft Sequence Clustering](../../2014/analysis-services/data-mining/microsoft-sequence-clustering-algorithm-technical-reference.md).  
  
3.  Recherchez le cluster dans la liste des caractéristiques du cluster jusqu'à la première ligne de transition.  
  
4.  Une ligne de transition contient la transition de texte dans la colonne **variables** et une combinaison de valeurs d’attribut séquentielles dans la colonne **valeur** . La séquence peut contenir également des points de départ et des valeurs manquantes.  
  
     Par exemple, supposons que la transition ait la valeur, [Start]-> route pneu tube. Cela signifie que les clients dans ce cluster ont fréquemment mis en premier l'élément Road Tire Tube dans leur panier. Cela peut signifier que le produit est un article populaire que les clients recherchent en premier, ou cela peut indiquer uniquement que le produit est facile à localiser sur le site d'achat.  
  
5.  Faites défiler la liste jusqu’à ce que vous trouviez la première transition n’ayant pas **[Start]** ou **absente** .  
  
     Supposons, par exemple, que vous trouviez la transition, le **pneu de randonnée et le tube de randonnée**. Cela signifie que les clients dans ce cluster ont fréquemment acheté ces éléments ensemble, dans cet ordre précis.  
  
6.  Placez la souris sur la barre grisée pour cette transition.  
  
     La probabilité de cette transition s'affiche sous la forme d'un pourcentage.  
  
7.  Dans la liste déroulante **cluster** , sélectionnez **remplissage (tout)**.  
  
     La liste des attributs est mise à jour pour afficher les caractéristiques de toutes les commandes utilisées pour créer le modèle. Dans ce modèle d’exploration de données, la caractéristique la plus importante pour la distinction `Region`entre les clusters est, avec une valeur de **Amérique du Nord**.  
  
 Après avoir examiné ces tâches, vous pouvez faire un double constat. Le premier est que vous avez besoin de beaucoup de données pour obtenir un nombre pertinent de combinaisons. Par exemple, les séquences avec les probabilités les plus élevées sont susceptibles d’inclure un état **[Démarrer]** ou **manquant** .  
  
 Le deuxième est qu’il y a un effet de clustering élevé sur `Region`les attributs pour, ce qui rend plus difficile la vue des groupes de séquences. Par conséquent, vous décidez de créer un autre modèle qui utilise uniquement des séquences sans inclure les colonnes pour la région ou le revenu.  
  
 [Retour au début](#bkmk_CDiagram)  
  
##  <a name="cluster-discrimination-tab"></a><a name="bkmk_CDiscrim2"></a>Onglet discrimination de cluster  
 L’onglet **discrimination de cluster** vous permet de comparer deux clusters, afin de déterminer les attributs qui distinguent un cluster particulier d’un autre cluster. L’onglet contient quatre colonnes : **variables**, **valeurs**, **cluster 1**et **cluster 2**.  Vous pouvez choisir n’importe quel cluster à utiliser comme **cluster 1** et **cluster 2**.  
  
 La colonne **variables** indique le nom de l’attribut, qui peut être un nom de colonne ou une combinaison de nom de colonne et de la **transition**de mot. La colonne **valeurs** indique la valeur exacte de l’attribut ou de la transition. Les barres ombrées dans les colonnes pour **cluster 1** et **cluster 2** indiquent la force de l’attribut dans les clusters que vous comparez. Plus la barre est longue, plus grande est la probabilité que le cluster inclus des cas avec cet attribut.  
  
#### <a name="to-compare-two-clusters-by-using-the-cluster-discrimination-tab"></a>Pour comparer deux clusters à l'aide de l'onglet Discrimination de cluster  
  
1.  Dans l’onglet **discrimination de cluster** , pour **cluster 1**, `Pacific Cluster`sélectionnez.  
  
     Par défaut, la sélection pour **cluster 2** change en **complément du cluster Pacific**.  
  
     L’attribut Top qui distingue `Pacific Cluster` tous les autres cas est la région. La région est un attribut si fort pour le clustering qu'il masque d'autres attributs. Pour éviter cet effet, essayez de comparer plusieurs des clusters plus petits entre eux. Dans ce cas, la liste des attributs change et peut inclure plus de transitions entre les modèles.  
  
2.  Localisez une ligne de transition et placez la souris sur la barre grisée.  
  
     Les éléments de la colonne **valeurs** peuvent inclure des États et des transitions. L'ombrage de chaque élément indique le score de discrimination. Pour en savoir plus sur la signification des différents scores, consultez [Mining Model Content for Sequence Clustering models &#40;Analysis Services-data mining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-sequence-clustering-models.md).  
  
 [Retour au début](#bkmk_CDiagram)  
  
##  <a name="state-transitions-tab"></a><a name="bkmk_StateTran"></a>Onglet transitions d’État  
 Sous l’onglet **transitions d’État** , vous pouvez sélectionner un cluster et parcourir ses transitions d’État. Si vous sélectionnez **remplissage (tout)** dans la liste déroulante cluster, le diagramme affiche la distribution des États pour l’ensemble du modèle d’exploration de données.  
  
 Chaque nœud dans le graphique représente un état, ou une valeur possible, des séquences que vous essayez d'analyser. La couleur d'arrière-plan des nœuds représente la fréquence de cet état. Les lignes connectent des états et indiquent une transition entre des états. Vous pouvez déplacer le curseur vers le haut ou le bas pour modifier le seuil de probabilité pour les transitions. Des nombres sont associés à certains nœuds et indiquent la probabilité de cet état.  
  
#### <a name="to-explore-the-relationships-in-the-state-transition-tab"></a>Pour explorer les relations dans l'onglet Transitions d'état  
  
1.  Dans l’onglet **transitions d’État** de la visionneuse de modèle `Pacific Cluster` d’exploration de données, sélectionnez dans la liste des clusters. Assurez-vous que l’option **afficher les étiquettes Edge** est sélectionnée.  
  
     Le graphique est mis à jour pour afficher les transitions les plus courantes dans ce cluster.  
  
2.  Cliquez sur un nœud connecté par une ligne à un autre nœud.  
  
     Le graphique est mis à jour et met en surbrillance les nœuds connexes. La valeur numérique en regard de la ligne indique la probabilité de la transition.  
  
3.  Augmentez le curseur jusqu’à **tous les liens**, pour augmenter le nombre de transitions incluses dans le graphique.  
  
4.  Sélectionnez **remplissage (tout)** à partir du **cluster**.  
  
     Notez que lorsque vous chargez un cluster différent, le graphique réinitialise les paramètres d'affichage par défaut, donc le contrôle Slider est réinitialisé à la position centrale.  
  
5.  Cliquez sur le nœud le plus sombre dans le graphique, qui doit être **Sport-100**.  
  
     Notez qu'il n'y a pas de lignes qui connectent ce produit à d'autres produits.  
  
6.  Remontez le curseur d'une étape pour augmenter le nombre de transitions incluses dans le graphique. N’allez pas encore accéder à **tous les liens** .  
  
     Le graphique est mis à jour en ajoutant plusieurs transitions supplémentaires au graphique, mais aucune qui inclut le modèle Sport-100.  
  
7.  Déplacez le contrôle Slider jusqu’à **tous les liens**. Cliquez sur le nœud Sport-100 s'il n'est pas déjà sélectionné.  
  
     Le graphique est mis à jour pour afficher de nombreuses transitions qui incluent le produit Sport-100. La direction de la flèche sur la ligne de connexion indique si l'élément Sport-100 a été sélectionné comme le premier élément ou le deuxième élément dans la paire.  
  
8.  Cliquez sur le nœud pour Touring Tire et ramenez le contrôle Slider à la position centrale.  
  
     Au départ, il existe de nombreuses lignes de transition connectant le pneu à d’autres produits. Toutefois, lorsque vous augmentez le seuil de probabilité, les transitions moins probables sont éliminées du graphique, ce qui laisse simplement la transition, le pneu de randonnée > tube de randonnée. Cette transition signifie que si un client ajoute un élément Touring Tire (pneu de vélo) dans son panier, la probabilité qu'il ajoute ensuite un élément Touring Tire Tube (chambre à air de vélo) est forte.  
  
 [Retour au début](#bkmk_CDiagram)  
  
##  <a name="generic-content-tree-viewer"></a><a name="bkmk_Generic"></a>Visionneuse de l’arborescence de contenu générique  
 Cette visionneuse peut être utilisée pour tous les modèles, quels que soient l'algorithme ou le type de modèle. La **visionneuse de l’arborescence de contenu MicrosoftGeneric** est disponible dans la liste déroulante **visionneuse** .  
  
 Un arbre de contenu est une représentation de n'importe quel modèle d'exploration de données sous la forme d'une série de nœuds, où chaque nœud représente ce qui a été appris sur certaines données d'apprentissage. Le nœud peut contenir un modèle, un ensemble de règles, un cluster ou la définition d'une plage de dates qui partagent certains attributs. Le contenu exact du nœud diffère en fonction de l'algorithme et de l'attribut prédictible, mais la représentation générale du contenu reste la même.  
  
 Vous pouvez développer chaque nœud pour voir des informations de plus en plus détaillées et copier le contenu de n'importe quel nœud vers le Presse-papiers. Pour plus d’informations, consultez [Explorer un modèle à l’aide de la visionneuse de l’arborescence de contenu générique Microsoft](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-generic-content-tree-viewer.md).  
  
#### <a name="to-view-details-for-a-sequence-clustering-model-by-using-the-generic-content-tree-viewer"></a>Pour consulter des détails pour un modèle Sequence Clustering à l'aide de la Visionneuse de l'arborescence de contenu générique  
  
1.  Dans l’onglet **visionneuse de modèle d’exploration de données** , cliquez sur la liste **visionneuse** , puis sélectionnez **visionneuse de l’arborescence de contenu générique Microsoft**.  
  
2.  Dans le volet **légende du nœud** , `Pacific Cluster (1)`cliquez sur.  
  
     Le nom de ce nœud contient à la fois le nom convivial que vous avez assigné au cluster et l'ID de nœud sous-jacent. Vous pouvez utiliser les ID de nœud pour extraire les détails supplémentaires dans le modèle.  
  
3.  Développez le premier nœud enfant, nommé **niveau de séquence pour cluster 1**.  
  
     Le nœud de niveau séquence pour un cluster contient des détails relatifs aux états et transitions inclus dans ce cluster. Vous pouvez utiliser ces détails, disponibles dans la colonne NODE_DISTRIBUTION pour explorer les séquences et les états pour chaque cluster ou pour le modèle.  
  
4.  Continuez à développer des nœuds et consulter les détails dans le volet de visionneuse HTML.  
  
 Pour plus d’informations sur le contenu du modèle d’exploration de données et sur la façon d’utiliser les détails dans la visionneuse, consultez [Mining Model Content for Sequence Clustering models &#40;Analysis Services-data mining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-sequence-clustering-models.md).  
  
 [Retour au début](#bkmk_CDiagram)  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Création d’un modèle de clustering séquencé associé &#40;didacticiel sur l’exploration de données intermédiaire&#41;](../../2014/tutorials/creating-a-related-sequence-clustering-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Algorithme Microsoft Sequence Clustering](../../2014/analysis-services/data-mining/microsoft-sequence-clustering-algorithm.md)   
 [Sequence Clustering Model Query Examples](../../2014/analysis-services/data-mining/sequence-clustering-model-query-examples.md)  
  
  
