---
title: Sélection des fonctionnalités (exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models [Analysis Services], feature selections
- attributes [data mining]
- feature selection algorithms [Analysis Services]
- data mining [Analysis Services], feature selections
- neural network algorithms [Analysis Services]
- naive bayes algorithms [Analysis Services]
- decision tree algorithms [Analysis Services]
- datasets [Analysis Services]
- clustering algorithms [Analysis Services]
- coding [Data Mining]
ms.assetid: b044e785-4875-45ab-8ae4-cd3b4e3033bb
author: minewiskan
ms.author: owend
ms.openlocfilehash: 02eb89db44e08daf7de5d89a932a097df277b961
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84522485"
---
# <a name="feature-selection-data-mining"></a>Sélection des fonctionnalités (exploration de données)
  La *sélection des fonctionnalités* est un terme couramment utilisé dans l’exploration de données pour décrire les outils et les techniques disponibles pour réduire les entrées à une taille gérable pour le traitement et l’analyse. La sélection des caractéristiques implique non seulement une réduction de la *cardinalité*, ce qui signifie imposer une coupure arbitraire ou prédéfinie sur le nombre d’attributs qui peuvent être pris en compte lors de la création d’un modèle, mais également le choix des attributs, ce qui signifie que l’analyste ou l’outil de modélisation sélectionne ou ignore activement les attributs en fonction de leur utilité pour l’analyse.  
  
 La possibilité d'appliquer la sélection des fonctionnalités est essentielle pour une analyse efficace, car les datasets contiennent souvent beaucoup plus d'informations que nécessaire pour générer le modèle. Par exemple, un dataset peut contenir 500 colonnes qui décrivent les caractéristiques des clients, mais si les données de certaines colonnes sont très éparses, vous tireriez peu de bénéfices à les ajouter au modèle. Si vous gardez les colonnes inutiles pendant la génération du modèle, plus d'UC et de mémoire sont nécessaires au cours du processus d'apprentissage, et plus d'espace de stockage est requis pour le modèle terminé.  
  
 Même si les ressources sont suffisantes, en général il est préférable de supprimer les colonnes inutiles car elles peuvent dégrader la qualité des modèles découverts, pour les raisons suivantes :  
  
-   Certaines colonnes sont parasites ou redondantes, ce qui rend plus difficile la découverte de séquences significatives à partir des données.  
  
-   Pour découvrir des séquences de qualité, la plupart des algorithmes d'exploration de données nécessitent un jeu de données d'apprentissage beaucoup plus important dans le cas d'un jeu de données de grande dimension. Mais, dans certaines applications d'exploration de données, les données d'apprentissage sont peu importantes.  
  
 Si seules 50 de 500 colonnes de la source de données possèdent des informations utiles à la création d'un modèle, vous pouvez tout simplement les laisser hors du modèle, ou vous pouvez utiliser des techniques de sélection de fonctionnalités afin de découvrir automatiquement les meilleures fonctionnalités et exclure les valeurs qui sont statistiquement non significatives. La sélection des fonctionnalités permet à la fois d'éviter d'avoir trop de données qui présentent peu d'intérêt, ou de n'avoir pas assez de données de valeur.  
  
## <a name="feature-selection-in-analysis-services-data-mining"></a>Sélection des fonctionnalités pour l'exploration de données Analysis Services  
 Habituellement, la sélection des fonctionnalités est effectuée automatiquement dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], et chaque algorithme comporte un ensemble de techniques par défaut permettant d'appliquer intelligemment la réduction des fonctionnalités. La sélection des fonctionnalités est toujours effectuée avant l'apprentissage du modèle, afin de choisir automatiquement les attributs d'un dataset qui sont le plus susceptibles d'être utilisés dans le modèle. Toutefois, vous pouvez également définir manuellement des paramètres pour influencer le comportement de la sélection des fonctionnalités.  
  
 En général, la sélection des fonctionnalités calcule un score pour chaque attribut, puis retient uniquement les attributs qui ont les meilleurs scores. Vous pouvez également ajuster le seuil pour les scores les plus élevés. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] fournit plusieurs méthodes pour calculer les scores ; la méthode exacte appliquée dans un modèle dépend de ces facteurs :  
  
-   Algorithme utilisé dans votre modèle  
  
-   Type de données de l'attribut  
  
-   Tous les paramètres que vous pouvez avoir définis sur votre modèle  
  
 La sélection des fonctionnalités est appliquée aux entrées, aux attributs prévisibles ou aux états d'une colonne. Lorsque le calcul du score de sélection des fonctionnalités est terminé, seuls les attributs et les états que l'algorithme sélectionne sont inclus dans le processus de génération de modèle et peuvent être utilisés pour des prédictions. Si vous choisissez un attribut prédictible qui ne correspond pas au seuil pour la sélection des fonctionnalités, l'attribut peut toujours être utilisé pour la prédiction, mais les prédictions seront uniquement basées sur les statistiques globales qui existent dans le modèle.  
  
