---
title: Concepts clés pour MDX (Analysis Services) | Microsoft Docs
ms.date: 04/19/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b00478a739796d27b44899aa72099583b1d9a113
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59962165"
---
# <a name="key-concepts-in-mdx-analysis-services"></a>Concepts clés dans MDX (Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Avant de pouvoir utiliser MDX (Multidimensional Expressions) pour interroger des données multidimensionnelles ou créer des expressions MDX dans un cube, vous devez vous familiariser avec les concepts et les termes liés aux données multidimensionnelles.  
  
 Le plus simple est de commencer par un exemple de synthèse de données que vous connaissez déjà, puis d'évaluer MDX de ce point de vue. Voici un tableau croisé dynamique créé dans Excel, rempli avec les données à partir d’un exemple de cube Analysis Services.  
  
 ![Tableau croisé dynamique avec des mesures et dimensions appelées](../../../analysis-services/multidimensional-models/media/ssas-keyconcepts-pivot1-measures-dimensions.png "tableau croisé dynamique avec des mesures et dimensions appelées")  
  
## <a name="measures-and-dimensions"></a>Mesures et dimensions  
 Un cube Analysis Services est composé de mesures, de dimensions et d'attributs de dimension, ce que l'on observe très bien dans notre exemple de tableau croisé dynamique.  
  
 Les**mesures** sont des valeurs de données numériques dans des cellules, agrégées sous forme de somme, nombre, pourcentage, min, max ou moyenne. Les valeurs mesurées sont dynamiques, calculées en temps réel en réponse à la navigation de l'utilisateur et à l'interaction avec le tableau croisé dynamique. Dans cet exemple, les cellules indiquent des montants Reseller Sales Amounts qui augmentent ou diminuent selon que vous développez ou réduisez les axes. Pour toute combinaison de Date (année, trimestre, mois ou date) et de Sales Territory (Country group, Country, Region) vous pouvez obtenir un montant Reseller Sales Amount pour le contexte en question. Les faits (dans les entrepôts de données) et les champs calculés (dans les modèles de données tabulaires et Excel) sont d'autres termes synonymes de mesures.  
  
 Les**dimensions** sont les axes de colonne et de ligne d'un tableau croisé dynamique. Elles donnent une signification à la mesure. Les dimensions s'apparentent aux tables d'un modèle de données relationnelles. Temps, Géographie, Produits, Clients, Employés, et ainsi de suite, sont des exemples de dimension courantes. Cet exemple comporte deux dimensions, Sales Territory sur les lignes et Date en haut, mais vous pourriez facilement faire glisser et déplacer d'autres dimensions associées à Reseller Sales, telles que Promotions ou Products, pour afficher les performances de ventes pour ces dimensions. Votre capacité à explorer les données de manière intéressante dépend des dimensions que vous créez et du fait qu'elles sont liées aux tables de faits dans votre source de données.  
  
 Les**attributs de dimension** sont les éléments nommés dans une dimension. Ils s'apparentent aux colonnes d'une table. Dans cet exemple, les attributs de la dimension Sales Territory sont Country Group (Europe, North America, Pacific), Country (Canada, United States) et Region (Central, Northeast, Northwest, Southeast, Southwest).  
  
 Chaque attribut est associé à une collection de valeurs de données, ou membres. Dans notre exemple, les membres de l'attribut Country Group sont Europe, North America et Pacific. Les**membres** sont les valeurs de données réelles qui appartiennent à un attribut.  
  
