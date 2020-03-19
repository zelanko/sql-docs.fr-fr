---
title: 'Tutoriel T-SQL : créer et interroger des objets de base de données | Microsoft Docs'
ms.custom: ''
ms.date: 07/30/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: t-sql
ms.topic: conceptual
ms.assetid: 9fb8656b-0e4e-4ada-b404-4db4d3eea995
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d2bea423a9ea039dbc9f0128c7d6b6f106ee03fe
ms.sourcegitcommit: d1f6da6f0f5e9630261cf733c64958938a3eb859
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79198406"
---
# <a name="lesson-1-create-and-query-database-objects"></a>Leçon 1 : créer et interroger des objets de base de données
[!INCLUDE[tsql-appliesto-ss2008-all-md](../includes/tsql-appliesto-ss2008-all-md.md)]

Cette leçon vous montre comment créer une base de données, une table dans la base de données, puis accéder aux données et les modifier dans la table. Étant donné que cette leçon est une introduction à l’utilisation de [!INCLUDE[tsql](../includes/tsql-md.md)], elle n’utilise pas ni ne décrit les nombreuses options disponibles pour ces instructions.  
  
[!INCLUDE[tsql](../includes/tsql-md.md)] les instructions peuvent être écrites et soumises au [!INCLUDE[ssDE](../includes/ssde-md.md)] comme suit :  
  
-   À l'aide de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Ce didacticiel suppose que vous utilisez [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], mais vous pouvez aussi utiliser [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] Express, disponible gratuitement en téléchargement à partir du [Centre de téléchargement Microsoft](https://www.microsoft.com/download/details.aspx?id=14630).  
  
-   À l’aide de [l’utilitaire sqlcmd](../tools/sqlcmd-utility.md).  
  
-   En vous connectant à partir d'une application que vous créez.  
  
Le code s’exécute sur le [!INCLUDE[ssDE](../includes/ssde-md.md)] de la même façon et avec les mêmes autorisations, quelle que soit la manière dont vous soumettez les instructions de code.  
  
Pour exécuter des instructions [!INCLUDE[tsql](../includes/tsql-md.md)] dans [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], ouvrez [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] et connectez-vous à une instance du [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)].  

## <a name="prerequisites"></a>Prérequis
Pour suivre ce tutoriel, vous avez besoin de SQL Server Management Studio et d’un accès à une instance SQL Server. 

