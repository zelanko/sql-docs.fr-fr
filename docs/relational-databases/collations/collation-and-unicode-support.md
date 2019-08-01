---
title: Prise en charge d’Unicode et du classement | Microsoft Docs
ms.custom: ''
ms.date: 06/26/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- binary collations [SQL Server]
- expression-level collations [SQL Server]
- Windows collations [SQL Server]
- globalization [SQL Server], about globalization
- supplementary character support
- code pages [SQL Server], about code pages
- collations [SQL Server], about collations
- Unicode [SQL Server], collations
- database-level collations [SQL Server]
- reading order
- column-level collations
- locales [SQL Server], about locales
- locales [SQL Server]
- code pages [SQL Server]
- SQL Server collations
- UTF-8
- UTF-16
- server-level collations [SQL Server]
ms.assetid: 92d34f48-fa2b-47c5-89d3-a4c39b0f39eb
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: af749bdb7050d9e71fdfe698fe295255a4603add
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68118491"
---
# <a name="collation-and-unicode-support"></a>Prise en charge d’Unicode et du classement
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Les classements dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournissent les règles de tri et les propriétés de respect de la casse et des accents pour vos données. Les classements utilisés avec les types de données character, tels que **char** et **varchar** , déterminent la page de codes et les caractères correspondants qui peuvent être représentés pour ce type de données. Qu’il s’agisse d’installer une nouvelle instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], de restaurer une sauvegarde de base de données ou de connecter un serveur à des bases de données clientes, vous devez bien comprendre les exigences en termes de paramètres régionaux, d’ordre de tri et de respect de la casse et des accents des données que vous utilisez. Pour répertorier les classements disponibles sur votre instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [sys.fn_helpcollations &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-helpcollations-transact-sql.md).    
    
Quand vous sélectionnez un classement pour votre serveur, base de données, colonne ou expression, vous assignez certaines caractéristiques à vos données qui affectent les résultats de nombreuses opérations dans la base de données. Par exemple, quand vous construisez une requête avec `ORDER BY`, l’ordre de tri de votre jeu de résultats peut dépendre du classement qui est appliqué à la base de données ou qui est stipulé dans une clause `COLLATE` au niveau de l’expression de la requête.    
    
Pour exploiter au mieux la prise en charge des classements dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous devez comprendre les termes qui sont définis dans cette rubrique et la relation qu'ils entretiennent avec les caractéristiques de vos données.    
    
##  <a name="Terms"></a> Termes de classement    
    
