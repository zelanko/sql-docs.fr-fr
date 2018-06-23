---
title: Analyse du panier (outils d’analyse de Table pour Excel) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- shopping basket analysis
- mining model, association
- Table Analysis tools
- association [data mining]
- market basket analysis
ms.assetid: ba40cf43-f286-49ad-8316-70f5b11f1dae
caps.latest.revision: 19
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 593a854d689268b753b8ebeab544bbf51d2d0455
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36053394"
---
# <a name="shopping-basket-analysis-table-analysistools-for-excel"></a>Analyse du panier d'achat (Outils d'analyse de table pour Excel)
  ![Outil panier d’achat](media/tat-shopbskt.gif "outil panier d’achat")  
  
 Le **analyse du panier** outil vous permet de trouver `associations` dans vos données. Une association peut vous dire quels éléments sont fréquemment achetés en même temps. Dans l’exploration de données, cette technique est une méthode bien connue appelée *panier*, elle permet d’analyser le comportement d’achat des clients dans les jeux de données très volumineux. Les spécialistes du marketing peuvent utiliser ces informations pour recommander des produits connexes aux clients et promouvoir les produits connexes en les plaçant dans un proche voisinage sur les pages Web, dans les catalogues ou sur les rayons.  
  
 Pour utiliser l'analyse du panier d'achat, les éléments que vous souhaitez analyser doivent être liés par un ID de transaction. Par exemple, si vous analysez toutes les commandes reçues via un site Web, chaque commande aurait un ID de commande ou ID de transaction associé à un ou plusieurs éléments acheté.  
  
 Lorsque l’Assistant a terminé d’analyser les données, il crée deux nouvelles feuilles de calcul, **groupes d’éléments de panier d’achat** et **règles de panier d’achat**.  
  
 Le **groupes d’éléments de panier d’achat** feuille de calcul contient une liste des éléments qui apparaissent fréquemment ensemble dans des transactions. Ces groupements communs sont appelés *jeux d’éléments*. La feuille de calcul contient également des statistiques, telles que *prennent en charge* et *de courbes d’élévation*, pour vous aider à comprendre l’importance du jeu d’éléments. Si les informations de prix sont disponibles, la feuille de calcul crée également une somme de la valeur de tous les éléments connexes, afin de donner une indication de la valeur totale des transactions.  
  
 Vous pouvez effectuer un filtrage et un tri sur les colonnes dans le rapport. Par exemple, vous souhaiterez peut-être afficher uniquement les jeux de données avec 2 ou plusieurs produits ou classer les jeux d’éléments par **valeur moyenne du panier**.  
  
 Le **règles de panier d’achat** feuille de calcul utilise les statistiques dérivées de l’analyse pour créer des règles sur la façon dont les éléments sont liés. Par exemple, une règle peut être que si les clients achètent le produit A, ils sont très susceptibles d’acheter le produit B. Les règles peuvent être utilisés pour créer des recommandations. Chaque règle a des statistiques de confirmation qui vous aident à évaluer la force potentielle de la règle, afin que vous puissiez faire une recommandation uniquement si la règle dépasse un certain seuil de probabilité.  
  
## <a name="using-the-shopping-basket-analysis-tool"></a>Utilisation de l'outil Analyse du panier d'achat  
  
1.  Ouvrez un tableau Excel qui contient des données appropriées. Dans l'exemple de classeur, cliquez sur la feuille de calcul Associer.  
  
2.  Cliquez sur **analyse du panier**.  
  
3.  Dans le **analyse du panier** boîte de dialogue, choisissez la colonne qui contient l’ID de transaction, puis la colonne qui contient les éléments ou les produits que vous souhaitez analyser.  
  
4.  Le cas échéant, vous pouvez ajouter une colonne qui contient des valeurs de produits.  
  
