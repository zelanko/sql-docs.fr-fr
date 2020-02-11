---
title: Prise en charge d’Unicode et du classement | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2019
ms.prod: sql-server-2014
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
- server-level collations [SQL Server]
ms.assetid: 92d34f48-fa2b-47c5-89d3-a4c39b0f39eb
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c63b7c0d1acad34bb273e4a49921d55818965e80
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "72688732"
---
# <a name="collation-and-unicode-support"></a>Prise en charge d’Unicode et du classement
  Les classements dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournissent les règles de tri et les propriétés de respect de la casse et des accents pour vos données. Les classements utilisés avec les types de données character, tels que `char` et `varchar`, déterminent la page de codes et les caractères correspondants qui peuvent être représentés pour ce type de données. Que vous installiez une nouvelle instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], restauriez une sauvegarde de base de données ou connectiez un serveur à des bases de données clientes, il est important que vous compreniez les besoins en termes de paramètres régionaux, ordre de tri et respect de la casse et des accents des données avec lesquelles vous travaillez. Pour répertorier les classements disponibles sur votre instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [sys.fn_helpcollations &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-helpcollations-transact-sql).  
  
 Lorsque vous sélectionnez un classement pour votre serveur, base de données, colonne ou expression, vous assignez certaines caractéristiques à vos données qui affecteront les résultats de nombreuses opérations dans la base de données. Par exemple, lorsque vous construisez une requête à l'aide d'ORDER BY, l'ordre de tri de votre jeu de résultats peut dépendre du classement appliqué à la base de données ou stipulé dans une clause COLLATE au niveau expression de la requête.  
  
 Pour exploiter au mieux la prise en charge des classements dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous devez comprendre les termes qui sont définis dans cette rubrique et la relation qu'ils entretiennent avec les caractéristiques de vos données.  
  
  
###  <a name="Collation_Defn"></a> Classement  
 Un classement désigne les modèles binaires qui représentent chaque caractère dans un jeu de données. Les classements déterminent également les règles de tri et de comparaison des données. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge le stockage d’objets ayant des classements différents dans une même base de données. Pour les colonnes non-Unicode, le paramètre de classement spécifie la page de codes pour les données et les caractères qui peuvent être représentés. Les données déplacées entre des colonnes non-Unicode doivent être converties de la page de codes source vers la page de codes de destination.  
  
 Le résultat d'une instruction[!INCLUDE[tsql](../../includes/tsql-md.md)] peut varier lorsque cette dernière est exécutée dans un contexte réunissant plusieurs bases de données dont chacune a un paramètre de classement différent. Dans la mesure du possible, choisissez un classement normalisé pour votre organisation. De cette manière, vous n'avez pas à spécifier explicitement le classement dans chaque caractère ou expression Unicode. Si vous devez utiliser des objets qui ont des paramètres de classement et de page de codes différents, codez vos requêtes conformément aux règles de priorité des classements. Pour plus d’informations, consultez [Priorité de classement (Transact-SQL)](/sql/t-sql/statements/collation-precedence-transact-sql).  
  
 Les options associées à un classement sont le respect de la casse, le respect des accents, le respect du jeu de caractères Kana et le respect de la largeur. Pour spécifier ces options, vous devez les ajouter au nom du classement. Par exemple, le classement `Japanese_Bushu_Kakusu_100_CS_AS_KS_WS` respecte la casse, les accents, le jeu de caractères Kana et la largeur. Le tableau suivant décrit le comportement associé à ces options.  
  
