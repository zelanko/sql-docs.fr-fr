---
title: "Guide pratique pour cr&#233;er des requ&#234;tes MDX &#224; l’aide d’olapR | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "R"
ms.assetid: c12b988e-be7e-41ba-a84c-299a5c45d4ab
caps.latest.revision: 3
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 3
---
# Guide pratique pour cr&#233;er des requ&#234;tes MDX &#224; l’aide d’olapR
## <a name="how-to-build-an-mdx-query-from-r"></a>Guide pratique pour créer une requête MDX à partir de R

1. Définissez une chaîne de connexion qui spécifie la source de données OLAP (instance SSAS) et le fournisseur MSOLAP.

2. Utilisez la fonction `OlapConnection(connectionString)` pour créer un handle de la requête MDX et passez la chaîne de connexion.

3. Utilisez le constructeur `Query()` pour instancier un objet de requête.

4. Utilisez les fonctions d’assistance suivantes pour fournir plus de détails sur les dimensions et les mesures à inclure dans la requête MDX :
     + `cube()` Spécifiez le nom de la base de données SSAS.
     + `columns()` Fournissez les noms des mesures à utiliser dans l’argument ON COLUMNS.  
     + `rows()` Fournissez les noms des mesures à utiliser dans l’argument ON ROWS.
     + `slicers()` Spécifiez un ou plusieurs membres à utiliser comme segment. Un segment est comme un filtre appliqué à toutes les données de requête MDX.
     
     + `axis()` Spécifiez le nom d’un axe supplémentaire à utiliser dans la requête. Un cube OLAP peut contenir jusqu’à 128 axes de requête. En règle générale, les quatre premiers axes se nomment Columns, Rows, Pages et Chapters. Si votre requête est relativement simple, vous pouvez utiliser les fonctions `columns`, `rows`, et ainsi de suite pour créer votre requête.     
     Toutefois, vous pouvez aussi utiliser la fonction `axis()` avec une valeur d’index non nulle pour créer une requête MDX avec de nombreux qualificateurs, ou pour ajouter des dimensions supplémentaires comme qualificateurs.

5. Passez le handle et la requête MDX terminée dans les fonctions `executeMD` ou `execute2D`, selon la forme des résultats.

  + `executeMD` Retourne un tableau multidimensionnel
  + `execute2D` Retourne une trame de données à deux dimensions (tabulaire)


## <a name="how-to-run-an-existing-mdx-query-from-r"></a>Guide pratique pour exécuter une requête MDX existante à partir de R

1. Définissez une chaîne de connexion qui spécifie la source de données OLAP (instance SSAS) et le fournisseur MSOLAP.

2. Utilisez la fonction `OlapConnection(connectionString)` pour créer un handle de la requête MDX et passez la chaîne de connexion.

3. Définissez une variable R pour stocker le texte de la requête MDX.

4. Passez le handle et la variable contenant la requête MDX dans les fonctions `executeMD` ou `execute2D`, selon la forme des résultats.

    + `executeMD` Retourne un tableau multidimensionnel
    + `execute2D` Retourne une trame de données à deux dimensions (tabulaire)



## <a name="examples"></a>Exemples

### <a name="1-basic-mdx-with-slicer"></a>1. MDX de base avec segment

Cette requête MDX sélectionne les _mesures_ pour le nombre et le montant des ventes sur Internet, puis les place sur l’axe des colonnes. Elle ajoute un membre de la dimension SalesTerritory comme *segment* pour filtrer la requête et que seules les ventes en Australie soient utilisées dans les calculs.

```MDX
SELECT {[Measures].[Internet Sales Count], [Measures].[InternetSales-Sales Amount]} ON COLUMNS, 
{[Product].[Product Line].[Product Line].MEMBERS} ON ROWS 
FROM [Analysis Services Tutorial] 
WHERE [Sales Territory].[Sales Territory Country].[Australia]
```

+ Sur les colonnes, vous pouvez spécifier plusieurs mesures comme éléments d’une chaîne séparés par des virgules.
+ L’axe des lignes utilise toutes les valeurs possibles (tous les MEMBRES) de la dimension « Product Line ». 
+ Cette requête retourne une table avec trois colonnes, contenant un récapitulatif avec _regroupement_ des ventes sur Internet dans tous les pays. 
+ La clause WHERE est _l’axe de segment_. Le segment utilise un membre de la dimension SalesTerritory pour filtrer la requête et que seules les ventes en Australie soient utilisées dans les calculs.

#### <a name="to-build-this-query-using-the-functions-provided-in-olapr"></a>Pour générer cette requête à l’aide des fonctions fournies dans olapR