5.  Cliquez sur**avancé**pour ouvrir le **configuration des paramètres avancés** boîte de dialogue. Augmentez la valeur de **prise en charge minimale** afin de réduire le nombre de produits qui sont considérés comme des jeux d’éléments. Augmenter la **probabilité de règle Minimum** pour filtrer les jeux d’éléments très courants.  
  
### <a name="requirements"></a>Spécifications  
 Pour utiliser le **analyse du panier** outil, vos données doivent être stockées dans un tableau Excel et doit contenir les colonnes suivantes :  
  
-   Colonne qui contient un ID unique représentant la transaction. L'ID peut être numérique ou texte, du moment que la valeur dans chaque ligne est unique.  
  
-   La colonne qui contient l'élément ou produit que vous analysez.  
  
-   Une colonne numérique facultative qui représente le prix ou la valeur de chaque élément. Cette colonne est utilisée pour agréger la valeur des jeux d'éléments lesquels chaque produit est trouvé et peut vous aider à comprendre la valeur totale de certaines transactions.  
  
## <a name="how-items-are-associated"></a>Association des éléments  
 Les différents éléments que vous analysez doivent être groupés par quelque identificateur qui représente le cas, la transaction ou l'occasion. Par conséquent, choisissez cette colonne d'ID de transaction comme identificateur, et non le numéro d'ID client ni le numéro d'ID produit.  
  
 Lorsque l'outil examine les produits dans chaque transaction, il crée un jeu d'éléments pour chaque combinaison d'éléments qu'il trouve. Par exemple, si un client a acheté trois éléments lors d'une seule visite, il existe 7 jeux d'éléments possibles : chaque produit considéré seul, chaque produit groupé avec un autre produit et la combinaison des trois produits ensemble.  
  
> [!NOTE]  
>  Vous pouvez éliminer par filtrage les jeux d'éléments qui contiennent des éléments uniques, mais l'outil doit les analyser pour générer des statistiques significatives pour le jeu de données.  
  
 La prise en charge de chaque élément de jeux est calculée en tant que nombre de clients qui achètent un élément de jeux. Dans l'exemple qui vient d'être présenté, s'il y a juste un client qui a acheté 3 éléments, avec 7 jeux d'éléments possibles, chacun des 7 jeux d'éléments a une valeur de prise en charge égale à 1. À mesure que le nombre de clients augmente et le nombre de combinaisons grandit, le délai de traitement du rapport peut s'allonger considérablement. Toutefois, certains jeux d'éléments peuvent avoir une prise en charge très limitée. Par conséquent, vous pouvez décider de réduire le temps qu'il faut pour générer le rapport en limitant le nombre d'éléments dans chaque jeu d'éléments à 3 au plus. En général, les grands jeux d'éléments ont une prise en charge beaucoup plus faible, ce qui fait que le compromis est acceptable.  
  
## <a name="specifying-minimum-support-and-rule-probability"></a>Spécification de prise en charge minimale et de règle de probabilité  
 Lorsque la taille de votre jeu de données augmente, le nombre de groupements d'éléments et de règles possibles peut devenir énorme. Toutefois, vous pouvez contrôler le nombre de résultats qui sont générés par l'outil, afin de vous concentrer uniquement sur les jeux d'éléments et les règles les plus précieux. Vous définissez ces options dans le **analyse du panier d’achat paramètres boîte de dialogue avancés**.  
  
### <a name="minimum-support"></a>Prise en charge minimale  
 *Prise en charge minimale* signifie que le nombre de transactions qui doivent contenir un jeu d’éléments particulier pour le jeu d’éléments soit considéré comme significatif. Par exemple, vous pouvez ne pas être intéressé par un jeu d'éléments s'il n'a pas été acheté dans au moins 10 transactions différentes. Il existe deux façons de contrôler le seuil pour l’importance du jeu d’éléments et les deux utilisent le **prise en charge minimale** paramètre.  
  
 **Une valeur absolue :** Entrez un nombre qui représente le nombre de transactions qui contiennent les éléments de la cible. Par exemple, si vous entrez 10, tout jeu d'éléments qui apparaît dans au moins 10 paniers d'achat est inclus dans les résultats.  
  
 **En tant que pourcentage :** Entrez un nombre qui représente un pourcentage de la collection entière de jeux d’éléments. Par exemple, si vous spécifiez 10, tous les jeux d'éléments sont comptés et le jeu d'éléments ciblé doit apparaître et constituer au moins 10 pour cent de ce nombre total de jeux d'éléments. Si vous avez un jeu de données très volumineux, l'utilisation de pourcentages à la place d'un nombre peut vous aider à rester concentré sur les groupements d'élément les plus importants.  
  