|Option|Description|  
|------------|-----------------|  
|Respecter la casse (_CS)|Fait la distinction entre les majuscules et les minuscules. Si cette option est activée, les minuscules sont triées avant leurs équivalents majuscules. Si cette option n'est pas sélectionnée, le classement ne respecte pas la casse. Dans ce cas, SQL Server considère que les versions en majuscules et en minuscules des lettres sont identiques dans les opérations de tri. Vous pouvez explicitement sélectionner le non-respect de la casse en spécifiant _CI.|  
|Respecter les accents (_AS)|Fait la distinction entre les caractères accentués et non accentués. Par exemple, « a » n’est pas égal à « &#x1EA5; ». Si cette option n'est pas sélectionnée, le classement ne respecte pas les accents. Dans ce cas, SQL Server considère que les versions accentuées et non accentuées des lettres sont identiques dans les opérations de tri. Vous pouvez explicitement sélectionner le non-respect des accents en spécifiant _AI.|  
|Respecter le jeu de caractères Kana (_KS)|Fait la distinction entre les deux types de caractères japonais Kana : Hiragana et Katakana. Si cette option n'est pas sélectionnée, le classement ne respecte pas les caractères Kana. Dans ce cas, SQL Server considère que les caractères Hiragana et Katakana sont identiques dans les opérations de tri. L'omission de cette option est le seul moyen de spécifier le non-respect du jeu de caractères Kana.|  
|Respecter la largeur (_WS)|Fait la différence entre les caractères pleine largeur et demi-largeur. Si cette option n'est pas sélectionnée, SQL Server considère que la représentation pleine largeur et demi-largeur d'un même caractère sont identiques dans les opérations de tri. L'omission de cette option est le seul moyen de spécifier le non-respect de la largeur.|  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge les ensembles de classement suivants :  
  
 classements Windows  
 Les classements Windows définissent les règles de stockage des données de type caractère selon les paramètres régionaux système Windows associés. Pour un classement Windows, la comparaison de données non-Unicode est implémentée via le même algorithme que les données Unicode. Les règles de classement Windows de base spécifient l'alphabet ou la langue utilisée pour le tri du dictionnaire, et la page de codes utilisée pour stocker les données de type caractère non-Unicode. Les tris Unicode et non-Unicode sont compatibles avec les comparaisons de chaînes dans une version particulière de Windows. Les types de données sont ainsi cohérents dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ce qui permet aux développeurs de trier les chaînes dans leurs applications en appliquant les mêmes règles que celles utilisées par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations, consultez [Nom de classement Windows &#40;Transact-SQL&#41;](/sql/t-sql/statements/windows-collation-name-transact-sql).  
  
 Classements binaires  
 Les classements binaires trient les données en fonction de la séquence des valeurs codées qui sont définies par les paramètres régionaux et le type de données. Ils respectent la casse. Un classement binaire dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] définit les paramètres régionaux et la page de codes ANSI qui seront utilisés. Cela applique un ordre de tri binaire. Parce qu'ils sont relativement simples, les classements binaires aident à améliorer les performances de l'application. Pour les types de données non-Unicode, les comparaisons de données sont basées sur les points de code qui sont définis dans la page de codes ANSI. Pour les données de type Unicode, les comparaisons de données se basent sur les points de code Unicode. Pour le classement binaire des types de données Unicode, les paramètres régionaux (la langue) ne sont pas pris en compte dans les tris de données. Par exemple, Latin_1_General_BIN et Japanese_BIN produisent des résultats de tri identiques quand ils sont utilisés avec des données Unicode.  
  
 Il existe deux types de classement binaire dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ; les anciens classements `BIN` et les nouveaux classements `BIN2`. Dans un classement `BIN2` tous les caractères sont triés en fonction de leurs points de code. Dans un classement `BIN` seul le premier caractère est trié selon le point de code, et les autres caractères sont triés en fonction de leurs valeurs d'octet. (En raison de l'architecture little endian de la plateforme Intel, les caractères de code Unicode sont toujours triés inversés par octet.)  
  
 classements SQL Server  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]les classements (SQL_ *) fournissent la compatibilité d’ordre de tri [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]avec les versions antérieures de. Les règles de tri du dictionnaire pour les données non-Unicode ne sont pas compatibles avec les routines de tri fournies par les systèmes d'exploitation Windows. Toutefois, le tri de données Unicode est compatible avec une version particulière de règles de tri Windows. Comme les classements [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilisent des règles de comparaison différentes pour les données Unicode et non-Unicode, vous pouvez obtenir des résultats différents pour des comparaisons traitant des mêmes données, selon le type de données sous-jacent. Pour plus d’informations, consultez [Nom du classement SQL Server &#40;Transact-SQL&#41;](/sql/t-sql/statements/sql-server-collation-name-transact-sql).  
  
