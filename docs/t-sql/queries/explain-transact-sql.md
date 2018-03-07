---
title: EXPLIQUEZ (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 08/09/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4846a576-57ea-4068-959c-81e69e39ddc1
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 515c21cbf7874c0268eeedad0b67e0ce7cf3726d
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="explain-transact-sql"></a>EXPLAIN (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Retourne le plan de requête pour un [!INCLUDE[ssDW](../../includes/ssdw-md.md)] [!INCLUDE[DWsql](../../includes/dwsql-md.md)] instruction sans l’instruction en cours d’exécution. Utilisez **expliquer** aperçu quelles opérations nécessitera le déplacement des données et d’afficher les coûts estimés des opérations de requête.  
  
 Pour plus d’informations sur les plans de requête, consultez « Présentation des Plans de requête » dans la [!INCLUDE[pdw-product-documentation_md](../../includes/pdw-product-documentation-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  

```  
EXPLAIN SQL_statement  
[;]  
```  
  
## <a name="arguments"></a>Arguments  
 *SQL_statement*  
 Le [!INCLUDE[DWsql](../../includes/dwsql-md.md)] instruction sur laquelle **expliquer** s’exécutera. *SQL_statement* peut être une de ces commandes : **sélectionnez**, **insérer**, **mise à jour**, **supprimer**, **CREATE TABLE AS SELECT**, **CREATE REMOTE TABLE**.  
  
## <a name="permissions"></a>Autorisations  
 Requiert le **SHOWPLAN** autorisation et l’autorisation d’exécuter *SQL_statement*. Consultez [autorisations : GRANT, DENY, REVOKE &#40; Entrepôt de données SQL Azure, Parallel Data Warehouse &#41; ](../../t-sql/statements/permissions-grant-deny-revoke-azure-sql-data-warehouse-parallel-data-warehouse.md).  
  
## <a name="return-value"></a>Valeur retournée  
 La valeur de retour à partir de la **expliquer** commande est un document XML avec la structure illustré ci-dessous. Ce document XML répertorie toutes les opérations dans le plan de requête pour la requête, chacune délimitée par le `<dsql_operation>` balise. La valeur de retour est de type **nvarchar (max)**.  
  
 Le plan de requête retournée représente les instructions SQL séquentielles ; lors de la requête s’exécute, il peut inclure opérations parallélisées, pour certaines instructions séquentielles indiquées peuvent s’exécuter en même temps.  
  
```  
\<?xml version="1.0" encoding="utf-8"?>  
<dsql_query>  
  <sql>. . .</sql>  
  <params />  
  <dsql_operations>  
    <dsql_operation>  
     . . .      
    </dsql_operation>  
    [ . . . n ]  
  <dsql_operations>  
</dsql_query>  
```  
  
 Les balises XML contient ces informations :  
  
|Balise XML|Résumé, attributs et du contenu|  
|-------------|--------------------------------------|  
|\<dsql_query>|Élément de niveau supérieur ou de document.|
|\<sql>|Retourne les données *SQL_statement*.|  
|\<params>|Cette balise n’est pas utilisée pour l’instant.|  
|\<dsql_operations>|Résume et contient les étapes de la requête et inclut des informations de coût de la requête. Contient également tous les `<dsql_operation>` blocs. Cette balise contient des informations d’inventaire pour l’intégralité de la requête :<br /><br /> `<dsql_operations total_cost=total_cost total_number_operations=total_number_operations>`<br /><br /> *total_cost* est le temps total estimé de la requête à exécuter, en millisecondes.<br /><br /> *total_number_operations* est le nombre total d’opérations de la requête. Une opération qui va être parallélisée et exécuter sur plusieurs nœuds est comptée comme une seule opération.|  
|\<dsql_operation>|Décrit une opération unique dans le plan de requête. Le \<dsql_operation > balise contient le type d’opération en tant qu’attribut :<br /><br /> `<dsql_operation operation_type=operation_type>`<br /><br /> *type_opération* est une des valeurs figurant dans [interrogation des données (SQL Server PDW)](http://msdn.microsoft.com/en-us/3f4f5643-012a-4c36-b5ec-691c4bbe668c).<br /><br /> Le contenu de la `\<dsql_operation>` bloc est dépendant du type d’opération.<br /><br /> Consultez le tableau ci-dessous.|  
  
|Type d’opération|Contenu|Exemple|  
|--------------------|-------------|-------------|  
|BROADCAST_MOVE, DISTRIBUTE_REPLICATED_TABLE_MOVE, MASTER_TABLE_MOVE, PARTITION_MOVE, SHUFFLE_MOVE et TRIM_MOVE|`<operation_cost>`élément avec ces attributs. Valeurs reflètent uniquement l’opération locale :<br /><br /> -   *coût* est le coût de l’opérateur local et affiche le temps estimé pour l’opération à exécuter, en millisecondes.<br />-   *accumulative_cost* est la somme de toutes les opérations vue dans le plan, y compris les valeurs additionnées pour les opérations en parallèle, en ms.<br />-   *average_rowsize* est la taille de ligne moyenne estimée (en octets) de lignes récupéré et passé lors de l’opération.<br />-   *output_rows* est la cardinalité de sortie (nœud) et indique le nombre de lignes de sortie.<br /><br /> `<location>`: Les nœuds ou les distributions où l’opération se produit. Les options sont : « Contrôle », « ComputeNode », « AllComputeNodes », « AllDistributions », « SubsetDistributions », « Distribution » et « SubsetNodes ».<br /><br /> `<source_statement>`: Les données sources pour la réorganisation de la déplacement.<br /><br /> `<destination_table>`: La table temporaire interne, les données seront déplacées dans.<br /><br /> `<shuffle_columns>`: (Applicable uniquement aux opérations de SHUFFLE_MOVE). Une ou plusieurs colonnes qui servira comme colonnes de distribution pour la table temporaire.|`<operation_cost cost="40" accumulative_cost="40" average_rowsize = "50" output_rows="100"/>`<br /><br /> `<location distribution="AllDistributions" />`<br /><br /> `<source_statement type="statement">SELECT [TableAlias_3b77ee1d8ccf4a94ba644118b355db9d].[dist_date] FROM [qatest].[dbo].[flyers] [TableAlias_3b77ee1d8ccf4a94ba644118b355db9d]       </source_statement>`<br /><br /> `<destination_table>Q_[TEMP_ID_259]_[PARTITION_ID]</destination_table>`<br /><br /> `<shuffle_columns>dist_date;</shuffle_columns>`|  
|CopyOperation|`<operation_cost>`: Consultez `<operation_cost>` ci-dessus.<br /><br /> `<DestinationCatalog>`: Le nœud de destination ou les nœuds.<br /><br /> `<DestinationSchema>`: Le schéma de destination dans DestinationCatalog.<br /><br /> `<DestinationTableName>`: Nom de la table de destination ou un « TableName ».<br /><br /> `<DestinationDatasource>`: Les informations de connexion ou de nom pour la source de données de destination.<br /><br /> `<Username>`et `<Password>`: ces champs indiquent qu’un nom d’utilisateur et un mot de passe pour la destination peuvent être nécessaire.<br /><br /> `<BatchSize>`: La taille de lot pour l’opération de copie.<br /><br /> `<SelectStatement>`: L’instruction select utilisée pour effectuer la copie.<br /><br /> `<distribution>`: La distribution sur lequel la copie est effectuée.|`<operation_cost cost="0" accumulative_cost="0" average_rowsize="4" output_rows="1" />`<br /><br /> `<DestinationCatalog>master</DestinationCatalog>`<br /><br /> `<DestinationSchema>dbo</DestinationSchema>`<br /><br /> `<DestinationTableName>[TableName]</DestinationTableName>`<br /><br /> `<DestinationDatasource>localhost, 8080</DestinationDatasource>`<br /><br /> `<Username>...</Username>`<br /><br /> `<Password>...</Password>`<br /><br /> `<BatchSize>6000</BatchSize>`<br /><br /> `<SelectStatement>SELECT T1_1.c1 AS c1 FROM [qatest].[dbo].[gigs] AS T1_1</SelectStatement>`<br /><br /> `<distribution>ControlNode</distribution>`|  
|MetaDataCreate_Operation|`<source_table>`: La table source de l’opération.<br /><br /> `<destionation_table>`: La table de destination pour l’opération.|`<source_table>databases</source_table>`<br /><br /> `<destination_table>MetaDataCreateLandingTempTable</destination_table>`|  
|ON|`<location>`: Consultez `<location>` ci-dessus.<br /><br /> `<sql_operation>`: Identifie la commande SQL qui est exécutée sur un nœud.|`<location permanent="false" distribution="AllDistributions">Compute</location>`<br /><br /> `<sql_operation type="statement">CREATE TABLE [tempdb].[dbo]. [Q_[TEMP_ID_259]]_ [PARTITION_ID]]]([dist_date] DATE) WITH (DISTRIBUTION = HASH([dist_date]),) </sql_operation>`|  
|RemoteOnOperation|`<DestinationCatalog>`: Le catalogue de destination.<br /><br /> `<DestinationSchema>`: Le schéma de destination dans DestinationCatalog.<br /><br /> `<DestinationTableName>`: Nom de la table de destination ou un « TableName ».<br /><br /> `<DestinationDatasource>`: Nom de la source de données de destination.<br /><br /> `<Username>`et `<Password>`: ces champs indiquent qu’un nom d’utilisateur et un mot de passe pour la destination peuvent être nécessaire.<br /><br /> `<CreateStatement>`: L’instruction de création de table pour la base de données de destination.|`<DestinationCatalog>master</DestinationCatalog>`<br /><br /> `<DestinationSchema>dbo</DestinationSchema>`<br /><br /> `<DestinationTableName>TableName</DestinationTableName>`<br /><br /> `<DestinationDatasource>DestDataSource</DestinationDatasource>`<br /><br /> `<Username>...</Username>`<br /><br /> `<Password>...</Password>`<br /><br /> `<CreateStatement>CREATE TABLE [master].[dbo].[TableName] ([col1] BIGINT) ON [PRIMARY] WITH(DATA_COMPRESSION=PAGE);</CreateStatement>`|  
|RETURN|`<resultset>`: L’identificateur du jeu de résultats.|`<resultset>RS_19</resultset>`|  
|RND_ID|`<identifier>`: L’identificateur de l’objet créé.|`<identifier>TEMP_ID_260</identifier>`|  
  
## <a name="limitations-and-restrictions"></a>Limitations et restrictions  
 **EXPLIQUEZ** peuvent être appliquées à *conditions* uniquement, les requêtes qui sont des requêtes qui peuvent être améliorés ou modifiés selon les résultats d’une **EXPLIQUENT** commande. La prise en charge **expliquer** commandes sont répertoriés ci-dessus. Toute tentative d’utilisation **expliquer** avec une requête non pris en charge type sera retournent une erreur ou la requête d’écho.  
  
 **EXPLIQUEZ** n’est pas pris en charge dans une transaction utilisateur.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant montre une **expliquer** commande exécutée sur un **sélectionnez** instruction et le résultat XML.  
  
 **Envoi d’une instruction d’expliquer**  
  
 La commande soumise pour cet exemple est la suivante :  
  
```  
-- Uses AdventureWorks  
  
EXPLAIN   
    SELECT CAST (AVG(YearlyIncome) AS int) AS AverageIncome,   
        CAST(AVG(FIS.SalesAmount) AS int) AS AverageSales,   
        G.StateProvinceName, T.SalesTerritoryGroup  
    FROM dbo.DimGeography AS G  
    JOIN dbo.DimSalesTerritory AS T  
        ON G.SalesTerritoryKey = T.SalesTerritoryKey  
    JOIN dbo.DimCustomer AS C  
        ON G.GeographyKey = C.GeographyKey  
    JOIN dbo.FactInternetSales AS FIS  
        ON C.CustomerKey = FIS.CustomerKey  
    WHERE T.SalesTerritoryGroup IN ('North America', 'Pacific')  
        AND Gender = 'F'  
    GROUP BY G.StateProvinceName, T.SalesTerritoryGroup  
    ORDER BY AVG(YearlyIncome) DESC;  
GO  
```  
  
 Après l’exécution de l’instruction en utilisant la **expliquer** option, l’onglet message présente une seule ligne intitulée **expliquent**et en commençant par le texte XML `\<?xml version="1.0" encoding="utf-8"?>` cliquez sur le code XML pour ouvrir l’intégralité du texte dans une fenêtre XML. Pour mieux comprendre les commentaires suivants, vous devez activer l’affichage des numéros de ligne dans SSDT.  
  
#### <a name="to-turn-on-line-numbers"></a>Pour activer les numéros de ligne  
  
1.  Avec la sortie apparaît dans le **expliquent** onglet SSDT, sur le **outils** menu, sélectionnez **Options**.  
  
2.  Développez le **éditeur de texte** , développez **XML**, puis cliquez sur **général**.  
  
3.  Dans le **affichage** zone, cocher **numéros de ligne**.  
  
4.  Cliquez sur **OK**.  
  
 **Exemple de sortie expliquer**  
  
 Le résultat XML de la **expliquer** avec des numéros de ligne est activée la commande est :  
  
```  
1  \<?xml version="1.0" encoding="utf-8"?>  
2  <dsql_query>  
3    <sql>SELECT CAST (AVG(YearlyIncome) AS int) AS AverageIncome,   
4          CAST(AVG(FIS.SalesAmount) AS int) AS AverageSales,   
5          G.StateProvinceName, T.SalesTerritoryGroup  
6      FROM dbo.DimGeography AS G  
7      JOIN dbo.DimSalesTerritory AS T  
8          ON G.SalesTerritoryKey = T.SalesTerritoryKey  
9      JOIN dbo.DimCustomer AS C  
10          ON G.GeographyKey = C.GeographyKey  
11      JOIN dbo.FactInternetSales AS FIS  
12          ON C.CustomerKey = FIS.CustomerKey  
13      WHERE T.SalesTerritoryGroup IN ('North America', 'Pacific')  
14          AND Gender = 'F'  
15      GROUP BY G.StateProvinceName, T.SalesTerritoryGroup  
16      ORDER BY AVG(YearlyIncome) DESC</sql>  
17    <dsql_operations total_cost="0.926237696" total_number_operations="9">  
18      <dsql_operation operation_type="RND_ID">  
19        <identifier>TEMP_ID_16893</identifier>  
20      </dsql_operation>  
21      <dsql_operation operation_type="ON">  
22        <location permanent="false" distribution="AllComputeNodes" />  
23        <sql_operations>  
24          <sql_operation type="statement">CREATE TABLE [tempdb].[dbo].[TEMP_ID_16893] ([CustomerKey] INT NOT NULL, [GeographyKey] INT, [YearlyIncome] MONEY ) WITH(DATA_COMPRESSION=PAGE);</sql_operation>  
25        </sql_operations>  
26      </dsql_operation>  
27      <dsql_operation operation_type="BROADCAST_MOVE">  
28        <operation_cost cost="0.121431552" accumulative_cost="0.121431552" average_rowsize="16" output_rows="31.6228" />  
29        <source_statement>SELECT [T1_1].[CustomerKey] AS [CustomerKey],  
30         [T1_1].[GeographyKey] AS [GeographyKey],  
31         [T1_1].[YearlyIncome] AS [YearlyIncome]  
32  FROM   (SELECT [T2_1].[CustomerKey] AS [CustomerKey],  
33                 [T2_1].[GeographyKey] AS [GeographyKey],  
34                 [T2_1].[YearlyIncome] AS [YearlyIncome]  
35          FROM   [AdventureWorksPDW2012].[dbo].[DimCustomer] AS T2_1  
36          WHERE  ([T2_1].[Gender] = CAST (N'F' COLLATE Latin1_General_100_CI_AS_KS_WS AS NVARCHAR (1)) COLLATE Latin1_General_100_CI_AS_KS_WS)) AS T1_1</source_statement>  
37        <destination_table>[TEMP_ID_16893]</destination_table>  
38      </dsql_operation>  
39      <dsql_operation operation_type="RND_ID">  
40        <identifier>TEMP_ID_16894</identifier>  
41      </dsql_operation>  
42      <dsql_operation operation_type="ON">  
43        <location permanent="false" distribution="AllDistributions" />  
44        <sql_operations>  
45          <sql_operation type="statement">CREATE TABLE [tempdb].[dbo].[TEMP_ID_16894] ([StateProvinceName] NVARCHAR(50) COLLATE Latin1_General_100_CI_AS_KS_WS, [SalesTerritoryGroup] NVARCHAR(50) COLLATE Latin1_General_100_CI_AS_KS_WS NOT NULL, [col] BIGINT, [col1] MONEY NOT NULL, [col2] BIGINT, [col3] MONEY NOT NULL ) WITH(DATA_COMPRESSION=PAGE);</sql_operation>  
46        </sql_operations>  
47      </dsql_operation>  
48      <dsql_operation operation_type="SHUFFLE_MOVE">  
49        <operation_cost cost="0.804806144" accumulative_cost="0.926237696" average_rowsize="232" output_rows="108.406" />  
50        <source_statement>SELECT [T1_1].[StateProvinceName] AS [StateProvinceName],  
51         [T1_1].[SalesTerritoryGroup] AS [SalesTerritoryGroup],  
52         [T1_1].[col2] AS [col],  
53         [T1_1].[col] AS [col1],  
54         [T1_1].[col3] AS [col2],  
55         [T1_1].[col1] AS [col3]  
56  FROM   (SELECT ISNULL([T2_1].[col1], CONVERT (MONEY, 0.00, 0)) AS [col],  
57                 ISNULL([T2_1].[col3], CONVERT (MONEY, 0.00, 0)) AS [col1],  
58                 [T2_1].[StateProvinceName] AS [StateProvinceName],  
59                 [T2_1].[SalesTerritoryGroup] AS [SalesTerritoryGroup],  
60                 [T2_1].[col] AS [col2],  
61                 [T2_1].[col2] AS [col3]  
62          FROM   (SELECT   COUNT_BIG([T3_2].[YearlyIncome]) AS [col],  
63                           SUM([T3_2].[YearlyIncome]) AS [col1],  
64                           COUNT_BIG(CAST ((0) AS INT)) AS [col2],  
65                           SUM([T3_2].[SalesAmount]) AS [col3],  
66                           [T3_2].[StateProvinceName] AS [StateProvinceName],  
67                           [T3_1].[SalesTerritoryGroup] AS [SalesTerritoryGroup]  
68                  FROM     (SELECT [T4_1].[SalesTerritoryKey] AS [SalesTerritoryKey],  
69                                   [T4_1].[SalesTerritoryGroup] AS [SalesTerritoryGroup]  
70                            FROM   [AdventureWorksPDW2012].[dbo].[DimSalesTerritory] AS T4_1  
71                            WHERE  (([T4_1].[SalesTerritoryGroup] = CAST (N'North America' COLLATE Latin1_General_100_CI_AS_KS_WS AS NVARCHAR (13)) COLLATE Latin1_General_100_CI_AS_KS_WS)  
72                                    OR ([T4_1].[SalesTerritoryGroup] = CAST (N'Pacific' COLLATE Latin1_General_100_CI_AS_KS_WS AS NVARCHAR (7)) COLLATE Latin1_General_100_CI_AS_KS_WS))) AS T3_1  
73                           INNER JOIN  
74                           (SELECT [T4_1].[SalesTerritoryKey] AS [SalesTerritoryKey],  
75                                   [T4_2].[YearlyIncome] AS [YearlyIncome],  
76                                   [T4_2].[SalesAmount] AS [SalesAmount],  
77                                   [T4_1].[StateProvinceName] AS [StateProvinceName]  
78                            FROM   [AdventureWorksPDW2012].[dbo].[DimGeography] AS T4_1  
79                                   INNER JOIN  
80                                   (SELECT [T5_2].[GeographyKey] AS [GeographyKey],  
81                                           [T5_2].[YearlyIncome] AS [YearlyIncome],  
82                                           [T5_1].[SalesAmount] AS [SalesAmount]  
83                                    FROM   [AdventureWorksPDW2012].[dbo].[FactInternetSales] AS T5_1  
84                                           INNER JOIN  
85                                           [tempdb].[dbo].[TEMP_ID_16893] AS T5_2  
86                                           ON ([T5_1].[CustomerKey] = [T5_2].[CustomerKey])) AS T4_2  
87                                   ON ([T4_2].[GeographyKey] = [T4_1].[GeographyKey])) AS T3_2  
88                           ON ([T3_1].[SalesTerritoryKey] = [T3_2].[SalesTerritoryKey])  
89                  GROUP BY [T3_2].[StateProvinceName], [T3_1].[SalesTerritoryGroup]) AS T2_1) AS T1_1</source_statement>  
90        <destination_table>[TEMP_ID_16894]</destination_table>  
91        <shuffle_columns>StateProvinceName;</shuffle_columns>  
92      </dsql_operation>  
93      <dsql_operation operation_type="ON">  
94        <location permanent="false" distribution="AllComputeNodes" />  
95        <sql_operations>  
96          <sql_operation type="statement">DROP TABLE [tempdb].[dbo].[TEMP_ID_16893]</sql_operation>  
97        </sql_operations>  
98      </dsql_operation>  
99      <dsql_operation operation_type="RETURN">  
100        <location distribution="AllDistributions" />  
101        <select>SELECT   [T1_1].[col] AS [col],  
102           [T1_1].[col1] AS [col1],  
103           [T1_1].[StateProvinceName] AS [StateProvinceName],  
104           [T1_1].[SalesTerritoryGroup] AS [SalesTerritoryGroup],  
105           [T1_1].[col2] AS [col2]  
106  FROM     (SELECT CONVERT (INT, [T2_1].[col], 0) AS [col],  
107                   CONVERT (INT, [T2_1].[col1], 0) AS [col1],  
108                   [T2_1].[StateProvinceName] AS [StateProvinceName],  
109                   [T2_1].[SalesTerritoryGroup] AS [SalesTerritoryGroup],  
110                   [T2_1].[col] AS [col2]  
111            FROM   (SELECT CASE  
112                            WHEN ([T3_1].[col] = CAST ((0) AS BIGINT)) THEN CAST (NULL AS MONEY)  
113                            ELSE ([T3_1].[col1] / CONVERT (MONEY, [T3_1].[col], 0))  
114                           END AS [col],  
115                           CASE  
116                            WHEN ([T3_1].[col2] = CAST ((0) AS BIGINT)) THEN CAST (NULL AS MONEY)  
117                            ELSE ([T3_1].[col3] / CONVERT (MONEY, [T3_1].[col2], 0))  
118                           END AS [col1],  
119                           [T3_1].[StateProvinceName] AS [StateProvinceName],  
120                           [T3_1].[SalesTerritoryGroup] AS [SalesTerritoryGroup]  
121                    FROM   (SELECT ISNULL([T4_1].[col], CONVERT (BIGINT, 0, 0)) AS [col],  
122                                   ISNULL([T4_1].[col1], CONVERT (MONEY, 0.00, 0)) AS [col1],  
123                                   ISNULL([T4_1].[col2], CONVERT (BIGINT, 0, 0)) AS [col2],  
124                                   ISNULL([T4_1].[col3], CONVERT (MONEY, 0.00, 0)) AS [col3],  
125                                   [T4_1].[StateProvinceName] AS [StateProvinceName],  
126                                   [T4_1].[SalesTerritoryGroup] AS [SalesTerritoryGroup]  
127                            FROM   (SELECT   SUM([T5_1].[col]) AS [col],  
128                                             SUM([T5_1].[col1]) AS [col1],  
129                                             SUM([T5_1].[col2]) AS [col2],  
130                                             SUM([T5_1].[col3]) AS [col3],  
131                                             [T5_1].[StateProvinceName] AS [StateProvinceName],  
132                                             [T5_1].[SalesTerritoryGroup] AS [SalesTerritoryGroup]  
133                                    FROM     [tempdb].[dbo].[TEMP_ID_16894] AS T5_1  
134                                    GROUP BY [T5_1].[StateProvinceName], [T5_1].[SalesTerritoryGroup]) AS T4_1) AS T3_1) AS T2_1) AS T1_1  
135  ORDER BY [T1_1].[col2] DESC</select>  
136      </dsql_operation>  
137      <dsql_operation operation_type="ON">  
138        <location permanent="false" distribution="AllDistributions" />  
139        <sql_operations>  
140          <sql_operation type="statement">DROP TABLE [tempdb].[dbo].[TEMP_ID_16894]</sql_operation>  
141        </sql_operations>  
142      </dsql_operation>  
143    </dsql_operations>  
144  </dsql_query>  
  
```  
  
 **Sens de la sortie d’expliquer**  
  
 Le résultat ci-dessus contient 144 lignes numérotées. Sortie de cette requête peut-être différer légèrement. La liste suivante décrit les sections importantes.  
  
-   Lignes 3 à 16 fournissent une description de la requête est en cours d’analyse.  
  
-   Ligne 17, spécifie que le nombre total d’opérations est 9. Vous pouvez trouver le début de chaque opération, en recherchant les mots **dsql_operation**.  
  
-   La ligne 18 démarre l’opération 1. Lignes 18 et 19 indiquent qu’un **RND_ID** opération permet de créer un numéro d’ID aléatoire qui sera utilisé pour une description de l’objet. L’objet décrit dans la sortie ci-dessus est **TEMP_ID_16893**. Votre numéro de sera différent.  
  
-   La ligne 20 démarre l’opération 2. Lignes 21 à 25 : sur tous les nœuds de calcul, créez une table temporaire nommée **TEMP_ID_16893**.  
  
-   La ligne 26 démarre l’opération 3. Lignes 27 à 37 : déplacer des données **TEMP_ID_16893** à l’aide d’un déplacement de diffusion. La requête envoyée à chaque nœud de calcul est fournie. Ligne 37 spécifie la table de destination est **TEMP_ID_16893**.  
  
-   La ligne 38 démarre l’opération de 4. Lignes 39 à 40 : créer un ID aléatoire pour une table. **TEMP_ID_16894** est le numéro d’ID dans l’exemple ci-dessus. Votre numéro de sera différent.  
  
-   Ligne 41 démarre l’opération 5. Lignes 42 via 46 : tous les nœuds, créer une table temporaire nommée **TEMP_ID_16894**.  
  
-   Ligne 47 démarre l’opération 6. Lignes 48 à 91 : déplacer des données de diverses tables (y compris **TEMP_ID_16893**) à la table **TEMP_ID_16894**, à l’aide d’une réorganisation de l’opération de déplacement. La requête envoyée à chaque nœud de calcul est fournie. Ligne 90 spécifie la table de destination en tant que **TEMP_ID_16894**. Ligne 91 spécifie les colonnes.  
  
-   Ligne 92 démarre l’opération de 7. 93 lignes via 97 : sur tous les nœuds de calcul, de supprimer la table temporaire **TEMP_ID_16893**.  
  
-   Ligne 98 démarre l’opération de 8. 99 lignes via 135 : retourner des résultats au client. Utilise la requête fournie pour obtenir les résultats.  
  
-   Ligne 136 démarre l’opération 9. Lignes 137 à 140 : tous les nœuds, supprimer la table temporaire **TEMP_ID_16894**.  
  
  