> [!NOTE]  
>  L'un des aspects de la modélisation des données est la formalisation des modèles et des relations qui existent déjà dans les données proprement dites. Lors de l’utilisation de données qui respectent une hiérarchie naturelle, comme c’est le cas avec pays-régions-villes, vous pouvez formaliser cette relation en créant une **relation d’attribut**. Une relation d’attribut est une relation un-à-plusieurs entre les attributs, par exemple, une relation entre un état et une ville : un état a de nombreuses villes, mais une ville n’appartient qu’un seul état. Création de relations d’attributs dans le modèle accélère les performances de la requête, il est recommandé de les créer si les données le prend en charge. Vous pouvez créer une relation d'attribut dans le Concepteur de dimensions de SQL Server Data Tools. Consultez [Define Attribute Relationships](../../../analysis-services/multidimensional-models/attribute-relationships-define.md).  
  
 Dans Excel, les métadonnées de modèle figurent dans la liste des champs du tableau croisé dynamique.  Comparez le tableau croisé dynamique ci-dessus à la liste de champs ci-dessous. Notez que la liste de champs contient Sales Territory, Group, Country, Region (métadonnées), tandis que le tableau croisé dynamique contient uniquement les membres (valeurs de données). Le fait de connaître la signification des icônes peut vous aider à mettre facilement en rapport les différentes parties d'un modèle multidimensionnel avec un tableau croisé dynamique dans Excel.  
  
 ![Liste de champs de tableau croisé dynamique](../../../analysis-services/multidimensional-models/mdx/media/ssas-keyconcepts-ptfieldlist.png "liste de champs de tableau croisé dynamique")  
  
## <a name="attribute-hierarchies"></a>Hiérarchies d'attributs  
 Presque sans avoir à y réfléchir, vous savez que les valeurs d'un tableau croisé dynamique montent ou descendent à mesure que vous développez ou réduisez les niveaux le long de chaque axe, mais à quoi cela est-il dû ? La réponse est liée aux hiérarchies d'attributs.  
  
 Réduisez tous les niveaux et notez les totaux de chaque Country Group et Calendar Year. La valeur est dérivée d’un élément nommé **membre (All)** dans une hiérarchie. Le membre (All) désigne la valeur calculée de tous les membres dans une hiérarchie d'attribut.  
  
-   Le membre (All) pour tous les Country Groups et les Dates combinés est $80 450 596,98  
  
-   Le membre (All) pour CY2008 est $16 038 062,60  
  
-   Le membre (All) pour Pacific est $1 594 335,38  
  
 Les agrégats tels que ceux-ci sont précalculés et stockés au préalable, ce qui constitue l'un des facteurs de performances des requêtes Analysis Services.  
  
 ![Tableau croisé dynamique avec tous les membres appelés](../../../analysis-services/multidimensional-models/mdx/media/ssas-keyconcepts-pivot2-allmember.png "tableau croisé dynamique avec tous les membres appelés")  
  
 Développez la hiérarchie et vous finissez par atteindre le niveau le plus bas. Il s'agit du **membre feuille**. Un membre feuille appartient à une hiérarchie qui n'a pas d'enfants. Dans cet exemple, Sud-Ouest est le membre feuille.  
  
 ![Tableau croisé dynamique avec un membre feuille](../../../analysis-services/multidimensional-models/mdx/media/ssas-keyconcepts-pivot3-leafparent.PNG "tableau croisé dynamique avec un membre feuille")  
  
 Tout ce qui se trouve plus haut est un **membre parent**. United States est le parent de la région Sud-Ouest.  
  
 **Composants d'une hiérarchie d'attribut**  
  
 Ensemble, tous ces concepts mènent à celui de **hiérarchie d'attribut**. Une hiérarchie d'attribut est une arborescence de membres d'attributs composée des niveaux suivants :  
  
-   un niveau feuille accueillant chaque membre d'attribut distinct (chaque membre du niveau feuille est également connu sous le terme de **membre feuille**) ;  
  
-   des niveaux intermédiaires si la hiérarchie d'attribut est une hiérarchie parent-enfant (voir plus loin) ;  
  