> [!NOTE]
>  Lorsque vous mettez à niveau une instance anglaise [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez spécifier les classements (SQL_*) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour permettre la compatibilité avec les instances [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] existantes. Le classement par défaut d'une instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] étant défini au cours de la procédure d'installation, assurez-vous de spécifier soigneusement les paramètres de classement dans les cas suivants :  
> 
>  -   Votre code d'application dépend du comportement des classements [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] précédents.  
> -   Vous devez stocker des données de caractères de plusieurs langues.  
  
 Les paramétrages des classements sont pris en charge aux niveaux suivants d'une instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
 Classements au niveau du serveur  
 Le classement du serveur par défaut est défini durant l'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , et devient également le classement par défaut des bases de données système et de toutes les bases de données utilisateur. Notez que les classements Unicode ne peuvent pas être sélectionnés pendant la procédure d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , car ils ne sont pas pris en charge en tant que classements au niveau du serveur.  
  
 Lorsqu'un classement a été affecté au serveur, vous ne pouvez pas le modifier le classement, à moins d'exporter la totalité des objets et des données de la base de données, de reconstruire la base de données `master` et d'importer la totalité des objets et des données de la base de données. Au lieu de modifier le classement par défaut d'une instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez spécifier le classement désiré au moment de la création d'une nouvelle base de données ou colonne de base de données.  
  
 Classements au niveau de la base de données  
 Lorsque vous créez ou modifiez une base de données, vous pouvez utiliser la clause COLLATE de l'instruction CREATE DATABASE ou ALTER DATABASE pour spécifier le classement par défaut de la base de données. Si aucun classement n'est spécifié, le classement du serveur est affecté à la base de données.  
  
 Vous ne pouvez pas modifier le classement des bases de données système, à moins de modifier le classement du serveur.  
  
 Le classement de la base de données est utilisé pour toutes les métadonnées de la base de données. Il constitue le classement par défaut pour l'ensemble des colonnes de chaîne, des objets temporaires, des noms de variable et des autres chaînes utilisées dans la base de données. Quand vous modifiez le classement d'une base de données utilisateur, des conflits de classement risquent de se produire quand des requêtes de la base de données accèdent à des tables temporaires. Les tables temporaires sont toujours stockées dans la base de données système `tempdb`, qui utilise le classement de l'instance. Les requêtes qui comparent les données caractères entre la base de données utilisateur et `tempdb` risquent d'échouer si les classements génèrent un conflit lors de l'évaluation des données caractères. Vous pouvez résoudre ce problème en spécifiant la clause COLLATE dans la requête. Pour plus d’informations, consultez [COLLATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/collations).  
  
 Classements au niveau des colonnes  
 Lorsque vous créez ou modifiez une table, vous pouvez spécifier des classements pour chaque colonne de chaîne de caractères à l'aide de la clause COLLATE. Si aucun classement n'est spécifié, le classement par défaut de la base de données est attribué à la colonne.  
  
 Classements au niveau de l'expression  
 Les classements au niveau de l'expression sont définis lors de l'exécution d'une instruction et ils affectent la façon dont l'ensemble de résultats est retourné. Cela permet aux résultats de tri ORDER BY d'être spécifiques aux paramètres régionaux. Utilisez une clause COLLATE telle que la suivante pour implémenter les classements au niveau de l'expression :  
  
```  
SELECT name FROM customer ORDER BY name COLLATE Latin1_General_CS_AI;  
```  
  
  
###  <a name="Locale_Defn"></a> Paramètres régionaux  
 Les paramètres régionaux sont un ensemble d'informations associées à un emplacement ou à une culture. Il peut s'agir du nom et de l'identificateur de la langue parlée, du script utilisé pour écrire la langue et des conventions culturelles. Les classements peuvent être associés à un ou plusieurs ensembles de paramètres régionaux. Pour plus d'informations, consultez [Locale IDs Assigned by Microsoft (en anglais)](https://msdn.microsoft.com/goglobal/bb964664.aspx).  
  
  
###  <a name="Code_Page_Defn"></a>Page de codes  
 Une page de codes est le jeu ordonné de caractères d'un script donné dans lequel un index numérique (ou une valeur de point de code) est associé à chaque caractère. Une page de codes Windows est généralement appelée *jeu de caractères* ou *charset*. Les pages de codes permettent d'assurer la prise en charge des jeux de caractères et des dispositions du clavier utilisés par différents paramètres régionaux système Windows.  
  
  
###  <a name="Sort_Order_Defn"></a>Ordre de tri  
 L'ordre de tri spécifie comment sont triées les valeurs de données. Cela affecte les résultats de comparaison de données. Les données sont triées en utilisant les classements et peuvent être optimisées à l'aide des index.  
  
  
##  <a name="Unicode_Defn"></a>Prise en charge Unicode  
 Unicode est un standard en matière de correspondance de points de code avec des caractères. Comme il est conçu pour couvrir tous les caractères de toutes les langues du monde, il n'y a pas besoin de pages de codes différentes pour gérer des jeux de caractères différents. Si vous stockez des données de caractères de plusieurs langues, utilisez toujours les types de données Unicode (`nchar`, `nvarchar` et `ntext`) à la place des types de données non-Unicode (`char`, `varchar` et `text`).  
  
 Des limitations significatives sont associées aux types de données non-Unicode. C'est parce qu'un ordinateur non-Unicode sera restreint quant à l'utilisation d'une page de codes unique. Vous pouvez bénéficier de gains de performances en utilisant Unicode parce qu'un moins grand nombre de conversions de page de codes est requis. Les classements unicode doivent être sélectionnés individuellement au niveau de la base de données, de la colonne ou de l'expression parce qu'ils ne sont pas pris en charge au niveau serveur.  
  
 Les pages de codes qu'utilise un client sont déterminées par les paramètres du système d'exploitation. Pour définir les pages de codes du client sur le système d'exploitation Windows, utilisez **Paramètres régionaux** dans le Panneau de configuration.  
  
 Lorsque vous déplacez des données d'un serveur vers un client, votre classement du serveur peut ne pas être reconnu par les pilotes de clients plus anciens. Cela peut se produire lorsque vous déplacez des données d'un serveur Unicode vers un client non-Unicode. La meilleure solution peut alors consister à mettre à niveau le système d'exploitation du client afin de mettre aussi à jour les classements du système sous-jacent. Si le client est équipé du logiciel client de base de données, vous pouvez envisager de lui appliquer une mise à jour du service.  
  
 Vous pouvez également essayer d'utiliser un autre classement pour les données du serveur. Choisissez un classement qui établit un mappage à une page de codes du client.  
  
 Pour utiliser les classements UTF-16 disponibles dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], sélectionnez l'un des classements `_SC` de caractères supplémentaires (classements Windows uniquement) afin d'améliorer la recherche et le tri de certains caractères Unicode.  
  
 Pour déterminer les problèmes qui sont liés à l'utilisation des types de données Unicode ou non-Unicode, testez votre scénario pour mesurer les écarts de performances dans votre environnement. Vous devez normaliser le classement utilisé sur les systèmes de votre organisation et déployer des serveurs et clients Unicode partout où vous le pouvez.  
  
 Dans de nombreuses situations, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] entre en interaction avec d'autres serveurs ou clients et votre organisation peut utiliser différentes normes d'accès aux données entre les applications et les instances de serveur. Les clients[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont l'un des deux types principaux :  
  
-   **Les clients Unicode** qui utilisent OLE DB et Open Database Connectivity (ODBC) version 3,7 ou une version ultérieure.  
  
-   **Clients non-Unicode** qui utilisent DB-Library et ODBC version 3,6 ou une version antérieure.  
  
 Le tableau suivant présente des informations sur l'utilisation des données multilingues avec diverses combinaisons de serveurs Unicode et non-Unicode.  
  
|Serveur|Client|Avantages ou restrictions|  
|------------|------------|-----------------------------|  
|Unicode|Unicode|Comme les données Unicode seront utilisées dans la totalité du système, ce scénario fournit les meilleures performances et la meilleure protection contre la modification des données extraites. C’est le cas avec ActiveX Data Objects (ADO), OLE DB et ODBC 3.7 ou version ultérieure.|  
|Unicode|Non-Unicode|Dans ce scénario, et surtout avec les connexions entre un serveur exécutant un système d'exploitation récent et un client exécutant une version antérieure de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ou un système d'exploitation plus ancien, il peut y avoir des limitations ou des erreurs lorsque vous déplacez des données vers un ordinateur client. Les données Unicode sur le serveur tenteront d'établir un mappage à une page de codes correspondante sur le client non-Unicode afin de convertir les données.|  
|Non-Unicode|Unicode|Cette configuration n'est pas idéale pour l'utilisation de données multilingues. Vous ne pouvez pas écrire des données Unicode sur le serveur non-Unicode. Des problèmes peuvent survenir lorsque les données sont envoyées à des serveurs qui sont en dehors de la page de codes du serveur.|  
|Non-Unicode|Non-Unicode|Cette configuration est la plus limitée pour des données multilingues. Vous pouvez utiliser uniquement une seule page de codes.|  
  
  
##  <a name="Supplementary_Characters"></a>Caractères supplémentaires  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]fournit des types de données `nchar` tels `nvarchar` que et pour stocker des données Unicode. Ces types de données encodent le texte dans un format appelé *UTF-16*. Le Consortium Unicode alloue à chaque caractère un codepoint unique, qui est une valeur comprise entre 0x0000 et 0x10FFFF. Les caractères les plus fréquemment utilisés ont des valeurs de codepoint qui correspondent à un mot de 16 bits en mémoire et sur le disque, mais les caractères dont les valeurs de codepoint sont supérieures à 0xFFFF requièrent deux mots de 16 bits consécutifs. Ces caractères sont appelés des *caractères supplémentaires*et les deux mots de 16 bits consécutifs sont appelés des *paires de substitution*.  
  
 Si vous utilisez des caractères supplémentaires :  
  
-   Les caractères supplémentaires peuvent être utilisés dans des opérations de tri et de comparaison dans les versions de classement 90 ou versions supérieures.  
  
-   Tous les nouveaux classements de niveau _100 prennent en charge le tri linguistique avec les caractères supplémentaires.  
  
-   Les caractères supplémentaires ne sont pas utilisables dans les métadonnées, telles que les noms d'objets de base de données.  
  
-   Depuis [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], une nouvelle famille de classements de caractères supplémentaires (SC) peut être utilisée avec les types de données `nchar`, `nvarchar` et `sql_variant`. Par exemple : `Latin1_General_100_CI_AS_SC` ou si vous utilisez un classement japonais, `Japanese_Bushu_Kakusu_100_CI_AS_SC`.  
  
     L’indicateur SC peut s’appliquer aux éléments suivants :  
  
    -   Classements Windows version 90  
  
    -   Classements Windows version 100  
  
     L’indicateur SC ne peut pas s’appliquer aux éléments suivants :  
  
    -   Classements Windows version 80 et sans version  
  
    -   Classements binaires BIN ou BIN2  
  
    -   Classements SQL*  
  
 Le tableau suivant compare le comportement de quelques fonctions de chaîne et opérateurs d'enchaînement lorsqu'ils utilisent des caractères supplémentaires avec et sans classement SC.  
  
|Fonction de chaîne ou opérateur|Avec un classement SC|Sans classement SC|  
|---------------------------------|--------------------------|-----------------------------|  
|[CHARINDEX](/sql/t-sql/functions/charindex-transact-sql)<br /><br /> [LEN](/sql/t-sql/functions/len-transact-sql)<br /><br /> [PATINDEX](/sql/t-sql/functions/patindex-transact-sql)|La paire de substitution UTF-16 est comptée comme un codepoint unique.|La paire de substitution UTF-16 est comptée comme deux codepoints.|  
|[LEFT](/sql/t-sql/functions/left-transact-sql)<br /><br /> [REPLACE](/sql/t-sql/functions/replace-transact-sql)<br /><br /> [REVERSE](/sql/t-sql/functions/reverse-transact-sql)<br /><br /> [RIGHT](/sql/t-sql/functions/right-transact-sql)<br /><br /> [SUBSTRING](/sql/t-sql/functions/substring-transact-sql)<br /><br /> [STUFF](/sql/t-sql/functions/stuff-transact-sql)|Ces fonctions traitent chaque paire de substitution comme un codepoint unique et fonctionnent comme attendu.|Ces fonctions peuvent fractionner toutes les paires de substitution et conduire à des résultats inattendus.|  
|[NCHAR](/sql/t-sql/functions/nchar-transact-sql)|Retourne le caractère qui correspond à la valeur de codepoint Unicode spécifiée dans la plage 0 à 0x10FFFF. Si la valeur spécifiée se trouve dans la plage 0 à 0xFFFF, un seul caractère est retourné. Pour les valeurs plus élevées, la paire de substitution correspondante est retournée.|Une valeur supérieure à 0xFFFF retourne NULL au lieu du substitut correspondant.|  
|[UNICODE](/sql/t-sql/functions/unicode-transact-sql)|Retourne un codepoint UTF-16 dans la plage 0 à 0x10FFFF.|Retourne un codepoint UCS-2 dans la plage 0 à 0xFFFF.|  
|[Recherche de correspondance d’un seul caractère générique](/sql/t-sql/language-elements/wildcard-match-one-character-transact-sql)<br /><br /> [Caractère générique - Caractères à ne pas faire correspondre](/sql/t-sql/language-elements/wildcard-character-s-not-to-match-transact-sql)|Les caractères supplémentaires sont pris en charge pour toutes les opérations génériques.|Les caractères supplémentaires ne sont pas pris en charge pour ces opérations génériques. D'autres opérateurs génériques sont pris en charge.|  
  
  
##  <a name="GB18030"></a>Prise en charge de GB18030  
 GB18030 est une norme distincte utilisée en République populaire de Chine pour l'encodage des caractères chinois. Dans la norme GB18030, les caractères peuvent être encodés sur 1, 2 ou 4 octets de longueur. Pour prendre en charge les caractères encodés selon la norme GB18030,[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les reconnaît lorsqu'ils entrent dans le serveur en provenance d'une application côté client, puis les convertit et les stocke en mode natif en tant que caractères Unicode. Une fois stockés dans le serveur, ils sont traités en tant que caractères Unicode dans toutes les opérations suivantes. Vous pouvez utiliser n'importe quel classement chinois, de préférence la version 100 la plus récente. Tous les classements de niveau _100 prennent en charge le tri linguistique avec les caractères GB18030. Si les données incluent des caractères supplémentaires (paires de substitution), vous pouvez utiliser les classements SC disponibles dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] pour améliorer la recherche et le tri.  
  
  