-   [Classement](#Collation_Defn)    
    
-   [Paramètres régionaux](#Locale_Defn)    
    
-   [Page de codes](#Code_Page_Defn)    
    
-   [Ordre de tri](#Sort_Order_Defn)    
    
###  <a name="Collation_Defn"></a> Classement    
Un classement désigne les modèles binaires qui représentent chaque caractère dans un jeu de données. Les classements déterminent également les règles de tri et de comparaison des données. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge le stockage d’objets ayant des classements différents dans une même base de données. Pour les colonnes non-Unicode, le paramètre de classement spécifie la page de codes pour les données et les caractères qui peuvent être représentés. Les données déplacées entre des colonnes non-Unicode doivent être converties de la page de codes source vers la page de codes de destination.    
    
Le résultat d'une instruction[!INCLUDE[tsql](../../includes/tsql-md.md)] peut varier lorsque cette dernière est exécutée dans un contexte réunissant plusieurs bases de données dont chacune a un paramètre de classement différent. Dans la mesure du possible, choisissez un classement normalisé pour votre organisation. De cette manière, vous n'avez pas à spécifier explicitement le classement dans chaque caractère ou expression Unicode. Si vous devez utiliser des objets qui ont des paramètres de classement et de page de codes différents, codez vos requêtes conformément aux règles de priorité des classements. Pour plus d’informations, consultez [Priorité de classement (Transact-SQL)](../../t-sql/statements/collation-precedence-transact-sql.md).    
    
Les options associées à un classement sont le respect de la casse, le respect des accents, le respect du jeu de caractères Kana, le respect de la largeur et le respect du sélecteur de variante. [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] introduit une option supplémentaire pour l’encodage [UTF-8](https://www.wikipedia.org/wiki/UTF-8). Pour spécifier ces options, vous devez les ajouter au nom du classement. Par exemple, le classement `Japanese_Bushu_Kakusu_100_CS_AS_KS_WS_UTF8` respecte la casse, les accents, le jeu de caractères Kana et la largeur, et il est encodé en UTF-8. Autre exemple : le classement `Japanese_Bushu_Kakusu_140_CI_AI_KS_WS_VSS` ne respecte pas la casse, ne respecte pas les accents, respecte le jeu de caractères Kana, respecte la largeur, respecte le sélecteur de variante et utilise un encodage non-Unicode. Le tableau suivant décrit le comportement associé à ces différentes options.    
    
|Option|Description|    
|------------|-----------------|    
|Respecter la casse (\_CS)|Fait la distinction entre les majuscules et les minuscules. Si cette option est activée, les minuscules sont triées avant leurs équivalents majuscules. Si cette option n’est pas sélectionnée, le classement ne respecte pas la casse. Dans ce cas, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] considère que les versions en majuscules et en minuscules des lettres sont identiques dans les opérations de tri. Pour sélectionner explicitement le non-respect de la casse, spécifiez \_CI.|    
|Respecter les accents (\_AS)|Fait la distinction entre les caractères accentués et non accentués. Par exemple, « a » n'est pas équivalent à « ấ ». Si cette option n’est pas sélectionnée, le classement ne respecte pas les accents. Dans ce cas, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] considère que la version accentuée et la version non accentuée d’une même lettre sont identiques dans les opérations de tri. Pour sélectionner explicitement le non-respect des accents, spécifiez \_AI.|    
|Respecter le jeu de caractères Kana (\_KS)|Fait la distinction entre les deux types de caractères japonais Kana : Hiragana et Katakana. Si cette option n'est pas sélectionnée, le classement ne respecte pas les caractères Kana. Dans ce cas, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] considère que les caractères Hiragana et Katakana sont identiques dans les opérations de tri. L'omission de cette option est le seul moyen de spécifier le non-respect du jeu de caractères Kana.|    
|Respecter la largeur (\_WS)|Fait la différence entre les caractères pleine largeur et demi-largeur. Si cette option n’est pas sélectionnée, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] considère que la représentation pleine largeur et demi-largeur d’un même caractère sont identiques dans les opérations de tri. L'omission de cette option est le seul moyen de spécifier le non-respect de la largeur.|    
|Respecter le sélecteur de variante (\_VSS) | Fait la distinction entre différents sélecteurs de variante idéographiques dans les classements japonais Japanese_Bushu_Kakusu_140 et Japanese_XJIS_140 introduits dans [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)]. Une séquence de variantes se compose d’un caractère de base et d’un sélecteur de variante supplémentaire. Si l’option \_VSS n’est pas sélectionnée, le classement ne respecte pas le sélecteur de variante, qui n’est pas non plus pris en compte dans la comparaison. Autrement dit, SQL Server considère comme identiques (à des fins de tri) les caractères basés sur le même caractère de base avec différents sélecteurs de variante. Voir aussi  [Unicode Ideographic Variation Database (Base de données de variantes idéographiques Unicode)](https://www.unicode.org/reports/tr37/). <br/><br/> Les classements qui respectent le sélecteur de variante (\_VSS) ne sont pas pris en charge par les index de recherche en texte intégral, qui ne gèrent que les options Respecter les accents (\_AS), Respecter le jeu de caractères Kana (\_KS) et Respecter la largeur (\_WS). Les moteurs XML et CLR de SQL Server n’acceptent pas les sélecteurs de variante (\_VSS).
|UTF-8 (\_UTF8)|Permet le stockage des données encodées en UTF-8 dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si cette option n’est pas sélectionnée, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise le format d’encodage non-Unicode par défaut pour les types de données applicables.| 
    
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge les ensembles de classement suivants :    
    
#### <a name="windows-collations"></a>classements Windows    
Les classements Windows définissent les règles de stockage des données de type caractère selon les paramètres régionaux système Windows associés. Pour un classement Windows, la comparaison de données non-Unicode est implémentée via le même algorithme que les données Unicode. Les règles de classement Windows de base spécifient l'alphabet ou la langue utilisée pour le tri du dictionnaire, et la page de codes utilisée pour stocker les données de type caractère non-Unicode. Les tris Unicode et non-Unicode sont compatibles avec les comparaisons de chaînes dans une version particulière de Windows. Les types de données sont ainsi cohérents dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ce qui permet aux développeurs de trier les chaînes dans leurs applications en appliquant les mêmes règles que celles utilisées par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations, consultez [Nom de classement Windows &#40;Transact-SQL&#41;](../../t-sql/statements/windows-collation-name-transact-sql.md).    
    
#### <a name="binary-collations"></a>Classements binaires    
Les classements binaires trient les données en fonction de la séquence des valeurs codées qui sont définies par les paramètres régionaux et le type de données. Ils respectent la casse. Un classement binaire dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] définit les paramètres régionaux et la page de codes ANSI à utiliser. Cela applique un ordre de tri binaire. Parce qu'ils sont relativement simples, les classements binaires aident à améliorer les performances de l'application. Pour les types de données non-Unicode, les comparaisons de données sont basées sur les points de code qui sont définis dans la page de codes ANSI. Pour les données de type Unicode, les comparaisons de données se basent sur les points de code Unicode. Pour le classement binaire des types de données Unicode, les paramètres régionaux (la langue) ne sont pas pris en compte dans les tris de données. Par exemple, Latin_1_General_BIN et Japanese_BIN produisent des résultats de tri identiques quand ils sont utilisés avec des données Unicode.    
    
Il existe deux types de classements binaires dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les anciens classements **BIN** et les nouveaux classements **BIN2** . Dans un classement **BIN2** tous les caractères sont triés en fonction de leurs points de code. Dans un classement **BIN** seul le premier caractère est trié selon le point de code, et les autres caractères sont triés en fonction de leurs valeurs d'octet. (En raison de l'architecture little endian de la plateforme Intel, les caractères de code Unicode sont toujours triés inversés par octet.)    
    
#### <a name="sql-server-collations"></a>classements SQL Server    
Les classements de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SQL_\*) offrent la compatibilité des ordres de tri avec les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les règles de tri du dictionnaire pour les données non-Unicode ne sont pas compatibles avec les routines de tri fournies par les systèmes d'exploitation Windows. Toutefois, le tri de données Unicode est compatible avec une version particulière de règles de tri Windows. Comme les classements [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilisent des règles de comparaison différentes pour les données Unicode et non-Unicode, vous pouvez obtenir des résultats différents pour des comparaisons des mêmes données, selon le type de données sous-jacent. Pour plus d’informations, consultez [Nom du classement SQL Server &#40;Transact-SQL&#41;](../../t-sql/statements/sql-server-collation-name-transact-sql.md).    
    