-   un membre (All) qui contient la valeur agrégée de tous les attributs enfants. Si vous le souhaitez, vous pouvez masquer ou désactiver le niveau (All) lorsqu’il est inutile pour les données. Par exemple, bien que Product Code soit numérique, il n’aurait aucun sens pour une somme ou moyenne ou agréger tous les Codes de produit.  
  
> [!NOTE]  
>  Les développeurs BI définissent souvent des propriétés sur la hiérarchie d'attribut afin d'obtenir certains comportements des applications clientes ou certains avantages en termes de performances. Par exemple, vous pourriez définir AttributeHierarchyEnabled = False sur les attributs pour lesquels le membre (All) est inutile. Vous pourriez également simplement masquer le membre (All), auquel cas vous définiriez AttributeHierarchyVisible=False. Pour plus d'informations sur les propriétés, consultez [Dimension Attribute Properties Reference](../../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md) .  
  
## <a name="navigation-hierarchies"></a>Hiérarchies de navigation  
 Dans le tableau croisé dynamique (tout du moins dans notre exemple), les axes des lignes et des colonnes se développent pour afficher des niveaux d'attributs inférieurs. On obtient une arborescence extensible grâce aux hiérarchies de navigation créées dans un modèle.  Dans l'exemple de modèle AdventureWorks, la dimension Sales Territory possède une hiérarchie multiniveau qui commence par un Country Group, suivi de Country, suivi de Region.  
  
 Comme vous pouvez le voir, les hiérarchies servent à fournir un itinéraire de navigation dans un tableau croisé dynamique ou d'autres objets de synthèse de données. Il existe deux types de base : équilibré et non équilibré.  
  
 **Hiérarchies équilibrées**  
  
|||  
|-|-|  
|![Tableau croisé dynamique avec légende hiérarchie équilibrée appelé](../../../analysis-services/multidimensional-models/mdx/media/ssas-keyconcepts-pivot4-balancedhierarchy.PNG "tableau croisé dynamique avec légende hiérarchie équilibrée appelé")|Une **hiérarchie équilibrée** est une hiérarchie dans laquelle il existe le même nombre de niveaux entre le niveau supérieur et n'importe quel membre feuille.<br /><br /> Une **hiérarchie naturelle** est une hiérarchie qui émerge naturellement des données sous-jacentes. Pays-Région-Département, Année-Mois-Date ou Catégorie-Sous-catégorie-Modèle sont des exemples courants ; chaque niveau inférieur découle naturellement et de manière prévisible de son parent.<br /><br /> Dans un modèle multidimensionnel, la plupart des hiérarchies sont des hiérarchies équilibrées et bon nombre d'entre elles sont également des hiérarchies naturelles.<br /><br /> **Hiérarchie définie par l’utilisateur**est un autre terme de modélisation en rapport avec ce concept. On l’utilise souvent par opposition avec les hiérarchies d’attributs. Il fait simplement référence à une hiérarchie créée par le développeur BI, par opposition aux hiérarchies d'attributs générées automatiquement par Analysis Services lorsque vous définissez un attribut.|  
  
 **Hiérarchies déséquilibrées**  
  
|||  
|-|-|  
|![Tableau croisé dynamique avec légende hiérarchie irrégulière appelé](../../../analysis-services/multidimensional-models/mdx/media/ssas-keyconcepts-pivot15-raggedhierarchy.PNG "tableau croisé dynamique avec légende hiérarchie irrégulière appelé")|Une **hiérarchie irrégulière** ou **hiérarchie déséquilibrée** est une hiérarchie dans laquelle il existe de nombreux niveaux différents entre le niveau supérieur et les membres feuille. Là encore, il est une hiérarchie créée par le développeur BI, mais dans ce cas il existe des écarts dans les données.<br /><br /> Dans l'exemple de modèle AdventureWorks, Sales Territory constitue une hiérarchie irrégulière car les États-Unis ont un niveau supplémentaire (Regions) qui n'existe pas pour les autres pays de cet exemple.<br /><br /> Les hiérarchies irrégulières présentent des difficultés pour les développeurs BI si l'application cliente ne les gère pas de manière élégante. Dans le modèle Analysis Services, vous pouvez générer une **hiérarchie parent-enfant** qui définit de manière explicite une relation entre des données à plusieurs niveaux, éliminant ainsi toute ambiguïté quant aux rapports entre un niveau et le suivant. Pour plus d’informations, consultez [Dimensions Parent-enfant](../../../analysis-services/multidimensional-models/parent-child-dimension.md) .|  
  