> [!NOTE]  
>  La sélection des fonctionnalités affecte uniquement les colonnes utilisées dans le modèle et n'a aucun effet sur le stockage de la structure d'exploration de données. Les colonnes que vous omettez dans le modèle d'exploration de données restent disponibles dans la structure, et les données contenues dans les colonnes de structure d'exploration de données sont mises en cache.  
  
### <a name="definition-of-feature-selection-methods"></a>Définition de méthodes de sélection des fonctionnalités  
 Plusieurs méthodes s'offrent à vous pour implémenter la sélection des fonctionnalités, en fonction du type de données que vous utilisez et de l'algorithme que vous choisissez pour l'analyse. SQL Server Analysis Services fournit plusieurs méthodes bien établies et très utilisées pour calculer les scores des attributs. La méthode appliquée dans tout algorithme ou jeu de données dépend des types de données et de l'utilisation des colonnes.  
  
 Le score *d’intérêt et de pertinence* est utilisé pour classer par ordre de priorité et trier les attributs dans des colonnes qui contiennent des données numériques continues non binaires.  
  
 *L’entropie de Shannon* et deux scores *bayésiens* sont disponibles pour les colonnes qui contiennent des données discrètes et discrétisées. Toutefois, si le modèle contient des colonnes continues, le score d'intérêt et de pertinence est utilisé pour évaluer toutes les colonnes d'entrée, afin de garantir la cohérence.  
  
 La section suivante décrit chaque méthode de sélection des fonctionnalités.  
  
#### <a name="interestingness-score"></a>Score d'intérêt et de pertinence  
 Une fonctionnalité présente un intérêt si elle fournit des informations utiles. Étant donné que la définition de ce qui est utile varie selon le scénario, le secteur de l’exploration de données a développé différentes façons de mesurer l' *intérêt*. Par exemple, la *nouveauté* peut être intéressante dans la détection de valeurs hors norme, mais la possibilité de faire la distinction entre des éléments étroitement liés, ou un *poids distinctif*, peut être plus intéressante pour la classification.  
  
 La mesure d’intérêt qui est utilisée dans SQL Server Analysis Services est *basée sur l’entropie*, ce qui signifie que les attributs avec des distributions aléatoires ont une entropie plus élevée et un gain d’informations plus faible. par conséquent, ces attributs sont moins intéressants. L'entropie pour un attribut particulier est comparée à l'entropie de tous les autres attributs, comme suit :  
  
 Intérêt/Pertinence(Attribut) = - (m - Entropie(Attribut)) * (m - Entropie(Attribut))  
  
 L’entropie centrale, ou m, représente l’entropie de l’ensemble du jeu de fonctionnalités. En soustrayant l'entropie de l'attribut cible de l'entropie centrale, vous pouvez évaluer la quantité d'informations fournies par l'attribut.  
  
 Ce score est utilisé par défaut chaque fois que la colonne contient des données numériques continues non binaires.  
  
#### <a name="shannons-entropy"></a>Entropie de Shannon  
 L'entropie de Shannon mesure l'incertitude d'une variable aléatoire pour un résultat particulier. Par exemple, l'entropie d'une partie de pile ou face peut être représentée comme une fonction de la probabilité de la pièce tombant côté pile.  
  
 Analysis Services utilise la formule suivante pour calculer l'entropie de Shannon :  
  
 H(X) = -∑ P(xi) log(P(xi))  
  
 Cette méthode de calcul de score est disponible pour les attributs discrets et discrétisés.  
  