> [!NOTE]    
> Quand vous mettez à niveau une instance en anglais de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez spécifier les classements [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SQL_\*) pour la compatibilité avec les instances [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] existantes. Le classement par défaut d'une instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] étant défini au cours de la procédure d'installation, assurez-vous de spécifier soigneusement les paramètres de classement dans les cas suivants :    
>     
> -   Votre code d'application dépend du comportement des classements [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] précédents.    
> -   Vous devez stocker des données de caractères de plusieurs langues.    
    
 Les paramétrages des classements sont pris en charge aux niveaux suivants d'une instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:    
    
#### <a name="server-level-collations"></a>Classements au niveau du serveur   
Le classement du serveur par défaut est défini durant l'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , et devient également le classement par défaut des bases de données système et de toutes les bases de données utilisateur. Notez que les classements Unicode ne peuvent pas être sélectionnés pendant la procédure d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , car ils ne sont pas pris en charge en tant que classements au niveau du serveur.    
    
Lorsqu'un classement a été affecté au serveur, vous ne pouvez pas le modifier le classement, à moins d'exporter la totalité des objets et des données de la base de données, de reconstruire la base de données **master** et d'importer la totalité des objets et des données de la base de données. Au lieu de modifier le classement par défaut d'une instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez spécifier le classement désiré au moment de la création d'une nouvelle base de données ou colonne de base de données.    
    
#### <a name="database-level-collations"></a>Classements au niveau de la base de données    
Lorsque vous créez ou modifiez une base de données, vous pouvez utiliser la clause COLLATE de l'instruction CREATE DATABASE ou ALTER DATABASE pour spécifier le classement par défaut de la base de données. Si aucun classement n'est spécifié, le classement du serveur est affecté à la base de données.    
    
Vous ne pouvez pas modifier le classement des bases de données système, à moins de modifier le classement du serveur.    
    
Le classement de la base de données est utilisé pour toutes les métadonnées de la base de données. Il constitue le classement par défaut pour l'ensemble des colonnes de chaîne, des objets temporaires, des noms de variable et des autres chaînes utilisées dans la base de données. Quand vous modifiez le classement d'une base de données utilisateur, des conflits de classement risquent de se produire quand des requêtes de la base de données accèdent à des tables temporaires. Les tables temporaires sont toujours stockées dans la base de données système **tempdb**, qui utilise le classement de l’instance. Les requêtes qui comparent les données caractères entre la base de données utilisateur et **tempdb** risquent d'échouer si les classements génèrent un conflit lors de l'évaluation des données caractères. Vous pouvez résoudre ce problème en spécifiant la clause COLLATE dans la requête. Pour plus d’informations, consultez [COLLATE &#40;Transact-SQL&#41;](~/t-sql/statements/collations.md).    
    
#### <a name="column-level-collations"></a>Classements au niveau des colonnes    
Lorsque vous créez ou modifiez une table, vous pouvez spécifier des classements pour chaque colonne de chaîne de caractères à l'aide de la clause COLLATE. Si aucun classement n'est spécifié, le classement par défaut de la base de données est attribué à la colonne.    
    
#### <a name="expression-level-collations"></a>Classements au niveau de l'expression    
Les classements au niveau de l'expression sont définis lors de l'exécution d'une instruction et ils affectent la façon dont l'ensemble de résultats est retourné. Cela permet aux résultats de tri ORDER BY d'être spécifiques aux paramètres régionaux. Utilisez une clause COLLATE telle que la suivante pour implémenter les classements au niveau de l'expression :    
    
```sql    
SELECT name FROM customer ORDER BY name COLLATE Latin1_General_CS_AI;    
```    
    
###  <a name="Locale_Defn"></a> Paramètres régionaux    
Les paramètres régionaux sont un ensemble d'informations associées à un emplacement ou à une culture. Il peut s'agir du nom et de l'identificateur de la langue parlée, du script utilisé pour écrire la langue et des conventions culturelles. Les classements peuvent être associés à un ou plusieurs ensembles de paramètres régionaux. Pour plus d'informations, consultez [Locale IDs Assigned by Microsoft (en anglais)](https://msdn.microsoft.com/goglobal/bb964664.aspx).    
    
###  <a name="Code_Page_Defn"></a> Code Page    
 Une page de codes est le jeu ordonné de caractères d'un script donné dans lequel un index numérique (ou une valeur de point de code) est associé à chaque caractère. Une page de codes Windows est généralement appelée *jeu de caractères* ou *charset*. Les pages de codes permettent d'assurer la prise en charge des jeux de caractères et des dispositions du clavier utilisés par différents paramètres régionaux système Windows.     
 
###  <a name="Sort_Order_Defn"></a> Sort Order    
 L'ordre de tri spécifie comment sont triées les valeurs de données. Cela affecte les résultats de comparaison de données. Les données sont triées en utilisant les classements et peuvent être optimisées à l'aide des index.    
    
##  <a name="Unicode_Defn"></a> Prise en charge d’Unicode    
Unicode est un standard en matière de correspondance de points de code avec des caractères. Comme il est conçu pour couvrir tous les caractères de toutes les langues du monde, il n'y a pas besoin de pages de codes différentes pour gérer des jeux de caractères différents. 
   
Les pages de codes qu'utilise un client sont déterminées par les paramètres du système d'exploitation. Pour définir les pages de codes du client sur le système d'exploitation Windows, utilisez **Paramètres régionaux** dans le Panneau de configuration.    

Des limitations significatives sont associées aux types de données non-Unicode. C’est parce qu’un ordinateur non-Unicode ne peut utiliser qu’une seule page de codes. Vous pouvez bénéficier de gains de performances en utilisant Unicode parce qu'un moins grand nombre de conversions de page de codes est requis. Les classements Unicode doivent être sélectionnés individuellement au niveau de la base de données, de la colonne ou de l’expression parce qu’ils ne sont pas pris en charge au niveau du serveur.    
   
Lorsque vous déplacez des données d'un serveur vers un client, votre classement du serveur peut ne pas être reconnu par les pilotes de clients plus anciens. Cela peut se produire lorsque vous déplacez des données d'un serveur Unicode vers un client non-Unicode. La meilleure solution peut alors consister à mettre à niveau le système d'exploitation du client afin de mettre aussi à jour les classements du système sous-jacent. Si le client est équipé du logiciel client de base de données, vous pouvez envisager de lui appliquer une mise à jour du service.    
    
> [!TIP]
> Vous pouvez également essayer d'utiliser un autre classement pour les données du serveur. Choisissez un classement qui établit un mappage à une page de codes du client.    

Si vous stockez des données caractères qui reflètent plusieurs langues dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] à [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]), utilisez des types de données Unicode (**nchar**, **nvarchar** et **ntext**) au lieu de types de données non-Unicode (**char**, **varchar** et **text**). 

