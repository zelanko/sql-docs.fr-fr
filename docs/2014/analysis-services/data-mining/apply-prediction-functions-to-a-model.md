---
title: Appliquer des fonctions de prédiction à un modèle | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Mining Model Prediction [Analysis Services], selecting mining models
ms.assetid: cf9a97e2-c249-441b-af12-c977c1a91c44
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 41c7c447af3eb7e0f40c10b98be827caa59867e0
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66086143"
---
# <a name="apply-prediction-functions-to-a-model"></a>Appliquer des fonctions de prédiction à un modèle
  Pour créer une requête de prédiction, vous devez d'abord sélectionner le modèle d'exploration de données sur lequel la requête sera basée. Vous pouvez sélectionner n'importe quel modèle d'exploration de données existant du projet actuel.  
  
 Après avoir sélectionné un modèle, ajoutez une *fonction de prédiction* à la requête. Il est important de comprendre que les fonctions de prédiction sont utilisées pour à des fins de nombreux-Oui, vous pouvez prédire des valeurs, mais vous pouvez également obtenir des statistiques connexes, ainsi que des informations qui a été utilisées pour générer la prédiction. Les fonctions de prédiction peuvent retourner les types de valeurs suivants :  
  
-   le nom de l'attribut prédictible et la valeur prédite ;  
  
-   des statistiques sur la distribution et la variance des valeurs prédites ;  
  
-   la probabilité du résultat spécifié ou de tous les résultats possibles ;  
  
-   les scores ou valeurs les plus élevés ou les plus faibles ;  
  
-   les valeurs associées à un nœud, un objet ou un attribut spécifié.  
  
 Il existe une grande variété de fonctions de prédiction que vous pouvez utiliser, mais vous devez choisir la fonction adaptée au type de modèle que vous avez créé. Ce choix dépend généralement de l'algorithme utilisé pour créer le modèle.  
  
-   Pour obtenir la liste des fonctions de prédiction prises en charge pour presque tous les types de modèles, consultez [Fonctions de prédiction générales &#40;DMX&#41;](/sql/dmx/general-prediction-functions-dmx).  
  
-   De plus, des algorithmes individuels prennent en charge différentes fonctions spécialisées. Par exemple, si vous créez un modèle d'exploration de données basé sur l'algorithme de gestion de clusters Microsoft, vous pouvez utiliser des fonctions de prédiction spécialisées pour rechercher des informations sur les clusters, telles que la distance d'une valeur de données au centroïde du cluster.  
  
     Pour obtenir des exemples sur l’interrogation d’un type spécifique de modèle d’exploration de données, consultez la rubrique de référence relative aux algorithmes, dans [Algorithmes d’exploration de données &#40;Analysis Services – Exploration de données&#41;](data-mining-algorithms-analysis-services-data-mining.md).  
  
### <a name="choose-a-mining-model-to-use-for-prediction"></a>Choisir un modèle d'exploration de données à utiliser pour la prédiction  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], cliquez avec le bouton droit sur le modèle et sélectionnez **Générer une requête de prédiction**.  
  
     -- OU --  
  
     Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], cliquez sur l’onglet **Prédiction de modèle d’exploration de données**, puis cliquez sur **Sélectionner un modèle** dans la table  **Modèle d’exploration de données** .  
  
2.  Dans la boîte de dialogue **Sélectionner un modèle d’exploration de données** , sélectionnez un modèle d’exploration de données, puis cliquez sur **OK**.  
  
     Vous pouvez choisir n'importe quel modèle dans la base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] actuelle. Pour créer une requête à l'aide d'un modèle se trouvant dans une autre base de données, vous devez soit ouvrir une nouvelle fenêtre de requête dans le contexte de cette base de données, soit ouvrir le fichier solution contenant ce modèle.  
  
### <a name="add-prediction-functions-to-a-query"></a>Ajouter des fonctions de prédiction à une requête  
  
1.  Dans le **Générateur de requêtes de prédiction**, configurez les données d’entrée utilisées pour la prédiction, en fournissant des valeurs dans la boîte de dialogue **Entrée de requête singleton** ou en mappant le modèle à une source de données externe.  
  
     Pour plus d’informations, consultez [Choisir et mapper les données d’entrée pour une requête de prédiction](choose-and-map-input-data-for-a-prediction-query.md).  
  
    > [!WARNING]  
    >  Il n'est pas nécessaire de fournir des entrées pour générer des prédictions. Lorsqu'il n'y a aucune entrée, l'algorithme retourne généralement la valeur prédite la plus probable entre toutes les entrées possibles.  
  
2.  Cliquez sur la colonne **Source** , puis choisissez une valeur dans la liste :  
  
    |||  
    |-|-|  
    |**\<nom du modèle >**|Sélectionnez cette option pour inclure des valeurs du modèle d'exploration de données dans la sortie. Vous pouvez uniquement ajouter des colonnes prédictibles.<br /><br /> Lorsque vous ajoutez une colonne du modèle, le résultat retourné est la liste non distinctive des valeurs se trouvant dans cette colonne.<br /><br /> Les colonnes que vous ajoutez à cette option sont incluses dans la partie SELECT de l'instruction DMX obtenue.|  
    |**Prediction Function**|Sélectionnez cette option pour parcourir une liste de fonctions de prédiction.<br /><br /> Les valeurs ou fonctions que vous sélectionnez sont ajoutées à la partie SELECT de l'instruction DMX obtenue.<br /><br /> La liste des fonctions de prédiction n'est pas filtrée ou limitée par le type de modèle sélectionné. Par conséquent, si vous avez un doute sur la prise en charge, ou non, de la fonction pour le type de modèle actuel, vous pouvez simplement ajouter la fonction à la liste et voir s'il y a une erreur.<br /><br /> Les éléments de la liste qui sont précédés d'un symbole $ (tel que $AdjustedProbability) représentent les colonnes de la table imbriquée qui est produite en sortie lorsque vous utilisez la fonction `PredictHistogram`. Vous trouverez ci-après les raccourcis que vous pouvez utiliser pour retourner une seule colonne, et non une table imbriquée.|  
    |**Expression personnalisée**|Sélectionnez cette option pour taper une expression personnalisée puis affecter un alias à la sortie.<br /><br /> L'expression personnalisée est ajoutée à la partie SELECT de la requête de prédiction DMX obtenue.<br /><br /> Cette option est utile si vous voulez ajouter du texte pour une sortie avec chaque ligne, pour appeler des fonctions VB ou pour appeler des procédures stockées personnalisées.<br /><br /> Pour plus d’informations sur l’utilisation de fonctions VBA et Excel à partir de DMX, consultez [Fonctions VBA dans MDX et DAX](/sql/mdx/vba-functions-in-mdx-and-dax).|  
  
3.  Après avoir ajouté une fonction ou expression, basculez vers la vue DMX pour voir comment la fonction est ajoutée dans l'instruction DMX.  
  
    > [!WARNING]  
    >  Le Générateur de requêtes de prédiction ne valide pas l’instruction DMX tant que vous n’avez pas cliqué sur **Résultats**. Vous constaterez souvent que l'expression qui est produite par le générateur de requêtes n'est pas une instruction DMX valide. Les causes les plus courantes sont la référence à une colonne qui n'est pas liée à la colonne prédictible ou la tentative de prédire une colonne d'une table imbriquée, ce qui requiert une instruction sub-SELECT. À ce stade, vous pouvez basculer vers la vue DMX et continuer à modifier l'instruction.  
  
### <a name="example-create-a-query-on-a-clustering-model"></a>Exemple : Créer une requête sur un modèle de clustering  
  
1.  Si aucun modèle de clustering n’est disponible pour générer cet exemple de requête, créez le modèle, [TM_Clustering], en utilisant le [Didacticiel sur l’exploration de données de base](../../tutorials/basic-data-mining-tutorial.md).  
  
2.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], cliquez avec le bouton droit sur le modèle, [TM_Clustering], puis sélectionnez **Générer une requête de prédiction**.  
  
