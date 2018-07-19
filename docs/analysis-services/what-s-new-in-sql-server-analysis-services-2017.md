---
title: Quelles sont les nouveautés dans SQL Server Analysis Services 2017 | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c05e5d59dd303f6f0c74eaab0e749fe6c8252f32
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38042357"
---
# <a name="whats-new-in-sql-server-2017-analysis-services"></a>Quelles sont les nouveautés dans SQL Server 2017 Analysis Services
[!INCLUDE[ssas-appliesto-sql2017](../includes/ssas-appliesto-sql2017.md)]

SQL Server Analysis Services 2017 Découvrez certaines des améliorations plus importantes depuis SQL Server 2012. S’appuyant sur le succès du mode tabulaire (introduit dans SQL Server 2012 Analysis Services), cette version rend les modèles tabulaires plus puissante que jamais.

Mode multidimensionnel et PowerPivot pour le mode SharePoint sont un élément de base pour de nombreux déploiements d’Analysis Services. Dans le cycle de vie du produit de Analysis Services, ces modes sont matures. Il n’existe pas de nouvelles fonctionnalités pour une de ces modes dans cette version. Toutefois, les correctifs de bogues et améliorations des performances sont incluses.

Les fonctionnalités décrites ici sont incluses dans SQL Server 2017 Analysis Services. Mais pour tirer parti de ces fonctionnalités, vous devez également utiliser les dernières versions de [SQL Server Data Tools](../ssdt/download-sql-server-data-tools-ssdt.md) (SSDT) et [SQL Server Management Studio](../ssms/download-sql-server-management-studio-ssms.md) (SSMS). SSDT et SSMS sont mis à jour tous les mois des fonctionnalités nouvelles et améliorées qui coïncident généralement avec de nouvelles fonctionnalités dans SQL Server.  

S’il est important d’en savoir plus sur les nouvelles fonctionnalités, il est également important de savoir ce qui est en cours de déconseillées et supprimées dans cette version et les versions futures. Veillez à consulter [la compatibilité descendante (SQL Server 2017 Analysis Services)](analysis-services-backward-compatibility-sql2017.md).

Jetons un œil à certaines des nouvelles fonctionnalités majeures dans cette version.

## <a name="1400-compatibility-level-for-tabular-models"></a>Niveau de compatibilité 1400 pour les modèles tabulaires
  Pour tirer parti de la plupart des nouvelles fonctionnalités et des fonctionnalités décrites ici, les modèles tabulaires nouveau ou existants doivent être définis ou mis à niveau vers le niveau de compatibilité 1400. Les modèles au niveau de compatibilité 1400 ne peuvent pas être déployés vers SQL Server 2016 SP1 ou version antérieure, ni passés à une version antérieure pour réduire les niveaux de compatibilité. Pour plus d’informations, consultez [niveau de compatibilité pour les modèles tabulaires Analysis Services](../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md).
  
Dans SSDT, vous pouvez sélectionner le nouveau niveau de compatibilité 1400 lors de la création de projets de modèles tabulaires. 

![AS_NewTabular1400Project](../analysis-services/media/as-newtabular1400project.png)


Pour mettre à niveau un modèle tabulaire existant dans SSDT, dans l’Explorateur de solutions, cliquez sur **Model.bim**, puis dans **propriétés**, définissez le **niveau de compatibilité** propriété  **SQL Server 2017 (1400)**. 

![AS_Model_Properties](../analysis-services/media/as-model-properties.png)

Il est important de garder à l’esprit, une fois que vous mettez à niveau un modèle existant à 1400, vous ne pouvez pas rétrograder. Veillez à garder une sauvegarde de votre base de données model 1200.

## <a name="modern-get-data-experience"></a>Expérience moderne d’obtention des données
Lorsqu’il s’agit de l’importation de données à partir de sources de données dans vos modèles tabulaires, SQL Server Data Tools (SSDT) introduit la modern **obtenir des données** expérience pour les modèles au niveau de compatibilité 1400. Cette nouvelle fonctionnalité est basée sur des fonctionnalités similaires de Power BI Desktop et de Microsoft Excel 2016. L’expérience moderne Get Data fournit la transformation de données immenses opportunités et les fonctionnalités de mashup des données en utilisant le Générateur de requêtes d’obtenir des données et les expressions M.