> [!NOTE]
> Pour les types de données Unicode, le [!INCLUDE[ssde_md](../../includes/ssde_md.md)] peut représenter jusqu'à 65 535 caractères à l’aide de UCS-2 ou la plage Unicode complète (1 114 111 caractères) si les caractères supplémentaires sont utilisés. Pour plus d’informations sur l’activation de caractères supplémentaires, consultez [Caractères supplémentaires](#Supplementary_Characters).

D’autre part, à compter de [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)], si un classement compatible UTF-8 (\_UTF8) est utilisé, les types de données qui étaient auparavant non-Unicode (**char** et **varchar**) deviennent des types de données Unicode (UTF-8). [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] ne change pas le comportement des types de données Unicode (UTF-16) existants (**nchar**, **nvarchar** et **ntext**). Pour d’autres considérations, consultez [Différences de stockage entre UTF-8 et UTF-16](#storage_differences).
       
Pour utiliser les classements UTF-16 disponibles dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] à [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]) afin d’améliorer la recherche et le tri de certains caractères Unicode (classements Windows uniquement), vous pouvez sélectionner un des classements (\_SC) de caractères supplémentaires ou un des classements de la version 140.    
 
Pour utiliser les classements UTF-8 disponibles dans [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] afin d’améliorer la recherche et le tri de certains caractères Unicode (classements Windows uniquement), vous devez sélectionner des classements compatibles avec l’encodage UTF-8 (\_UTF8).
 
-   L’indicateur UTF8 peut être appliqué aux éléments suivants :    
    -   Classements version 90 
        > [!NOTE]
        > Seulement quand des caractères supplémentaires (\_SC) ou des classements compatibles avec le respect du sélecteur de variante (\_VSS) existent déjà dans cette version.
    -   Classements version 100    
    -   Classements version 140   
    -   BIN2<sup>1</sup> classement binaire
    
-   L’indicateur UTF8 ne peut pas être appliqué aux éléments suivants :    
    -   Classements version 90 qui ne prennent pas en charge les caractères supplémentaires (\_SC) ou le respect du sélecteur de variante (\_VSS)    
    -   Classements binaires BIN ou BIN2<sup>2</sup>    
    -   Classements SQL\*  
    
<sup>1</sup> À compter de [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] CTP 2.3. [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] Classement CTP 3.0 remplacé UTF8_BIN2 avec Latin1_General_100_BIN2_UTF8.     
<sup>2</sup> Jusqu’à [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] CTP 2.3. 
    
Pour déterminer les problèmes qui sont liés à l'utilisation des types de données Unicode ou non-Unicode, testez votre scénario pour mesurer les écarts de performances dans votre environnement. Vous devez normaliser le classement utilisé sur les systèmes de votre organisation et déployer des serveurs et clients Unicode partout où vous le pouvez.    
    
