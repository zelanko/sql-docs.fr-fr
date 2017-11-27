---
title: CAST et CONVERT (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 09/08/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CAST_TSQL
- CONVERT_TSQL
- CAST
- CONVERT
dev_langs: TSQL
helpviewer_keywords:
- CAST function
- automatic data type conversion
- varbinary data type
- CONVERT function
- data types [SQL Server], converting
- large value data types
- implicit data type conversions
- image data type, converting
- explicit data type conversions [SQL Server]
- binary [SQL Server], converting
- text data type, converting
- date and time [SQL Server], cast and convert
- truncating conversions
- converting data types [SQL Server], conversion functions
- time zones [SQL Server]
- roundtrip conversions
ms.assetid: a87d0850-c670-4720-9ad5-6f5a22343ea8
caps.latest.revision: "136"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: dd3db7627c4190a51db01082138677bc2b6d40d9
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="cast-and-convert-transact-sql"></a>CAST et CONVERT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Convertit une expression d'un type de données en un autre.  
Par exemple, les exemples suivants transformer le type de données d’entrée, deux autres types de données, avec différents niveaux de précision.
```sql  
SELECT 9.5 AS Original, CAST(9.5 AS int) AS int, 
    CAST(9.5 AS decimal(6,4)) AS decimal;
SELECT 9.5 AS Original, CONVERT(int, 9.5) AS int, 
    CONVERT(decimal(6,4), 9.5) AS decimal;
```  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
|Langue source   |int    |decimal |  
|----|----|----|  
|9.5 |9 |9.5000 |  

> [!TIP]
> Nombreux [exemples](#BKMK_examples) en bas de cette rubrique.  
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
-- Syntax for CAST:  
CAST ( expression AS data_type [ ( length ) ] )  
  
-- Syntax for CONVERT:  
CONVERT ( data_type [ ( length ) ] , expression [ , style ] )  
```  
  
## <a name="arguments"></a>Arguments  
*expression*  
Valide [expression](../../t-sql/language-elements/expressions-transact-sql.md).
  
*data_type*  
Type de données cible. Cela inclut les **xml**, **bigint**, et **sql_variant**. Les types de données alias ne sont pas autorisés.
  
*length*  
Entier facultatif qui spécifie la longueur du type de données cible. La valeur par défaut est 30.
  
*style*  
Expression entière qui spécifie comment la fonction CONVERT doit traduire *expression*. Si le style est NULL, une valeur NULL est retournée. La plage est déterminée par *data_type*. 
  
## <a name="return-types"></a>Types de retour
Retourne *expression* traduit en *data_type*.

## <a name="date-and-time-styles"></a>Styles de date et d'heure  
Lorsque *expression* est un type de données date ou heure *style* peut prendre l’une des valeurs indiquées dans le tableau suivant. Les autres valeurs sont traitées comme étant 0. À partir de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], les seuls styles pris en charge lors de la conversion de date et heure types **datetimeoffset** sont 0 ou 1. Tous les autres styles de conversion retournent l'erreur 9809.
  
>  [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge le format de date dans le style arabe à l'aide de l'algorithme koweitien.
  
|Sans siècle (aa) (<sup>1</sup>)|Avec siècle (aaaa)|Standard|Entrée/sortie (<sup>3</sup>)|  
|---|---|--|---|
|-|**0** ou **100** (<sup>1,</sup><sup>2</sup>)|Valeur par défaut pour datetime et smalldatetime|mois jj aaaa hh:miAM (ou PM)|  
|**1**|**101**|États-Unis|1 = mm/jj/aa<br /> 101 = mm/jj/aaaa|  
|**2**|**102**|ANSI|2 = aa.mm.jj<br /> 102 = aaaa.mm.jj|  
|**3**|**103**|Anglais/Français|3 = jj/mm/aa<br /> 103 = jj/mm/aaaa|  
|**4**|**104**|Allemand|4 = jj.mm.aa<br /> 104 = jj.mm.aaaa|  
|**5**|**105**|Italien|5 = jj-mm-aa<br /> 105 = jj-mm-aaaa|  
|**6**|**106** <sup>(1)</sup>|-|6 = jj mois aa<br /> 106 = jj mois aaaa|  
|**7**|**107** <sup>(1)</sup>|-|7 = Mois jj, aa<br /> 107 = Mois jj, aaaa|  
|**8**|**108**|-|hh:mi:ss|  
|-|**9** ou **109** (<sup>1,</sup><sup>2</sup>)|Valeur par défaut + millièmes de secondes|mois jj aaaa hh:mi:ss:mmmAM (ou PM)|  
|**10**|**110**|États-Unis|10 = mm-jj-aa<br /> 110 = mm-jj-aaaa|  
|**11**|**111**|Japon|11 = aa/mm/jj<br /> 111 = aaaa/mm/jj|  
|**12**|**112**|ISO|12 = aammjj<br /> 112 = aaaammjj|  
|-|**13** ou **113** (<sup>1,</sup><sup>2</sup>)|Valeur par défaut Europe + millièmes de secondes|jj mois aaaa hh:mi:ss:mmm (24h)|  
|**14**|**114**|-|hh:mi:ss:mmm(24h)|  
|-|**20** ou **120** (<sup>2</sup>)|ODBC canonique|aaaa-mm-jj hh:mi:ss (24h)|  
|-|**21** ou **121** (<sup>2</sup>)|Valeur par défaut canonique ODBC (avec millisecondes) pour time, date, datetime2, et datetimeoffset|aaaa-mm-jj hh:mi:ss.mmm (24h)|  
|-|**126** (<sup>4</sup>)|ISO8601|aaaa-mm-jjThh:mi:ss.mmm (sans espace)<br /> Remarque : Lorsque la valeur en millisecondes (mmm) est que 0, la valeur de milliseconde n’est pas affichée. Par exemple, la valeur « 2012-11-07T18:26:20.000 » est affichée comme suit « 2012-11-07T18:26:20 ».|  
|-|**127**(<sup>6, 7</sup>)|ISO8601 avec fuseau horaire Z.|aaaa-mm-jjThh:mi:ss.mmmZ (sans espace)<br /> Remarque : Lorsque la valeur en millisecondes (mmm) est que 0, la valeur en millisecondes n’est pas affichée. Par exemple, la valeur « 2012-11-07T18:26:20.000 » est affichée comme suit « 2012-11-07T18:26:20 ».|  
|-|**130** (<sup>1,</sup><sup>2</sup>)|Calendrier islamique (<sup>5</sup>)|jj mois aaaa hh:mi:ss:mmmAM<br /> Dans ce style, « mois » représente une représentation unicode Hijri à plusieurs jetons pour le nom complet du mois. Cette valeur ne rend pas correctement sur une valeur par défaut installation américain de SSMS.|  
|-|**131** (<sup>2</sup>)|Calendrier islamique (<sup>5</sup>)|jj/mm/yyyy hh:mi:ss:mmmAM|  
  
<sup>1</sup> ces valeurs de style retournent des résultats non déterministes. Inclut tous les styles (aa, c'est-à-dire sans siècle) et un sous-ensemble de styles (aaaa, c'est-à-dire avec siècle).
  
<sup>2</sup> les valeurs par défaut (*style** *0** ou **100**, **9** ou **109**, **13** ou **113**, **20** ou **120**, et **21** ou **121**) Retourne toujours le siècle (aaaa).
  
<sup>3</sup> d’entrée lors de la conversion **datetime**; sortie lorsque vous convertissez des données de type caractère.
  
<sup>4</sup> conçu pour une utilisation XML. Pour la conversion de **datetime** ou **smalldatetime** en données caractères, le format de sortie est tel que décrit dans le tableau précédent.
  
<sup>5</sup> Hijri est un système calendaire possédant plusieurs variations. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise l'algorithme koweitien.
  
> [!IMPORTANT]  
>  Par défaut, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] interprète les années à deux chiffres par rapport à l'année de coupure 2049. Autrement dit, l'année à deux chiffres 49 est interprétée comme étant 2049 et l'année 50 comme étant 1950. De nombreuses applications clientes, comme celles basées sur les objets Automation, utilisent l'année de coupure 2030. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]fournit l’option two digit year cutoff configuration qui modifie l’année de coupure utilisée par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et permet le traitement cohérent des dates. Nous vous recommandons d'utiliser la fonctionnalité d'années exprimées sur quatre chiffres.  
  
<sup>6</sup> prise en charge uniquement lors de la conversion de données caractères **datetime** ou **smalldatetime**. Lorsque les données de caractères qui représente uniquement date ou uniquement les composants d’heure est converti dans le **datetime** ou **smalldatetime** des types de données, le composant d’heure non spécifiée a la valeur 00:00:00.000 et le composant de date non spécifié est défini à 1900-01-01.
  
<sup>7</sup>l’indicateur de fuseau horaire Z, est utilisé pour faciliter le mappage XML **datetime** contenant des informations de fuseau horaire pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **datetime** les valeurs ayant aucun fuseau horaire. Z est l'indicateur du fuseau horaire UTC-0. Les autres fuseaux horaires sont indiqués avec le décalage HH:MM dans la direction + ou -. Par exemple : `2006-12-12T23:45:12-08:00`.
  
Lorsque vous convertissez des données de caractères de **smalldatetime**, les styles comportant les secondes ou les millisecondes affichent des zéros à ces positions. Vous pouvez tronquer les parties de date indésirables lorsque vous convertissez **datetime** ou **smalldatetime** valeurs à l’aide appropriée **char** ou **varchar** longueur de type de données.
  
Lorsque vous convertissez **datetimeoffset** à partir des données de caractères avec un style qui inclut une heure, un décalage de fuseau horaire est ajouté au résultat.
  
## <a name="float-and-real-styles"></a>styles float et real
Lorsque *expression* est **float** ou **réel**, *style* peut prendre l’une des valeurs indiquées dans le tableau suivant. Les autres valeurs sont traitées comme étant 0.
  
|Valeur|Sortie|  
|---|---|
|**0** (valeur par défaut)|6 chiffres maximum. À utiliser pour la notation scientifique si nécessaire.|  
|**1**|Toujours 8 chiffres. À utiliser obligatoirement pour la notation scientifique.|  
|**2**|Toujours 16 chiffres. À utiliser obligatoirement pour la notation scientifique.|  
|**3**|Toujours 17 chiffres. À utiliser pour la conversion sans perte. Avec ce style, chaque float distincte ou la valeur réelle est garantie pour convertir une chaîne de caractères distincts.<br /> **S’applique à :** [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]et à partir de [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)].|  
|**126, 128, 129**|Incluses pour des raisons d'héritage et peuvent être déconseillées dans une version ultérieure.|  
  
## <a name="money-and-smallmoney-styles"></a>styles Money et smallmoney
Lorsque *expression* est **money** ou **smallmoney**, *style* peut prendre l’une des valeurs indiquées dans le tableau suivant. Les autres valeurs sont traitées comme étant 0.
  
|Valeur|Sortie|  
|---|---|
|**0** (valeur par défaut)|Pas de virgule tous les trois chiffres à gauche du point décimal, et deux chiffres à droite de celui-ci. Par exemple, 4235.98.|  
|**1**|Insertion d'une virgule tous les trois chiffres à gauche du point décimal, et deux chiffres à droite de celui-ci. Par exemple 3,510.92.|  
|**2**|Pas de virgule tous les trois chiffres à gauche du point décimal, et quatre chiffres à droite de celui-ci. Par exemple 4235.9819.|  
|**126**|Équivalent du style 2 lors de la conversion en char(n) ou varchar(n)|  
  
## <a name="xml-styles"></a>styles XML
Lorsque *expression* est **xml***, style* peut prendre l’une des valeurs indiquées dans le tableau suivant. Les autres valeurs sont traitées comme étant 0.
  
|Valeur|Sortie|  
|---|---|
|**0** (valeur par défaut)|Utilisez le comportement d'analyse par défaut permettant de supprimer les espaces non significatifs et n'autorisant pas de sous-ensemble DTD interne.<br /> **Remarque :** lorsque vous convertissez la **xml** type de données, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] espaces blancs non significatifs est géré différemment de XML 1.0. Pour plus d’informations, consultez [créer les Instances de XML données](../../relational-databases/xml/create-instances-of-xml-data.md).|  
|**1**|Maintien des espaces non significatifs. Ce paramètre de style définit la valeur par défaut **XML : space** la manière de gérer se comportent comme si **XML : space = « preserve »** a été spécifié à la place.|  
|**2**|Activation du traitement limité de sous-ensembles DTD internes.<br /><br /> Si cette option est activée, le serveur peut utiliser les informations suivantes fournies dans un sous-ensemble DTD interne afin de procéder à des opérations d'analyse autres que celles de validation des données.<br /> -Les valeurs par défaut pour les attributs sont appliqués.<br /> -Références d’entité interne sont résolues et développées.<br /> -Le modèle de contenu DTD est vérification syntaxique.<br /> L’analyseur ignore les sous-ensembles DTD externes. Il n’évalue pas la déclaration XML pour voir si le **autonome** attribut a la valeur **Oui** ou **aucune**, mais analyse cependant l’instance XML comme s’il s’agit d’un document autonome.|  
|**3**|Maintien des espaces non significatifs et activation du traitement limité de sous-ensembles DTD internes.|  
  
## <a name="binary-styles"></a>Styles Binary
Lorsque *expression* est **Binary**, **varbinary (n)**, **char (n)**, ou **varchar (n)**, *style* peut prendre l’une des valeurs indiquées dans le tableau suivant. Les valeurs de style qui ne sont pas répertoriées dans le tableau retournent une erreur.
  
|Valeur|Sortie|  
|---|---|
|**0** (valeur par défaut)|Traduit des caractères ASCII en octets de binaire ou des octets de binaire en caractères ASCII. Chaque caractère ou octet est converti 1:1.<br /> Si le *data_type* est un type binaire, les caractères 0 x sont ajoutés à gauche du résultat.|  
|**1**, **2**|Si le *data_type* est un type binaire, l’expression doit être une expression de caractères. Le *expression* doit être composée d’un nombre pair de chiffres hexadécimaux (0, 1, 2, 3, 4, 5, 6, 7, 8, 9, A, B, C, D, E, F, a, b, c, d, e, f). Si le *style* est défini sur 1 les caractères 0 x doivent être les deux premiers caractères dans l’expression. Si l'expression contient un nombre impair de caractères ou si l'un des caractères n'est pas valide, une erreur est générée.<br /> Si la longueur de l’expression convertie est supérieure à la longueur de la *data_type* le résultat est tronqué à droite.<br /> Longueur fixe *data_types* qui sont plus longs que le résultat converti a ajouter des zéros à droite du résultat.<br /> Si le data_type est un type caractère, l'expression doit être une expression binaire. Chaque caractère binaire est converti en deux caractères hexadécimaux. Si la longueur de l’expression convertie est supérieure à la *data_type* longueur, il est tronqué à droite.<br /> Si le *data_type* est un type de caractère de taille fixe et la longueur du résultat converti est inférieure à la longueur de la *data_type*; des espaces sont ajoutés à droite de l’expression convertie pour conserver un nombre pair de chiffres hexadécimaux.<br /> Les caractères 0 x sera ajouté à gauche du résultat converti pour *style* 1.|  
  
## <a name="implicit-conversions"></a>Conversions implicites
Une conversion implicite est une conversion pour laquelle il n'est pas nécessaire de spécifier les fonctions CAST ou CONVERT. À l'inverse, une conversion explicite requiert que la fonction CAST ou CONVERT soit indiquée. L'illustration ci-dessous reprend toutes les conversions de types de données explicites et implicites autorisées pour les types de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournis par le système. Ceux-ci incluent **xml**, **bigint**, et **sql_variant**. Il n’existe aucune conversion implicite lors de l’attribution de la **sql_variant** type de données, mais il existe une conversion implicite vers **sql_variant**.
  
> [!TIP]  
>  Ce graphique est disponible en tant qu’un fichier PDF téléchargeable dans le [Microsoft Download Center](http://www.microsoft.com/download/details.aspx?id=35834).  
  
![Table de conversion de types de données](../../t-sql/data-types/media/lrdatahd.png "table de conversion de types de données")
  
Lorsque vous effectuez une conversion entre **datetimeoffset** et les types de caractères **char**, **varchar**, **nchar**, et **nvarchar** le fuseau horaire converti partie décalage doit toujours être composée de deux chiffres pour HH et MM, par exemple, -08:00.
  
> [!NOTE]  
>  Étant donné que les données Unicode utilisent toujours un nombre pair d’octets, soyez prudent lorsque vous convertissez **binaire** ou **varbinary** vers ou depuis Unicode prises en charge les types de données. Ainsi, la conversion suivante retourne la valeur hexadécimale 4100 et non pas 41 : `SELECT CAST(CAST(0x41 AS nvarchar) AS varbinary)`.  
  
## <a name="large-value-data-types"></a>Types de données de valeur élevée
Types de données de valeur élevée affichent le même comportement de conversion implicite et explicite que leurs homologues plus petits, plus précisément la **varchar**, **nvarchar** et **varbinary** des types de données. Vous devez cependant prendre en compte les recommandations suivantes :
-   Conversion de **image** à **varbinary (max)** et vice versa est une conversion implicite, et sont donc des conversions entre **texte** et **varchar (max)**, et **ntext** et **nvarchar (max)**.  
-   Types de conversion de données de grande valeur, tels que **varchar (max)**, à un plus petites équivalent et type de données, tel que **varchar**, est une conversion implicite, mais une troncation se produit si la valeur élevée est trop volumineux pour le la longueur spécifiée du type de données plus petit.  
-   Conversion de **varchar**, **nvarchar**, ou **varbinary** à leurs données de valeur élevée correspondantes types s’effectue implicitement.  
-   Conversion à partir de la **sql_variant** type de données pour les types de données de grande valeur est une conversion explicite.  
-   Impossible de convertir les types de données de valeur élevée pour le **sql_variant** type de données.  
  
Pour plus d’informations sur la conversion à partir de la **xml** de type de données, consultez [créer les Instances de XML données](../../relational-databases/xml/create-instances-of-xml-data.md).
  
## <a name="xml-data-type"></a>type de données xml
Lorsque vous explicitement ou implicitement converti le **xml** type de données à une chaîne ou de type de données binaire, le contenu de la **xml** type de données est sérialisé selon un ensemble de règles. Pour plus d’informations sur ces règles, consultez [définir la sérialisation de données XML](../../relational-databases/xml/define-the-serialization-of-xml-data.md). Pour plus d’informations sur la conversion d’autres types de données en le **xml** de type de données, consultez [créer les Instances de XML données](../../relational-databases/xml/create-instances-of-xml-data.md).
  
## <a name="text-and-image-data-types"></a>types de données text et image
Conversion automatique n’est pas pris en charge pour le **texte** et **image** des types de données. Vous pouvez convertir explicitement **texte** données en données caractères, et **image** données **binaire** ou **varbinary**, mais la longueur maximale est de 8 000 octets. Si vous essayez d’une conversion incorrecte, par exemple une expression de caractères contenant des lettres pour un **int**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] renvoie un message d’erreur.
  
## <a name="output-collation"></a>Classement des résultats  
Lorsque l'entrée et la sortie de CAST ou CONVERT sont des chaînes de caractères, l'entrée et la sortie présentent les mêmes classement et étiquette de classement. Si l'entrée n'est pas une chaîne de caractères, la sortie présente le classement par défaut de la base de données et une étiquette de classement de contrainte par défaut. Pour plus d’informations, consultez [priorité de classement &#40; Transact-SQL &#41; ](../../t-sql/statements/collation-precedence-transact-sql.md).
  
Pour attribuer un classement différent à la sortie, appliquez la clause COLLATE à l'expression de résultat de la fonction CAST ou CONVERT. Exemple :
  
`SELECT CAST('abc' AS varchar(5)) COLLATE French_CS_AS`
  
## <a name="truncating-and-rounding-results"></a>Troncation et arrondi des résultats
Lors de la conversion de caractères ou des expressions binaires (**char**, **nchar**, **nvarchar**, **varchar**, **binaire**, ou **varbinary**) à une expression de type de données différent, données peuvent être tronquées, partiellement affichées, ou une erreur est renvoyée, car le résultat est trop court pour être affichée. Les conversions en **char**, **varchar**, **nchar**, **nvarchar**, **binaire**, et **varbinary** sont tronquées, sauf pour les conversions répertoriées dans le tableau suivant.
  
|Du type de données|Au type de données|Résultat|  
|---|---|---|
|**int**, **smallint**, ou **tinyint**|**char**|*|  
||**varchar**|*|  
||**nchar**|E|  
||**nvarchar**|E|  
|**Money**, **smallmoney**, **numérique**, **décimal**, **float**, ou **réel**|**char**|E|  
||**varchar**|E|  
||**nchar**|E|  
||**nvarchar**|E|  
  
\*= Expression résultante trop courte pour l’afficher. E = Erreur retournée car l'expression résultante est trop courte pour être affichée.
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]garantit que seules les conversions aller-retour, conversions de convertir un type de données à partir de son type de données d’origine et vice versa, les mêmes valeurs d’une version à l’autre. L'exemple suivant illustre un tel cas de figure :
  
```sql
DECLARE @myval decimal (5, 2);  
SET @myval = 193.57;  
SELECT CAST(CAST(@myval AS varbinary(20)) AS decimal(10,5));  
-- Or, using CONVERT  
SELECT CONVERT(decimal(10,5), CONVERT(varbinary(20), @myval));  
```  
  
> [!NOTE]  
>  N’essayez pas de construire **binaire** les valeurs et puis de les convertir en un type de données de la catégorie de type de données numérique. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ne garantit pas que le résultat d’une **décimal** ou **numérique** la conversion en type de données **binaire** doit être le même entre les versions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
L'exemple suivant illustre une expression résultante trop petite pour être affichée.
  
```sql
USE AdventureWorks2012;  
GO  
SELECT p.FirstName, p.LastName, SUBSTRING(p.Title, 1, 25) AS Title,
    CAST(e.SickLeaveHours AS char(1)) AS [Sick Leave]  
FROM HumanResources.Employee e JOIN Person.Person p 
    ON e.BusinessEntityID = p.BusinessEntityID  
WHERE NOT e.BusinessEntityID >5;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```   
FirstName   LastName      Title   Sick Leave
---------   ------------- ------- --------`
Ken         Sanchez       NULL   *
Terri       Duffy         NULL   *
Roberto     Tamburello    NULL   *
Rob         Walters       NULL   *
Gail        Erickson      Ms.    *
(5 row(s) affected)  
```
  
Si vous convertissez des données dont le type de données diffère sur l'emplacement de la virgule, la valeur résultante peut parfois être tronquée, parfois être arrondie. Le tableau suivant illustre ce comportement.
  
|De|Pour|Comportement|  
|---|---|---|
|**numeric**|**numeric**|Arrondi|  
|**numeric**|**int**|Tronqué|  
|**numeric**|**money**|Arrondi|  
|**money**|**int**|Arrondi|  
|**money**|**numeric**|Arrondi|  
|**float**|**int**|Tronqué|  
|**float**|**numeric**|Arrondi<br /><br /> Conversion de **float** valeurs qui utilisent la notation scientifique pour **décimal** ou **numérique** est limitée à des valeurs de précision de 17 chiffres uniquement. Toute valeur avec une précision plus élevée que 17 sera arrondie à zéro.|  
|**float**|**datetime**|Arrondi|  
|**datetime**|**int**|Arrondi|  
  
Par exemple, les valeurs 10.6496 et-10.6496 peuvent tronquées ou arrondies pendant la conversion **int** ou **numérique** types :
  
```sql
SELECT  CAST(10.6496 AS int) as trunc1,
         CAST(-10.6496 AS int) as trunc2,
         CAST(10.6496 AS numeric) as round1,
         CAST(-10.6496 AS numeric) as round2;
 ```
Résultats de la requête sont affichés dans le tableau suivant :
 
|trunc1|trunc2|round1|Round2|
|---|---|---|---|
|10|-10|11|-11|
 
Lors des conversions entre divers types de données dans lesquelles les types de données cibles comptent moins de chiffres décimaux que les types de données sources, la valeur obtenue est arrondie. Par exemple, le résultat découlant de la conversion suivante est `$10.3497` :
  
`SELECT CAST(10.3496847 AS money);`
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Retourne un message d’erreur lors de la non numérique **char**, **nchar**, **varchar**, ou **nvarchar** sont converties en données **int**, **float**, **numérique**, ou **décimal**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Renvoie également une erreur lorsqu’une chaîne vide (« ») est converti en **numérique** ou **décimal**.
  
## <a name="certain-datetime-conversions-are-nondeterministic"></a>Certaines conversions de valeurs datetime sont non déterministes
Le tableau ci-dessous répertorie les styles pour lesquels la conversion chaîne-datetime est non déterministe.
  
|||  
|-|-|  
|Tous les styles inférieurs à 100<sup>1</sup>|106|  
|107|109|  
|113|130|  
  
<sup>1</sup> à l’exception des styles 20 et 21
  
## <a name="supplementary-characters-surrogate-pairs"></a>Caractères supplémentaires (paires de substitution)
À compter de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], si vous utilisez des classements de caractères supplémentaires (SC), une opération de conversion à partir de **nchar** ou **nvarchar** à un **nchar** ou **nvarchar** type de longueur inférieure n’est pas tronqués à l’intérieur d’une paire de substitution ; elle sera tronquée avant le caractère supplémentaire. Par exemple, le fragment de code suivant laisse `@x` avec seulement `'ab'`. Il n'y a pas assez d'espace pour conserver le caractère supplémentaire.
  
```sql
DECLARE @x NVARCHAR(10) = 'ab' + NCHAR(0x10000);  
SELECT CAST (@x AS NVARCHAR(3));  
```  
  
Lors de l'utilisation de classements SC, le comportement de `CONVERT`, est analogue à celui de `CAST`.
  
## <a name="compatibility-support"></a>Prise en charge de la compatibilité
Dans les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le style par défaut pour les opérations CAST et CONVERT sur **temps** et **datetime2** des types de données est 121, sauf lorsque le type est utilisé dans une expression de colonne calculée. Pour les colonnes calculées, le style par défaut est 0. Ce comportement influe sur les colonnes calculées lorsqu'elles sont créées, utilisées dans des requêtes impliquant le paramétrage automatique, ou utilisées dans des définitions de contraintes.
  
Niveau de compatibilité est 110 et supérieur, le style par défaut pour les opérations CAST et CONVERT sur **temps** et **datetime2** des types de données est toujours 121. Si votre requête repose sur l'ancien comportement, utilisez un niveau de compatibilité inférieur à 110, ou spécifiez explicitement le style 0 dans la requête affectée.
  
La mise à niveau de la base de données vers le niveau de compatibilité 110 et supérieur ne modifie pas les données utilisateur stockées sur le disque. Vous devez corriger manuellement ces données comme il convient. Par exemple, si vous avez utilisé SELECT INTO pour créer une table à partir d'une source qui contenait une expression de colonne calculée décrite ci-dessus, les données (utilisant le style 0) sont stockées à la place de la définition de colonne calculée. Vous devez mettre à jour manuellement ces données pour qu'elles correspondent au style 121.
  
## <a name="BKMK_examples"></a> Exemples  
  
### <a name="a-using-both-cast-and-convert"></a>A. Utilisation simultanée de CAST et CONVERT  
Chacun des exemples récupère le nom de chaque produit possédant un `3` au premier chiffre de son prix et convertit son champ `ListPrice` en type `int`.
  
```sql
-- Use CAST  
USE AdventureWorks2012;  
GO  
SELECT SUBSTRING(Name, 1, 30) AS ProductName, ListPrice  
FROM Production.Product  
WHERE CAST(ListPrice AS int) LIKE '3%';  
GO  
  
-- Use CONVERT.  
USE AdventureWorks2012;  
GO  
SELECT SUBSTRING(Name, 1, 30) AS ProductName, ListPrice  
FROM Production.Product  
WHERE CONVERT(int, ListPrice) LIKE '3%';  
GO  
```  
  
### <a name="b-using-cast-with-arithmetic-operators"></a>B. Utilisation de CAST avec des opérateurs arithmétiques  
L'exemple suivant illustre le calcul effectué sur une colonne unique (intitulée `Computed`) où le total des ventes de l'année en cours (`SalesYTD`) est divisé par le pourcentage de commission (dont la valeur se trouve dans `CommissionPCT`). Le résultat est converti en type de données `int` après avoir été arrondi au chiffre entier le plus proche.
  
```sql
USE AdventureWorks2012;  
GO  
SELECT CAST(ROUND(SalesYTD/CommissionPCT, 0) AS int) AS Computed  
FROM Sales.SalesPerson   
WHERE CommissionPCT != 0;  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
```  
Computed
------
379753754
346698349
257144242
176493899
281101272
0  
301872549
212623750
298948202
250784119
239246890
101664220
124511336
97688107
(14 row(s) affected)  
```  
  
### <a name="c-using-cast-to-concatenate"></a>C. Utilisation de CAST pour la concaténation d'expressions  
L’exemple suivant concatène les expressions à l’aide de CAST. Utilise AdventureWorksDW.
  
```sql
SELECT 'The list price is ' + CAST(ListPrice AS varchar(12)) AS ListPrice  
FROM dbo.DimProduct  
WHERE ListPrice BETWEEN 350.00 AND 400.00;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
ListPrice
------------------------
The list price is 357.06
The list price is 364.09
The list price is 364.09
The list price is 364.09
The list price is 364.09  
```  
  
### <a name="d-using-cast-to-produce-more-readable-text"></a>D. Utilisation de CAST pour faciliter la lecture des résultats  
L’exemple suivant utilise le CAST dans la liste de sélection pour convertir le `Name` colonne à un **char (10)** colonne. Utilise AdventureWorksDW.
  
```sql
SELECT DISTINCT CAST(EnglishProductName AS char(10)) AS Name, ListPrice  
FROM dbo.DimProduct  
WHERE EnglishProductName LIKE 'Long-Sleeve Logo Jersey, M';  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
Name        UnitPrice
----------  ---------
Long-Sleev  31.2437
Long-Sleev  32.4935
Long-Sleev  49.99  
```  
  
### <a name="e-using-cast-with-the-like-clause"></a>E. Utilisation de CAST avec la clause LIKE  
L'exemple suivant convertit la colonne `money` de type `SalesYTD` en colonne de type `int`, puis en colonne de type `char(20)` de façon à pouvoir l'utiliser avec la clause `LIKE`.
  
```sql
USE AdventureWorks2012;  
GO  
SELECT p.FirstName, p.LastName, s.SalesYTD, s.BusinessEntityID  
FROM Person.Person AS p   
JOIN Sales.SalesPerson AS s   
    ON p.BusinessEntityID = s.BusinessEntityID  
WHERE CAST(CAST(s.SalesYTD AS int) AS char(20)) LIKE '2%';  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
FirstName        LastName            SalesYTD         SalesPersonID
---------------- ------------------- ---------------- -------------
Tsvi             Reiter              2811012.7151      279
Syed             Abbas               219088.8836       288
Rachel           Valdez              2241204.0424      289
(3 row(s) affected)  
```
  
### <a name="f-using-convert-or-cast-with-typed-xml"></a>F. Utilisation de CONVERT ou de CAST avec des données au format XML typé  
Voici plusieurs exemples qui illustrent l’utilisation de CONVERT pour convertir en XML typé à l’aide de la [Type de données XML et les colonnes &#40; SQL Server &#41; ](../../relational-databases/xml/xml-data-type-and-columns-sql-server.md).
  
Cet exemple convertit une chaîne incluant des espaces, du texte et des balises en XML typé, puis supprime tous les espaces non significatifs (correspondant aux espaces délimitant les nœuds) :
  
```sql
CONVERT(XML, '<root><child/></root>')  
```  
  
Cet exemple convertit une chaîne similaire incluant des espaces, du texte et des balises en XML typé, mais conserve les espaces non significatifs (correspondant aux espaces délimitant les nœuds) :
  
```sql
CONVERT(XML, '<root>          <child/>         </root>', 1)  
```  
  
Enfin, cet exemple convertit une chaîne similaire incluant des espaces, du texte et des balises en XML typé :
  
```sql
CAST('<Name><FName>Carol</FName><LName>Elliot</LName></Name>'  AS XML)  
```  
  
Pour plus d’exemples, consultez [créer les Instances de XML données](../../relational-databases/xml/create-instances-of-xml-data.md).
  
### <a name="g-using-cast-and-convert-with-datetime-data"></a>G. Utilisation de CAST et de CONVERT avec des données de type datetime  
L'exemple suivant affiche la date et l'heure actuelles, utilise `CAST` pour convertir la date et l'heure actuelles en type de données caractères, puis utilise `CONVERT` pour afficher la date et l'heure au format `ISO 8901`.
  
```sql
SELECT   
   GETDATE() AS UnconvertedDateTime,  
   CAST(GETDATE() AS nvarchar(30)) AS UsingCast,  
   CONVERT(nvarchar(30), GETDATE(), 126) AS UsingConvertTo_ISO8601  ;  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
UnconvertedDateTime     UsingCast              UsingConvertTo_ISO8601
----------------------- ---------------------- ------------------------------
2006-04-18 09:58:04.570 Apr 18 2006  9:58AM    2006-04-18T09:58:04.570
(1 row(s) affected)  
```
  
L'exemple suivant est plus ou moins l'inverse de l'exemple précédent. Cet exemple affiche la date et l'heure sous forme de données caractères, utilise `CAST` pour convertir les données caractères en type de données `datetime`, puis utilise `CONVERT` pour convertir le type de données caractères en type de données `datetime`.
  
```sql
SELECT   
   '2006-04-25T15:50:59.997' AS UnconvertedText,  
   CAST('2006-04-25T15:50:59.997' AS datetime) AS UsingCast,  
   CONVERT(datetime, '2006-04-25T15:50:59.997', 126) AS UsingConvertFrom_ISO8601 ;  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
UnconvertedText         UsingCast               UsingConvertFrom_ISO8601
----------------------- ----------------------- ------------------------
2006-04-25T15:50:59.997 2006-04-25 15:50:59.997 2006-04-25 15:50:59.997
(1 row(s) affected)  
```
  
### <a name="h-using-convert-with-binary-and-character-data"></a>H. Utilisation de CONVERT avec des données binaires et caractères  
Les exemples suivants montrent les résultats de la conversion de données binaires et caractères en utilisant des styles différents.
  
```sql
--Convert the binary value 0x4E616d65 to a character value.  
SELECT CONVERT(char(8), 0x4E616d65, 0) AS [Style 0, binary to character];  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
Style 0, binary to character
----------------------------
Name  
(1 row(s) affected)  
```
 
L’exemple suivant montre comment Style 1 pour forcer le résultat est tronqué. La troncation est due à inclure les caractères 0 x dans le résultat.  
```sql  
SELECT CONVERT(char(8), 0x4E616d65, 1) AS [Style 1, binary to character];  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
Style 1, binary to character
------------------------------
0x4E616D
(1 row(s) affected)  
```  
 
L’exemple suivant montre que 2 de Style ne tronque pas le résultat étant donné que les caractères 0 x ne sont pas inclus dans le résultat.  
```sql  
SELECT CONVERT(char(8), 0x4E616d65, 2) AS [Style 2, binary to character];  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
Style 2, binary to character
------------------------------
4E616D65
(1 row(s) affected)  
```
  
Convertir la valeur de caractère « Name » en une valeur binaire.  
```sql
SELECT CONVERT(binary(8), 'Name', 0) AS [Style 0, character to binary];  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
Style 0, character to binary
----------------------------
0x4E616D6500000000
(1 row(s) affected)  
```
  
```sql
SELECT CONVERT(binary(4), '0x4E616D65', 1) AS [Style 1, character to binary];  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
Style 1, character to binary
---------------------------- 
0x4E616D65
(1 row(s) affected)  
```  

```sql
SELECT CONVERT(binary(4), '4E616D65', 2) AS [Style 2, character to binary];  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
Style 2, character to binary  
----------------------------------  
0x4E616D65
(1 row(s) affected)  
```  
  
### <a name="i-converting-date-and-time-data-types"></a>I. Convertit les types de données de date et d'heure  
L'exemple suivant décrit la conversion des types de données date, time, et datetime.
  
```sql
DECLARE @d1 date, @t1 time, @dt1 datetime;  
SET @d1 = GETDATE();  
SET @t1 = GETDATE();  
SET @dt1 = GETDATE();  
SET @d1 = GETDATE();  
-- When converting date to datetime the minutes portion becomes zero.  
SELECT @d1 AS [date], CAST (@d1 AS datetime) AS [date as datetime];  
-- When converting time to datetime the date portion becomes zero   
-- which converts to January 1, 1900.  
SELECT @t1 AS [time], CAST (@t1 AS datetime) AS [time as datetime];  
-- When converting datetime to date or time non-applicable portion is dropped.  
SELECT @dt1 AS [datetime], CAST (@dt1 AS date) AS [datetime as date], 
   CAST (@dt1 AS time) AS [datetime as time];  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="j-using-cast-and-convert"></a>J. À l’aide de CAST et CONVERT  
Cet exemple récupère le nom du produit pour les produits qui ont un `3` dans le premier chiffre de leurs prix et le convertit leur `ListPrice` à **int**. Utilise AdventureWorksDW.
  
```sql
SELECT EnglishProductName AS ProductName, ListPrice  
FROM dbo.DimProduct  
WHERE CAST(ListPrice AS int) LIKE '3%';  
```  
  
Cet exemple montre la même requête, à l’aide de la conversion au lieu de CAST. Utilise AdventureWorksDW.
  
```sql
SELECT EnglishProductName AS ProductName, ListPrice  
FROM dbo.DimProduct  
WHERE CONVERT(int, ListPrice) LIKE '3%';  
```  
  
### <a name="k-using-cast-with-arithmetic-operators"></a>K. Utilisation de CAST avec des opérateurs arithmétiques  
L’exemple suivant calcule un calcul de colonne unique en divisant le prix unitaire du produit (`UnitPrice`) par le pourcentage de remise (`UnitPriceDiscountPct`). Le résultat est converti en type de données `int` après avoir été arrondi au chiffre entier le plus proche. Utilise AdventureWorksDW.
  
```sql
SELECT ProductKey, UnitPrice,UnitPriceDiscountPct,  
       CAST(ROUND (UnitPrice*UnitPriceDiscountPct,0) AS int) AS DiscountPrice  
FROM dbo.FactResellerSales  
WHERE SalesOrderNumber = 'SO47355'   
      AND UnitPriceDiscountPct > .02;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
ProductKey  UnitPrice  UnitPriceDiscountPct  DiscountPrice
----------  ---------  --------------------  -------------
323         430.6445   0.05                  22
213         18.5043    0.05                  1
456         37.4950    0.10                  4
456         37.4950    0.10                  4
216         18.5043    0.05                  1  
```  
  
### <a name="l-using-cast-with-the-like-clause"></a>L. Utilisation de CAST avec la clause LIKE  
L’exemple suivant convertit le **money** colonne `ListPrice` à un **int** type puis un **char (20)** type afin qu’il peut être utilisé avec la clause LIKE. Utilise AdventureWorksDW.
  
```sql
SELECT EnglishProductName AS Name, ListPrice  
FROM dbo.DimProduct  
WHERE CAST(CAST(ListPrice AS int) AS char(20)) LIKE '2%';  
```  
  
### <a name="m-using-cast-and-convert-with-datetime-data"></a>M. Utilisation de CAST et de CONVERT avec des données de type datetime  
L’exemple suivant affiche la date et heure actuelles, utilise CAST pour modifier la date et l’heure à un type de données caractère, et puis utilise CONVERT affiche la date et l’heure au format ISO 8601. Utilise AdventureWorksDW.
  
```sql
SELECT TOP(1)  
   SYSDATETIME() AS UnconvertedDateTime,  
   CAST(SYSDATETIME() AS nvarchar(30)) AS UsingCast,  
   CONVERT(nvarchar(30), SYSDATETIME(), 126) AS UsingConvertTo_ISO8601  
FROM dbo.DimCustomer;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
UnconvertedDateTime     UsingCast                     UsingConvertTo_ISO8601  
---------------------   ---------------------------   ---------------------------  
07/20/2010 1:44:31 PM   2010-07-20 13:44:31.5879025   2010-07-20T13:44:31.5879025  
```  
  
L'exemple suivant est plus ou moins l'inverse de l'exemple précédent. L’exemple affiche une date et heure sous forme de caractères, utilise un CAST pour convertir les données de caractères à la **datetime** type de données, puis utilise CONVERT pour convertir les données de caractères à la **datetime** type de données. Utilise AdventureWorksDW.
  
```sql
SELECT TOP(1)   
   '2010-07-25T13:50:38.544' AS UnconvertedText,  
CAST('2010-07-25T13:50:38.544' AS datetime) AS UsingCast,  
   CONVERT(datetime, '2010-07-25T13:50:38.544', 126) AS UsingConvertFrom_ISO8601  
FROM dbo.DimCustomer;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
UnconvertedText         UsingCast               UsingConvertFrom_ISO8601
----------------------- ----------------------- ------------------------
2010-07-25T13:50:38.544 07/25/2010 1:50:38 PM   07/25/2010 1:50:38 PM  
```  
  
## <a name="see-also"></a>Voir aussi
[Conversion de Type de données &#40; moteur de base de données &#41;](../../t-sql/data-types/data-type-conversion-database-engine.md)  
[SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)  
[Fonctions système &#40; Transact-SQL &#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)  
[Rédiger des instructions Transact-SQL internationales](../../relational-databases/collations/write-international-transact-sql-statements.md)
  