> [!NOTE]  
>  N'oubliez pas, le nombre de jeux d'éléments est différent du nombre des transactions dans vos données. Chaque transaction peut contenir plusieurs jeux de données ; toutefois, la plupart des jeux d'éléments se répètent plusieurs fois dans le jeu de données.  
  
### <a name="rule-probability-and-rule-importance"></a>Probabilité de règle et importance de la règle  
 La probabilité d'une règle correspond à la probabilité que le résultat de cette règle se produise. La probabilité de règle est calculée en utilisant la fréquence des jeux d'éléments qui prennent en charge une règle. Si un jeu d'éléments se produit très rarement, il aura une faible probabilité.  
  
 Toutefois, les règles qui ont une haute probabilité ne sont pas toujours utiles. Elles peuvent indiquer des jeux d'éléments qui sont fréquemment achetés et, par conséquent, ne nécessitent aucune promotion supplémentaire. L'importance sert à mesurer l'utilité d'une règle. Quelquefois, une règle peut avoir probabilité très haute mais une importance basse, car la prédiction ne fournit pas de nouvelles informations. Par exemple, si tous les jeux d'éléments contiennent un état spécifique d'un attribut, une règle prédisant cet état est insignifiante même si sa probabilité est très élevée.  
  
 Vous devez essayer ces paramètres pour obtenir différents résultats et déterminer quel paramètre produit les règles les plus intéressantes.  
  
## <a name="understanding-the-reports"></a>Présentation des rapports  
 Le **analyse du panier** outil crée deux rapports complémentaires. Le premier rapport, intitulé **groupes importantes des éléments identifiés lors de l’analyse**, fournit une liste de tous les jeux d’éléments qui ont été trouvés. Vous pouvez utiliser les nouveaux outils de table dans Microsoft Excel pour trier, filtrer et explorer les données.  
  
 Le deuxième rapport, intitulé **règles de panier d’achat**, qui vous indique le type d’inférences peut porter sur les jeux d’éléments répertoriés dans le premier rapport. Alors que la liste de jeux d'éléments est plus utile pour explorer et comprendre vos données, la liste de règles est plus utile pour élaborer des prédictions et des recommandations.  
  
### <a name="shopping-basket-item-groups-report"></a>Rapport des groupes d'éléments du panier d'achat  
 Ce rapport contient une liste de toutes les combinaisons possibles des éléments qui ont été trouvés dans votre jeu de données. Par exemple, si vos données de transaction contient des commandes pour chaque commande le **analyse du panier** outil calcule le nombre de fois où l’élément individuel a été commandé, puis calcule toutes les combinaisons de cet élément avec d’autres éléments.  
  
 Le rapport répertorie les jeux d'éléments qui ont été trouvés par ordre de finesse. La finesse est un score qui vous indique l'importance du jeu d'éléments.  
  
