---
title: "Utilisation des types de donn&#233;es R | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "01/31/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5df99e1c-a89a-42c1-9d68-ffe8d9577c94
caps.latest.revision: 16
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 12
---
# Utilisation des types de donn&#233;es R
  Alors que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge plusieurs types de douzaines données, R a un nombre limité de types de données scalaires (numériques, entier, caractère complexe, logique, de date/heure et raw). Par conséquent, lorsque vous utilisez des données de  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans des scripts R, plusieurs choses peuvent se produire :  
  
-   Les données sont implicitement converties en un type de données compatible.  
  
-   Les données ne peuvent pas être implicitement converties et une erreur est retournée.  
  
 En général, en cas de doute sur la manière dont un type ou une structure de données spécifique est utilisé dans R, vous pouvez faire appel à la fonction  `str()` pour obtenir la structure interne et le type de l’objet R. Le résultat de la fonction s’affiche dans la console R et est également disponible dans les résultats de requête, dans l’onglet **Messages** de [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
 Si un rôle particulier [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type de données n’est pas pris en charge par R, mais vous devez utiliser les colonnes de données dans le script R, nous vous recommandons d’utiliser le [CAST et CONVERT & #40 ; Transact-SQL & #41 ;](../../t-sql/functions/cast-and-convert-transact-sql.md) fonctions pour garantir que les données des conversions de type sont exécutées comme prévu avant d’utiliser les données dans votre script R.  
  
 Pour plus d’informations sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] des types de données, consultez la page [Types de données & #40 ; Transact-SQL & #41 ;](../../t-sql/data-types/data-types-transact-sql.md)  
  
## Conversion de types de données entre R et SQL Server  
 Le tableau suivant présente les modifications de types de données et de valeurs lorsque des données de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont utilisées dans un script R et retournées à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|||||  
|-|-|-|-|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type|Classe R|Type dans **RESULT SET**|Commentaires|  
|**smalldatetime**|`POSIXct`|**datetime**|Représenté au format GMT|  
|**smallmoney**|`numeric`|**float**||  
|**datetime**|`POSIXct`|**datetime**|Représenté au format GMT|  
|**money**|`numeric`|**float**||  
|**uniqueidentifier**|`character`|**varchar(max)**||  
|**numeric**|`numeric`|**float**||  
|**Decimal(p,s)**|`numeric`|**float**||  
|**date**|`POSIXct`|**datetime**|Représenté au format GMT|  
|**tinyint**|`integer`|**int**||  
|**bit**|`logical`|**bit**||  
|**smallint**|`integer`|**int**||  
|**int**|`integer`|**int**||  
|**float**|`numeric`|**float**||  
|**real**|`numeric`|**float**||  
|**bigint**|`numeric`|**float**||  
|**binary(n)**<br /><br /> n <= 8000|`raw`|**varbinary(max)**|Uniquement autorisé en tant que paramètre d’entrée et sortie|  
|**char(n)**<br /><br /> n <= 8000|`character`|**varchar(max)**||  
|**varbinary (n)**<br /><br /> n <= 8000|`raw`|**varbinary(max)**|Uniquement autorisé en tant que paramètre d’entrée et sortie|  
|**varchar (n)**<br /><br /> n <= 8000|`character`|**varchar(max)**||  
|**varbinary(max)**|`raw`|**varbinary(max)**|Uniquement autorisé en tant que paramètre d’entrée et sortie|  
  
## Exemples de conversion de types de données  
 La requête suivante extrait une série de valeurs d’une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table et utilise la procédure stockée  [sp_execute_external_script & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) pour sortir les valeurs à l’aide de l’exécution de R.  
  
```  
CREATE TABLE MyTable (    
 c1 int,    
 c2 varchar(10),    
 c3 uniqueidentifier    
);    
go    
INSERT MyTable VALUES(1, 'Hello', newid());    
INSERT MyTable VALUES(-11, 'world', newid());    
SELECT * FROM MyTable;    
  
EXECUTE sp_execute_external_script    
 @language = N'R'    
 , @script = N'    
inputDataSet["cR"] <- c(4, 2)    
str(inputDataSet)    
outputDataSet <- inputDataSet'    
 , @input_data_1 = N'SELECT c1, c2, c3 FROM MyTable'    
 , @input_data_1_name = N'inputDataSet'    
 , @output_data_1_name = N'outputDataSet'    
 WITH RESULT SETS((C1 int, C2 varchar(max), C3 varchar(max), C4 float));  
```  
  
 **Résultats**  
  
||||||  
|-|-|-|-|-|  
||C1|C2|C3|C4|  
|1|1|Hello|6e225611-4b58-4995-a0a5-554d19012ef1|4|  
|1|-11|world|6732ea46-2d5d-430b-8ao1-86e7f3351c3e|2|  
  
 Notez l’utilisation de la fonction `str` dans R pour obtenir le schéma des données de sortie. Cette fonction retourne les informations suivantes :  
  
```  
'data.frame':2 obs. of  4 variables:   
 $ c1: int  1 -11   
 $ c2: Factor w/ 2 levels "Hello","world": 1 2   
 $ c3: Factor w/ 2 levels "6732EA46-2D5D-430B-8A01-86E7F3351C3E",..: 2 1   
 $ cR: num  4 2  
```  
  
 Vous pouvez voir que les conversions de types de données suivantes ont été effectuées implicitement dans le cadre de cette requête :  
  
-   **Colonne C1**. La colonne est représentée en tant que **int** dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], `integer` dans R, et **int** dans le résultat de sortie définie.  
  
     Aucune conversion de type n’a été effectuée.  
  
-   **Colonne C2**. La colonne est représentée en tant que **varchar (10)** dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], `factor` dans R, et **varchar (max)** dans la sortie.  
  
     Notez comment la sortie change ; toute chaîne de R (un facteur ou une chaîne normale) est représenté comme **varchar (max)**, quel que soit la longueur des chaînes.  
  
-   **Colonne C3**.  La colonne est représentée en tant que **uniqueidentifier** dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], `character` dans R, et **varchar (max)** dans la sortie.  
  
     Remarque la conversion de type de données qui se produit. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge la **uniqueidentifier** mais n’est pas le cas de R ; par conséquent, les identificateurs sont représentées sous forme de chaînes.  
  
-   **Colonne C4**. La colonne contient des valeurs générées par le script R et non présentes dans les données d’origine.  
 
 ## Voir aussi
 [Fonctionnalités et tâches de SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services-features-and-tasks.md)
  
  