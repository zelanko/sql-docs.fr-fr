---
title: Création de prédictions pour les modèles de centre d’appels (didacticiel d’exploration de données intermédiaire) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 5be0cec7-f639-4eeb-835e-e3204ae619e9
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 30f24ab457669f572189d2eb13deca3f672f5e18
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63217884"
---
# <a name="creating-predictions-for-the-call-center-models-intermediate-data-mining-tutorial"></a>Création de prédictions pour les modèles de centre d'appels (Didacticiel sur l'exploration de données intermédiaire)
  Maintenant que vous en savez plus sur les interactions entre les équipes, le nombre d'opérateurs, les appels et le niveau de service, vous êtes prêt à créer des requêtes de prédiction qui peuvent être utilisées dans l'analyse commerciale et la planification. Vous allez d'abord créer des prédictions sur le modèle exploratoire afin de tester des hypothèses. Ensuite, vous allez créer des prédictions en bloc en utilisant le modèle de régression logistique.  
  
 Cette leçon suppose que vous soyez déjà au fait du concept des requêtes de prédiction.  
  
## <a name="creating-predictions-using-the-neural-network-model"></a>Création de prédictions à l'aide du modèle de réseau neuronal  
 L'exemple suivant montre comment élaborer une prédiction singleton à l'aide du modèle de réseau neuronal créé pour l'exploration. Les prédictions singleton représentent une méthode efficace pour essayer des valeurs différentes afin de voir l'effet dans le modèle. Dans ce scénario, vous allez prédire le niveau de service de l'équipe de nuit (midnight) (sans spécification d'un jour de la semaine) si six opérateurs expérimentés sont de service.  
  
#### <a name="to-create-a-singleton-query-by-using-the-neural-network-model"></a>Pour créer une requête singleton à l'aide du modèle de réseau neuronal  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez la solution qui contient le modèle à utiliser.  
  
2.  Dans le Concepteur d’exploration de données, cliquez sur le **prévision de modèle d’exploration de données** onglet.  
  
3.  Dans le **Mining Model** volet, cliquez sur **sélectionner un modèle**.  
  
4.  Le **sélectionner un modèle d’exploration de données** boîte de dialogue affiche une liste de structures d’exploration de données. Développez la structure d'exploration de données pour afficher la liste des modèles d'exploration de données qui lui sont associés.  
  
5.  Développez la structure d'exploration de données Call Center Default (Centre d'appels par défaut), puis sélectionnez le modèle de réseau neuronal, Call Center - LR (Call Center Default - LR).  
  
6.  Dans le menu **Modèle d’exploration de données** , sélectionnez **Requête singleton**.  
  
     Le **entrée de requête Singleton** boîte de dialogue s’affiche, avec des colonnes mappées aux colonnes dans le modèle d’exploration de données.  
  
7.  Dans le **entrée de requête Singleton** boîte de dialogue, cliquez sur la ligne pour la touche MAJ enfoncée, puis sélectionnez *minuit*.  
  
8.  Cliquez sur la ligne pour les opérateurs Lvl 2 et le type `6`.  
  
9. Dans la partie inférieure la moitié de la **prévision de modèle d’exploration de données** , cliquez sur la première ligne dans la grille.  
  
10. Dans le **Source** colonne, cliquez sur la flèche vers le bas, puis sélectionnez **fonction de prédiction**. Dans le **champ** colonne, sélectionnez **PredictHistogram**.  
  
     Une liste d’arguments que vous pouvez utiliser avec cette fonction de prédiction automatiquement s’affiche dans le **critères/argument** boîte.  
  
11. Faites glisser la colonne ServiceGrade dans la liste des colonnes dans le **Mining Model** volet pour le **critères/argument** boîte.  
  
     Le nom de la colonne est automatiquement inséré comme argument. Vous pouvez choisir n'importe quelle colonne d'attribut prédictible et la faire glisser vers cette zone de texte.  
  
12. Cliquez sur le bouton **affichage des résultats de commutateur à requête**, dans le coin supérieur du Générateur de requêtes de prédiction.  
  
 Les résultats attendus contiennent les valeurs prédites possibles pour chaque niveau de service donné en fonction de ces entrées, ainsi que les valeurs de support et de probabilité pour chaque prédiction. Vous pouvez repasser en mode Conception à tout moment pour modifier les entrées ou en ajouter.  
  
