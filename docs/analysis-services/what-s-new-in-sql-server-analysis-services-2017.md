---
title: Quel &#39; est nouvelle dans SQL Server 2017 Analysis Services | Documents Microsoft
ms.custom: 
ms.date: 07/27/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1eb6afc9-76ed-45a2-a188-374a4fc23224
caps.latest.revision: 17
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: a6aeda8e785fcaabef253a8256b5f6f7a842a324
ms.openlocfilehash: eb98483d6237f2db2fdb0cb9aa444dd938a431f0
ms.contentlocale: fr-fr
ms.lasthandoff: 09/21/2017

---
# <a name="what39s-new-in-sql-server-2017-analysis-services"></a>Quel &#39; est nouvelle dans SQL Server 2017 Analysis Services
[!INCLUDE[tsql-appliesto-ssvNxt-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md)]


## <a name="sql-server-2017-analysis-services-rc2"></a>SQL Server 2017 Analysis Services RC2
Cette version ne comporte aucune nouvelle fonctionnalité. Améliorations apportées dans cette version incluent des correctifs de bogues et les performances.

## <a name="sql-server-2017-analysis-services-rc1"></a>SQL Server 2017 Analysis Services RC1
Il n’existe aucune fonctionnalité nouvelle dans cette version, toutefois, cette version inclut les améliorations apportées aux [vues de gestion dynamique](https://docs.microsoft.com/sql/analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services) (DMV) pour les modèles tabulaires aux niveaux de compatibilité 1200 et 1400.

Fonctionne maintenant DISCOVER_CALC_DEPENDENCY avec les modèles tabulaires 1200 et 1400. Les modèles tabulaires 1400 affichent les dépendances entre les partitions de M, M expressions et des sources de données structurées. Pour plus d’informations, consultez la [blog Analysis Services](https://blogs.msdn.microsoft.com/analysisservices/).

Améliorations de MDSCHEMA_MEASUREGROUP_DIMENSIONS sont incluses dans cette vue de gestion dynamique, qui est utilisé par divers outils clients pour afficher une dimension de mesures. Par exemple, la fonctionnalité d’exploration dans des tableaux croisés dynamiques Excel permet à l’utilisateur à cross-extraction des dimensions liées aux mesures sélectionnés. Cette version corrige les colonnes de la cardinalité, qui ont été précédemment montrant les valeurs incorrectes.

## <a name="sql-server-analysis-services-ctp-21"></a>SQL Server Analysis Services CTP 2.1
Cette version ne comporte aucune nouvelle fonctionnalité. Améliorations apportées dans cette version incluent des correctifs de bogues et améliorations de performances et à [vues de gestion dynamique](https://docs.microsoft.com/sql/analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services) (DMV). Vues de gestion dynamique sont des requêtes qui retournent des informations sur les opérations de serveur local et de l’intégrité du serveur dans SQL Server Profiler. Pour plus d’informations, consultez la [blog Analysis Services](https://blogs.msdn.microsoft.com/analysisservices/).

## <a name="sql-server-analysis-services-ctp-20"></a>SQL Server Analysis Services version CTP 2.0
Cette version comporte de nombreuses nouvelles améliorations pour le modèle tabulaire, y compris :

* Sécurité au niveau objet pour sécuriser les métadonnées des modèles tabulaires.
* Améliorations des performances des transactions pour une expérience de développement plus réactive.
* Améliorations de la vue de gestion dynamiques pour les modèles 1200 et 1400 permettant l’analyse de dépendance et de création de rapports.
* Améliorations apportées à l’expérience de création pour les Expressions de lignes de détails.
* Hiérarchie et colonne réutiliser pour être exposés à des emplacements plus utiles dans la liste de champs Power BI.
* Relations de date pour créer facilement des relations aux dimensions de date en fonction des champs de date.
* Option d’installation par défaut pour Analysis Services est maintenant en mode tabulaire.
* Nouvelles sources de données d’obtenir des données (Power Qery).
* Éditeur DAX pour SSDT.
* Les sources de données DirectQuery existantes prend en charge pour les requêtes de M.
* Améliorations de SSMS, telles que l’affichage, modification et la prise en charge pour les sources de données structurées de script.

Pour obtenir plus de détails sur cette version CTP 2.0, consultez le [blog Analysis Services](https://blogs.msdn.microsoft.com/analysisservices/).

## <a name="sql-server-analysis-services-on-windows-ctp-14"></a>SQL Server Analysis Services sur Windows CTP 1.4
[SQL Server Data Tools (SSDT)](https://docs.microsoft.com/sql/ssdt/sql-server-data-tools-ssdt-release-candidate) et [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms-release-candidate) versions préliminaires coïncident avec les versions préliminaires de SQL Server 2017. Veillez à utiliser la dernière pour obtenir de nouvelles fonctionnalités. Pour plus d’informations, consultez la [blog Analysis Services](https://blogs.msdn.microsoft.com/analysisservices/).



## <a name="sql-server-analysis-services-on-windows-ctp-13"></a>SQL Server Analysis Services sur Windows CTP 1.3

### <a name="encoding-hints"></a>Indications de codage

Cette version introduit des indications de codage, une fonctionnalité avancée permet d’optimiser le traitement (actualisation des données) de grands modèles tabulaires en mémoire. Pour mieux comprendre l’encodage, consultez [performances réglage de modèles tabulaires dans SQL Server 2012 Analysis Services](https://msdn.microsoft.com/library/dn393915.aspx) livre blanc pour mieux comprendre l’encodage. Le processus de codage décrit ici s’applique dans CTP 1.3.

* Valeur d’encodage offre de meilleures performances de requête pour les colonnes qui sont généralement utilisés uniquement pour les agrégations.

* Encodage du hachage est recommandée pour les colonnes group by (souvent des valeurs de table de dimension) et les clés étrangères. Colonnes de type chaîne sont toujours encodée de hachage.

Colonnes numériques peuvent utiliser une de ces méthodes d’encodage. Lorsque Analysis Services commence à traiter une table, si la table est vide (avec ou sans partitions) ou une opération de traitement de la table entière est effectuée, les valeurs des échantillons proviennent pour chacune des colonnes numériques déterminer s’il faut appliquer l’encodage de hachage ou de la valeur. Par défaut, la valeur d’encodage est choisi lorsque l’exemple de valeurs distinctes dans la colonne est suffisante, sinon l’encodage de hachage fournira généralement une meilleure compression. Il est possible pour Analysis Services modifier la méthode de codage, une fois que la colonne est partiellement traitée basée sur plus d’informations sur la distribution des données, redémarrez le processus de codage. Bien entendu, cela augmente le temps de traitement et est inefficace. Le livre blanc de réglage des performances présente réencodage plus en détail et explique comment détecter à l’aide du Générateur de profils SQL Server.

Indications de codage dans le CTP 1.3 autoriser le Modélisateur de spécifier une préférence pour la méthode de codage étant donnée la connaissance préalable de profilage des données et/ou en réponse à recodage des événements de trace. Étant donné que l’agrégation sur les colonnes de hachage encodé est plus lente que sur les colonnes de valeur encodée, encodage de valeur peut être spécifié en tant qu’indicateur pour ces colonnes. Il n’est pas garanti que la préférence est appliquée ; Par conséquent, il s’agit d’un indicateur par opposition à un paramètre. Pour spécifier un indicateur d’encodage, définir la propriété EncodingHint sur la colonne. Les valeurs possibles sont « Default », « Value » et « Hachage ». Au moment de l’écriture, la propriété n’est pas encore exposée dans SSDT, doit donc être attribuée à l’aide de la métadonnées JSON, TMSL Tabular Model Scripting Language () ou le modèle d’objet tabulaire (TOM). L’extrait suivant de JSON en fonction des métadonnées à partir du fichier Model.bim spécifie la valeur d’encodage pour la colonne de montant des ventes.

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

### <a name="extended-events-not-working-in-ctp-13"></a>Ne fonctionne ne pas dans le CTP 1.3 des événements étendus
SSAS, événements étendus ne fonctionnent pas dans le CTP 1.3. Un correctif est prévu dans le CTP suivant.

## <a name="sql-server-analysis-services-on-windows-ctp-12"></a>SQL Server Analysis Services sur Windows CTP 1.2

Cette version ne comporte aucune nouvelle fonctionnalité. Les améliorations incluent les correctifs de bogues et concernent les performances.

La dernière version de SQL Server Data Tools (SSDT), qui coïncide avec le SQL Server 2017 CTP 1.2, améliore la nouvelle expérience obtenir des données moderne introduite dans CTP 1.1 avec nouveau menu de l’éditeur de requête et de la fonctionnalité d’accès rapide. 

## <a name="sql-server-analysis-services-on-windows-ctp-11"></a>SQL Server Analysis Services sur Windows CTP 1.1 

Cette version introduit des améliorations pour les modèles tabulaires. 

### <a name="1400-compatibility-level-for-tabular-models"></a>Niveau de compatibilité&1400; pour les modèles tabulaires
  Pour tirer parti des fonctionnalités décrites dans cet article, les modèles tabulaires nouveaux ou existants doivent être définis sur le niveau de compatibilité 1400. Les modèles au niveau de compatibilité 1400 ne peuvent pas être déployés vers SQL Server 2016 SP1 ou version antérieure, ni passés à une version antérieure pour réduire les niveaux de compatibilité.
  
  Pour créer ou mettre à niveau des projets de modèles tabulaires existants vers le niveau de compatibilité 1400, téléchargez et installez une **version préliminaire** de [SQL Server Data Tools (SSDT) 17.0 RC2](https://go.microsoft.com/fwlink?LinkId=837939). 
  
Dans SSDT, vous pouvez sélectionner le nouveau niveau de compatibilité 1400 lors de la création de projets de modèles tabulaires. 

![AS_NewTabular1400Project](../analysis-services/media/as-newtabular1400project.png)

>[!NOTE]
> L’espace de travail intégré dans la version de décembre de SQL Server Data Tools (SSDT) prend en charge le niveau de compatibilité 1400. Si vous créez des projets de modèles tabulaires sur une instance de serveur d’espace de travail, cette instance ou toute instance que vous déployez doit être [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] CTP 1.1. 

Pour mettre à niveau un modèle tabulaire existant dans SSDT, dans l’Explorateur de solutions, cliquez sur **Model.bim**, puis dans **propriétés**, définissez le **le niveau de compatibilité** propriété **SQL Server 2017 (1400)**. 

![AS_Model_Properties](../analysis-services/media/as-model-properties.png)

### <a name="modern-get-data-experience"></a>Expérience moderne d’obtention des données
La dernière version préliminaire de SQL Server Data Tools (SSDT), qui coïncide avec la version [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] CTP 1.1, introduit une expérience moderne **d’obtention des données** pour les modèles tabulaires au niveau de compatibilité 1400. Cette nouvelle fonctionnalité est basée sur des fonctionnalités similaires de Power BI Desktop et de Microsoft Excel 2016.

![AS_Get_Data_in_SSDT](../analysis-services/media/as-get-data-in-ssdt.png)

>[!NOTE]
> Pour cette version, un nombre limité de sources de données est pris en charge. Les mises à jour ultérieures prendront en charge des sources de données et des fonctionnalités supplémentaires.

Pour en savoir plus sur l’expérience moderne d’obtention des données, consultez le [Blog de l’équipe Analysis Services](https://blogs.msdn.microsoft.com/analysisservices/2016/12/16/introducing-a-modern-get-data-experience-for-sql-server-2017-on-windows-ctp-1-1-for-analysis-services/).

## <a name="ragged-hierarchies"></a>Hiérarchies déséquilibrées
Dans les modèles tabulaires, vous pouvez modéliser les hiérarchies parent-enfant. Les hiérarchies avec différents nombres de niveaux sont souvent appelées hiérarchies déséquilibrées. Par défaut, les hiérarchies déséquilibrées sont affichées avec des vides pour les niveaux en dessous de l’enfant le plus bas. Voici un exemple de hiérarchie déséquilibrée dans un organigramme :

![AS_Ragged_Hierarchy](../analysis-services/media/as-ragged-hierarchy.png)

Cette version introduit la propriété **Masquer les membres** . Vous pouvez définir la propriété **Masquer les membres** pour une hiérarchie sur **Masquer les membres vides**.

![AS_Hide_Blank_Members](../analysis-services/media/as-hide-blank-members.png)

 >[!NOTE]
 > Dans le modèle, les membres vides sont représentés par une valeur vide DAX, et non par une chaîne vide.

Lorsque la propriété **Masquer les membres vides**est définie, et lorsque le modèle est déployé, une version plus lisible de la hiérarchie est affichée dans les clients de gestion de rapports comme Excel.

![AS_Non_Ragged_Hierarchy](../analysis-services/media/as-non-ragged-hierarchy.png)

### <a name="detail-rows"></a>Lignes de détails
Vous pouvez maintenant définir un ensemble de lignes personnalisées contribuant à une valeur de mesure. Les lignes de détails sont similaires à l’action d’extraction par défaut dans les modèles multidimensionnels. Cela permet aux utilisateurs finaux d’afficher des informations de manière plus détaillée que le niveau agrégé. 

Le tableau croisé dynamique suivant montre le total des ventes sur Internet par an de l’exemple de modèle tabulaire Adventure Works. Cliquez avec le bouton droit sur une cellule avec une valeur agrégée de la mesure, puis cliquez sur **Afficher les détails** pour afficher les lignes de détails.

![AS_Show_Details](../analysis-services/media/as-show-details.png)

Par défaut, les données associées à la table des ventes sur Internet s’affiche. Ce comportement limité n’est généralement pas significatif pour l’utilisateur car la table ne dispose peut-être pas des colonnes nécessaires pour afficher des informations utiles telles que le nom du client et les informations de commande. Avec les lignes de détails, vous pouvez spécifier une propriété **Expression de lignes de détails** pour les mesures.

#### <a name="detail-rows-expression-property-for-measures"></a>Propriété Expression de lignes de détails pour les mesures
La propriété **Expression de lignes de détails** pour les mesures permet aux créateurs de modèles de personnaliser les colonnes et les lignes renvoyées à l’utilisateur final.

![AS_Detail_Rows_Expression_Property](../analysis-services/media/as-detail-rows-expression-property.png)

La fonction DAX [SELECTCOLUMNS](https://msdn.microsoft.com/library/mt761759.aspx) est couramment utilisée dans une Expression de lignes de détails. L’exemple suivant définit les colonnes à renvoyer pour les lignes dans la table des ventes sur Internet, dans l’exemple de modèle tabulaire Adventure Works :

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
Outre les mesures, les tables possèdent également une propriété pour définir une expression de lignes de détails. La propriété **Expression de lignes de détails par défaut** agit comme valeur par défaut pour toutes les mesures de la table. Les mesures qui n’ont pas leur propre expression définie héritent de l’expression de la table et affichent l’ensemble de lignes défini pour la table. Ceci permet de réutiliser des expressions, et les nouvelles mesures ajoutées à la table ultérieurement héritent automatiquement de l’expression.

![AS_Default_Detail_Rows_Expression](../analysis-services/media/as-default-detail-rows-expression.png)
 
#### <a name="detailrows-dax-function"></a>Fonction DETAILROWS DAX
Cette version comprend une nouvelle fonction DAX `DETAILROWS` qui renvoie l’ensemble de lignes défini par l’expression de lignes de détails. Elle fonctionne de façon similaire à l’instruction `DRILLTHROUGH` dans MDX, qui est également compatible avec les expressions de lignes de détails définies dans les modèles tabulaires.

La requête DAX suivante retourne l’ensemble de lignes défini par l’expression de lignes de détails pour la mesure ou pour sa table. Si aucune expression n’est définie, les données pour la table des ventes sur Internet sont renvoyées, car c’est la table qui contient la mesure.

```
EVALUATE DETAILROWS([Internet Total Sales])
```

## <a name="dax-enhancements"></a>Améliorations DAX
Cette version inclut un opérateur `IN` pour les expressions DAX. Elle est similaire à l’opérateur [`TSQL IN`](/sql-docs/docs/t-sql/language-elements/in-transact-sql) couramment utilisé pour spécifier plusieurs valeurs dans une clause `WHERE`.

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


## <a name="table-level-security"></a>Sécurité au niveau des tables
Cette version introduit la sécurité au niveau des tables. Outre la restriction d’accès aux données des tables, les noms de tables sensibles peuvent être sécurisés. Cela permet d’empêcher qu’un utilisateur malveillant découvre l’existence de cette table.

La sécurité au niveau des tables doit être définie en utilisant les métadonnées basées sur JSON, le langage TMSL (Tabular Model Scripting Language) ou le modèle d’objet tabulaire (TOM). 

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


