---
title: Comment créer des requêtes MDX dans R à l’aide d’olapr
description: Utilisez la bibliothèque de packages OLAP dans SQL Server pour écrire des requêtes MDX dans le script R Language.
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/22/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 0b98e2bafd53eaabd606d09b3e0b51dd3d53aceb
ms.sourcegitcommit: f5807ced6df55dfa78ccf402217551a7a3b44764
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69494062"
---
# <a name="how-to-create-mdx-queries-in-r-using-olapr"></a>Comment créer des requêtes MDX dans R à l’aide d’olapr
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Le [package](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) olapr prend en charge les requêtes MDX sur les cubes hébergés dans SQL Server Analysis Services. Vous pouvez créer une requête sur un cube existant, explorer des dimensions et d’autres objets de cube, et coller des requêtes MDX existantes pour récupérer des données.

Cet article décrit les deux utilisations principales du package **olapr** :

+ [Créer une requête MDX à partir de R, à l’aide des constructeurs fournis dans le package olapr](#buildMDX)
+ [Exécuter une requête MDX existante et valide à l’aide d’olapr et d’un fournisseur OLAP](#executeMDX)

Les opérations suivantes ne sont pas prises en charge:

+ Requêtes DAX sur un modèle tabulaire
+ Création de nouveaux objets OLAP
+ Écriture différée sur des partitions, y compris des mesures ou des sommes

## <a name="buildMDX"></a>Créer une requête MDX à partir de R

1. Définissez une chaîne de connexion qui spécifie la source de données OLAP (instance SSAS) et le fournisseur MSOLAP.

2. Utilisez la fonction `OlapConnection(connectionString)` pour créer un handle de la requête MDX et passez la chaîne de connexion.

3. Utilisez le constructeur `Query()` pour instancier un objet de requête.

4. Utilisez les fonctions d’assistance suivantes pour fournir plus de détails sur les dimensions et les mesures à inclure dans la requête MDX :

     + `cube()` Spécifiez le nom de la base de données SSAS. En cas de connexion à une instance nommée, indiquez le nom de l’ordinateur et le nom de l’instance. 
     + `columns()`Fournissez les noms des mesures à utiliser dans l’argument **on Columns** .
     + `rows()`Fournissez les noms des mesures à utiliser dans l’argument **on Rows** .
     + `slicers()` Spécifiez un ou plusieurs membres à utiliser comme segment. Un segment est comme un filtre appliqué à toutes les données de requête MDX.
     
     + `axis()` Spécifiez le nom d’un axe supplémentaire à utiliser dans la requête. 
     
         Un cube OLAP peut contenir jusqu’à 128 axes de requête. En règle générale, les quatre premiers axes sont désignés sous le terme de **colonnes**, de **lignes**, de **pages**et de **chapitres**. 
         
         Si votre requête est relativement simple, vous pouvez utiliser les fonctions `columns`, `rows`, et ainsi de suite pour créer votre requête. Toutefois, vous pouvez aussi utiliser la fonction `axis()` avec une valeur d’index non nulle pour créer une requête MDX avec de nombreux qualificateurs, ou pour ajouter des dimensions supplémentaires comme qualificateurs.

5. Transmettez le descripteur, et la requête MDX terminée, dans l’une des fonctions suivantes, en fonction de la forme des résultats: 

  + `executeMD` Retourne un tableau multidimensionnel
  + `execute2D` Retourne une trame de données à deux dimensions (tabulaire)

## <a name="executeMDX"></a>Exécuter une requête MDX valide à partir de R

1. Définissez une chaîne de connexion qui spécifie la source de données OLAP (instance SSAS) et le fournisseur MSOLAP.

2. Utilisez la fonction `OlapConnection(connectionString)` pour créer un handle de la requête MDX et passez la chaîne de connexion.

3. Définissez une variable R pour stocker le texte de la requête MDX.

4. Passez le handle et la variable contenant la requête MDX dans les fonctions `executeMD` ou `execute2D`, selon la forme des résultats.

    + `executeMD` Retourne un tableau multidimensionnel
    + `execute2D` Retourne une trame de données à deux dimensions (tabulaire)

## <a name="examples"></a>Exemples

Les exemples suivants sont basés sur le mini-Data Warehouse et le projet de cube AdventureWorks, car ce projet est largement disponible, dans plusieurs versions, y compris les fichiers de sauvegarde qui peuvent être facilement restaurés sur Analysis Services. Si vous ne disposez pas d’un cube existant, récupérez un exemple de cube à l’aide de l’une des options suivantes:

+ Créez le cube utilisé dans ces exemples en suivant le didacticiel Analysis Services jusqu’à la leçon 4: [Création d’un cube OLAP](https://docs.microsoft.com/analysis-services/multidimensional-tutorial/multidimensional-modeling-adventure-works-tutorial)

+ Téléchargez un cube existant en tant que sauvegarde, puis restaurez-le dans une instance de Analysis Services. Par exemple, ce site fournit un cube entièrement traité au format zippé: [Modèle multidimensionnel Adventure Works SQL 2014](https://msftdbprodsamples.codeplex.com/downloads/get/882334). Extrayez le fichier, puis restaurez-le dans votre instance SSAS. Pour plus d’informations, consultez [Backup and Restore](https://docs.microsoft.com/analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases), ou l’applet de commande Restore [-ASDatabase](/powershell/module/sqlserver/restore-asdatabase).

### <a name="1-basic-mdx-with-slicer"></a>1. MDX de base avec segment

Cette requête MDX sélectionne les _mesures_ pour le nombre et le montant des ventes sur Internet, puis les place sur l’axe des colonnes. Elle ajoute un membre de la dimension SalesTerritory comme *segment*pour filtrer la requête et que seules les ventes en Australie soient utilisées dans les calculs.

```MDX
SELECT {[Measures].[Internet Sales Count], [Measures].[InternetSales-Sales Amount]} ON COLUMNS, 
{[Product].[Product Line].[Product Line].MEMBERS} ON ROWS 
FROM [Analysis Services Tutorial] 
WHERE [Sales Territory].[Sales Territory Country].[Australia]
```

+ Sur les colonnes, vous pouvez spécifier plusieurs mesures comme éléments d’une chaîne séparés par des virgules.
+ L’axe des lignes utilise toutes les valeurs possibles (tous les MEMBRES) de la dimension « Product Line ». 
+ Cette requête retourne une table avec trois colonnes, contenant un résumé _cumulatif_ des ventes sur Internet de tous les pays.
+ La clause WHERE spécifie l' _axe de secteur_. Dans cet exemple, le segment utilise un membre de la dimension **SalesTerritory** pour filtrer la requête afin que seules les ventes en Australie soient utilisées dans les calculs.

#### <a name="to-build-this-query-using-the-functions-provided-in-olapr"></a>Pour générer cette requête à l’aide des fonctions fournies dans olapR

```R
cnnstr <- "Data Source=localhost; Provider=MSOLAP; initial catalog=Analysis Services Tutorial"
ocs <- OlapConnection(cnnstr)

qry <- Query()
cube(qry) <- "[Analysis Services Tutorial]"
columns(qry) <- c("[Measures].[Internet Sales Count]", "[Measures].[Internet Sales-Sales Amount]")
rows(qry) <- c("[Product].[Product Line].[Product Line].MEMBERS") 
slicers(qry) <- c("[Sales Territory].[Sales Territory Country].[Australia]")

result1 <- executeMD(ocs, qry)

```

Pour une instance nommée, veillez à échapper tous les caractères qui pourraient être considérés comme des caractères de contrôle dans R.  Par exemple, la chaîne de connexion suivante fait référence à une instance OLAP01, sur un serveur nommé ContosoHQ:

```R
cnnstr <- "Data Source=ContosoHQ\\OLAP01; Provider=MSOLAP; initial catalog=Analysis Services Tutorial"
```

#### <a name="to-run-this-query-as-a-predefined-mdx-string"></a>Pour exécuter cette requête comme chaîne MDX prédéfinie

```R
cnnstr <- "Data Source=localhost; Provider=MSOLAP; initial catalog=Analysis Services Tutorial"
ocs <- OlapConnection(cnnstr)

mdx <- "SELECT {[Measures].[Internet Sales Count], [Measures].[InternetSales-Sales Amount]} ON COLUMNS, {[Product].[Product Line].[Product Line].MEMBERS} ON ROWS FROM [Analysis Services Tutorial] WHERE [Sales Territory].[Sales Territory Country].[Australia]"

result2 <- execute2D(ocs, mdx)
```

Si vous définissez une requête à l’aide du générateur MDX dans SQL Server Management Studio puis enregistrez la chaîne MDX, les axes sont numérotés à partir de 0, comme illustré ici: 

```MDX
SELECT {[Measures].[Internet Sales Count], [Measures].[Internet Sales-Sales Amount]} ON AXIS(0), 
   {[Product].[Product Line].[Product Line].MEMBERS} ON AXIS(1) 
   FROM [Analysis Services Tutorial] 
   WHERE [Sales Territory].[Sales Territory Countr,y].[Australia]
```

Vous pouvez toujours exécuter cette requête comme chaîne MDX prédéfinie. Toutefois, pour générer la même requête à l’aide de `axis()` R à l’aide de la fonction, vous devez renuméroter les axes à partir de 1.

### <a name="2-explore-cubes-and-their-fields-on-an-ssas-instance"></a>2. Explorer les cubes et leurs champs sur une instance SSAS

Vous pouvez utiliser la fonction `explore` pour retourner une liste de cubes, de dimensions ou de membres à utiliser lors de la construction de votre requête. Cela est pratique si vous n’avez pas accès à d’autres outils de navigation OLAP, ou si vous souhaitez manipuler ou créer la requête MDX par programmation.

#### <a name="to-list-the-cubes-available-on-the-specified-connection"></a>Pour dresser la liste des cubes disponibles sur la connexion spécifiée

Pour afficher tous les cubes ou perspectives sur l’instance que vous êtes autorisé à afficher, fournissez le handle comme argument de `explore`.

> [!IMPORTANT]
> Le résultat final n’est **pas** un cube; TRUE indique simplement que l’opération de métadonnées a réussi. Une erreur est levée si les arguments ne sont pas valides.

```R
cnnstr <- "Data Source=localhost; Provider=MSOLAP; initial catalog=Analysis Services Tutorial"
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
cnnstr <- "Data Source=localhost; Provider=MSOLAP; initial catalog=Analysis Services Tutorial"
ocs \<- OlapConnection(cnnstr)
explore(ocs, "Sales")
```

| Résultats  |
| ----|
| _Customer_|
|_Date_|
|_Region_|


#### <a name="to-return-all-members-of-the-specified-dimension-and-hierarchy"></a>Pour retourner tous les membres de la dimension et de la hiérarchie spécifiées

Après avoir défini la source et créé le handle, spécifiez le cube, la dimension et la hiérarchie à retourner. Dans les résultats retournés, les éléments qui sont **->** préfixés avec représentent les enfants du membre précédent.

```R
cnnstr <- "Data Source=localhost; Provider=MSOLAP; initial catalog=Analysis Services Tutorial"
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

[Utilisation de données de cubes OLAP dans R](../../advanced-analytics/r/using-data-from-olap-cubes-in-r.md)