3.  Dans le menu **Modèle d’exploration de données** , sélectionnez **Requête singleton**.  
  
4.  Dans la boîte de dialogue **Entrée de requête singleton** , définissez les valeurs suivantes comme entrées :  
  
    -   Sexe = M  
  
    -   Distance domicile-travail = 5 à 10 miles  
  
5.  Dans la grille de requête, pour **Source**, sélectionnez le modèle d’exploration de données TM_Clustering, puis ajoutez la colonne [Bike Buyer].  
  
6.  Pour **Source**, sélectionnez **fonction de prédiction**et ajoutez la fonction `Cluster`.  
  
7.  Pour **Source**, sélectionnez **fonction de prédiction**, ajoutez la fonction `PredictSupport`, puis faites glisser la colonne du modèle [Bike Buyer] dans le **critères/Argument** boîte. Tapez **Support** dans la colonne **Alias** .  
  
     Copiez l’expression représentant la fonction de prédiction et la référence de colonne dans la zone **Critères/Argument** .  
  
8.  Pour **Source**, sélectionnez **Expression personnalisée**, tapez un alias, puis référencez la fonction Excel CEILING en utilisant la syntaxe suivante :  
  
    ```  
    Excel![CEILING](<arguments) as <return type>  
    ```  
  
     Collez la référence de colonne comme argument de la fonction.  
  
     Par exemple, l'expression suivante retourne le plafond (CEILING) de la valeur de support :  
  
    ```  
    EXCEL!CEILING(PredictSupport([TM_Clustering].[Bike Buyer]),2)  
    ```  
  
     Tapez CEILING dans la colonne **Alias** .  
  
9. Cliquez sur **Basculer vers l’affichage du texte de la requête** pour vérifier l’instruction DMX qui a été générée, puis cliquez sur **Basculer vers l’affichage du résultat de la requête** pour afficher la sortie des colonnes par la requête de prédiction.  
  
     Le tableau suivant indique les résultats attendus :  
  
    |Bike Buyer|$Cluster|Support|CEILING|  
    |----------------|--------------|-------------|-------------|  
    |0|Cluster 8|954|953.948638926372|  
  
 Si vous souhaitez ajouter d’autres clauses ailleurs dans l’instruction-par exemple, si vous souhaitez ajouter une clause WHERE-vous ne pouvez pas l’ajouter à l’aide de la grille ; Vous devez tout d’abord basculer vers la vue DMX.  
  
## <a name="see-also"></a>Voir aussi  
 [Requêtes d’exploration de données](data-mining-queries.md)  
  
  
