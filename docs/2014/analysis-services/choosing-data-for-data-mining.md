---
title: Choix des données pour l’exploration de données | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- content type [data mining]
- nested tables
- key [data mining]
- continuous values
- key sequence [data mining]
- table data type
- key time [data mining]
- discrete values
- discretized
ms.assetid: 7c72d80e-913c-4bbe-b258-444294a78838
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9bec249e483c5736ee7cf0e66f4aff0af98e08c7
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66088027"
---
# <a name="choosing-data-for-data-mining"></a>Choisir les données pour l'exploration de données
  Lorsque vous commencez l’exploration de données, vous vous demandez peut-être « la quantité de données besoin ? » ou « Quels sont les exigences spéciales à que connaître lors du nettoyage ou de mise en forme de mes données ? »  
  
 En particulier, ces personnes rencontrent souvent des problèmes avec les données Excel, notamment, pour mettre en forme uniformément les données dans les colonnes, pour nettoyer les valeurs manquantes, ou pour placer des nombres dans un conteneur. Cette section répertorie également les spécifications de données pour des types de modèles spécifiques.  
  
 [Choix des données](#bkmk_ChoosingData)  
  
 [Problèmes de données courants](#bkmk_CommonDataProblems)  
  
 [Autres spécifications de données](#bkmk_OtherRequirements)  
  
##  <a name="bkmk_ChoosingData"></a> Choix des données  
 Le choix des données utilisées pour l'analyse est peut-être l'étape la plus importante du processus d'exploration de données, plus encore que le choix d'un algorithme. En effet, l'exploration des données ne repose généralement pas sur des hypothèses, mais est pilotée par les données. Plutôt que choisir et tester les variables à l'avance, comme vous le feriez dans le cadre d'une modélisation statistique traditionnelle, l'exploration des données peut extraire des données et découvrir de nouvelles corrélations (ou ne trouver aucun modèle). La qualité et la quantité des données peuvent avoir un impact significatif sur les résultats.  
  
 En général, suivez les règles suivantes :  
  
-   Obtenez autant de données viables que possible.  
  
-   Effectuez un profilage des données avant d'essayer les modèles. Vous devez comprendre vos données avant de pouvoir tirer parti de leur interprétation. Au minimum :  
  
    1.  Utilisez les outils inclus dans les compléments pour rechercher votre valeurs maximales et minimales, les valeurs les plus courantes, et les valeurs moyennes.  
  
    2.  Remplissez les valeurs manquantes. Les compléments (et certains algorithmes) comportent des outils qui permettent de saisir les valeurs manquantes.  
  
    3.  Corrigez autant que possible les données incorrectes. Souvent, les projets d'exploration de données donnent l'impulsion pour de nouvelles initiatives visant à améliorer la qualité des données.  
  
-   Essayez de créer un modèle de test et de détecter ainsi les problèmes de données. Pendant l'analyse des résultats, vous pourriez par exemple découvrir que les projections de ventes reposent sur des données anormales dues à une erreur de conversion monétaire.  
  
-   Essayez de convertir vos données dans différents formats, ou essayez de créer des compartiments de nombres. Les modèles émergent souvent lorsque les données sont transformées.  
  
     Par exemple, le niveau de service d'un centre d'appels peut varier en fonction du jour de la semaine, et cette information vous échappera si vous utilisez uniquement des valeurs datetime. Les prévisions peuvent s'avérer plus fiables lorsqu'elles reposent sur des cycles de 10 jours plutôt que sur des unités hebdomadaires ou quotidiennes.  
  
-   Placez les données dans des conteneurs appropriés, afin de réduire le nombre de valeurs possibles pour l'analyse.  
  
-   Créez plusieurs versions de vos données et construisez plusieurs modèles.  
  
 Pour des conseils supplémentaires sur la façon de sélectionner, modifier et analyser les données, consultez [liste de vérification de préparation pour l’exploration de données](checklist-of-preparation-for-data-mining.md).  
  
### <a name="how-much-data-do-i-need"></a>De quelle quantité de données a-t-on besoin ?  
 En règle générale, vous devez avoir au moins 50 à 100 lignes de données pour les types de modèles et les scénarios les plus simples. Par exemple, si vous évaluez un seul attribut à l'aide d'un modèle utilisant la classification naïve bayésienne et le jeu de données est bien constitué, vous obtiendrez des prédictions assez précises en utilisant 50 à 100 lignes de données.  
  
 Pour les modèles d’association, vous devez généralement beaucoup plus de données - un millier de lignes peut ne pas suffire si vous analysez beaucoup d’attributs, tels que des associations entre les produits. Si votre jeu de données est trop grand ou trop petit, vous obtiendrez parfois de meilleurs résultats en réduisant les lignes en catégories. Par exemple, au lieu d'analyser les associations entre des produits individuels, vous pouvez classer les produits par catégorie.  
  
 Si vous disposez d'un jeu de données d'une taille raisonnable, concentrez-vous davantage sur leur qualité au lieu d'ajouter une plus grande quantité de données. Au bout d'un certain temps, vous aurez déterminé tous les modèles statistiquement valides, et l'ajout de plus de données n'aura pas d'influence sur leur validité. À l'inverse, lorsque vous ajoutez plus de données, des corrélations accidentelles sont parfois introduites.  
  
### <a name="discrete-vs-continuous-numbers"></a>Nombres discrets et Nombres continus  
 Une colonne *discrète* contient un nombre fini de valeurs. Par exemple, le texte est toujours traité comme valeurs discrètes.  
  
 Certains attributs sont importants pour distinguer les valeurs. Par exemple, si vous considérez les nombres comme des valeurs discrètes, aucun ordre réciproque n'est implicite, et vous ne pouvez pas faire la moyenne ou la somme de ces nombres. Les indicatifs de téléphone régionaux sont un bon exemple de données numériques discrètes que vous n'utiliserez jamais pour effectuer des opérations mathématiques.  
  
 Les valeurs discrètes sont parfois appelées valeurs de catégories, car vous pouvez regrouper un ensemble de données en fonction de celles-ci, alors que vous ne pouvez pas le faire avec des nombres organisés dans une série infinie.  
  
 Vous pouvez également décider de considérer les nombres comme des valeurs discrètes lorsque les valeurs sont clairement séparées, sans possibilité de valeurs fractionnaires, ou lorsque les valeurs fractionnaires ne sont pas utiles.  
  
 Les données numériques*continues* peuvent contenir un nombre infini de valeurs fractionnaires. Une colonne de revenus est un exemple de colonne d'attributs continue. Si vous spécifiez qu'une colonne est numérique, chaque valeur dans cette colonne doit être un nombre, à l'exception des valeurs NULL. Notez que dans Excel, les horodateurs et les autres représentations de date-heure qui peuvent être converties en type de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] peuvent être pris en compte.  
  
 **Conversion de nombres en Variables catégorielles**  
  
 Le fait qu'une colonne contienne des nombres ne signifie pas que vous devez les traiter comme des nombres continus. La*discrétisation* fournit de nombreux avantages pour l'analyse. Le problème d'espace est réduit. Par ailleurs, les nombres ne sont parfois pas la meilleure façon d'exprimer un résultat.  
  
 Par exemple, le nombre d'enfants par famille peut être traité comme une valeur discrète ou continue. Étant donné qu'il est impossible d'avoir 2,5 enfants dans la famille, les familles avec 3 enfants ou plus peuvent se comporter très différemment des familles avec 2 enfants. Par conséquent, vous obtiendrez de meilleurs résultats en traitant ce nombre comme une catégorie. Cependant, si vous créez un modèle de régression ou si avez besoin d'une valeur moyenne (par exemple, 1,357 enfants par famille), vous devriez utiliser un type de données numériques continues.  
  
 Il n'est pas possible de créer un modèle d'exploration de données dont les données sont continues puis de traiter par la suite la colonne comme discrète. Les deux jeux de données doivent être traités différemment et sont gérés au niveau principal comme des structures d'exploration de données distinctes. Si vous n'êtes pas sûr de la façon dont traiter correctement les données, vous devez créer des modèles distincts qui gèrent différemment les données. Dans tous les cas, vous aurez une autre perspective de vos données, voire des résultats différents.  
  
 **Conversion de nombres en texte**  
  
 Très souvent, les valeurs discrètes, telles que Male et Female, sont représentées comme données numériques et utilisent les étiquettes 1 et 2. En général, ce codage est effectué pour simplifier l'entrée de données ou pour économiser l'espace de stockage dans une base de données, mais le codage peut être source d'ambiguïté quant à la nature ou la signification des valeurs. De plus, dans la mesure où les valeurs discrètes sont stockées sous forme de nombres, lorsque vous déplacez des données entre applications vous pouvez rencontrer des erreurs de conversion de type de données, et les valeurs peuvent être calculées ou traitées comme continues. Pour empêcher de tels problèmes, avant de commencer l'exploration de données, vous devez convertir les étiquettes numériques en étiquettes de texte discrètes.  
  
 **Numéros de compartimentage**  
  
 Même si tous les nombres sont en principe infinis et donc continus, il est souvent plus efficace lorsque vous modélisez des informations de *discrétiser* ou *placer dans un conteneur* les valeurs disponibles.  
  
 Vous pouvez placer les données dans un conteneur de plusieurs manières :  
  
-   Spécifiez un nombre fini de compartiments et laissez l'algorithme trier les valeurs dans les compartiments.  
  
-   Préregroupez les valeurs, en créant un certain ensemble de regroupements qui a une signification pour l'entreprise ou qui est plus facile à utiliser. Avec cette approche, vous ignorez souvent la distribution réelle des valeurs, mais les plages sont plus faciles à lire pour les utilisateurs.  
  
-   Laissez l'algorithme déterminer le nombre optimal de compartiments et la distribution des valeurs. Il s'agit de la valeur par défaut dans la plupart des outils, mais vous pouvez la remplacer dans les Assistants de la barre d'outils **Exploration de données** .  
  
-   En les approchant d'une moyenne ou d'une valeur représentative.  
  
##  <a name="bkmk_CommonDataProblems"></a> Problèmes de données courants  
  
### <a name="excel-number-formats"></a>Formats de nombres Excel  
 Excel est un outil facile à utiliser, car il est indulgent : vous pouvez placer n’importe quel type de données n’importe où ! Toutefois, avant de commencer à rechercher des modèles et à analyser les corrélations, vous devez appliquer une structure ou des contraintes à vos données.  
  
 Par défaut, lors de l'importation de données numériques dans [!INCLUDE[msCoName](../includes/msconame-md.md)] Office Excel, les nombres sont stockés au format décimal avec deux décimales. Si ce format numérique ne convient pas, vous devez le remplacer par un format numérique différent ou changer le nombre de décimales.  
  
 L'une des possibilités consiste à utiliser l'outil [Réétiqueter](relabel-sql-server-data-mining-add-ins.md) , disponible dans les outils d'analyse de table pour Excel, pour modifier le mode d'affichage ou de regroupement des nombres.  
  
 Toutefois, si vos données sont trop compliquées à traiter à l'aide de l'outil **Réétiqueter** , utilisez les fonctions numériques dans Excel pour les convertir en plages discrètes, enregistrer ce résultat dans une colonne séparée, puis utilisez à la place la colonne discrétisée pour la classification.  
  
 Par exemple, si vous analysez les résultats d'une course et voulez regrouper les concurrents en fonction de leur temps de course en minutes, vous pouvez arrondir à la minute la plus proche, puis enregistrer cette valeur arrondie dans une nouvelle colonne. Vous pouvez également extraire uniquement la minute à l'aide de la fonction `MINUTE`, puis enregistrer cette valeur dans une nouvelle colonne à des fins d'analyse.  
  
### <a name="discretizing-numbers-and-dates-in-excel"></a>Discrétisation des nombres et des dates dans Excel  
 Par défaut, les données numériques dans Excel sont stockées sous la forme `Double`. Les données de date et heure sont aussi stockées dans un format numérique. Si vous devez discrétiser des nombres ou des dates pour l'exploration de données, ajoutez de nouvelles colonnes avant de créer votre modèle d'exploration de données ou convertissez au préalable les dates et les nombres sous un autre format.  
  
### <a name="scientific-number-formats"></a>Formats de nombres scientifiques  
 Les outils d'exploration de données génèrent souvent des probabilités en notation scientifique pour représenter des nombres qui sont très grands ou très petits. Si vous n'êtes pas familier avec la notation scientifique, vous pouvez afficher facilement ces nombres dans un autre format en modifiant simplement la mise en forme des cellules.  
  
##### <a name="to-change-scientific-notation-to-a-decimal-numeric-format"></a>Pour modifier la notation scientifique en un format numérique décimal  
  
1.  Dans le tableau de données Microsoft Excel, mettez en surbrillance la colonne ou cellule qui contient le nombre en notation scientifique.  
  
2.  Cliquez avec le bouton droit et sélectionnez **Format de cellules** dans le menu contextuel.  
  
3.  Dans la liste **Catégorie** , sélectionnez **Nombre**.  
  
4.  Augmentez le nombre de décimales. Une probabilité représentée en notation scientifique est généralement très petite.  
  
     Seul l'affichage du nombre est modifié, pas la valeur sous-jacente.  
  
### <a name="working-with-dates-and-times"></a>Utilisation des dates et des heures  
 Lorsqu'un tableau Excel contient des dates et que vous utilisez la colonne soit comme entrée, soit pour la prédiction, vous pouvez obtenir des résultats inattendus selon le format des informations de date ou d'heure. Par exemple, si vous utilisez **Détecter les catégories** ou **Classer** et incluez une colonne qui contient des dates, celles-ci sont catégorisées comme nombres à plusieurs décimales. Ce n'est pas une erreur ; il s'agit d'une représentation exacte des données sous-jacentes. L'algorithme d'exploration de données fonctionne avec le format de stockage sous-jacent, pas le format d'affichage.  
  
 Si vous rencontrez des difficultés pour utiliser des dates et que vous souhaitez analyser celles-ci en utilisant des regroupements classiques tels que le mois ou le jour, faites appel aux fonctions DATE dans Excel pour extraire l'année, le mois ou le jour dans une colonne séparée, puis utilisez à la place cette colonne pour la classification.  
  
##  <a name="bkmk_OtherRequirements"></a> Autres spécifications de données  
  
### <a name="requirements-by-algorithm-type"></a>Spécifications par type d'algorithme  
 Certains algorithmes utilisés dans les compléments requièrent des types de données ou des types de contenu spécifiques pour créer un modèle.  
  
 **Modèles Naïve Bayes**  
  
-   L'algorithme [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes ne peut pas utiliser des colonnes continues comme entrée. Cela signifie que vous devez placer les nombres dans des conteneurs ou, si les valeurs sont peu nombreuses, les traiter comme des valeurs discrètes.  
  
-   En outre, ce type de modèle ne peut pas prédire des valeurs continues. Par conséquent, si vous voulez prédire un nombre continu, par exemple un revenu, vous devez d'abord placer les valeurs dans des conteneurs selon des plages significatives. Si vous avez des doutes en ce qui concerne les plages correctes, utilisez l'algorithme de clustering pour identifier les blocs de nombres dans vos données.  
  
-   Lorsque vous utilisez un Assistant basé sur cet algorithme (tel que [analyser les facteurs d’influence clés &#40;Table Analysis Tools pour Excel&#41;](analyze-key-influencers-table-analysis-tools-for-excel.md)), colonnes continues sont placées dans un conteneur par l’Assistant vous.  
  
-   Si vous générez un modèle Naive Bayes avec le [avancés de modélisation &#40;des compléments d’exploration de données pour Excel&#41; ](advanced-modeling-data-mining-add-ins-for-excel.md) option, colonnes de nombres sont supprimées à partir du modèle. Si vous souhaitez éviter ce problème, utilisez le [Réétiqueter &#40;SQL Server Data Mining Add-ins&#41; ](relabel-sql-server-data-mining-add-ins.md) outil pour créer une nouvelle colonne avec les valeurs compartimentées.  
  
 **Modèles de clustering**  
  
-   Les outils de clustering ([Assistant Cluster &#40;des compléments d’exploration de données pour Excel&#41; ](cluster-wizard-data-mining-add-ins-for-excel.md) et [détecter les catégories &#40;Table Analysis Tools pour Excel&#41;](detect-categories-table-analysis-tools-for-excel.md)) ne pouvez pas utiliser continue nombres, mais ces deux outils placent automatiquement colonnes de nombres pour vous.  
  
-   Les deux outils vous donnent la possibilité de choisir le nombre de catégories de sortie dans les résultats, mais si vous souhaitez contrôler la façon dont les valeurs de colonnes sont regroupées, vous devez créer une nouvelle colonne avec le regroupement souhaité.  
  
 **Modèles de prévision**  
  
-   Tous les outils de prédictions exigent la prédiction d'un nombre continu. Vous ne pouvez pas prédire un nombre qui a été enregistré en tant que texte.  
  
-   Si vos données contiennent des colonnes numériques avec un type de données incorrect, utilisez les fonctions d'Excel ou de PowerPivot pour copier la colonne avec le type de données numériques correct. Si vous procédez ainsi, assurez-vous de supprimer la copie de la colonne contenant les nombres sous forme de texte, afin que les valeurs ne soient pas dupliquées.  
  
-   Si vous souhaitez créer un nuage de points à partir d'un modèle de régression, les variables d'entrée doivent également être des nombres continus, exprimés comme un type de données correct.  
  
### <a name="using-content-types-to-make-better-models"></a>Utilisation des types de contenu pour créer des modèles plus efficaces  
 Un *type de contenu* est une propriété que vous appliquez à une colonne pour spécifier comment les données de la colonne doivent être utilisées par le modèle. L'algorithme peut utiliser le type de contenu comme instruction ou indicateur dans l'analyse.  
  
 Par exemple, si une colonne contient des nombres qui se répètent à une fréquence spécifique pour indiquer les jours de la semaine, définissez le type de contenu de cette colonne comme étant `Cyclical`.  
  
 Vous n’avez pas à vous soucier des types de contenu si vous utilisez les Assistants et les outils fournis dans ce module complémentaire. Toutefois, si vous utilisez le [ajouter le modèle à la Structure &#40;des compléments d’exploration de données pour Excel&#41; ](add-model-to-structure-data-mining-add-ins-for-excel.md) option pour ajouter un nouveau modèle aux données existantes de modélisation, vous pouvez obtenir une erreur relative aux types de contenu.  
  
 La raison en est que certains types de modèle requièrent un certain type de données (par exemple un horodatage). Les outils traitent ces colonnes en fonction d'exigences spécifiques et ajoutent également une propriété de type de contenu. Par conséquent, si vous réutilisez les données avec un algorithme complètement différent, il sera peut-être nécessaire de remplacer le type de données ou le type de contenu.  
  
 La liste suivante décrit les types de contenu utilisés dans le cadre de l'exploration de données et identifie les types de données qui prennent en charge chacun de ces types.  
  
 `Discrete`  
 La colonne contient un nombre fini de valeurs sans continuum entre les valeurs. Une colonne Sexe (homme/femme) est un exemple classique de colonne d'attributs discrète, en ce sens que les données représentent un nombre spécifique de catégories.  
  
 Le type de contenu `Discrete` peut être utilisé avec tous les types de données.  
  
 `Continuous`  
 Cette colonne contient des valeurs qui représentent des données numériques sur une échelle qui autorise des valeurs intérimaires. Une colonne continue représente des mesures évolutives et les données peuvent contenir un nombre infini de valeurs fractionnaires. Une colonne de températures est un exemple de colonne d'attributs continue.  
  
 Le type de contenu `Continuous` peut être utilisé avec les types de données suivants : `Date`, `Double` et `Long`.  
  
 `Discretized`  
 La colonne contient des valeurs qui représentent des groupes de valeurs dérivées d'une colonne continue. Les compartiments sont traités comme des valeurs discrètes et **ordonnées** .  
  
 Le type de contenu `Discretized` peut être utilisé avec les types de données suivants : `Date`, `Double` et `Long`.  
  
 **Clé**  
 La colonne identifie de manière unique une ligne.  
  
 En général la colonne clé est un identificateur numérique ou texte qui ne doit pas être utilisé pour l'analyse, uniquement pour le suivi des enregistrements. Les exceptions sont les clés de série chronologique et les clés de séquence.  
  
 Les**clés de tables imbriquées** s'utilisent uniquement si vous obtenez les données d'une source de données externe ayant été définie comme une vue de source de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] . Pour plus d’informations sur les tables imbriquées, consultez [ https://msdn.microsoft.com/library/ms175659.aspx ](https://msdn.microsoft.com/library/ms175659.aspx):  
  
 Ce type de contenu peut être utilisé avec les types de données suivants : `Date`, `Double`, `Long` et `Text`.  
  
 **Séquence clé**  
 La colonne contient des valeurs qui représentent une séquence d'événements. Les valeurs sont ordonnées, mais elles n'ont pas besoin d'être séparées par une distance égale.  
  
 Ce type de contenu est pris en charge par les types de données suivants : `Double`, `Long`, `Text` et `Date`.  
  
 **Temps clé**  
 La colonne contient des valeurs qui sont ordonnées et qui représentent une échelle de temps. Utilisez le type de contenu de temps clé uniquement si le modèle est un modèle de série chronologique ou un modèle Sequence Clustering.  
  
 Ce type de contenu est pris en charge par les types de données suivants : `Double`, `Long` et `Date`.  
  
 **Table**  
 Ce type de contenu s'utilise uniquement si vous obtenez les données d'une source de données externe ayant été définie comme une vue de source de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
 Cela signifie que chaque ligne de données contient réellement une table de données imbriquée, avec une ou plusieurs colonnes et une ou plusieurs lignes.  
  
 Tables imbriquées sont très pratiques, mais vous pouvez les utiliser uniquement avec le [avancés de modélisation &#40;des compléments d’exploration de données pour Excel&#41; ](advanced-modeling-data-mining-add-ins-for-excel.md) options de modélisation. Par exemple, les exemples de données pour le [Assistant associer &#40;Client d’exploration de données pour Excel&#41; ](associate-wizard-data-mining-client-for-excel.md) Assistant et [analyse de panier d’achat &#40;outils d’analyse de Table pour Excel&#41; ](shopping-basket-analysis-table-analysistools-for-excel.md) outil contient des données qui ont été aplaties à partir d’une table imbriquée.  

  
  