Dans de nombreuses situations, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] interagit avec d’autres serveurs ou clients, et votre organisation peut utiliser plusieurs normes d’accès aux données entre les applications et les instances de serveur. Les clients[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont l'un des deux types principaux :    
    
-   Les**clients Unicode** qui utilisent OLE DB et ODBC (Open Database Connectivity) 3.7 ou version ultérieure.    
-   Les**clients non-Unicode** qui utilisent DB-Library et ODBC 3.6 ou version antérieure.    
    
Le tableau suivant présente des informations sur l'utilisation des données multilingues avec diverses combinaisons de serveurs Unicode et non-Unicode.    
    
|Serveur|Client|Avantages ou restrictions|    
|------------|------------|-----------------------------|    
|Unicode|Unicode|Comme les données Unicode sont utilisées dans tout le système, ce scénario fournit les meilleures performances et la meilleure protection contre l’altération des données récupérées. C’est le cas avec ActiveX Data Objects (ADO), OLE DB et ODBC 3.7 ou version ultérieure.|    
|Unicode|Non-Unicode|Dans ce scénario, et surtout avec les connexions entre un serveur exécutant un système d'exploitation récent et un client exécutant une version antérieure de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ou un système d'exploitation plus ancien, il peut y avoir des limitations ou des erreurs lorsque vous déplacez des données vers un ordinateur client. Les données Unicode sur le serveur tentent d’établir un mappage à une page de codes correspondante sur le client non-Unicode afin de convertir les données.|    
|Non-Unicode|Unicode|Cette configuration n'est pas idéale pour l'utilisation de données multilingues. Vous ne pouvez pas écrire des données Unicode sur le serveur non-Unicode. Des problèmes peuvent survenir lorsque les données sont envoyées à des serveurs qui sont en dehors de la page de codes du serveur.|    
|Non-Unicode|Non-Unicode|Cette configuration est la plus limitée pour des données multilingues. Vous pouvez utiliser uniquement une seule page de codes.|    
    
##  <a name="Supplementary_Characters"></a> Caractères supplémentaires    
Le Consortium Unicode alloue à chaque caractère un code de caractère unique, qui est une valeur comprise entre 000000 et 10FFFF. Les caractères les plus fréquemment utilisés ont des valeurs de code de caractère dans la plage de 000000 à 00FFFF (65 535 caractères) qui correspondent à un mot de 8 ou 16 bits en mémoire et sur le disque. Cette plage est généralement désignée en tant que Plan multilingue de base (BMP). 

Mais le Consortium Unicode a établi des 16 « plans » de caractères supplémentaires, chacun ayant la même taille que le BMP. Cette définition accorde à Unicode le potentiel de représenter 1 114 112 caractères (autrement dit, 2<sup>16</sup> * 17 caractères) au sein de la plage de code de caractère de 000000 à 10FFFF. Les caractères dont les valeurs de code de caractère supérieures à 00FFFF requièrent entre deux et quatre mots de 8 bits consécutifs (UTF-8) ou deux mots de 16 bits consécutifs (UTF-16). Ces caractères situés au-delà du BMP sont appelés *caractères supplémentaires* et les deux mots de 8 ou 16 bits consécutifs supplémentaires sont appelés *paires de substitution*. Pour plus d’informations sur les caractères supplémentaires, des substitutions et des paires de substitution, reportez-vous à [la norme Unicode](http://www.unicode.org/standard/standard.html).    

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournit des types de données tels que **nchar** et **nvarchar** pour stocker les données Unicode dans la plage BMP (de 000000 à 00FFFF), ce que [!INCLUDE[ssde_md](../../includes/ssde_md.md)] encode à l’aide de UCS-2. 

[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] introduit une nouvelle famille de classements de caractères supplémentaires (\_SC) pouvant être utilisée avec les types de données **nchar**, **nvarchar** et **sql_variant** pour représenter la plage de caractères Unicode (de 000000 à 10FFFF). Par exemple : `Latin1_General_100_CI_AS_SC` ou si vous utilisez un classement japonais, `Japanese_Bushu_Kakusu_100_CI_AS_SC`. 
 
[!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] étend le support des caractères supplémentaires aux types de données **char** et **varchar** avec les nouveaux classements prenant en charge UTF-8 ([\_UTF8](#utf8)). Ils sont également capables de représenter la plage de caractères Unicode complète.   

> [!NOTE]
> À compter de [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], tous les nouveaux classements **\_140** prennent en charge automatiquement les caractères supplémentaires.

Si vous utilisez des caractères supplémentaires :    
    
-   Les caractères supplémentaires peuvent être utilisés dans des opérations de tri et de comparaison dans les versions de classement 90 ou versions supérieures.    
-   Tous les classements version 100 prennent en charge le tri linguistique avec les caractères supplémentaires.    
-   Les caractères supplémentaires ne sont pas utilisables dans les métadonnées, telles que les noms d'objets de base de données.    
-   Les bases de données qui utilisent des classements avec des caractères supplémentaires (\_SC) ne peuvent pas être activées pour la réplication [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. C’est parce que certaines des tables système et des procédures stockées créées pour la réplication utilisent le type de données **ntext** hérité qui ne prend pas en charge les caractères supplémentaires.  

-   L’indicateur SC peut s’appliquer aux éléments suivants :    
    -   Classements version 90    
    -   Classements version 100    
    
-   L’indicateur SC ne peut pas s’appliquer aux éléments suivants :    
    -   Classements Windows version 80 et sans version    
    -   Classements binaires BIN ou BIN2    
    -   Classements SQL\*    
    -   Classements version 140 (ces derniers n’ont pas besoin de l’indicateur SC, car ils prennent déjà en charge les caractères supplémentaires)    
    
Le tableau suivant compare le comportement de quelques fonctions de chaîne et opérateurs de chaîne quand ils utilisent des caractères supplémentaires avec et sans classement sensible aux caractères supplémentaires :    
    
|Fonction de chaîne ou opérateur|Avec un classement sensible aux caractères supplémentaires|Sans classement sensible aux caractères supplémentaires|    
|---------------------------------|--------------------------|-----------------------------|    
|[CHARINDEX](../../t-sql/functions/charindex-transact-sql.md)<br /><br /> [LEN](../../t-sql/functions/len-transact-sql.md)<br /><br /> [PATINDEX](../../t-sql/functions/patindex-transact-sql.md)|La paire de substitution UTF-16 est comptée comme un codepoint unique.|La paire de substitution UTF-16 est comptée comme deux codepoints.|    
|[LEFT](../../t-sql/functions/left-transact-sql.md)<br /><br /> [REPLACE](../../t-sql/functions/replace-transact-sql.md)<br /><br /> [REVERSE](../../t-sql/functions/reverse-transact-sql.md)<br /><br /> [RIGHT](../../t-sql/functions/right-transact-sql.md)<br /><br /> [SUBSTRING](../../t-sql/functions/substring-transact-sql.md)<br /><br /> [STUFF](../../t-sql/functions/stuff-transact-sql.md)|Ces fonctions traitent chaque paire de substitution comme un codepoint unique et fonctionnent comme attendu.|Ces fonctions peuvent fractionner toutes les paires de substitution et conduire à des résultats inattendus.|    
|[NCHAR](../../t-sql/functions/nchar-transact-sql.md)|Retourne le caractère qui correspond à la valeur de codepoint Unicode spécifiée dans la plage 0 à 0x10FFFF. Si la valeur spécifiée se trouve dans la plage 0 à 0xFFFF, un seul caractère est retourné. Pour les valeurs plus élevées, la paire de substitution correspondante est retournée.|Une valeur supérieure à 0xFFFF retourne NULL au lieu du substitut correspondant.|    
|[UNICODE](../../t-sql/functions/unicode-transact-sql.md)|Retourne un codepoint UTF-16 dans la plage 0 à 0x10FFFF.|Retourne un codepoint UCS-2 dans la plage 0 à 0xFFFF.|    
|[Recherche de correspondance d’un seul caractère générique](../../t-sql/language-elements/wildcard-match-one-character-transact-sql.md)<br /><br /> [Caractère générique - Caractères à ne pas faire correspondre](../../t-sql/language-elements/wildcard-character-s-not-to-match-transact-sql.md)|Les caractères supplémentaires sont pris en charge pour toutes les opérations génériques.|Les caractères supplémentaires ne sont pas pris en charge pour ces opérations génériques. D'autres opérateurs génériques sont pris en charge.|    
    
## <a name="GB18030"></a> Prise en charge du langage GB18030    
GB18030 est une norme distincte utilisée en République populaire de Chine pour l'encodage des caractères chinois. Dans la norme GB18030, les caractères peuvent être encodés sur 1, 2 ou 4 octets de longueur. Pour prendre en charge les caractères encodés selon la norme GB18030,[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les reconnaît lorsqu'ils entrent dans le serveur en provenance d'une application côté client, puis les convertit et les stocke en mode natif en tant que caractères Unicode. Une fois stockés dans le serveur, ils sont traités en tant que caractères Unicode dans toutes les opérations suivantes. Vous pouvez utiliser n'importe quel classement chinois, de préférence la version 100 la plus récente. Tous les classements de niveau _100 prennent en charge le tri linguistique avec les caractères GB18030. Si les données incluent des caractères supplémentaires (paires de substitution), vous pouvez utiliser les classements SC disponibles dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] pour améliorer la recherche et le tri.    
    
## <a name="Complex_script"></a> Prise en charge des scripts complexes    
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut prendre en charge l'entrée, le stockage, la modification et l'affichage de scripts complexes. Les scripts complexes sont notamment les suivants :    
    
-   Scripts qui associent l'utilisation de textes écrits de droite à gauche et de gauche à droite, par exemple les textes écrits en arabe et en anglais.    
-   Scripts dont les caractères changent de forme en fonction de leur position ou lorsqu'ils sont associés à d'autres caractères, par exemple les caractères arabes, indiens et thaï.    
-   Les langues telles que le thaï nécessitent des dictionnaires internes pour la reconnaissance des mots, car ces derniers ne sont pas séparés.    
    
Les applications de base de données qui interagissent avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doivent utiliser des contrôles qui prennent en charge les scripts complexes. Les contrôles Windows Form standard créés dans du code managé peuvent prendre en charge les scripts complexes.    

## <a name="Japanese_Collations"></a> Classements japonais ajoutés dans  [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)]
 
À compter de [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)], de nouvelles familles de classement du japonais sont prises en charge, avec les permutations de différentes options (\_CS, \_AS, \_KS, \_WS, \_VSS). 

Pour lister ces classements, vous pouvez interroger le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] :      

```sql 
SELECT Name, Description FROM fn_helpcollations()  
WHERE Name LIKE 'Japanese_Bushu_Kakusu_140%' OR Name LIKE 'Japanese_XJIS_140%'
``` 

Tous les nouveaux classements disposent d’un support intégré des caractères supplémentaires, par conséquent, aucun des nouveaux classements **\_140** n’a (ni ne requiert) l’indicateur SC.

Ces classements sont pris en charge dans les index, les tables optimisées en mémoire, les index columnstore et les modules compilés en mode natif [!INCLUDE[ssde_md](../../includes/ssde_md.md)].

<a name="ctp23"></a>

## <a name="utf8"></a> Support UTF-8
[!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] introduit le complet support du codage de caractères UTF-8 largement utilisé en tant qu’encodage d’importation ou d’exportation et en tant que classement au niveau des base de données et au niveau des colonnes pour les données de chaîne. UTF-8 est autorisé dans les types de données **char** et **varchar** et est activé pendant la création ou la modification d’un classement d’objet en un classement avec le suffixe `UTF8`. Par exemple,`LATIN1_GENERAL_100_CI_AS_SC` en `LATIN1_GENERAL_100_CI_AS_SC_UTF8`. 

UTF-8 est uniquement disponible pour les classements Windows qui prennent en charge les caractères supplémentaires, comme introduit dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]. **nchar** et **nvarchar** autorisent l’encodage UCS-2 ou UTF-16 uniquement et restent inchangées.

### <a name="storage_differences"></a> Différences de stockage entre UTF-8 et UTF-16
Le Consortium Unicode alloue à chaque caractère un code de caractère unique, qui est une valeur comprise entre 000000 et 10FFFF. Avec [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)], les encodages UTF-8 et UTF-16 sont disponibles pour représenter la plage complète :    
-  Avec l’encodage UTF-8, les caractères dans la plage ASCII (000000 – 00007F) utilisent 1 octet, les codes de caractère de 000080 à 0007FF nécessitent 2 octets, les codes de caractère de 000800 à 00FFFF nécessitent 3 octets et les codes de caractère de 0010000 à 0010FFFF nécessitent 4 octets. 
-  Avec l’encodage UTF-16, les codes de caractère de 000000 à 00FFFF nécessitent 2 octets et les codes de caractère de 0010000 à 0010FFFF nécessitent 4 octets. 