## <a name="creating-predictions-by-using-a-logistic-regression-model"></a>Création de prédictions à l’aide d’un modèle de régression logistique  
 Si vous connaissez déjà les attributs qui sont pertinents pour le problème de l'entreprise, vous pouvez utiliser un modèle de régression logistique pour prédire l'effet de la modification de certains attributs. La régression logistique est une méthode statistique utilisée communément pour élaborer des prédictions en fonction des modifications apportées aux variables indépendantes : par exemple, elle est utilisée dans le calcul de scores financiers, pour prédire le comportement de client en fonction des données démographiques de la clientèle.  
  
 Au cours de cette tâche, vous allez apprendre à créer une source de données qui sera utilisée pour des prédictions, puis à élaborer des prédictions afin de répondre à plusieurs questions pratiques.  
  
### <a name="generating-data-used-for-bulk-prediction"></a>Génération des données utilisées pour la prédiction en bloc  
 De nombreuses méthodes s'offrent à vous pour fournir des données d'entrée : par exemple, vous pouvez importer des niveaux d'affectation de personnel à partir d'une feuille de calcul, puis exécuter ces données par le modèle pour prédire la qualité du service pour le mois suivant.  
  
 Dans cette leçon, vous allez utiliser la vue de source de données pour créer une requête nommée. Cette requête nommée est une instruction Transact-SQL personnalisée qui, pour chaque équipe de travail, calcule le nombre maximal d'opérateurs du personnel, le nombre minimal d'appel reçu et le nombre moyen de problèmes générés. Vous joindrez ensuite ces données à un modèle d'exploration de données pour faire des prédictions sur une série de dates à venir.  
  
##### <a name="to-generate-input-data-for-a-bulk-prediction-query"></a>Pour générer des données d'entrée pour une requête de prédiction en bloc  
  
1.  Dans l’Explorateur de solutions, cliquez sur **les vues de sources de données**, puis sélectionnez **nouvelle vue de Source de données**.  
  
2.  Dans l’Assistant vue de Source de données, sélectionnez [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] comme la source de données, puis cliquez sur **suivant**.  
  
3.  Sur le **sélectionner des Tables et vues** , cliquez sur **suivant** sans sélectionner de tables.  
  
4.  Sur le **fin de l’Assistant** page, tapez le nom, `Shifts`.  
  
     Ce nom apparaîtra dans l'Explorateur de solutions comme nom de la vue de source de données.  
  
5.  Cliquez sur le volet de conception vide, puis sélectionnez **nouvelle requête nommée**.  
  
6.  Dans le **créer une requête nommée** boîte de dialogue pour **nom**, type `Shifts for Call Center`.  
  
     Ce nom apparaîtra dans le Concepteur de vue de source de données uniquement comme nom de la requête nommée.  
  
7.  Collez l'instruction de requête suivante dans le volet de texte SQL situé dans la moitié inférieure de la boîte de dialogue.  
  
    ```  
    SELECT DISTINCT WageType, Shift,   
    AVG(Orders) as AvgOrders, MIN(Orders) as MinOrders, MAX(Orders) as MaxOrders,  
    AVG(Calls) as AvgCalls, MIN(Calls) as MinCalls, MAX(Calls) as MaxCalls,  
    AVG(LevelTwoOperators) as AvgOperators, MIN(LevelTwoOperators) as MinOperators, MAX(LevelTwoOperators) as MaxOperators,  
    AVG(IssuesRaised) as AvgIssues, MIN(IssuesRaised) as MinIssues, MAX(IssuesRaised) as MaxIssues  
    FROM dbo.FactCallCenter  
    GROUP BY Shift, WageType  
    ```  
  
8.  Dans le volet de conception, cliquez sur la table, les équipes pour le centre d’appels, puis sélectionnez **Explorer les données** aperçu des données tel que retourné par la requête T-SQL.  
  
9. Cliquez sur l’onglet, **Shifts.dsv (Design),** puis cliquez sur **enregistrer** pour enregistrer la nouvelle définition de vue de source de données.  
  
### <a name="predicting-service-metrics-for-each-shift"></a>Prédiction de mesures de niveau de service pour chaque équipe  
 Maintenant que vous avez généré des valeurs pour chaque équipe, vous allez utiliser ces valeurs comme entrée pour le modèle de régression logistique que vous avez créé, afin de générer des prédictions à utiliser dans la planification des entreprises.  
  
##### <a name="to-use-the-new-dsv-as-input-to-a-prediction-query"></a>Pour utiliser la nouvelle vue de source de données comme entrée pour une requête de prédiction  
  
1.  Dans le Concepteur d’exploration de données, cliquez sur le **prévision de modèle d’exploration de données** onglet.  
  
2.  Dans le **Mining Model** volet, cliquez sur **sélectionner un modèle**, puis choisissez centre d’appels - LR dans la liste des modèles disponibles.  
  