##  <a name="Complex_script"></a>Prise en charge des scripts complexes  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut prendre en charge l'entrée, le stockage, la modification et l'affichage de scripts complexes. Les scripts complexes sont les suivants :  
  
-   Scripts qui associent l'utilisation de textes écrits de droite à gauche et de gauche à droite, par exemple les textes écrits en arabe et en anglais.  
  
-   Scripts dont les caractères changent de forme en fonction de leur position ou lorsqu'ils sont associés à d'autres caractères, par exemple les caractères arabes, indiens et thaï.  
  
-   Les langues telles que le thaï nécessitent des dictionnaires internes pour la reconnaissance des mots, car ces derniers ne sont pas séparés.  
  
 Les applications de base de données qui interagissent avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doivent utiliser des contrôles qui prennent en charge les scripts complexes. Les contrôles Windows Form standard créés dans du code managé peuvent prendre en charge les scripts complexes.  
  
  
##  <a name="Related_Tasks"></a> Tâches associées  
  
|Tâche|Rubrique|  
|----------|-----------|  
|Explique comment définir ou modifier le classement de l'instance de SQL Server.|[Définir ou modifier le classement du serveur](set-or-change-the-server-collation.md)|  
|Explique comment définir ou modifier le classement d'une base de données utilisateur.|[Définir ou modifier le classement de la base de données](set-or-change-the-database-collation.md)|  
|Explique comment définir ou modifier le classement d'une colonne dans la base de données.|[Définir ou modifier le classement des colonnes](set-or-change-the-column-collation.md)|  
|Explique comment retourner des informations de classement au niveau du serveur, de la base de données ou de la colonne.|[Afficher des informations de classement](view-collation-information.md)|  
|Explique comment écrire des instructions Transact-SQL qui sont plus portables d'un langage à un autre ou qui prennent en charge plusieurs langues plus facilement.|[Rédiger des instructions Transact-SQL internationales](write-international-transact-sql-statements.md)|  
|Explique comment modifier la langue des messages d'erreur et des paramètres relatifs à l'utilisation et l'affichage de la date, de l'heure et des devises.|[Définir une langue de session](set-a-session-language.md)|  
  
  
##  <a name="Related_Content"></a> Contenu associé  
 [SQL Server Best Practices Collation Change (Bonnes pratiques relatives au changement de classement dans SQL Server)](https://go.microsoft.com/fwlink/?LinkId=113891)  
  
 [« SQL Server les meilleures pratiques en matière de migration vers Unicode »](https://go.microsoft.com/fwlink/?LinkId=113890)  
  
 [Site Web du consortium Unicode](https://go.microsoft.com/fwlink/?LinkId=48619)  
  
## <a name="see-also"></a>Voir aussi  
 [Classements de base de données autonome](../databases/contained-database-collations.md)   
 [Choisir une langue lors de la création d’un index de recherche en texte intégral](../search/choose-a-language-when-creating-a-full-text-index.md)   
 [sys.fn_helpcollations (Transact-SQL)](https://msdn.microsoft.com/library/ms187963(SQL.130).aspx)  
  
  