## <a name="key-attributes"></a>Attributs clés  
 Les modèles sont une collection d'objets liés qui reposent sur des clés et des index pour établir les associations. Les modèles Analysis Services ne diffèrent en rien de ce point de vue. Pour chaque dimension (souvenez-vous que cela équivaut à une table dans un modèle relationnel), il existe un attribut clé. **L’attribut clé** est utilisé dans les relations entre les clés étrangères et la table de faits (groupe de mesures). Tous les attributs non-clés de la dimension sont liés (directement ou indirectement) à l'attribut clé.  
  
 Souvent, mais pas toujours, l'attribut clé est également l' **attribut de granularité**. La granularité renvoie au niveau de détail ou de précision des données. Là encore, un exemple courant permet de mieux comprendre de quoi il s'agit. Tenez compte des valeurs de date : Pour les ventes quotidiennes, vous avez besoin de valeurs de date spécifiées au jour ; pour les quotas, tous les trimestres peuvent suffire, mais si vos données analytiques sont constituées de résultats d’une course à partir d’un événement sportif, le niveau de granularité très devra peut-être être millisecondes. Le niveau de précision de vos valeurs de données est le grain.  
  
 Devise est un autre exemple : une application financière peut effectuer le suivi valeurs monétaires à plusieurs décimales, tandis que la collecte de fonds de votre établissement local besoin de ces valeurs au dollar plus proche. La compréhension du grain est importante, car il vaut mieux éviter de stocker des données inutiles. La suppression des millisecondes d'un horodateur ou des centimes d'un montant des ventes peut économiser du stockage et du temps de traitement lorsque ce niveau de détail n'est pas pertinent pour votre analyse.  
  
 Pour définir l'attribut de granularité, utilisez l'onglet Utilisation de la dimension du Concepteur de cube dans SQL Server Data Tools. Dans l'exemple de modèle AdventureWorks, l'attribut clé de la dimension Date est la clé Date. Pour Sales Orders, l'attribut de granularité équivaut à l'attribut clé. Pour Sales Targets, le niveau de granularité est trimestrielle. L'attribut de granularité est donc défini sur Calendar Quarter.  
  
 ![Modèle montrant l’attribut de granularité](../../../analysis-services/multidimensional-models/mdx/media/ssas-keyconcepts-granularityattrib.png "modèle montrant l’attribut de granularité")  
  
> [!NOTE]  
>  Si l'attribut de granularité et l'attribut clé sont différents, tous les attributs non-clés doivent être liés, directement ou indirectement, à l'attribut de granularité. Dans un cube, l'attribut de granularité définit la granularité d'une dimension.  
  