3.  À partir de la **Mining Model** menu, désactivez l’option, **requête Singleton**. Un avertissement vous indique que les entrées de requête singleton seront perdues. Cliquez sur **OK**.  
  
     Le **entrée de requête Singleton** boîte de dialogue est remplacée par le **sélectionner une ou plusieurs tables d’entrée** boîte de dialogue.  
  
4.  Cliquez sur **Sélectionner la table de cas**.  
  
5.  Dans le **sélectionner une Table** boîte de dialogue, selectShifts dans la liste des sources de données. Dans le **nom de la Table/vue** , sélectionnez Shifts for Call Center (il peut être sélectionné automatiquement), puis cliquez sur **OK.**  
  
     Le **prévision de modèle d’exploration de données** aire de conception est mise à jour pour afficher les mappages sont créés selon les types de données et les noms des colonnes dans les données d’entrée et dans le modèle.  
  
6.  Avec le bouton droit de la ligne de jointure, puis sélectionnez **modifier les connexions**.  
  
     Dans cette boîte de dialogue, vous pouvez voir exactement les colonnes qui sont mappées et celles qui ne le sont pas. Le modèle d'exploration de données contient des colonnes pour Calls, Order, IssuesRaised et LevelTwoOperators, que vous pouvez mapper à n'importe lequel des agrégats que vous avez créés en fonction de ces colonnes dans les données sources. Dans ce scénario, vous allez effectuer un mappage aux moyennes.  
  
7.  Cliquez sur la cellule vide en regard de LevelTwoOperators, puis sélectionnez **Shifts for Call Center.AvgOperators**.  
  
8.  Cliquez sur la cellule vide en regard de Calls, sélectionnez **Shifts for Call Center.AvgCalls**. puis cliquez sur **OK**.  
  
##### <a name="to-create-the-predictions-for-each-shift"></a>Pour créer les prédictions pour chaque équipe  
  
1.  Dans la grille en bas de la moitié de la **Générateur de requêtes de prédiction**, cliquez sur la cellule vide sous **Source,** , puis sélectionnez Shifts for Call Center.  
  
2.  Dans la cellule vide sous **champ**, sélectionnez la touche MAJ enfoncée.  
  
3.  Cliquez sur la ligne vide suivante dans la grille, et répétez la procédure décrite ci-dessus pour ajouter une autre ligne pour WageType.  
  
4.  Cliquez sur la ligne vide suivante dans la grille. Dans le **Source** colonne, sélectionnez **fonction de prédiction**. Dans le **champ** colonne, sélectionnez **Predict**.  
  
5.  Faites glisser la colonne ServiceGrade de la **modèle d’exploration de données** volet jusqu'à la grille et dans le **critères/Argument** cellule. Dans le **Alias** , tapez **prédite de niveau de Service**.  
  
6.  Cliquez sur la ligne vide suivante dans la grille. Dans le **Source** colonne, sélectionnez **fonction de prédiction**. Dans le **champ** colonne, sélectionnez **PredictProbability**.  
  
7.  Faites glisser la colonne ServiceGrade de la **modèle d’exploration de données** volet jusqu'à la grille et dans le **critères/Argument** cellule. Dans le **Alias** , tapez **probabilité**.  
  
8.  Cliquez sur **basculer vers l’affichage des résultats de requête** pour consulter les prédictions.  
  
 Le tableau suivant montre des exemples de résultats pour chaque équipe.  
  
|Shift|WageType|Niveau de service (Service Grade) prédit|Probabilité|  
|-----------|--------------|-----------------------------|-----------------|  
|AM|holiday|0.165|0.377520666|  
|midnight|holiday|0.105|0.364105573|  
|PM1|holiday|0.165|0.40056055|  
|PM2|holiday|0.165|0.338532973|  
|AM|weekday|0.165|0.370847617|  
|midnight|weekday|0.08|0.352999173|  
|PM1|weekday|0.165|0.317419177|  
|PM2|weekday|0.105|0.311672027|  
  