- Installez [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

Si vous n’avez pas d’instance SQL Server, créez-en une. Pour cela, sélectionnez votre plateforme parmi les liens suivants. Si vous choisissez l’authentification SQL, utilisez vos informations d’identification de connexion SQL Server.
- **Windows** : [Télécharger SQL Server 2017 Developer Edition](https://www.microsoft.com/sql-server/sql-server-downloads).
- **macOS** : [Télécharger SQL Server 2017 sur Docker](https://docs.microsoft.com/sql/linux/quickstart-install-connect-docker).

## <a name="create-a-database"></a>Création d'une base de données
Comme de nombreuses instructions [!INCLUDE[tsql](../includes/tsql-md.md)], l’instruction [`CREATE DATABASE`](statements/create-database-transact-sql.md) a un paramètre obligatoire : le nom de la base de données.` CREATE DATABASE` a aussi de nombreux paramètres facultatifs, notamment l’emplacement du disque où vous souhaitez placer les fichiers de base de données. Quand vous exécutez `CREATE DATABASE` sans les paramètres facultatifs, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] utilise les valeurs par défaut pour un grand nombre de ces paramètres.

1.  Dans une fenêtre de l'Éditeur de requête, tapez mais sans l'exécuter le code suivant :  
  
    ```sql  
    CREATE DATABASE TestData  
    GO  
    ```  
  
2.  Utilisez le pointeur pour sélectionner les mots `CREATE DATABASE`, et appuyez sur la touche **F1**. La rubrique `CREATE DATABASE` correspondante de la documentation en ligne de Microsoft SQL Server doit s’ouvrir. Vous pouvez faire appel à cette technique pour rechercher la syntaxe complète de `CREATE DATABASE` et pour les autres instructions utilisées dans ce tutoriel.  
  
3.  Dans l'Éditeur de requête, appuyez sur la touche **F5** pour exécuter l'instruction et créer une base de données nommée `TestData`.  
  
Lorsque vous créez une base de données, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] effectue une copie de la base de données **model** et remplace le nom de la copie par le nom de la base de données. Cette opération ne doit prendre que quelques secondes, sauf si vous spécifiez une taille initiale importante pour la base de données comme paramètre facultatif.  
  
> [!NOTE]  
> Le mot clé GO sépare les instructions si plus d'une instruction est envoyée dans un même traitement. GO est facultatif lorsque le traitement contient uniquement une seule instruction.  

## <a name="create-a-table"></a>Créer une table

[!INCLUDE[tsql-appliesto-ss2008-all-md](../includes/tsql-appliesto-ss2008-all-md.md)]

Pour créer une table, vous devez fournir un nom pour la table et les noms et les types de données de chaque colonne dans la table. Il est aussi recommandé d'indiquer si les valeurs Null sont autorisées dans chaque colonne. Pour créer une table, vous devez avoir les autorisations `CREATE TABLE` et `ALTER SCHEMA` sur le schéma qui contiendra la table. Le rôle fixe de base de données [`db_ddladmin`](../relational-databases/security/authentication-access/database-level-roles.md) dispose de ces autorisations.  
  
La plupart des tables possèdent une clé primaire constituée d'une ou plusieurs colonnes de la table. Une clé primaire est toujours unique. Le [!INCLUDE[ssDE](../includes/ssde-md.md)] applique la restriction qui veut que les valeurs de clé primaire ne peuvent pas être répétées dans la table.  
  
Pour obtenir une liste des types de données et des liens contenant une description individuelle, consultez [Types de données &#40;Transact-SQL&#41;](../t-sql/data-types/data-types-transact-sql.md).  
  
> [!NOTE]  
> Vous pouvez configurer le [!INCLUDE[ssDE](../includes/ssde-md.md)] pour qu’il respecte la casse ou non. Si vous installez le [!INCLUDE[ssDE](../includes/ssde-md.md)] pour qu’il respecte la casse, les noms des objets doivent toujours avoir la même casse. Par exemple, une table nommée OrderData est différente d'une table nommée ORDERDATA. Si le [!INCLUDE[ssDE](../includes/ssde-md.md)] ne respecte pas la casse, ces deux noms de tables sont considérés comme une seule et même table, et ce nom ne peut être utilisé qu’une fois.  
  
  
### <a name="switch-the-query-editor-connection-to-the-testdata-database"></a>Passer la connexion de l'Éditeur de requête à la base de données TestData  

Dans une fenêtre Éditeur de requêtes, tapez et exécutez le code suivant pour modifier votre connexion à la base de données `TestData` .  
  
  ```sql  
  USE TestData  
  GO  
  ```  
  
### <a name="create-the-table"></a>Créer la table

Dans une fenêtre Éditeur de requêtes, tapez et exécutez le code suivant pour créer une table nommée `Products`. Les colonnes de la table sont nommées `ProductID`, `ProductName`, `Price`, et `ProductDescription`. La colonne `ProductID` est la clé primaire de la table. `int`, `varchar(25)`, `money`et `varchar(max)` sont tous des types de données. Seules les colonnes `Price` et `ProductionDescription` peuvent n'avoir aucune données lors de l'insertion ou de la modification d'une ligne. Cette instruction contient un élément facultatif (`dbo.`) appelé un schéma. Le schéma est l'objet de base de données qui est propriétaire de la table. Si vous êtes administrateur, `dbo` est le schéma par défaut. `dbo` représente le propriétaire de la base de données.  
  
  ```sql  
  CREATE TABLE dbo.Products  
     (ProductID int PRIMARY KEY NOT NULL,  
     ProductName varchar(25) NOT NULL,  
     Price money NULL,  
     ProductDescription varchar(max) NULL)  
  GO  
 ```  

## <a name="insert-and-update-data-in-a-table"></a>Insérer et mettre à jour des données dans une table
Une fois que vous avez créé la table **Products** , vous pouvez insérer des données dans la table à l’aide de l’instruction INSERT. Une fois les données insérées, vous allez modifier le contenu d'une ligne à l'aide d'une l'instruction UPDATE. Vous allez utiliser la clause WHERE de l'instruction UPDATE pour restreindre la mise à jour à une seule ligne. Les quatre instructions entrent les données suivantes.  
  
|IDProduit|ProductName|Price|ProductDescription|  
|-------------|---------------|---------|----------------------|  
|1|Clamp|12.48|Workbench clamp|  
|50|Screwdriver|3.17|Flat head|  
|75|Tire Bar||Outil pour changer des pneus.|  
|3000|3 mm Bracket|0.52||  
  
La syntaxe de base est la suivante : INSERT, nom de table, liste de colonne, VALUES, puis la liste des valeurs à insérer. Les deux tirets en début de ligne indiquent que celle-ci est un commentaire et que le texte sera ignoré par le compilateur. Dans ce cas, le commentaire décrit une variation autorisée de la syntaxe.  
  
### <a name="insert-data-into-a-table"></a>Insérer des données dans une table  
  
1.  Exécutez l'instruction suivante pour insérer une ligne dans la table `Products` créée au cours de la tâche précédente.
  
   ```sql 
   -- Standard syntax  
   INSERT dbo.Products (ProductID, ProductName, Price, ProductDescription)  
       VALUES (1, 'Clamp', 12.48, 'Workbench clamp')  
   GO   
   ```  

   > [!NOTE]
   > Si l’insertion réussit, passez à l’étape suivante.
   >
   > Si l’insertion échoue, c’est peut-être que la table `Product` contient déjà une ligne avec cet ID de produit. Pour continuer, supprimez toutes les lignes de la table et répétez l’étape précédente. [`TRUNCATE TABLE`](statements/truncate-table-transact-sql.md) supprime toutes les lignes de la table. 
   >
   > Exécutez la commande suivante pour supprimer toutes les lignes de la table :
   > 
   > ```sql
   >TRUNCATE TABLE TestData.dbo.Products;
   > GO
   >```
   >
   > Après avoir tronqué la table, répétez la commande `INSERT` dans cette étape.

2.  L'instruction suivante montre comment vous pouvez modifier l'ordre dans lequel les paramètres sont fournis en alternant la position de `ProductID` et `ProductName` dans la liste des champs (entre parenthèses) et dans la liste des valeurs.  
  
   ```sql  
   -- Changing the order of the columns  
   INSERT dbo.Products (ProductName, ProductID, Price, ProductDescription)  
       VALUES ('Screwdriver', 50, 3.17, 'Flat head')  
   GO    
   ```  
  
3.  L'instruction suivante montre que les noms des colonnes sont facultatifs tant que les valeurs sont répertoriées dans le bon ordre. Cette syntaxe est courante mais n'est pas recommandée car elle peut rendre votre code difficile à comprendre. `NULL` est spécifié pour la colonne `Price` car le prix du produit n’est pas encore connu.  
  
   ```sql  
   -- Skipping the column list, but keeping the values in order  
   INSERT dbo.Products  
       VALUES (75, 'Tire Bar', NULL, 'Tool for changing tires.')  
   GO  
  ```  
  
4.  Le nom de schéma est facultatif tant que vous accédez et modifiez une table dans votre schéma par défaut. Comme la colonne `ProductDescription` autorise les valeurs Null et qu'aucune valeur n'est fournie, le nom de colonne et la valeur `ProductDescription` peuvent être supprimés de l'instruction complètement.  
  
   ```sql  
   -- Dropping the optional dbo and dropping the ProductDescription column  
   INSERT Products (ProductID, ProductName, Price)  
       VALUES (3000, '3 mm Bracket', 0.52)  
   GO  
   ```  
  
### <a name="update-the-products-table"></a>Mettre à jour la table Products  
Tapez et exécutez l'instruction `UPDATE` suivante pour remplacer le `ProductName` du deuxième produit à partir de `Screwdriver`par `Flat Head Screwdriver`.  
  
  ```sql  
  UPDATE dbo.Products  
      SET ProductName = 'Flat Head Screwdriver'  
      WHERE ProductID = 50  
  GO  
  ```  

## <a name="read-data-from-a-table"></a>Lire les données d’une table
Utilisez l'instruction SELECT pour lire les données dans une table. L'instruction SELECT est une des instructions [!INCLUDE[tsql](../includes/tsql-md.md)] les plus importantes et dont la syntaxe comporte beaucoup de variations. Pour ce didacticiel, vous allez travailler avec cinq versions simples.  
  
### <a name="read-the-data-in-a-table"></a>Lire les données d’une table  
  
1.  Tapez et exécutez les instructions suivantes pour lire les données dans la table `Products` .  
  
  ```sql 
  -- The basic syntax for reading data from a single table  
  SELECT ProductID, ProductName, Price, ProductDescription  
      FROM dbo.Products  
  GO  
  ```  
  
2.  Vous pouvez utiliser un astérisque (`*`) pour sélectionner toutes les colonnes de la table. L’astérisque est destiné aux requêtes ad hoc. Dans le code permanent, fournissez la liste des colonnes pour que l’instruction retourne les colonnes prédites, même si une nouvelle colonne est par la suite ajoutée à la table.  
  
  ```sql  
  -- Returns all columns in the table  
  -- Does not use the optional schema, dbo  
  SELECT * FROM Products  
  GO   
  ```  
  
3.  Vous pouvez omettre les colonnes que vous ne souhaitez pas retourner. Les colonnes seront retournées dans leur ordre d'apparition.  
  
  ```sql  
  -- Returns only two of the columns from the table  
  SELECT ProductName, Price  
      FROM dbo.Products  
  GO    
  ```  
  
4.  Utilisez une clause `WHERE` pour limiter les lignes retournées à l'utilisateur.  
  
  ``` sql 
  -- Returns only two of the records in the table  
  SELECT ProductID, ProductName, Price, ProductDescription  
      FROM dbo.Products  
      WHERE ProductID < 60  
  GO    
  ```  
  
5.  Vous pouvez travailler avec les valeurs des colonnes à mesure qu'elles sont retournées. L'exemple suivant effectue une opération mathématique sur la colonne `Price` . Les colonnes ayant été modifiées de cette manière n'ont pas de nom sauf si vous en fournissez un à l'aide du mot clé `AS` .  
  
  ```sql  
  -- Returns ProductName and the Price including a 7% tax  
  -- Provides the name CustomerPays for the calculated column  
  SELECT ProductName, Price * 1.07 AS CustomerPays  
      FROM dbo.Products  
  GO  
  ```  
  
### <a name="useful-functions-in-a-select-statement"></a>Fonctions utiles dans une instruction SELECT  
Pour des informations sur certaines fonctions que vous pouvez utiliser pour travailler avec des données dans les instructions SELECT, consultez les rubriques suivantes :  
  
|||  
|-|-|  
|[Fonctions de chaîne &#40;Transact-SQL&#41;](../t-sql/functions/string-functions-transact-sql.md)|[Types de données et fonctions de date et d’heure &#40;Transact-SQL&#41;](../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md)|  
|[Fonctions mathématiques &#40;Transact-SQL&#41;](../t-sql/functions/mathematical-functions-transact-sql.md)|[Fonctions texte et image &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/b9c70488-1bf5-4068-a003-e548ccbc5199)|  

## <a name="create-views-and-stored-procedures"></a>Créer des vues et des procédures stockées
Une vue est une instruction SELECT stockée, et une procédure stockée correspond à une ou plusieurs instructions [!INCLUDE[tsql](../includes/tsql-md.md)] qui s'exécutent comme un traitement.  
  
Les vues peuvent être interrogées comme des tables et n'acceptent pas de paramètres. Les procédures stockées sont plus complexes que les vues. Elles peuvent contenir des paramètres d'entrée et de sortie et peuvent contenir des instructions pour contrôler le flux du code, comme les instructions IF et WHILE. Il est recommandé de faire appel aux procédures stockées pour coder toutes les actions répétitives dans la base de données  
  
Pour cet exemple, vous allez utiliser CREATE VIEW pour créer une vue qui sélectionne seulement deux des colonnes dans la table **Products** . Puis, vous allez utiliser l'instruction CREATE PROCEDURE pour créer une procédure stockée qui accepte un paramètre de prix et retourne uniquement les produits dont le prix est inférieur à la valeur de paramètre spécifiée.  
  
### <a name="create-a-view"></a>Créer une vue  
  
Exécutez l’instruction suivante pour créer une vue qui exécute une instruction SELECT et retourne les noms et les prix de nos produits à l’utilisateur.  
  
  ```sql  
  CREATE VIEW vw_Names  
     AS  
     SELECT ProductName, Price FROM Products;  
  GO    
  ```  
  
### <a name="test-the-view"></a>Tester la vue  
  
Les vues sont traitées comme des tables. Utilisez une instruction `SELECT` pour accéder à une vue.  
  
  ```sql  
  SELECT * FROM vw_Names;  
  GO   
  ```  
  
### <a name="create-a-stored-procedure"></a>Créer une procédure stockée  
  
L'instruction suivante crée un nom de procédure stockée `pr_Names`, accepte un paramètre d'entrée nommé `@VarPrice` du type de données `money`. La procédure stockée affiche l'instruction `Products less than` concaténée avec le paramètre d'entrée dont le type de données `money` est remplacé par un type de données character `varchar(10)`. Puis, la procédure exécute une instruction `SELECT` sur la vue et passe le paramètre d'entrée dans le cadre de la clause `WHERE`. Cette opération retourne tous les produits dont le prix est inférieur à la valeur du paramètre d'entrée.  
  
  ```sql  
  CREATE PROCEDURE pr_Names @VarPrice money  
     AS  
     BEGIN  
        -- The print statement returns text to the user  
        PRINT 'Products less than ' + CAST(@VarPrice AS varchar(10));  
        -- A second statement starts here  
        SELECT ProductName, Price FROM vw_Names  
              WHERE Price < @varPrice;  
     END  
  GO    
  ```  
  
### <a name="test-the-stored-procedure"></a>Tester la procédure stockée  
  
Pour tester la procédure stockée, tapez et exécutez l'instruction suivante. La procédure doit retourner les noms des deux produits entrés dans la table `Products` à la leçon 1 avec un prix inférieur à `10.00`.  
  
  ```sql  
  EXECUTE pr_Names 10.00;  
  GO  
  ```  

## <a name="next-steps"></a>Étapes suivantes
L’article suivant vous apprend à configurer des autorisations sur des objets de base de données. Les objets créés dans la leçon 1 sont également utilisés dans la leçon 2. 

Passez à l’article suivant pour en savoir plus :
> [!div class="nextstepaction"]
> [Étapes suivantes](../t-sql/lesson-2-configuring-permissions-on-database-objects.md)
  
  
  