|Colonne de rapport|Qu’il vous indique|  
|----------------------|-----------------------|  
|Groupe d'éléments|Répertorie les jeux d'éléments, ou la combinaison d'éléments.|  
|Taille de groupe|Décompte du nombre d'éléments figurant dans le jeu d'éléments. Vous pouvez filtrer sur ce champ pour afficher uniquement des paires d'éléments, des éléments uniques, etc.|  
|Support technique|Décompte du nombre de cas où cette combinaison s'est produite. Vous pouvez trier sur cette colonne pour afficher les jeux d'éléments les plus courants.|  
|Valeur moyenne|Somme de la valeur des éléments figurant uniquement dans ce jeu d'éléments, divisée par la prise en charge. Vous pouvez trier et filtrer sur cette colonne pour cibler des produits dans différentes gammes de prix.|  
|Valeur moyenne du panier|Somme des valeurs de tous les éléments dans les commandes contenant ce jeu d'éléments, divisée par la prise en charge. Cette statistique est intéressante lorsqu'elle est combinée avec la valeur moyenne du jeu d'éléments.|  
|Finesse|Score qui représente le niveau d'intérêt de ce jeu d'éléments dans le jeu de données entier. La finesse est calculée en obtenant la probabilité de voir les deux éléments se produire ensemble, puis en les divisant par la probabilité de voir ces deux éléments se produire séparément. Par conséquent, s'il existe une forte corrélation entre les éléments, le score de finesse sera supérieur.|  
  
### <a name="shopping-basket-rules-report"></a>Rapport des règles du panier d'achat  
 Ce rapport contient un jeu des règles construites en analysant les jeux d'éléments qui ont été trouvés. Par exemple, si vos données de transaction ont révélé que les produits A et B ont fréquemment été achetés ensemble, l'outil Analyse du panier d'achat créera une règle qui prédit A compte tenu de l'existence de B, ou B compte tenu de l'existence de A.  
  
 Chaque règle est associée à une probabilité, dérivée des données de prise en charge. Ces probabilités sont utiles pour élaborer des recommandations. Par exemple, vous pouvez souhaiter consulter uniquement les règles qui ont au moins 50 pour cent de chances d'être exactes, selon les données existantes.  
  
 Le rapport répertorie les jeux d'éléments qui ont été trouvés par ordre de finesse. La finesse est un score qui vous indique l'importance du jeu d'éléments.  
  
|Colonne de rapport|Qu’il vous indique|  
|----------------------|-----------------------|  
|Éléments existants|Répertorie les éléments qui sont nécessaires pour élaborer une recommandation.<br /><br /> Dans l’exploration de données, ces éléments sont dits se situer sur le *gauche* de la règle d’association.|  
|Élément prédit|Répertorie l'élément à recommander.<br /><br /> Dans l’exploration de données, ces éléments sont dits se situer sur le *droite* de la règle d’association.|  
|Probabilité|Affiche la probabilité que cette règle est correcte.|  
|Support technique|Indique le nombre de cas dans les données existantes qui fournissent la preuve pour cette règle.|  
|Valeur de règle|Si vous fournissez une valeur pour les éléments dans le panier d'achat, cette colonne calcule la valeur de la prédiction, compte tenu du coût des éléments.|  
|Finesse|Indique la force de la corrélation entre les éléments dans la première colonne et les éléments dans la deuxième colonne. Également appelé *importance*.<br /><br /> Une finesse 0 équivaut à une absence de corrélation. Une valeur positive signifie que les éléments dans la première colonne prédisent l'élément dans la deuxième colonne. Plus cette valeur est élevée, plus cette corrélation est forte.|  
  
## <a name="related-tools"></a>Outils connexes  
 Le client d'exploration de données pour Excel, complément séparé qui fournit d'autres fonctionnalités d'exploration de données plus avancées, contient aussi un Assistant qui se charge de l'analyse d'association. Pour plus d’informations, consultez [associer un Assistant &#40;Client d’exploration de données pour Excel&#41;](associate-wizard-data-mining-client-for-excel.md).  
  
 Pour plus d'informations sur l'algorithme utilisé pour effectuer cette analyse, consultez la rubrique « Algorithme Microsoft Association » dans la documentation en ligne de SQL Server.  
  
## <a name="see-also"></a>Voir aussi  
 [Outils d’analyse de table pour Excel](table-analysis-tools-for-excel.md)  
  
  