L’expérience moderne Get Data prend en charge un large éventail de sources de données. À l’avenir, les mises à jour prendra en charge encore plus importantes.

![AS_Get_Data_in_SSDT](../analysis-services/media/as-get-data-in-ssdt.png)

 Une interface utilisateur intuitive et puissante permet de sélectionner vos données et les fonctionnalités de transformation/mashup des données plus faciles que jamais.

![Application Web hybride avancé](../analysis-services/media/as-get-data-advanced.png)


Expérience moderne Get Data et les fonctionnalités de mashup M ne s’appliquent pas aux upraded de modèles tabulaires existants à partir du niveau de compatibilité 1200 à 1400. La nouvelle expérience s’applique uniquement aux nouveaux modèles créés au niveau de compatibilité 1400.

## <a name="encoding-hints"></a>Indications de codage
Cette version introduit des indications de codage, une fonctionnalité avancée permet d’optimiser les modèles tabulaires en mémoire volumineux, le traitement (actualisation des données). Pour mieux comprendre le codage, voir [performances réglage de modèles tabulaires dans SQL Server 2012 Analysis Services](https://msdn.microsoft.com/library/dn393915.aspx) livre blanc pour mieux comprendre l’encodage.

* Valeur d’encodage offre de meilleures performances de requête pour les colonnes qui sont généralement utilisés uniquement pour les agrégations.

* Codage de hachage est préférable pour les colonnes group by (souvent des valeurs de table de dimension) et les clés étrangères. Colonnes de type chaîne sont toujours hachage encodé.

Colonnes numériques peuvent utiliser une de ces méthodes d’encodage. Lorsque Analysis Services commence à traiter une table, si la table est vide (avec ou sans partitions) ou une opération de traitement de la table entière est effectuée, les exemples de valeurs sont effectuées pour chaque colonne déterminer s’il faut appliquer l’encodage de hachage ou de la valeur numérique . Par défaut, le codage de valeur est choisi lorsque l’exemple de valeurs distinctes dans la colonne est suffisamment grand : sinon codage de hachage fournit généralement une meilleure compression. Il est possible pour Analysis Services modifier la méthode de codage, une fois que la colonne est partiellement traitée en fonction de plus d’informations sur la distribution des données et redémarrer le processus d’encodage ; Toutefois, cela augmente le temps de traitement et est inefficace. Le livre blanc de réglage des performances présente le nouvel encodage plus en détail et explique comment détecter à l’aide de SQL Server Profiler.

Indications de codage permettent le Modeleur de spécifier une préférence pour la méthode de codage donnée connaissance préalable de profilage des données et/ou en réponse à la ré-encodage des événements de trace. Dans la mesure où l’agrégation sur les colonnes de hachage encodé est plus lente que sur les colonnes de valeur encodée, l’encodage de valeur peut être spécifié en tant qu’indicateur pour ces colonnes. Il n’est pas garanti que la préférence est appliquée. C’est un indice par opposition à un paramètre. Pour spécifier un indicateur d’encodage, définissez la propriété EncodingHint sur la colonne. Les valeurs possibles sont « Default », « Valeur » et « Hachage ». L’extrait suivant de métadonnées JSON à partir du fichier Model.bim spécifie la valeur d’encodage pour la colonne de montant des ventes.

```
{
    "name": "Sales Amount",
    "dataType": "decimal",
    "sourceColumn": "SalesAmount",
    "formatString": "\\$#,0.00;(\\$#,0.00);\\$#,0.00",
    "sourceProviderType": "Currency",
    "encodingHint": "Value"
}
```

## <a name="ragged-hierarchies"></a>Hiérarchies déséquilibrées
Dans les modèles tabulaires, vous pouvez modéliser les hiérarchies parent-enfant. Les hiérarchies avec différents nombres de niveaux sont souvent appelées hiérarchies déséquilibrées. Par défaut, les hiérarchies déséquilibrées sont affichées avec des vides pour les niveaux en dessous de l’enfant le plus bas. Voici un exemple de hiérarchie déséquilibrée dans un organigramme :

![AS_Ragged_Hierarchy](../analysis-services/media/as-ragged-hierarchy.png)

Cette version introduit la propriété **Masquer les membres** . Vous pouvez définir la propriété **Masquer les membres** pour une hiérarchie sur **Masquer les membres vides**.

![AS_Hide_Blank_Members](../analysis-services/media/as-hide-blank-members.png)

 >[!NOTE]
 > Dans le modèle, les membres vides sont représentés par une valeur vide DAX, et non par une chaîne vide.

Lorsque la propriété **Masquer les membres vides**est définie, et lorsque le modèle est déployé, une version plus lisible de la hiérarchie est affichée dans les clients de gestion de rapports comme Excel.

![AS_Non_Ragged_Hierarchy](../analysis-services/media/as-non-ragged-hierarchy.png)


## <a name="detail-rows"></a>Lignes de détails
Vous pouvez maintenant définir un ensemble de lignes personnalisées contribuant à une valeur de mesure. Les lignes de détails sont similaires à l’action d’extraction par défaut dans les modèles multidimensionnels. Cela permet aux utilisateurs finaux d’afficher des informations de manière plus détaillée que le niveau agrégé. 

Le tableau croisé dynamique suivant montre le total des ventes sur Internet par an de l’exemple de modèle tabulaire Adventure Works. Cliquez avec le bouton droit sur une cellule avec une valeur agrégée de la mesure, puis cliquez sur **Afficher les détails** pour afficher les lignes de détails.

![AS_Show_Details](../analysis-services/media/as-show-details.png)

Par défaut, les données associées à la table des ventes sur Internet s’affiche. Ce comportement limité n’est généralement pas significatif pour l’utilisateur car la table ne dispose peut-être pas des colonnes nécessaires pour afficher des informations utiles telles que le nom du client et les informations de commande. Avec les lignes de détails, vous pouvez spécifier une propriété **Expression de lignes de détails** pour les mesures.

#### <a name="detail-rows-expression-property-for-measures"></a>Propriété Expression de lignes de détails pour les mesures
La propriété **Expression de lignes de détails** pour les mesures permet aux créateurs de modèles de personnaliser les colonnes et les lignes renvoyées à l’utilisateur final.

![AS_Detail_Rows_Expression_Property](../analysis-services/media/as-detail-rows-expression-property.png)

Le [SELECTCOLUMNS](https://msdn.microsoft.com/library/mt761759.aspx) DAX fonction est couramment utilisée dans une Expression de lignes de détail. L’exemple suivant définit les colonnes à renvoyer pour les lignes dans la table des ventes sur Internet, dans l’exemple de modèle tabulaire Adventure Works :

```
SELECTCOLUMNS(
    'Internet Sales',
    "Customer First Name", RELATED( Customer[Last Name]),
    "Customer Last Name", RELATED( Customer[First Name]),
    "Order Date", 'Internet Sales'[Order Date],
    "Internet Total Sales", [Internet Total Sales]
)
```

Lorsque la propriété est définie et lorsque le modèle est déployé, un ensemble de lignes personnalisé est renvoyé quand l’utilisateur sélectionne **Afficher les détails**. Il respecte automatiquement le contexte de filtre de la cellule sélectionnée. Dans cet exemple, seules les lignes pour la valeur 2010 sont affichées :

![AS_Detail_Rows](../analysis-services/media/as-detail-rows.png)

#### <a name="default-detail-rows-expression-property-for-tables"></a>Propriété Expression de lignes de détails par défaut pour les tables
Outre les mesures, les tables possèdent également une propriété pour définir une expression de lignes de détails. La propriété **Expression de lignes de détails par défaut** agit comme valeur par défaut pour toutes les mesures de la table. Les mesures qui n’ont pas leur propre expression définie hérite de l’expression de la table et afficher l’ensemble de lignes défini pour la table. Ceci permet de réutiliser des expressions et ajoutées à la table ultérieurement automatiquement de nouvelles mesures hérite de l’expression.

![AS_Default_Detail_Rows_Expression](../analysis-services/media/as-default-detail-rows-expression.png)
 
#### <a name="detailrows-dax-function"></a>Fonction DETAILROWS DAX
Cette version comprend une nouvelle fonction DAX `DETAILROWS` qui renvoie l’ensemble de lignes défini par l’expression de lignes de détails. Elle fonctionne de façon similaire à l’instruction `DRILLTHROUGH` dans MDX, qui est également compatible avec les expressions de lignes de détails définies dans les modèles tabulaires.

La requête DAX suivante retourne l’ensemble de lignes défini par l’expression de lignes de détails pour la mesure ou pour sa table. Si aucune expression n’est définie, les données pour la table des ventes sur Internet sont renvoyées, car c’est la table qui contient la mesure.

```
EVALUATE DETAILROWS([Internet Total Sales])
```

## <a name="object-level-security"></a>Sécurité au niveau de l’objet
Cette version introduit [sécurité au niveau de l’objet](../analysis-services/tabular-models/object-level-security.md) pour les tables et colonnes. En plus de restreindre l’accès aux données de table et de colonne, noms de table et de colonne sensibles peuvent être sécurisées. Cela permet d’empêcher qu’un utilisateur malveillant découvre l’existence de cette table.

Sécurité au niveau de l’objet doit être définie en utilisant les métadonnées basé sur JSON, tabulaire modèle Scripting Language (TMSL) ou le modèle d’objet tabulaire (TOM). 

Par exemple, le code suivant permet de sécuriser la table Produit dans l’exemple de modèle tabulaire Adventure Works en définissant la propriété **MetadataPermission** de la classe **TablePermission** sur **Aucun**.

```
//Find the Users role in Adventure Works and secure the Product table
ModelRole role = db.Model.Roles.Find("Users");
Table productTable = db.Model.Tables.Find("Product");
if (role != null && productTable != null)
{
    TablePermission tablePermission;
    if (role.TablePermissions.Contains(productTable.Name))
    {
        tablePermission = role.TablePermissions[productTable.Name];
    }
    else
    {
        tablePermission = new TablePermission();
        role.TablePermissions.Add(tablePermission);
        tablePermission.Table = productTable;
    }
    tablePermission.MetadataPermission = MetadataPermission.None;
}
db.Update(UpdateOptions.ExpandFull);
```

## <a name="dynamic-management-views-dmvs"></a>Vues de gestion dynamique
[Vues de gestion dynamique](../analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md) dans SQL Server Profiler, les requêtes qui retournent des informations sur les opérations de serveur local et de l’intégrité du serveur.
Cette version inclut les améliorations apportées à [vues de gestion dynamique](https://docs.microsoft.com/sql/analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services) (DMV) pour les modèles tabulaires aux niveaux de compatibilité 1200 et 1400.

[DISCOVER_CALC_DEPENDENCY](../analysis-services/schema-rowsets/xml/discover-calc-dependency-rowset.md) fonctionne désormais avec les modèles tabulaires 1200 et 1400. Les modèles tabulaires 1400 affichent les dépendances entre les partitions M, les expressions M et les sources de données structurées. Pour plus d’informations, consultez le [blog Analysis Services](https://blogs.msdn.microsoft.com/analysisservices/2017/07/17/whats-new-in-sql-server-2017-rc1-for-analysis-services/).

[MDSCHEMA_MEASUREGROUP_DIMENSIONS](../analysis-services/schema-rowsets/ole-db-olap/mdschema-measuregroup-dimensions-rowset.md) améliorations sont incluses pour cette vue DMV, qui est utilisée par les outils clients différents pour afficher la dimensionnalité de mesure. Par exemple, la fonctionnalité Explorer dans les tableaux croisés dynamiques Excel permet à l’utilisateur à cross-extraction des dimensions associées pour les mesures sélectionnées. Cette version corrige les colonnes de cardinalité, qui ont été précédemment montrant les valeurs incorrectes.

## <a name="dax-enhancements"></a>Améliorations DAX
Cette version inclut la prise en charge des fonctionnalités et de nouvelles fonctions DAX. Pour tirer parti, vous devez utiliser la dernière version de SSDT. Pour plus d’informations, consultez [fonctions DAX nouvelle](https://msdn.microsoft.com/library/mt704075.aspx).

Un des éléments plus importants de nouvelles fonctionnalités DAX est la nouvelle [opérateur IN / fonction CONTAINSROW](https://msdn.microsoft.com/library/mt842621.aspx) pour les expressions DAX. Elle est similaire à l’opérateur [`TSQL IN`](https://msdn.microsoft.com/library/ms177682.aspx) couramment utilisé pour spécifier plusieurs valeurs dans une clause `WHERE` .

Auparavant, il était courant de spécifier des filtres à valeurs multiples à l’aide de l’opérateur `OR` logique comme dans l’expression de mesure suivante :

```
Filtered Sales:=CALCULATE (
        [Internet Total Sales],
                 'Product'[Color] = "Red"
            || 'Product'[Color] = "Blue"
            || 'Product'[Color] = "Black"
    )
```

Ce processus est simplifié à l’aide de l’opérateur `IN` :
```
Filtered Sales:=CALCULATE (
        [Internet Total Sales], 'Product'[Color] IN { "Red", "Blue", "Black" }
    )
```

Dans ce cas, l’opérateur `IN` fait référence à une table d’une seule colonne avec 3 lignes ; une pour chacune des couleurs spécifiées. Notez que la syntaxe du constructeur de table utilise des accolades.

L’opérateur `IN` équivaut d’un point de vue fonctionnel à la fonction `CONTAINSROW` :
```
Filtered Sales:=CALCULATE (
        [Internet Total Sales], CONTAINSROW({ "Red", "Blue", "Black" }, 'Product'[Color])
    )
```

L’opérateur `IN` peut également être utilisé efficacement avec les constructeurs de table. Par exemple, la mesure suivante filtre par combinaisons de couleurs et de catégories de produits :
```
Filtered Sales:=CALCULATE (
        [Internet Total Sales],
        FILTER( ALL('Product'),
              ( 'Product'[Color] = "Red"   && Product[Product Category Name] = "Accessories" )
         || ( 'Product'[Color] = "Blue"  && Product[Product Category Name] = "Bikes" )
         || ( 'Product'[Color] = "Black" && Product[Product Category Name] = "Clothing" )
        )
    )
```

Avec le nouvel opérateur `IN` , l’expression de mesure ci-dessus est maintenant équivalente à celle qui suit :
```
Filtered Sales:=CALCULATE (
        [Internet Total Sales],
        FILTER( ALL('Product'),
            ('Product'[Color], Product[Product Category Name]) IN
            { ( "Red", "Accessories" ), ( "Blue", "Bikes" ), ( "Black", "Clothing" ) }
        )
    )
```

## <a name="additional-improvements"></a>Autres améliorations
En plus de toutes les nouvelles fonctionnalités, Analysis Services, SSDT et SSMS incluent également les améliorations suivantes :

* Réutilisation de hiérarchie et de colonne apparaît dans des emplacements plus utiles dans la liste de champs Power BI.
* Relations de dates pour créer facilement des relations aux dimensions de date en fonction des champs de date.
* Option d’installation par défaut pour Analysis Services est désormais pour le mode tabulaire.
* Nouvelles sources de données d’obtenir des données (Power Query).
* Éditeur DAX pour SSDT.
* Les sources de données DirectQuery existantes prennent en charge pour les requêtes de M.
* Améliorations de SSMS, notamment l’affichage, la modification et la prise en charge des sources de données structurées de script.



## <a name="see-also"></a>Voir aussi
[Notes de mise à jour de SQL Server 2017](../sql-server/sql-server-2017-release-notes.md)   
[Nouveautés de SQL Server 2017](../sql-server/what-s-new-in-sql-server-2017.md)