La table suivante présente les octets de stockage d’encodage pour chaque plage de caractères et type d’encodage :

|Plage de codes (hexadécimal)|Plage de codes (décimal)|Octets de stockage <sup>1</sup> avec UTF-8|Octets de stockage <sup>1</sup> avec UTF-16|    
|---------------------------------|---------------------------------|--------------------------|-----------------------------|   
|000000 – 00007F|0 - 127|1|2|
|000080 – 00009F<br />0000A0 – 0003FF<br />000400 – 0007FF|128 – 159<br />160 – 1,023<br />1,024 – 2,047|2|2|
|000800 – 003FFF<br />004000 – 00FFFF|2,048 - 16,383<br />16,384 – 65,535|3|2|
|010000 – 03FFFF <sup>2</sup><br /><br />040000 – 10FFFF <sup>2</sup>|65,536 – 262,143 <sup>2</sup><br /><br />262,144 – 1,114,111 <sup>2</sup>|4|4|

<sup>1</sup> Les octets de stockage font référence à la longueur d’octets encodés et pas à la taille de stockage sur disque des types de données respectifs. Pour plus d’informations sur les tailles de stockage sur disque, consultez [nchar et nvarchar](../../t-sql/data-types/nchar-and-nvarchar-transact-sql.md) et [char et varchar](../../t-sql/data-types/char-and-varchar-transact-sql.md).