## <a name="query-scope-cube-space"></a>Étendue de requête (espace du cube)  
 L'étendue d'une requête désigne les limites dans lesquelles les données sont sélectionnées. Elle peut aller du cube entier (un cube est l'objet de requête le plus grand) à une cellule.  
  
 L'**espace du cube** est le produit des membres des hiérarchies d'attribut d'un cube associés aux mesures du cube.  
  
 Un**sous-cube** est le sous-ensemble d'un cube qui représente une vue filtrée du cube. Les sous-cubes peuvent être définis dans une instruction Scope à l'intérieur du script de calcul MDX, dans une clause de sous-sélection au sein d'une requête MDX ou en tant que cube de session.  
  
 Une**cellule** désigne l'espace à l'intersection d'un membre du membre de dimension de mesures et d'un membre de chaque hiérarchie d'attribut dans un cube.  
  
## <a name="other-modeling-terms"></a>Autres termes de modélisation  
 Cette section est une collection de concepts et termes qui n’appartiennent à d’autres sections, mais vous devez toujours savoir sur.  
  
 Un**membre calculé** est un membre de dimension défini et calculé au moment de la requête. Il peut être défini dans une requête de l'utilisateur ou dans le script de calcul MDX et stocké sur le serveur. Un membre calculé correspond aux lignes dans la table de dimension de la dimension dans laquelle il est défini.  
  
 **Comptage de valeurs** est un type spécial de mesure utilisé pour les éléments de données qui ne doivent être comptés qu'une seule fois. L'exemple de modèle AdventureWorks contient des mesures de comptage de valeurs pour Internet Orders, Reseller Orders et Sales Orders.  
  
 Les**groupes de mesures** sont une collection composée d'une ou plusieurs mesures. Ils sont pour la plupart définis par l'utilisateur et vous les utilisez pour maintenir une association entre des mesures liées. Les mesures de comptage de valeurs sont une exception. Elles sont toujours placées dans un groupe de mesures dédié qui contient uniquement la mesure de comptage. Vous ne voyez pas le groupe de mesures dans l’illustration d’exemple de tableau croisé dynamique, mais il apparaît dans une liste de champs de tableau croisé dynamique, comme une collection nommée de mesures.  
  
 Une**dimension de mesures** est la dimension qui accueille toutes les mesures figurant dans un cube. Il n’est pas exposé dans un modèle multidimensionnel que vous générez dans SQL Server Data Tools, mais il existe quand même. Comme une dimension de mesures contient des mesures, tous ses membres sont en général agrégés (par somme ou par nombre).  
  
 **Dimensions de base de données et dimensions de cube**. Dans un modèle, vous pouvez définir des dimensions autonomes qui sont ensuite incluses dans un nombre quelconque de cubes du même modèle. Lorsque vous ajoutez une dimension à un cube, il s’agit d’une dimension de cube. Par lui-même dans un projet, comme un élément autonome dans l’Explorateur d’objets, il s’agit d’une dimension de base de données. Pourquoi cette distinction ? Car vous pouvez définir des propriétés dessus indépendamment. Dans la documentation du produit, vous verrez les deux termes utilisés, il est utile de comprendre leur signification.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Maintenant que vous avez compris la terminologie et saisi les concepts importants, vous pouvez continuer avec ces rubriques supplémentaires qui expliquent plus en détails les concepts fondamentaux d'Analysis Services :  
  
-   [Requête MDX de base &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-the-basic-query.md)  
  
-   [Script MDX de base &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/the-basic-mdx-script-mdx.md)  
  
-   [Modélisation multidimensionnelles &#40;didacticiel Adventure Works&#41;](../../../analysis-services/multidimensional-modeling-adventure-works-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Cube Space](../../../analysis-services/multidimensional-models/mdx/cube-space.md)   
 [Tuples](../../../analysis-services/multidimensional-models/mdx/tuples.md)   
 [Autoexists](../../../analysis-services/multidimensional-models/mdx/autoexists.md)   
 [Utilisation de membres, de tuples et de jeux &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/working-with-members-tuples-and-sets-mdx.md)   
 [Valeurs totales affichées et non affichées](../../../analysis-services/multidimensional-models/mdx/visual-totals-and-non-visual-totals.md)   
 [Principes de base des requêtes MDX &#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)   
 [Principes de base des scripts MDX &#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md)   
 [Informations de référence sur le langage MDX &#40;MDX&#41;](../../../mdx/mdx-language-reference-mdx.md)   
 [Référence MDX &#40;Multidimensional Expressions&#41;](../../../mdx/multidimensional-expressions-mdx-reference.md)  
  
  