#### <a name="bayesian-with-k2-prior"></a>Bayésien avec a priori K2  
 Analysis Services fournit deux scores de sélection des fonctionnalités qui sont basés sur les réseaux bayésiens. Un réseau bayésien est un graphique *dirigé* ou *acyclique* d’états et de transitions entre états. Cela signifie que certains états sont toujours antérieurs à l’état actuel, que certains états sont postérieurs et que le graphique ne se répète pas ou ne fait pas de boucle. Par définition, les réseaux bayésiens autorisent l'utilisation de connaissances antérieures. Toutefois, la question de savoir quels états antérieurs utiliser pour le calcul des probabilités des états ultérieurs est importante pour la conception, les performances et la précision de l'algorithme.  
  
 Développé par Cooper et Herskovits, l'algorithme K2 pour l'apprentissage à partir d'un réseau bayésien est couramment employé dans le cadre de l'exploration de données. Cet algorithme est évolutif et peut analyser plusieurs variables, mais il requiert le tri des variables utilisées comme entrée. Pour plus d’informations, consultez la documentation [Learning Bayesian Networks](https://go.microsoft.com/fwlink/?LinkId=105885) de Chickering, Geiger et Heckerman.  
  
 Cette méthode de calcul de score est disponible pour les attributs discrets et discrétisés.  
  
#### <a name="bayesian-dirichlet-equivalent-with-uniform-prior"></a>Équivalent bayésien de Dirichlet avec a priori uniforme  
 Le score d'équivalent bayésien de Dirichlet (BDE) utilise également l'analyse bayésienne pour évaluer un réseau pour un dataset donné. La méthode de calcul de score BDE a été développée par Heckerman et est basée sur la métrique BD développée par Cooper et Herskovits. La distribution de Dirichlet est une distribution multinomiale qui décrit la probabilité conditionnelle de chaque variable dans le réseau et qui possède de nombreuses propriétés utiles pour l'apprentissage.  
  
 L'équivalent bayésien de Dirichlet avec a priori uniforme (BDEU) suppose un cas spécial de la distribution de Dirichlet dans laquelle une constante mathématique est utilisée pour créer une distribution fixe ou uniforme d'états antérieurs. Le score BDE suppose aussi l'équivalence de vraisemblance, ce qui signifie que les données ne sont pas censées faire la distinction entre des structures équivalentes. En d’autres termes, si le score pour If A Then B est le même que le score pour If B Then A, les structures ne peuvent pas être différenciées sur la base des données, et la causalité ne peut pas être déduite.  
  
 Pour plus d’informations sur les réseaux bayésiens et l’implémentation de ces méthodes de calcul de scores, consultez la documentation [Learning Bayesian Networks](https://go.microsoft.com/fwlink/?LinkId=105885).  
  
### <a name="feature-selection-methods-used-by-analysis-services-algorithms"></a>Méthodes de sélection des fonctionnalités utilisées par les algorithmes Analysis Services  
 Le tableau suivant répertorie les algorithmes qui prennent en charge la sélection des fonctionnalités, les méthodes de sélection des fonctionnalités utilisées par l'algorithme et les paramètres à définir pour contrôler le comportement de la sélection des fonctionnalités :  
  
|Algorithm|Méthode d'analyse|Commentaires|  
|---------------|------------------------|--------------|  
|Naive Bayes|Entropie de Shannon<br /><br /> Bayésien avec a priori K2<br /><br /> Équivalent bayésien de Dirichlet avec a priori uniforme (par défaut)|L'algorithme Microsoft Naïve Bayes accepte uniquement les attributs discrets ou discrétisés ; par conséquent, il ne peut pas utiliser le score d'intérêt et de pertinence.<br /><br /> Pour plus d’informations sur cet algorithme, consultez [Informations techniques de référence relatives à l’algorithme MNB (Microsoft Naive Bayes)](microsoft-naive-bayes-algorithm-technical-reference.md).|  
|Arbres de décision|Score d'intérêt et de pertinence<br /><br /> Entropie de Shannon<br /><br /> Bayésien avec a priori K2<br /><br /> Équivalent bayésien de Dirichlet avec a priori uniforme (par défaut)|Si des colonnes contiennent des valeurs continues non binaires, le score d'intérêt et de pertinence est utilisé pour toutes les colonnes afin de garantir la cohérence. Sinon, la méthode de sélection des fonctionnalités par défaut ou la méthode que vous avez spécifiée lors de la création du modèle est utilisée.<br /><br /> Pour plus d’informations sur cet algorithme, consultez [Références techniques relatives à l’algorithme MDT (Microsoft Decision Trees)](microsoft-decision-trees-algorithm-technical-reference.md).|  
|Réseau neuronal|Score d'intérêt et de pertinence<br /><br /> Entropie de Shannon<br /><br /> Bayésien avec a priori K2<br /><br /> Équivalent bayésien de Dirichlet avec a priori uniforme (par défaut)|L'algorithme MNN (Microsoft Neural Network, réseau neuronal de Microsoft) peut utiliser les deux méthodes de type bayésien et entropie tant que les données contiennent des colonnes continues.<br /><br /> Pour plus d’informations sur cet algorithme, consultez [Informations techniques de référence relatives à l’algorithme MDT (Microsoft Decision Trees)](microsoft-neural-network-algorithm-technical-reference.md).|  
|MLR (Microsoft Logistic Regression)|Score d'intérêt et de pertinence<br /><br /> Entropie de Shannon<br /><br /> Bayésien avec a priori K2<br /><br /> Équivalent bayésien de Dirichlet avec a priori uniforme (par défaut)|Bien que l'algorithme MLR (Microsoft Logistic Regression) soit basé sur l'algorithme MNN (Microsoft Neural Network), vous ne pouvez pas personnaliser les modèles de régression logistique de façon à contrôler le comportement de la sélection des fonctionnalités ; par conséquent, la valeur par défaut de la sélection des fonctionnalités est toujours la méthode la plus appropriée pour l'attribut.<br /><br /> Si tous les attributs sont discrets ou discrétisés, la valeur par défaut est BDEU.<br /><br /> Pour plus d’informations sur cet algorithme, consultez [Informations techniques de référence relatives à l’algorithme MLR (Microsoft Logistic Regression)](microsoft-logistic-regression-algorithm-technical-reference.md).|  
|Clustering|Score d'intérêt et de pertinence|L'algorithme de gestion de clusters Microsoft peut utiliser des données discrètes ou discrétisées. Toutefois, le score de chaque attribut étant calculé en tant que distance et étant représenté sous la forme d'un nombre continu, le score d'intérêt et de pertinence doit être utilisé.<br /><br /> Pour plus d’informations sur cet algorithme, consultez [Informations techniques de référence relatives à l’algorithme de gestion de clusters Microsoft](microsoft-clustering-algorithm-technical-reference.md).|  
|Régression linéaire|Score d'intérêt et de pertinence|L'algorithme MLR (Microsoft Linear Regression) Microsoft peut utiliser uniquement le score d'intérêt et de pertinence, car il prend en charge uniquement les colonnes continues.<br /><br /> Pour plus d’informations sur cet algorithme, consultez [Informations techniques de référence relatives à l’algorithme MLR (Microsoft Linear Regression)](microsoft-linear-regression-algorithm-technical-reference.md).|  
|Règles d’association<br /><br /> Sequence clustering|Non utilisé|La sélection des fonctionnalités n'est pas appelée avec ces algorithmes.<br /><br /> Toutefois, vous pouvez contrôler le comportement de l'algorithme et, si nécessaire, réduire la taille des données d'entrée en définissant la valeur des paramètres MINIMUM_SUPPORT et MINIMUM_PROBABILITY.<br /><br /> Pour plus d’informations, consultez [Informations techniques de référence relatives à l’algorithme Microsoft Association](microsoft-association-algorithm-technical-reference.md) et [Informations techniques de référence relatives à l’algorithme MSC (Microsoft Sequence Clustering)](microsoft-sequence-clustering-algorithm-technical-reference.md).|  
|Série chronologique|Non utilisé|La sélection des fonctionnalités ne s'applique pas aux modèles de série chronologique.<br /><br /> Pour plus d’informations sur cet algorithme, consultez [Informations techniques de référence relatives à l’algorithme MTS (Microsoft Time Series)](microsoft-time-series-algorithm-technical-reference.md).|  
  
## <a name="feature-selection-parameters"></a>Paramètres de sélection des fonctionnalités  
 Dans les algorithmes qui prennent en charge la sélection des fonctionnalités, vous pouvez contrôler à quel moment la sélection des fonctionnalités est activée au moyen des paramètres suivants. Chaque algorithme a une valeur par défaut pour le nombre des entrées autorisées, mais vous pouvez remplacer cette valeur par défaut et spécifier le nombre d'attributs. Cette section répertorie les paramètres qui sont fournis pour gérer la sélection des fonctionnalités.  
  
#### <a name="maximum_input_attributes"></a>MAXIMUM_INPUT_ATTRIBUTES  
 Si un modèle contient plus de colonnes que le nombre spécifié par le paramètre *MAXIMUM_INPUT_ATTRIBUTES* , l’algorithme ignore toutes les colonnes qu’il évalue comme inintéressantes.  
  
#### <a name="maximum_output_attributes"></a>MAXIMUM_OUTPUT_ATTRIBUTES  
 De manière similaire, si un modèle contient plus de colonnes prédictibles que le nombre spécifié par le paramètre *MAXIMUM_OUTPUT_ATTRIBUTES* , l’algorithme ignore toutes les colonnes qu’il évalue comme inintéressantes.  
  
#### <a name="maximum_states"></a>MAXIMUM_STATES  
 Si un modèle contient plus de cas que le nombre spécifié par le paramètre *MAXIMUM_STATES* , les états les moins utilisés sont regroupés et traités comme étant manquants. Si l'un de ces paramètres a la valeur 0, la sélection des fonctionnalités est désactivée, ce qui affecte le temps de traitement et les performances.  
  
 En plus de ces méthodes de sélection des fonctionnalités, vous pouvez améliorer la capacité de l’algorithme à identifier ou promouvoir des attributs explicites en définissant des *indicateurs de modélisation* sur le modèle ou en définissant des *indicateurs de distribution* sur la structure. Pour plus d’informations sur ces concepts, consultez [Indicateurs de modélisation &#40;exploration de données&#41;](modeling-flags-data-mining.md) et [Distributions de colonnes &#40;exploration de données&#41;](column-distributions-data-mining.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Personnaliser les modèles et les structures d'exploration de données](customize-mining-models-and-structure.md)  
  
  