<sup>2</sup> Plage de codes de caractère pour des [caractères supplémentaires](#Supplementary_Characters).

> [!TIP]   
> Il est courant de penser en [CHAR(*n*) et en VARCHAR(*n*)](../../t-sql/data-types/char-and-varchar-transact-sql.md), ou en [NCHAR(*n*) et en NVARCHAR(*n*)](../../t-sql/data-types/nchar-and-nvarchar-transact-sql.md), le *n* définissant le nombre de caractères. En effet, dans l’exemple d’une colonne de type CHAR(10), 10 caractères ASCII de la plage 0-127 peuvent être stockés à l’aide d’un classement tel que Latin1_General_100_CI_AI, car chaque caractère de cette plage utilise uniquement 1 octet.    
> Toutefois, dans [CHAR(*n*) et VARCHAR(*n*)](../../t-sql/data-types/char-and-varchar-transact-sql.md), le *n* définit la longueur de chaîne en **octets** (0-8000), tandis que dans [NCHAR(*n*) et NVARCHAR(*n*)](../../t-sql/data-types/nchar-and-nvarchar-transact-sql.md), le *n* définit la longueur de la chaîne en **paires d’octets** (0-4000). *n* ne définit jamais des nombres de caractères pouvant être stockés.

Comme décrit ci-dessus, le choix de l’encodage Unicode et du type de données appropriés peut fournir des gains de stockage significatifs ou augmenter votre encombrement de stockage actuel, en fonction du jeu de caractères utilisé. Par exemple, lors de l’utilisation d’un classement Latin prenant en charge UTF-8, comme Latin1_General_100_CI_AI_SC_UTF8, une colonne `CHAR(10)` stocke 10 octets et peut contenir 10 caractères ASCII dans la plage 0-127, mais seulement 5 caractères dans la plage 128-2047 et seulement 3 caractères dans plage 2048-65535. En comparaison, étant donné qu’une colonne `NCHAR(10)` stocke 10 paires d’octets (20 octets), elle peut contenir 10 caractères dans la plage 0-65535.  

Avant de choisir s’il faut utiliser l’encodage UTF-8 ou UTF-16 pour une base de données ou une colonne, prenez en compte la distribution des données de chaîne qui seront stockées :
-  Si elle est principalement dans la plage ASCII 0-127 (par exemple, en anglais), chaque caractère nécessite alors 1 octet en UTF-8 et 2 octets en UTF-16. L’utilisation UFT-8 offre des avantages du stockage. Le fait de transformer un type de données de colonne existant comportant des caractères ASCII de la plage 0-127 de `NCHAR(10)` en `CHAR(10)` avec un classement prenant en charge UTF-8 se traduit par une réduction de 50 % des besoins en stockage. Cette réduction correspond au fait que `NCHAR(10)` nécessite 20 octets pour le stockage, tandis que `CHAR(10)` nécessite 10 octets pour la même représentation de chaîne Unicode.    
-  Au-dessus de la plage ASCII, presque tout l’alphabet latin et également grec, cyrillique, copte, arménien, hébreu, arabe, syriaque, Tāna et n’ko nécessitera 2 octets par caractère dans les encodages UTF-8 et UTF-16. Dans ces cas, il n’existe pas de différences significatives de stockage pour les types de données comparables (par exemple à l’aide de **char** ou **nchar**).
-  S’il s’agit principalement d’un script d’Extrême-Orient (par exemple, coréen, chinois et japonais), chaque caractère nécessite alors 3 octets en UTF-8 et 2 octets en UTF-16. L’utilisation UFT-16 offre des avantages du stockage. 
-  Les caractères compris entre 010000 et 10FFFF nécessitent 4 octets en encodage UTF-8 et UTF-16. Dans ces cas, il n’existe pas de différences de stockage pour les types de données comparables (par exemple à l’aide de **char** ou **nchar**).

Pour d’autres considérations, consultez [Écrire des instructions Transact-SQL internationales](../../relational-databases/collations/write-international-transact-sql-statements.md).

##  <a name="Related_Tasks"></a> Tâches associées    
    
|Tâche|Rubrique|    
|----------|-----------|    
|Explique comment définir ou modifier le classement de l'instance de SQL Server.|[Définir ou modifier le classement du serveur](../../relational-databases/collations/set-or-change-the-server-collation.md)|    
|Explique comment définir ou modifier le classement d'une base de données utilisateur.|[Définir ou modifier le classement de la base de données](../../relational-databases/collations/set-or-change-the-database-collation.md)|    
|Explique comment définir ou modifier le classement d'une colonne dans la base de données.|[Définir ou modifier le classement des colonnes](../../relational-databases/collations/set-or-change-the-column-collation.md)|    
|Explique comment retourner des informations de classement au niveau du serveur, de la base de données ou de la colonne.|[Afficher des informations de classement](../../relational-databases/collations/view-collation-information.md)|    
|Décrit comment écrire des instructions Transact-SQL qui sont plus portables d’un langage à un autre ou qui prennent en charge plusieurs langages plus facilement.|[Rédiger des instructions Transact-SQL internationales](../../relational-databases/collations/write-international-transact-sql-statements.md)|    
|Explique comment modifier la langue des messages d'erreur et des paramètres relatifs à l'utilisation et l'affichage de la date, de l'heure et des devises.|[Définir une langue de session](../../relational-databases/collations/set-a-session-language.md)|    
    
##  <a name="Related_Content"></a> Contenu associé    
[SQL Server Best Practices Collation Change](https://go.microsoft.com/fwlink/?LinkId=113891)    
[Utiliser le format de caractère Unicode pour importer ou exporter des données &#40;SQL Server&#41;](../../relational-databases/import-export/use-unicode-character-format-to-import-or-export-data-sql-server.md)        
[Rédiger des instructions Transact-SQL internationales](../../relational-databases/collations/write-international-transact-sql-statements.md)     
["SQL Server Best Practices Migration to Unicode"](https://go.microsoft.com/fwlink/?LinkId=113890) - (Plus de support)   
[Site web du consortium Unicode](https://go.microsoft.com/fwlink/?LinkId=48619)   
[Norme Unicode](http://www.unicode.org/standard/standard.html)      
    
## <a name="see-also"></a>Voir aussi    
[Classements de base de données autonome](../../relational-databases/databases/contained-database-collations.md)     
[Choisir une langue lors de la création d’un index de recherche en texte intégral](../../relational-databases/search/choose-a-language-when-creating-a-full-text-index.md)     
[sys.fn_helpcollations &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-helpcollations-transact-sql.md)    
    
 