```R
cnnstr <- "Data Source=localhost; Provider=MSOLAP;"
ocs <- OlapConnection(cnnstr)

qry <- Query()
cube(qry) <- "[Analysis Services Tutorial]"
columns(qry) <- c("[Measures].[Internet Sales Count]", "[Measures].[Internet Sales-Sales Amount]")
rows(qry) <- c("[Product].[Product Line].[Product Line].MEMBERS") 
slicers(qry) <- c("[Sales Territory].[Sales Territory Country].[Australia]")

result1 <- executeMD(ocs, qry)

```

#### <a name="to-run-this-query-as-a-predefined-mdx-string"></a>Pour exécuter cette requête comme chaîne MDX prédéfinie

```R
cnnstr <- "Data Source=localhost; Provider=MSOLAP;"
ocs <- OlapConnection(cnnstr)

mdx <- "SELECT {[Measures].[Internet Sales Count], [Measures].[InternetSales-Sales Amount]} ON COLUMNS, {[Product].[Product Line].[Product Line].MEMBERS} ON ROWS FROM [Analysis Services Tutorial] WHERE [Sales Territory].[Sales Territory Country].[Australia]"

result2 <- execute2D(ocs, mdx)
```

Notez que si vous définissez une requête à l’aide du Générateur MDX dans SQL Server Management Studio et que vous enregistrez ensuite la chaîne MDX, elle numérote les axes à partir de 0, comme indiqué ici : 

~~~~
SELECT {[Measures].[Internet Sales Count], [Measures].[Internet Sales-Sales Amount]} ON AXIS(0), 
   {[Product].[Product Line].[Product Line].MEMBERS} ON AXIS(1) 
   FROM [Analysis Services Tutorial] 
   WHERE [Sales Territory].[Sales Territory Country].[Australia]
~~~~

Vous pouvez toujours exécuter cette requête comme chaîne MDX prédéfinie. Toutefois, pour générer la même requête à l’aide de R avec la fonction `axis()`, veillez à numéroter les axes à partir de 1.


### <a name="2-explore-cubes-and-their-fields-on-an-ssas-instance"></a>2. Explorer les cubes et leurs champs sur une instance SSAS

Vous pouvez utiliser la fonction `explore` pour retourner une liste de cubes, de dimensions ou de membres à utiliser lors de la construction de votre requête. Cela est pratique si vous n’avez pas accès à d’autres outils de navigation OLAP, ou si vous souhaitez manipuler ou créer la requête MDX par programmation.

#### <a name="to-list-the-cubes-available-on-the-specified-connection"></a>Pour dresser la liste des cubes disponibles sur la connexion spécifiée

Pour afficher tous les cubes ou perspectives sur l’instance que vous êtes autorisé à afficher, fournissez le handle comme argument de `explore`.
Notez que le résultat final n’est pas un cube ; TRUE indique simplement que l’opération de métadonnées a réussi. Une erreur est levée si les arguments ne sont pas valides.

```R
cnnstr <- "Data Source=localhost; Provider=MSOLAP;"
ocs <- OlapConnection(cnnstr)
explore(ocs)
```

| Résultats  |  
| ----|
| _Analysis Services Tutorial_|
|_Internet Sales_|
|_Reseller Sales_|
|_Sales Summary_|
|_[1] TRUE_|
     


#### <a name="to-get-a-list-of-cube-dimensions"></a>Pour obtenir une liste de dimensions de cube

Pour afficher toutes les dimensions du cube ou de la perspective, spécifiez le nom du cube ou de la perspective.

```R
cnnstr <- "Data Source=localhost; Provider=MSOLAP;"
ocs <- OlapConnection(cnnstr)
explore(ocs, "Sales")
```

| Résultats  |  
| ----|
| _Customer_|
|_Date_|
|_Region_|


#### <a name="to-return-all-members-of-the-specified-dimension-and-hierarchy"></a>Pour retourner tous les membres de la dimension et de la hiérarchie spécifiées

Après avoir défini la source et créé le handle, spécifiez le cube, la dimension et la hiérarchie à retourner.
Notez que les éléments dans les résultats retournés précédés de **->** représentent des enfants du membre précédent.

```R
cnnstr <- "Data Source=localhost; Provider=MSOLAP;"
ocs <- OlapConnection(cnnstr)
explore(ocs, "Analysis Services Tutorial", "Product", "Product Categories", "Category")
```

| Résultats  |  
| ----|
| _Accessories_|
|_Bikes_|
|_Clothing_|
|_Components_|
|-> Assembly Components|
|-> Assembly Components|



## <a name="see-also"></a>Voir aussi

[Utilisation de données à partir de cubes OLAP dans R](../../advanced-analytics/r-services/using-data-from-olap-cubes-in-r.md)