### <a name="predicting-the-effect-of-reduced-response-time-on-service-grade"></a>Prédiction de l'effet de temps de réponse réduit sur Service Grade  
 Vous avez généré des valeurs moyennes pour chaque équipe et utilisé ces valeurs comme entrée pour le modèle de régression logistique. Toutefois, étant donné que l'objectif de l'entreprise est de maintenir le taux d'abandon dans la plage 0.00-0.05, les résultats ne sont pas encourageants.  
  
 Par conséquent, en se basant sur le modèle d'origine, qui montrait une forte influence du temps de réponse sur le niveau de service, l'équipe Opérations décide d'exécuter des prédictions pour évaluer si la réduction du temps moyen de réponse aux appels peut améliorer la qualité du service. Par exemple, que se passerait-il pour les valeurs de niveau de service si le temps de réponse aux appels était réduit à 90 % ou même à 80 % du temps de réponse actuel ?  
  
 Il est facile de créer une vue de source de données qui calcule les temps de réponse moyens pour chaque équipe et d'ajouter ensuite des colonnes qui calculent 80 % ou 90 % du temps de réponse moyen. Vous pouvez ensuite utiliser la vue de source de données comme entrée pour le modèle.  
  
 Bien que les étapes exactes ne sont pas affichées ici, le tableau suivant compare les effets sur le niveau de service lorsque vous réduisez les temps de réponse à 80 % ou 90 % des temps de réponse actuels.  
  
 D'après ces résultats, vous pouvez conclure que, sur les équipes ciblées, que vous devez réduire le temps de réponse à 90 % du taux actuel afin d'améliorer la qualité de service.  
  
|Équipe, salaire et jour|Qualité prédite du service avec le temps de réponse moyen actuel|Qualité prédite du service avec réduction de 90 pour cent de temps de réponse|Qualité prédite du service à 80 pour cent de réduction du temps de réponse|  
|--------------------------|------------------------------------------------------------------|--------------------------------------------------------------------------|--------------------------------------------------------------------------|  
|Congé AM|0.165|0,05|0,05|  
|Congé PM1|0,05|0,05|0,05|  
|Congé Minuit|0.165|0,05|0,05|  
  
 Vous pouvez créer diverses autres requêtes de prédiction sur ce modèle. Par exemple, vous pourrez prédire le nombre d’opérateurs est nécessaire pour répondre à un certain niveau de service ou pour répondre à un certain nombre d’appels entrants. Étant donné que vous pouvez inclure plusieurs sorties dans un modèle de régression logistique, il est facile de faire des essais avec différentes variables indépendantes et sorties sans qu'il soit nécessaire de créer de nombreux modèles distincts.  
  
## <a name="remarks"></a>Notes  
 Les données d’exploration de données des compléments pour Excel 2007 fournissent des Assistants de régression logistique qui permettent de facilement répondre aux questions complexes, telles que les opérateurs de niveau 2 combien seraient nécessaire pour améliorer le niveau de service à un niveau cible pour une équipe spécifique. Les compléments d'exploration de données, qui peuvent être téléchargés gratuitement, incluent des Assistants basés sur l'algorithme MNN (Microsoft Neural Network) ou l'algorithme MLR (Microsoft Logistic Regression). Pour plus d'informations, consultez les liens suivants :  
  
-   [SQL Server 2005 Data Mining Add-Ins pour Office 2007](https://www.microsoft.com/sql/technologies/dm/addins.mspx): La valeur cible et que se passe-t-il si analyse de scénario  
  
-   [SQL Server 2008 Data Mining Add-Ins pour Office 2007](https://go.microsoft.com/fwlink/?LinkID=117790): Valeur cible de l’analyse de scénario, que se passe-t-il si l’analyse de scénario et calcul de prédiction  
  
## <a name="conclusion"></a>Conclusion  
 Vous avez appris à créer, à personnaliser et à interpréter des modèles d'exploration de données basés sur l'algorithme MNN (Microsoft Neural Network) et sur l'algorithme MLR (Microsoft Logistic Regression). Ces types de modèles élaborés permettent une diversité presque infinie d'analyses ; ils peuvent, par conséquent, être complexes et difficiles à maîtriser.  
  
 Toutefois, ces algorithmes peuvent s'itérer par le biais de plusieurs combinaisons de facteurs et identifier automatiquement les corrélations les plus fortes en fournissant la prise en charge statistique des analyses qui seraient très difficiles à identifier par l'exploration manuelle des données à l'aide de Transact-SQL ou même de PowerPivot.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples de requêtes de modèle de régression logistique](../../2014/analysis-services/data-mining/logistic-regression-model-query-examples.md)   
 [Algorithme MLR (Microsoft Logistic Regression)](../../2014/analysis-services/data-mining/microsoft-logistic-regression-algorithm.md)   
 [Microsoft Neural Network Algorithm](../../2014/analysis-services/data-mining/microsoft-neural-network-algorithm.md)   
 [Exemples de requêtes de modèle de réseau neuronal](../../2014/analysis-services/data-mining/neural-network-model-query-examples.md)  
  
  
