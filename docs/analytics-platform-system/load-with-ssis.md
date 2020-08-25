---
title: Charger avec Integration Services
description: Fournit des informations de référence et de déploiement pour le chargement de données dans des Data Warehouse parallèles (PDW) à l’aide de packages SQL Server Integration Services (SSIS).
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: ea2a4f39b16fe2f8b23d6a6a229ce9b936e6e6d7
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88766758"
---
# <a name="load-data-with-integration-services-to-parallel-data-warehouse"></a>Charger des données avec des Integration Services à des Data Warehouse parallèles
Fournit des informations de référence et de déploiement pour le chargement de données dans SQL Server Data Warehouse parallèles à l’aide de packages SQL Server Integration Services (SSIS).  
  
<!-- MISSING LINKS

## <a name="BeforeBegin"></a>Before You Begin  
Before you can start loading data, use the following topics to install the Integration Services Destination Adapters and to create an Integration Services package that connects SQL Server PDW:  


-   [Install Integration Services destination adapters](install-integration-services-destination-adapters.md)  
  
-   [Connect With Integration Services for loading](connect-with-ssis-for-loading.md)  
  
For general information about developing Integration Services packages, see [Designing and Implementing Packages (Integration Services)](https://msdn.microsoft.com/library/ms141091\(v=sql11\).aspx) on MSDN.  

-->
  
## <a name="basics"></a><a name="Basics"></a>Concepts de base  
Integration Services est le composant de SQL Server pour l’extraction, la transformation et le chargement (ETL) des données à hautes performances, et est couramment utilisé pour remplir et mettre à jour un entrepôt de données.  
  
L’adaptateur de destination PDW est un composant Integration Services qui vous permet de charger des données dans PDW à l’aide de Integration Services packages dtsx. Dans un flux de travail de package pour SQL ServerPDW, vous pouvez charger et fusionner des données à partir de plusieurs sources et charger des données vers plusieurs destinations. Les charges se produisent en parallèle, toutes les deux dans un package et entre plusieurs packages s'exécutant simultanément, avec un maximum de 10 charges s'exécutant en parallèle sur la même appliance.  
  
Outre les tâches décrites dans cette rubrique, vous pouvez utiliser d’autres fonctionnalités de Integration Services pour filtrer, transformer, analyser et nettoyer vos données avant de les charger dans l’entrepôt de données. Vous pouvez également améliorer le flux de travail du package en exécutant des instructions SQL, en exécutant des packages enfants ou en envoyant des messages électroniques.  
  
Pour obtenir une documentation complète sur Integration Services, consultez [SQL Server Integration Services](../integration-services/sql-server-integration-services.md).  
  
## <a name="methods-for-running-an-integration-services-package"></a><a name="HowToDeployPackage"></a>Méthodes d’exécution d’un package Integration Services  
Utilisez l’une des méthodes suivantes pour exécuter un package de Integration Services.  
  
### <a name="run-from-sql-server-2008-r2-business-intelligence-development-studio-bids"></a>Exécuter à partir de SQL Server 2008 R2 Business Intelligence Development Studio (BIDS)  
Pour exécuter le package à partir d’enchères, cliquez avec le bouton droit sur votre package et choisissez **exécuter le package**.  
  
Par défaut, BIDS exécute les packages en utilisant des binaires 64 bits. Cela est déterminé par la propriété du package **Run64BitRuntime** . Pour définir cette propriété, accédez à **Explorateur de solutions**, cliquez avec le bouton droit sur votre projet et choisissez **Propriétés**. Dans les **pages de propriétés de Integration Services**, accédez à **Propriétés de configuration** et sélectionnez **débogage**. La propriété **Run64BitRuntime** s’affiche sous les **options de débogage**. Pour utiliser des runtimes 32 bits, affectez la valeur **false**. Pour utiliser des runtimes 64 bits, affectez la valeur **true**.  
  
### <a name="run-from-sql-server-2012-sql-server-data-tools"></a>Exécuter à partir de SQL Server 2012 SQL Server Data Tools  
Pour exécuter le package à partir de SQL Server Data Tools, cliquez avec le bouton droit sur votre package et choisissez **exécuter le package**.  
  
### <a name="run-from-powershell"></a>Exécuter à partir de PowerShell  
Pour exécuter le package à partir de Windows PowerShell, à l’aide de l’utilitaire **dtexec** : `dtexec /FILE <packagePath>`  
  
Par exemple : `dtexec /FILE "C:\Users\User1\Desktop\Package.dtsx"`  
  
### <a name="run-from-a-windows-command-prompt"></a>Exécuter à partir d’une invite de commandes Windows 
Pour exécuter le package à partir d’une invite de commandes Windows, à l’aide de l’utilitaire **dtexec** : `dtexec /FILE <packagePath>`  
  
Par exemple : `dtexec /FILE "C:\Users\User1\Desktop\Package.dtsx"`  
  
## <a name="data-types"></a><a name="DataTypes"></a>Type de données  
Lorsque vous utilisez Integration Services pour charger des données à partir d’une source de données dans une base de données SQL Server PDW, les données sont d’abord mappées à partir des données sources vers des types de données Integration Services. Cela permet à des données provenant de plusieurs sources de données d'être mappées à un ensemble commun de types de données.  
  
Ensuite, les données sont mappées à partir de Integration Services à des types de données SQL Server PDW. Pour chaque type de données SQL Server PDW, le tableau suivant répertorie les types de données Integration Services qui peuvent être convertis en SQL Server PDW type de données.  
  
|Type de données PDW|Integration Services le ou les types de données mappés au type de données PDW|  
|---------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------|  
|BIT|DT_BOOL|  
|bigint|DT_I1, DT_I2, DT_I4, DT_I8, DT_UI1, DT_UI2, DT_UI4|  
|CHAR|DT_STR|  
|DATE|DT_DBDATE|  
|DATETIME|DT_DATE, DT_DBDATE, DT_DBTIMESTAMP, DT_DBTIMESTAMP2|  
|DATETIME2|DT_DATE, DT_DBDATE, DT_DBTIMESTAMP, DT_DBTIMESTAMP2|  
|DATETIMEOFFSET|DT_WSTR|  
|DECIMAL|DT_DECIMAL, DT_I1, DT_I2, DT_I4, DT_I4, DT_I8, DT_NUMERIC, DT_UI1, DT_UI2, DT_UI4, DT_UI8|  
|FLOAT|DT_R4, DT_R8|  
|INT|DT_I1, DTI2, DT_I4, DT_UI1, DT_UI2|  
|MONEY|DT_CY|  
|NCHAR|DT_WSTR|  
|NUMERIC|DT_DECIMAL, DT_I1, DT_I2, DT_I4, DT_I8, DT_NUMERIC, DT_UI1, DT_UI2, DT_UI4, DT_UI8|  
|NVARCHAR|DT_WSTR, DT_STR|  
|real|DT_R4|  
|SMALLDATETIME|DT_DBTIMESTAMP2|  
|SMALLINT|DT_I1, DT_I2, DT_UI1|  
|SMALLMONEY|DT_R4|  
|TEMPS|DT_WSTR|  
|TINYINT|DT_I1|  
|VARBINARY|DT_BYTES|  
|VARCHAR|DT_STR|  
  
**Prise en charge limitée de la précision des types de données**  
  
PDW génère une erreur de validation si vous mappez une DT_NUMERIC ou DT_DECIMAL colonne d’entrée qui contient une valeur avec une précision supérieure à 28.  
  
**Types de données non pris en charge**  
  
SQL Server PDW ne prend pas en charge les types de données Integration Services suivants :  
  
-   DT_DBTIMESTAMPOFFSET  
  
-   DT_DBTIME2  
  
-   DT_GUID  
  
-   DT_IMAGE  
  
-   DT_NTEXT  
  
-   DT_TEXT  
  
Pour charger des colonnes qui contiennent des données de ces types dans SQL Server PDW, vous devez ajouter une transformation de conversion de données en amont dans le flux de données pour convertir les données en un type de données compatible.  
  
## <a name="permissions"></a>Autorisations  
Pour exécuter un package de charge Integration Services, vous avez besoin des éléments suivants :  
  
-   Autorisation LOAD sur la base de données.  
  
-   Autorisations INSERT, UPDATE et DELETE applicables sur la table de destination.  
  
-   Si une base de données de mise en lots est utilisée, créez l’autorisation sur la base de données de mise en lots. Il s’agit de la création d’une table temporaire.  
  
-   Si aucune base de données de mise en lots n’est utilisée, créez l’autorisation sur la base de données de destination. Il s’agit de la création d’une table temporaire.  
  
## <a name="general-remarks"></a><a name="GenRemarks"></a>Remarques générales  
Lorsqu’un package de Integration Services a plusieurs destinations SQL Server PDW en cours d’exécution et que l’une des connexions est terminée, Integration Services arrête de pousser les données vers toutes les destinations de SQL Server PDW.  
  
## <a name="limitations-and-restrictions"></a><a name="Limits"></a>Limitations et restrictions  
Pour un package Integration Services, le nombre de destinations de SQL Server PDW pour la même source de données est limité par le nombre maximal de charges actives. Le maximum est préconfiguré et n'est pas configurable par l'utilisateur. 

<!-- MISSING LINKS
For the maximum number of loads and queued loads per appliance, see [Minimum and maximum values](minimum-and-maximum-values.md).  
-->
  
Chaque destination de package Integration Services pour la même source de données compte comme une charge lorsque le package est en cours d’exécution. Supposons, par exemple, que le nombre maximal de charges actives soit de 10. Le package ne s'exécute pas s'il tente d'ouvrir 11 destinations ou plus pour la même source de données.  
  
Plusieurs packages peuvent s'exécuter simultanément à condition que chaque package n'utilise pas plus de charges actives que le nombre maximal. Par exemple, si le nombre maximal de charges actives est de 10, vous pouvez exécuter simultanément deux packages qui utilisent chacun 10 destinations. Un package s'exécute pendant que l'autre attend dans la file d'attente des charges.  
  
Si le nombre de charges présentes dans la file d'attente des charges dépasse le nombre maximal de charges mises en file d'attente, le package ne s'exécute pas. Par exemple, si le nombre maximal de charges est de 10 par appliance et que le nombre maximal de charges en file d’attente est de 40 par appliance, vous pouvez exécuter simultanément cinq packages de Integration Services qui ouvrent chacun 10 destinations. Si vous essayez d'exécuter un sixième package, il ne s'exécute pas.  

> [!IMPORTANT]
> L’utilisation d’une source de données OLE DB dans SSIS avec l’adaptateur de destination PDW peut endommager les données si la table source contient des colonnes char et varchar avec des classements SQL. Nous vous recommandons d’utiliser une source ADO.NET si la table source contient des colonnes char ou varchar avec des classements SQL. 

  
## <a name="locking-behavior"></a><a name="Locks"></a>Comportement de verrouillage  
Lors du chargement de données avec Integration Services, SQL ServerPDW utilise des verrous de niveau ligne pour mettre à jour les données dans la table de destination. Cela signifie que chaque ligne est verrouillée en lecture et en écriture pendant sa mise à jour. Les lignes de la table de destination ne sont pas verrouillées pendant le chargement des données dans la table de mise en lots.  
  
## <a name="examples"></a><a name="Examples"></a>Exemples  
  
### <a name="a-simple-load-from-flat-file"></a><a name="Walkthrough"></a>A. Chargement simple à partir d’un fichier plat  
La procédure pas à pas suivante illustre un chargement de données simple à l’aide de Integration Services pour charger des données de fichier plat sur un appareil SQL Server PDW.  Cet exemple suppose que Integration Services a déjà été installé sur l’ordinateur client et que la destination de SQL Server PDW a été installée, comme décrit ci-dessus.  
  
Dans cet exemple, nous allons charger dans la `Orders` table, qui a la DDL suivante. La `Orders` table fait partie de la `LoadExampleDB` base de données.  
  
```sql  
CREATE TABLE LoadExampleDB.dbo.Orders (  
   id INT,  
   city varchar(25),  
   lastUpdateDate DATE,  
   orderDate DATE)  
;  
```  
  
Voici les données de chargement :  
  
```  
id        city           lastUpdateDate     orderdate  
--------- -------------- ------------------ ----------  
1         Seattle        2010-05-01         2010-01-01  
2         Denver         2002-06-25         1999-01-02  
```  
  
Pour préparer le chargement, créez le fichier plat `exampleLoad.txt` , contenant les données de chargement :  
  
```  
id,city,lastUpdateDate,orderDate  
1,Seattle,2010-05-01,2010-01-01  
2,Denver,2002-06-25,1999-01-02  
```  
  
Commencez par créer un package Integration Services en effectuant les étapes suivantes :  
  
1.  Dans SQL Server Data Tools \( SSDT \) , sélectionnez **fichier**, **nouveau**, puis **projet**. Sélectionnez **Integration Services projet** dans les options de la liste. Nommez ce projet `ExampleLoad` , puis cliquez sur **OK**.  
  
2.  Cliquez sur l’onglet **Flow Control** , puis faites glisser la **tâche de workflow** de la **boîte à outils** vers le volet **Flow Control** .  
  
3.  Cliquez sur l’onglet **Flow Data** , puis faites glisser **source de fichier plat** de la **boîte à outils** vers le volet de **Workflow** . Double-cliquez sur la zone que vous venez de créer pour ouvrir l' **éditeur de source de fichier plat**.  
  
4.  Cliquez sur **Gestionnaire de connexions** , puis sur **nouveau**.  
  
5.  Dans la zone **nom du gestionnaire de connexions** , entrez un nom convivial pour la connexion. Pour cet exemple, `Example Load Flat File CM` .  
  
6.  Cliquez sur **Parcourir** et sélectionnez le `ExampleLoad.txt` fichier sur l’ordinateur local.  
  
7.  Étant donné que le fichier plat contient une ligne avec des noms de colonnes, cliquez sur les **noms des colonnes dans la première zone de ligne de données** .  
  
8.  Cliquez sur **colonnes** dans la colonne de gauche, puis affichez un aperçu des données qui seront chargées pour vérifier que les noms de colonne et les données ont été interprétés correctement.  
  
9. Dans la colonne de gauche, cliquez sur **avancé** . Cliquez sur chaque nom de colonne pour vérifier le type de données qui a été associé aux données. Le type est modifié dans la zone afin que les types de données des données chargées soient compatibles avec les types de colonne de destination.  
  
10. Cliquez sur **OK** pour enregistrer votre gestionnaire de connexions.  
  
11. Cliquez sur **OK** pour quitter l **'éditeur de source de fichier plat**.  
  
Spécifiez la destination du Workflow.  
  
1.  Faites glisser le **SQL Server PDW destination** de la **boîte à outils** vers le volet de répartition des **données** .  
  
2.  Double-cliquez sur la zone que vous venez de créer pour charger l' **éditeur de Destination SQL Server PDW**.  
  
3.  Cliquez sur la flèche vers le bas en regard de **Gestionnaire de connexions**.  
  
4.  Sélectionnez **créer une nouvelle connexion**.  
  
5.  Renseignez les informations du serveur, de l’utilisateur, du mot de passe et de la base de données de destination avec des informations spécifiques à votre appliance. (Des exemples sont illustrés ci-dessous). Cliquez ensuite sur **OK**.  
  
    Pour les connexions InfiniBand, **nom du serveur**: entrez <Appliance-Name>-SQLCTL01, 17001.  
  
    Pour les connexions Ethernet, **nom du serveur**: entrez l’adresse IP du cluster de nœuds de contrôle, la virgule, le port 17001. Par exemple, 10.192.63.134, 17001.  
  
    **Utilisateur**`user1`  
  
    **De**`password1`  
  
    **Base de données de destination :**`LoadExampleDB`  
  
6.  Sélectionnez la table de destination : `Orders` .  
  
7.  Sélectionnez **Ajouter** en tant que mode de chargement, puis cliquez sur **OK**.  
  
Spécifiez le workflow de la source vers la destination.  
  
1.  Dans le volet de **Workflow** , faites glisser la flèche verte de la zone **source de fichier plat** vers la zone de **destination SQL Server PDW** .  
  
2.  Double-cliquez sur la zone de **destination SQL Server PDW** pour afficher à nouveau l' **éditeur de destination SQL Server PDW** . Vous devez voir les noms des colonnes à partir du fichier plat situé à gauche, sous **colonnes d’entrée non mappées**. Vous devez voir les noms des colonnes à partir de la table de destination à droite, sous **colonnes de destination non mappées**. Mappez les colonnes en les faisant glisser ou en double-cliquant sur les noms de colonnes correspondants dans les listes colonnes **d’entrée non mappées** et **colonnes de destination non mappées** dans la zone **colonnes mappées** . Cliquez sur **OK** pour enregistrer vos paramètres.  
  
3.  Enregistrez le package en cliquant sur **Enregistrer** dans le menu **fichier** .  
  
Exécutez le package sur votre ordinateur Integration Services.  
  
1.  Dans la**Explorateur de solutions** Integration Services (colonne de droite), cliquez avec le bouton droit `Package.dtsx` et sélectionnez **exécuter**.  
  
2.  Le package s’exécute et la progression ainsi que toutes les erreurs sont affichées dans le volet de **progression** . Utilisez un client SQL pour confirmer la charge, ou surveillez la charge via la console d’administration SQL Server PDW.  
  
## <a name="see-also"></a>Voir aussi  
[Créer une tâche de script qui utilise l’adaptateur de destination SSIS PDW](create-ssis-script-task-using-pdw-destination-adapter.md)  
[SQL Server Integration Services](../integration-services/sql-server-integration-services.md)  
[Conception et implémentation de packages (Integration Services)](https://msdn.microsoft.com/library/ms141091\(v=sql11\).aspx)  
[Didacticiel : Création d'un package de base à l'aide d'un Assistant](https://technet.microsoft.com/library/ms365330\(v=sql11\).aspx)  
[Prise en main (Integration Services)](https://go.microsoft.com/fwlink/?LinkId=202412)  
[Exemple de génération de package dynamique](https://go.microsoft.com/fwlink/?LinkId=202413)  
[Conception de vos packages SSIS pour le parallélisme (Vidéo liée à SQL Server)](/previous-versions/sql/sql-server-2008/dd795221(v=sql.100))  
[Exemples de la communauté Microsoft SQL Server : Integration Services](https://go.microsoft.com/fwlink/?LinkId=202415)  
[Amélioration des chargements incrémentiels avec la capture de données modifiées](../integration-services/change-data-capture/change-data-capture-ssis.md)  
[Transformation de dimension à variation lente](../integration-services/data-flow/transformations/slowly-changing-dimension-transformation.md)  
[Tâche d’insertion en bloc](../integration-services/control-flow/bulk-insert-task.md)  
  
<!-- MISSING LINKS
[Grant permissions to load data](grant-permissions-to-load-data.md)  
[Common metadata query examples](metadata-query-examples.md)
-->