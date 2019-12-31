---
title: Chargeur de ligne de commande dwloader
description: dwloader est un outil de ligne de commande PDW (Parallel Data Warehouse) qui charge des lignes de table en bloc dans une table existante.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 8ea941e45f5125beed0820c5d5242b0f86073f76
ms.sourcegitcommit: d587a141351e59782c31229bccaa0bff2e869580
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74401175"
---
# <a name="dwloader-command-line-loader-for-parallel-data-warehouse"></a>Chargeur de ligne de commande dwloader pour les Data Warehouse parallèles
**dwloader** est un outil de ligne de commande PDW (Parallel Data Warehouse) qui charge des lignes de table en bloc dans une table existante. Lors du chargement de lignes, vous pouvez ajouter toutes les lignes à la fin de la table (mode*Append* ou *mode fastappend*), ajouter de nouvelles lignes et mettre à jour les lignes existantes (*mode upsert*), ou supprimer toutes les lignes existantes avant le chargement, puis insérer toutes les lignes dans une table vide (*mode de rechargement*).  
  
**Processus de chargement des données**  
  
1.  Préparer les données source.  
  
    Utilisez votre propre processus ETL pour créer les données sources que vous souhaitez charger. Les données sources doivent être mises en forme pour correspondre au schéma de la table de destination. Stockez les données sources dans un ou plusieurs fichiers texte et copiez les fichiers texte dans le même répertoire sur votre serveur de chargement. Pour plus d’informations sur le serveur de chargement, consultez [acquérir et configurer un serveur de chargement](acquire-and-configure-loading-server.md)  
  
2.  Préparez les options de chargement.  
  
    Choisissez les options de chargement que vous allez utiliser. Stockez les options de chargement dans un fichier de configuration. Copiez le fichier de configuration dans un emplacement local sur votre serveur de chargement. Les options de configuration de **dwloader** sont décrites dans cette rubrique.  
  
3.  Préparez les options d’échec de chargement.  
  
    Décidez comment vous souhaitez que **dwloader** gère les lignes dont le chargement a échoué. Pour effectuer la charge, **dwloader** charge d’abord les données dans une table de mise en lots, puis transfère les données vers la table de destination. Au fur et à mesure que le chargeur charge des données dans la table de mise en lots, il effectue le suivi du nombre de lignes dont le chargement a échoué. Par exemple, le chargement des lignes qui ne sont pas mises en forme correctement échoue. Les lignes ayant échoué sont copiées dans un fichier de rejet. Par défaut, le chargement est abandonné après le premier rejet, sauf si vous spécifiez un autre seuil de rejet.  
  
4.  Installez **dwloader**.  
  
    Installez dwloader sur le serveur de chargement s’il n’est pas déjà installé. 

<!-- MISSING LINK
    See [Install dwloader Command-Line Loader &#40;SQL Server PDW&#41;](install-dwloader-command-line-loader-sql-server-pdw.md). 
--> 
  
5.  Exécutez **dwloader**.  
  
    Connectez-vous au serveur de chargement et exécutez le fichier exécutable **dwloader. exe** avec les options de ligne de commande appropriées.  
  
6.  Vérifiez les résultats.  
  
    Vous pouvez vérifier le fichier de lignes ayant échoué (spécifié avec-R) pour voir si des lignes n’ont pas pu être chargées. Si ce fichier est vide, toutes les lignes ont été chargées avec succès. **dwloader** étant transactionnel, si une étape échoue (à l’exception des lignes rejetées), toutes les étapes sont restaurées à leur état initial.  
  
<!-- 
![Topic link icon](media/topic-link.gif "Topic_Link")[Syntax Conventions](syntax-conventions-sql-server-pdw.md)  
-->  


## <a name="syntax"></a>Syntaxe  
  
```  
dwloader.exe { -h }  
  
dwloader.exe   
    {  
        { -U login_name  -P password  }  
        | -W  
    }  
    [ -f parameter_file ]  
    [ -S target_appliance ]  
    { -T target_database_name . [ schema ] . table_name }   
    { -i source_data_location } [ <source_data_options> ]  
    { -R load_failure_file_name } [ <load_failure_options> ]  
    [ <loading_options> ]  
}  
  
<source_data_options> ::=  
{  
    [ -fh number_header_rows ]  
    [ < variable_length_column_options > | < fixed_width_column_options > ]  
    [ -D { mdy | myd | ymd | ydm | dmy | dym | custom_date_format } ]  
    [ -dt datetime_format_file ]  
}  
  
<variable_length_column_options> ::=  
{  
    [ -e character_encoding ]  
    -r row_delimiter   
    [ -s string_delimiter ]  
    -t field_delimiter   
}  
  
<fixed_width_column_options> ::=  
{  
    -w fixed_width_config_file   
    [ -e character_encoding ]   
    -r row_delimiter   
}  
  
<load_failure_options> ::=  
{  
    [ -rt { value | percentage } ]  
    [ -rv reject_value ]  
    [ -rs reject_sample_value ]  
}  
  
<loading_options> ::=  
{  
    [ -d staging_database_name ]  
    [ -M { append | fastappend | upsert -K merge_column [ ,...n ] | reload } ]  
    [ -b batchsize ]   
    [ -c ]  
    [ -E ]  
    [ -m ]  
    [ -N ]  
    [ -se ]
    [ -l ]   
}  
```  
  
## <a name="arguments"></a>Arguments  
**-h**  
Affiche des informations d’aide simples sur l’utilisation du chargeur. L’aide s’affiche uniquement si aucun autre paramètre de ligne de commande n’est spécifié.  
  
**-U** *login_name*  
Une connexion d’authentification SQL Server valide avec les autorisations appropriées pour effectuer la charge.  
  
**-P** *mot de passe*  
Mot de passe d’une *Login_name*d’authentification SQL Server.  
  
**-W**  
Utiliser l'authentification Windows. (Aucun *login_name* ou *mot de passe* requis.) 

<!-- MISSING LINK
For information about configuring Windows Authentication, see [Security - Configure Domain Trusts](security-configure-domain-trusts.md).  
-->
  
**-f** *parameter_file_name*  
Utilisez un fichier de paramètres, *parameter_file_name*, à la place des paramètres de ligne de commande. *parameter_file_name* peut contenir n’importe quel paramètre de ligne de commande, à l’exception de *user_name* et du *mot de passe*. Si un paramètre est spécifié sur la ligne de commande et dans le fichier de paramètres, la ligne de commande remplace le paramètre de fichier.  
  
Le fichier de paramètres contient un paramètre, sans **-** le préfixe, par ligne.  
  
Exemples :  
  
`rt=percentage`  
  
`rv=25`  
  
**-S** *target_appliance*  
Spécifie le SQL Server PDW appliance qui recevra les données chargées.  
  
*Pour les connexions Infiniband*, *target_appliance* est spécifié comme <nom-appareil>-SQLCTL01. Pour configurer cette connexion nommée, consultez [configurer des cartes réseau InfiniBand](configure-infiniband-network-adapters.md).  
  
Pour les connexions Ethernet, *target_appliance* est l’adresse IP du cluster de nœuds de contrôle.  
  
En cas d’omission, la valeur par défaut de dwloader est celle qui a été spécifiée lors de l’installation de dwloader. 

<!-- MISSING LINK
For more information about this install option, see [Install dwloader Command-Line Loader](install-dwloader.md).  
-->
  
**-T** *target_database_name.* [*schéma*]. *table_name*  
Nom en trois parties pour la table de destination.  
  
**-I** *source_data_location*  
Emplacement d’un ou plusieurs fichiers sources à charger. Chaque fichier source doit être un fichier texte ou un fichier texte compressé avec gzip. Un seul fichier source peut être compressé dans chaque fichier gzip.  
  
Pour mettre en forme un fichier source :  
  
-   Le fichier source doit être mis en forme conformément aux options de chargement.  
  
-   Chaque ligne d’un fichier source contient les données d’une ligne de table. Les données sources doivent correspondre au schéma de la table de destination. L’ordre des colonnes et les types de données doivent également correspondre. Chaque champ de la ligne représente une colonne dans la table de destination.  
  
-   Par défaut, les champs sont de longueur variable et séparés par un délimiteur. Pour spécifier le type de délimiteur, utilisez les options de ligne de commande <variable_length_column_options>. Pour spécifier des champs de longueur fixe, utilisez les options de ligne de commande <fixed_width_column_options>.  
  
Pour spécifier l’emplacement des données sources :  
  
-   L’emplacement des données sources peut être un chemin d’accès réseau ou un chemin d’accès local à un répertoire sur le serveur de chargement.  
  
-   Pour spécifier tous les fichiers d’un répertoire, entrez le chemin d’accès du répertoire suivi du caractère générique *.  Le chargeur ne charge pas les fichiers de tous les sous-répertoires qui se trouvent dans l’emplacement des données sources. Le chargeur est erroné lorsqu’un répertoire existe dans un fichier gzip.  
  
-   Pour spécifier certains des fichiers dans un répertoire, utilisez une combinaison de caractères et le caractère générique *.  
  
Pour charger plusieurs fichiers à l’aide d’une commande :  
  
-   Tous les fichiers doivent se trouver dans le même répertoire.  
  
-   Les fichiers doivent être tous des fichiers texte, tous les fichiers gzip ou une combinaison de fichiers texte et gzip.  
  
-   Aucun des fichiers ne peut contenir d’informations d’en-tête.  
  
-   Tous les fichiers doivent utiliser le même type d’encodage de caractères. Consultez l’option-e.  
  
-   Tous les fichiers doivent être chargés dans la même table.  
  
-   Tous les fichiers sont concaténés et chargés comme s’il s’agissait d’un seul fichier, et les lignes rejetées sont dirigées vers un seul fichier rejeté.  
  
Exemples :  
  
-   -i \\\loadserver\loads\daily\\*. gz  
  
-   -i \\\loadserver\loads\daily\\*. txt  
  
-   -i \\\loadserver\loads\daily\monday. *  
  
-   -i \\\loadserver\loads\daily\monday.txt  
  
-   -i \\\loadserver\loads\daily\\*  
  
**-R** *load_failure_file_name*  
En cas d’échec de chargement, **dwloader** stocke la ligne qui n’a pas pu être chargée et la description de l’erreur les informations d’échec dans un fichier nommé *load_failure_file_name*. Si ce fichier existe déjà, dwloader remplacera le fichier existant. *load_failure_file_name* est créé lorsque le premier échec se produit. Si toutes les lignes sont chargées avec succès, *load_failure_file_name* n’est pas créé.  
  
**-fh** *number_header_rows*  
Nombre de lignes (lignes) à ignorer au début de *source_data_file_name*. La valeur par défaut est 0.  
  
<variable_length_column_options>  
Les options d’une *source_data_file_name* qui contient des colonnes de longueur variable délimitées par des caractères. Par défaut, *source_data_file_name* contient des caractères ASCII dans des colonnes de longueur variable.  
  
Pour les fichiers ASCII, les valeurs NULL sont représentées en plaçant les délimiteurs de manière consécutive. Par exemple, dans un fichier délimité par des barres verticales (« | »), une valeur NULL est indiquée par « | | ». Dans un fichier délimité par des virgules, la valeur NULL est indiquée par « ,, ». En outre, l’option **-E** (--emptyStringAsNull) doit être spécifiée. Pour plus d’informations sur-E, voir ci-dessous.  
  
**-e** *character_encoding*  
Spécifie un type d’encodage de caractères pour les données à charger à partir du fichier de données. Les options sont ASCII (valeur par défaut), UTF8, UTF16 ou UTF16BE, où UTF16 est Little endian et UTF16BE est Big endian. Ces options ne respectent pas la casse.  
  
**-t** *field_delimiter*  
Délimiteur pour chaque champ (colonne) dans la ligne. Le délimiteur de champ est un ou plusieurs de ces caractères d’échappement ASCII ou des valeurs hexadécimales ASCII.  
  
|Name|Caractère d'échappement|Caractère hexadécimal|  
|--------|--------------------|-----------------|  
|Tab|\t|0x09|  
|Retour chariot (CR)|\r|0x0D|  
|Saut de ligne (LF)|\n|0x0A|  
|CRLF|\r\n|0x0d0x0a|  
|Comma|','|0x2c|  
|Guillemet double|\\"|0x22|  
|Guillemet simple|\\'|0x27|  
  
Pour spécifier le caractère de barre verticale sur la ligne de commande, placez-le entre guillemets doubles, "|". Cela permet d’éviter une mauvaise interprétation par l’analyseur de ligne de commande. Les autres caractères sont encadrés par des guillemets simples.  
  
Exemples :  
  
-t "|"  
  
-t' '  
  
-t 0x0A  
  
-t \t  
  
-t' ~ | ~ '  
  
**-r** *row_delimiter*  
Délimiteur pour chaque ligne du fichier de données source. Le séparateur de lignes est une ou plusieurs valeurs ASCII.  
  
Pour spécifier un retour chariot (CR), un saut de ligne (LF) ou un caractère de tabulation comme délimiteur, vous pouvez utiliser les caractères d’échappement (\r, \n, \t) ou leurs valeurs hexadécimales (0x, 0d, 09). Pour spécifier d’autres caractères spéciaux en tant que délimiteurs, utilisez leur valeur hexadécimale.  
  
Exemples de CR + LF :  
  
-r \r\n  
  
-r 0x0d0x0a  
  
Exemples de CR :  
  
-r \r  
  
-r 0x0D  
  
Exemples de LF :  
  
-r \n  
  
-r 0x0A  
  
Un LF est requis pour UNIX. Un CR est requis pour Windows.  
  
**-s** *string_delimiter*  
Délimiteur du champ de type de données String d’un fichier d’entrée délimité par du texte. Le délimiteur de chaîne correspond à une ou plusieurs valeurs ASCII.  Il peut être spécifié sous la forme d’un caractère (par exemple,-s *) ou en tant que valeur hexadécimale (par exemple-s 0X22 pour un guillemet double).  
  
Exemples :  
  
x  
  
-s 0X22  
  
< fixed_width_column_options>  
Options d’un fichier de données source contenant des colonnes de longueur fixe. Par défaut, *source_data_file_name* contient des caractères ASCII dans des colonnes de longueur variable.  
  
Les colonnes à largeur fixe ne sont pas prises en charge lorsque-e est UTF8.  
  
**-w** *fixed_width_config_file*  
Chemin d’accès et nom du fichier de configuration qui spécifie le nombre de caractères dans chaque colonne. Chaque champ doit être spécifié.  
  
Ce fichier doit résider sur le serveur de chargement. Le chemin d’accès peut être un chemin d’accès UNC, relatif ou absolu. Chaque ligne de *fixed_width_config_file* contient le nom d’une colonne et le nombre de caractères de cette colonne. Il y a une ligne par colonne, comme suit, et l’ordre dans le fichier doit correspondre à l’ordre dans la table de destination :  
  
*column_name*=*num_chars*  
  
*column_name*=*num_chars*  
  
Exemple de fichier de configuration de largeur fixe :  
  
SalesCode = 3  
  
SalesID = 10  
  
Exemples de lignes dans *source_data_file_name*:  
  
230Shirts0056  
  
320Towels1356  
  
Dans l’exemple précédent, la première ligne chargée aura SalesCode = ' 230 'et SalesID = 'Shirts0056 '. La deuxième ligne chargée aura SalesCode = ' 320 'et SaleID = 'Towels1356 '.  
  
Pour plus d’informations sur la façon de gérer les espaces de début et de fin ou la conversion de type de données en mode de largeur fixe, consultez [règles de conversion de types de données pour dwloader](dwloader-data-type-conversion-rules.md).  
  
**-e** *character_encoding*  
Spécifie un type d’encodage de caractères pour les données à charger à partir du fichier de données. Les options sont ASCII (valeur par défaut), UTF8, UTF16 ou UTF16BE, où UTF16 est Little endian et UTF16BE est Big endian. Ces options ne respectent pas la casse.  
  
Les colonnes à largeur fixe ne sont pas prises en charge lorsque-e est UTF8.  
  
**-r** *row_delimiter*  
Délimiteur pour chaque ligne du fichier de données source. Le séparateur de lignes est une ou plusieurs valeurs ASCII.  
  
Pour spécifier un retour chariot (CR), un saut de ligne (LF) ou un caractère de tabulation comme délimiteur, vous pouvez utiliser les caractères d’échappement (\r, \n, \t) ou leurs valeurs hexadécimales (0x, 0d, 09). Pour spécifier d’autres caractères spéciaux en tant que délimiteurs, utilisez leur valeur hexadécimale.  
  
Exemples de CR + LF :  
  
-r \r\n  
  
-r 0x0d0x0a  
  
Exemples de CR :  
  
-r \r  
  
-r 0x0D  
  
Exemples de LF :  
  
-r \n  
  
-r 0x0A  
  
Un LF est requis pour UNIX. Un CR est requis pour Windows.  
  
**-D** { **AMJ** | ydm | mja | MYD |  DMY | DYM | *custom_date_format* }  
Spécifie l’ordre du mois (m), du jour (d) et de l’année (y) pour tous les champs DateTime du fichier d’entrée. L’ordre par défaut est AMJ. Pour spécifier plusieurs formats de commande pour le même fichier source, utilisez l’option-DT.  
  
AMJ | DMY  
ydm et DMY autorisent les mêmes formats d’entrée. Tous deux autorisent l’année à se trouver au début ou à la fin de la date. Par exemple, pour les formats de date **ydm** et **DMY** , vous pouvez avoir 2013-02-03 ou 02-03-2013 dans le fichier d’entrée.  
  
ydm  
Vous pouvez uniquement charger l’entrée mise en forme en tant que ydm dans les colonnes de type de données DateTime et smalldatetime. Vous ne pouvez pas charger les valeurs ydm dans une colonne du type de données datetime2, date ou DateTimeOffset.  
  
mdy  
<month> <space> <day>mja autorise <comma>. <year>  
  
Exemples de données d’entrée mja pour le 1er janvier 1975 :  
  
-   1er janvier 1975  
  
-   1er janvier 75  
  
-   Jan/1/75  
  
-   01011975  
  
maj  
Exemples de fichiers d’entrée pour le 04 mars 2010:03-2010-04, 3/2010/4  
  
jam  
Exemples de fichiers d’entrée pour le 04 mars 2010:04-2010-03, 4/2010/3  
  
*custom_date_format*  
*custom_date_format* est un format de date personnalisé (par exemple, mm/jj/aaaa) et inclus à des fins de compatibilité descendante uniquement. dwloader n’applique pas le format de date personnalisé. Au lieu de cela, lorsque vous spécifiez un format de date personnalisé, **dwloader** le convertit en paramètre correspondant AMJ, YDM, mja, MYD, Dym ou DMY.  
  
Par exemple, si vous spécifiez-D MM/JJ/AAAA, dwloader s’attend à ce que toutes les entrées de date soient triées avec le mois en premier, puis le jour, puis l’année (mja). Elle n’applique pas deux mois de 2 caractères, des jours à 2 chiffres et des années à 4 chiffres, comme spécifié par le format de date personnalisé. Voici quelques exemples de formats de dates pouvant être mis en forme dans le fichier d’entrée lorsque le format de date est-D MM/JJ/AAAA : 01/02/2013, Jan. 02.2013, 1/2/2013  
  
Pour obtenir des informations de mise en forme plus complètes, consultez [règles de conversion de types de données pour dwloader](dwloader-data-type-conversion-rules.md).  
  
**-dt** *datetime_format_file*  
Chaque format DateTime est spécifié dans un fichier nommé *datetime_format_file*. Contrairement aux paramètres de ligne de commande, les paramètres de fichier qui incluent des espaces ne doivent pas être placés entre guillemets doubles. Vous ne pouvez pas modifier le format DateTime lorsque vous chargez des données. Le fichier de données source et la colonne correspondante dans la table de destination doivent avoir le même format.  
  
Chaque ligne contient le nom d’une colonne dans la table de destination et son format DateTime.  
  
Exemples :  
  
`LastReceiptDate=ymd`  
  
`ModifiedDate=dym`  
  
**-d** *staging_database_name*  
Nom de la base de données qui contiendra la table de mise en lots. La valeur par défaut est la base de données spécifiée avec l’option-T, qui est la base de données de la table de destination. Pour plus d’informations sur l’utilisation d’une base de données de mise en lots, consultez [créer la base de données intermédiaire](staging-database.md).  
  
**-M** *load_mode_option*  
Spécifie s’il faut ajouter, upsert ou recharger des données. Le mode par défaut est Append.  
  
append  
Le chargeur insère des lignes à la fin des lignes existantes dans la table de destination.  
  
fastappend  
Le chargeur insère les lignes directement, sans utiliser de table temporaire, à la fin des lignes existantes dans la table de destination. fastappend nécessite l’option multi-transaction (-m). Une base de données intermédiaire ne peut pas être spécifiée lors de l’utilisation de fastappend. Il n’existe pas de restauration avec fastappend, ce qui signifie que la récupération à partir d’un échec ou d’une charge abandonnée doit être gérée par votre propre processus de chargement.  
  
upsert **-K**  *merge_column* [,...*n* ]    
Le chargeur utilise l’instruction SQL Server Merge pour mettre à jour les lignes existantes et insérer de nouvelles lignes.  
  
L’option-K spécifie la ou les colonnes sur lesquelles baser la fusion. Ces colonnes forment une clé de fusion, qui doit représenter une ligne unique. Si la clé de fusion existe dans la table de destination, la ligne est mise à jour. Si la clé de fusion n’existe pas dans la table de destination, la ligne est ajoutée.  
  
Pour les tables distribuées par hachage, la clé de fusion doit être ou inclure la colonne de distribution.  
  
Pour les tables répliquées, la clé de fusion est la combinaison d’une ou de plusieurs colonnes. Ces colonnes sont spécifiées en fonction des besoins de l’application.  
  
Plusieurs colonnes doivent être séparées par des virgules, sans espaces, ou séparées par des virgules par des espaces et placées entre guillemets simples.  
  
Si deux lignes de la table source ont des valeurs de clé de fusion correspondantes, leurs lignes respectives doivent être identiques.  
  
recharger  
Le chargeur tronque la table de destination avant d’insérer les données sources.  
  
**-b** *BatchSize*  
Recommandé uniquement pour une utilisation par Support Microsoft, *BatchSize* est la taille de lot SQL Server pour la copie en bloc effectuée par DMS dans SQL Server instances sur les nœuds de calcul.  Quand la valeur *BatchSize* est spécifiée, SQL Server PDW remplace la taille de chargement par lot qui est calculée de manière dynamique pour chaque charge.  
  
À partir de SQL Server 2012 PDW, le nœud de contrôle calcule dynamiquement une taille de lot pour chaque charge par défaut. Ce calcul automatique est basé sur plusieurs paramètres tels que la taille de la mémoire, le type de la table cible, le schéma de la table cible, le type de charge, la taille du fichier et la classe de ressources de l’utilisateur.  
  
Par exemple, si le mode de chargement est FASTAPPEND et que la table a un index ColumnStore cluster, SQL Server PDW tente par défaut d’utiliser une taille de lot de 1 048 576 afin que RowGroups soit fermé et chargé directement dans le ColumnStore sans passer par le magasin Delta. Si la mémoire n’autorise pas la taille de lot de 1 048 576, dwloader choisit une plus petite BatchSize.  
  
Si le type de charge est FASTAPPEND, la valeur *BatchSize* s’applique au chargement des données dans la table, sinon la méthode *BatchSize* s’applique au chargement des données dans la table de mise en lots.  
  
<reject_options>  
Spécifie les options permettant de déterminer le nombre d’échecs de chargement autorisés par le chargeur. Si les échecs de chargement dépassent le seuil, le chargeur s’arrêtera et ne validera aucune ligne.  
  
**-RT** { **valeur** | pourcentage}  
Spécifie si le*reject_value* dans l’option **-RV** *reject_value* est un nombre littéral de lignes (valeur) ou un taux d’échec (pourcentage). La valeur par défaut est la valeur.  
  
L’option pourcentage est un calcul en temps réel qui se produit à des intervalles en fonction de l’option-RS.  
  
Par exemple, si le chargeur tente de charger 100 lignes et que 25 échouent et 75 réussissent, le taux d’échec est de 25%.  
  
**-rv** *reject_value*  
Spécifie le nombre ou le pourcentage de rejets de ligne à autoriser avant l’arrêt du chargement. L’option **-RT** détermine si *reject_value* fait référence au nombre de lignes ou au pourcentage de lignes.  
  
La *reject_value* par défaut est 0.  
  
Lorsqu’il est utilisé avec la valeur-RT, le chargeur arrête le chargement lorsque le nombre de lignes rejetées dépasse reject_value.  
  
En cas d’utilisation avec le pourcentage-RT, le chargeur calcule le pourcentage aux intervalles (option-RS). Par conséquent, le pourcentage de lignes ayant échoué peut dépasser *reject_value*.  
  
**-rs** *reject_sample_size*  
Utilisé avec l' `-rt percentage` option pour spécifier les vérifications de pourcentage incrémentiel. Par exemple, si reject_sample_size est 1000, le chargeur calcule le pourcentage de lignes ayant échoué après avoir tenté de charger 1000 lignes. Il recalcule le pourcentage de lignes ayant échoué après avoir tenté de charger chaque 1000 lignes supplémentaires.  
  
**-c**  
Supprime les espaces blancs à gauche et à droite des champs char, nchar, varchar et nvarchar. Convertit chaque champ qui contient uniquement des espaces blancs en chaîne vide.  
  
Exemples :  
  
' 'est tronqué en' '  
  
« ABC » est tronqué à « ABC »  
  
Lorsque-c est utilisé avec-E, l’opération-E se produit en premier. Les champs qui contiennent uniquement des espaces blancs sont convertis en chaîne vide et non NULL.  
  
**-E**  
Convertit des chaînes vides en valeurs NULL. La valeur par défaut est de ne pas effectuer ces conversions.  
  
**-m**  
Utilisez le mode multi-transaction pour la deuxième phase de chargement ; lors du chargement de données à partir de la table de mise en lots dans une table distribuée.  
  
Avec **-m**, SQL Server PDW effectue et valide les charges en parallèle. Cela s’effectue beaucoup plus rapidement que le mode de chargement par défaut, mais n’est pas sécurisé pour les transactions.  
  
Sans **-m**, SQL Server PDW effectue et valide les chargements en série sur les distributions au sein de chaque nœud de calcul, et simultanément sur les nœuds de calcul. Cette méthode est plus lente que le mode multi-transaction, mais elle est sécurisée pour les transactions.  
  
**-m** est facultatif pour *Append*, *Reload*et *upsert*.  
  
**-m** est requis pour fastappend.  
  
**-m** ne peut pas être utilisé avec des tables répliquées.  
  
**-m** s’applique uniquement à la deuxième phase de chargement. Elle ne s’applique pas à la première phase de chargement ; chargement de données dans la table de mise en lots.  
  
Il n’existe pas de restauration avec mode multi-transaction, ce qui signifie que la récupération à partir d’un échec ou d’une charge abandonnée doit être gérée par votre propre processus de chargement.  
  
Nous vous recommandons d’utiliser **-m** uniquement lors du chargement dans une table vide afin de pouvoir effectuer une récupération sans perte de données. Pour récupérer suite à un échec de chargement : supprimez la table de destination, résolvez le problème de chargement, recréez la table de destination, puis réexécutez le chargement.  
  
**-N**  
Vérifiez que l’appliance cible dispose d’un certificat de SQL Server PDW valide d’une autorité de confiance. Utilisez-le pour vous assurer que vos données ne sont pas détournées par une personne malveillante et envoyées à un emplacement non autorisé. Le certificat doit déjà être installé sur l’appliance. La seule méthode prise en charge pour installer le certificat est que l’administrateur de l’appliance l’installe à l’aide de l’outil Configuration Manager. Demandez à l’administrateur de votre appareil si vous n’êtes pas sûr qu’un certificat approuvé est installé sur l’appareil.  
  
**-se**  
Ignorer le chargement des fichiers vides. Cela ignore également la décompression des fichiers gzip vides.

**-l**  
Disponible avec la mise à jour CU 7.4, spécifie la longueur maximale de ligne (en octets) pouvant être chargée. Les valeurs valides sont des entiers compris entre 32768 et 33554432. Utilisez uniquement lorsque cela est nécessaire pour charger des lignes volumineuses (supérieures à 32KO), car cela allouera plus de mémoire sur le client et le serveur.
  
## <a name="return-code-values"></a>Codet de retour  
0 (succès) ou autre valeur entière (échec)  
  
Dans une fenêtre de commande ou un fichier de `errorlevel` commandes, utilisez pour afficher le code de retour. Par exemple :  
  
```  
dwloader  
echo ReturnCode=%errorlevel%  
if not %errorlevel%==0 echo Fail  
if %errorlevel%==0 echo Success  
```  
  
Lorsque vous utilisez PowerShell, `$LastExitCode`utilisez.  
  
## <a name="permissions"></a>Autorisations  
Nécessite l’autorisation de chargement et les autorisations applicables (insertion, mise à jour, suppression) sur la table de destination. Nécessite l’autorisation CREATe (pour créer une table temporaire) sur la base de données de mise en lots. Si aucune base de données de mise en lots n’est utilisée, l’autorisation créer est requise sur la base de données de destination. 

<!-- MISSING LINK
For more information, see [Grant permissions to load data](grant-permissions-to-load-data.md).  
-->
  
## <a name="general-remarks"></a>Remarques d'ordre général  
Pour plus d’informations sur les conversions de types de données lors du chargement avec dwloader, consultez [règles de conversion de types de données pour dwloader](dwloader-data-type-conversion-rules.md).  
  
Si un paramètre comprend un ou plusieurs espaces, mettez-le entre guillemets doubles.  
  
Vous devez exécuter le chargeur à partir de son emplacement d’installation. L’exécutable dwloader est préinstallé avec l’appliance et se trouve dans le répertoire C:\Program Files\Microsoft SQL Server Data Warehouse\DWLoader  
  
Vous pouvez substituer un paramètre spécifié dans le fichier de paramètres (option-f) en le spécifiant en tant que paramètre de ligne de commande.  
  
Vous pouvez exécuter plusieurs instances du chargeur simultanément. Le nombre maximal d’instances de chargeur est préconfiguré et ne peut pas être modifié. 

<!-- MISSING LINK
For the maximum number of loads per appliance, see [Minimum and Maximum Values](minimum-maximum-values.md)  
-->
  
Les données chargées peuvent nécessiter plus ou moins d’espace sur l’appliance que dans l’emplacement source. Vous pouvez effectuer des importations de test avec des sous-ensembles de données pour estimer la consommation du disque.  
  
Bien que **dwloader** soit un processus de transaction et s’annule normalement en cas d’échec, il ne peut pas être restauré une fois que le chargement en masse a été effectué avec succès. Pour annuler un processus **dwloader** actif, tapez Ctrl + C.  
  
## <a name="limitations-and-restrictions"></a>Limitations et restrictions  
La taille totale de toutes les charges se produisant simultanément doit être inférieure à LOG_SIZE pour la base de données, et nous recommandons que la taille totale de toutes les charges simultanées soit inférieure à 50% du LOG_SIZE. Pour atteindre cette limite de taille, vous pouvez fractionner des charges importantes en plusieurs lots. Pour plus d’informations sur les LOG_SIZE, consultez [Create Database](../t-sql/statements/create-database-parallel-data-warehouse.md) .  
  
Lors du chargement de plusieurs fichiers à l’aide d’une commande de chargement, toutes les lignes rejetées sont écrites dans le même fichier de rejet. Le fichier rejeté n’indique pas quel fichier d’entrée contient chaque ligne rejetée.  
  
La chaîne vide ne doit pas être utilisée comme délimiteur. Lorsqu’une chaîne vide est utilisée comme délimiteur de ligne, le chargement échoue. Lorsqu’il est utilisé comme délimiteur de colonne, le chargement ignore le délimiteur et continue à utiliser la valeur par défaut « | » comme délimiteur de colonne. Lorsqu’elle est utilisée comme délimiteur de chaîne, la chaîne vide est ignorée et le comportement par défaut est appliqué.  
  
## <a name="locking-behavior"></a>Comportement de verrouillage  
le comportement de verrouillage **dwloader** varie en fonction de la *load_mode_option*.  
  
-   **Append** -Append est l’option recommandée et la plus courante. Ajouter charge des données dans une table de mise en lots. Le verrouillage est décrit en détail ci-dessous.  
  
-   **Ajout rapide** : les chargements rapides sont chargés directement dans la table finale en prenant un verrou de table ExclusiveUpdate et est le seul mode qui n’utilise pas de table de mise en lots.  
  
-   **recharger** : le rechargement charge des données dans une table de mise en lots et requiert un verrou exclusif sur la table de mise en lots et la table finale. Le rechargement n’est pas recommandé pour les opérations simultanées.  
  
-   **upsert** -upsert charge des données dans une table de mise en lots, puis effectue une opération de fusion à partir de la table de mise en lots vers la table finale. Upsert ne nécessite pas de verrous exclusifs sur la table finale. Les performances peuvent varier en cas d’utilisation de upsert. Testez le comportement dans votre environnement.  
  
### <a name="locking-behavior"></a>Comportement de verrouillage  
**Verrouillage du mode d’ajout**  
  
Append peut être exécutée en mode multi-transactionnel (à l’aide de l’argument-m), mais elle n’est pas sécurisée pour les transactions. Par conséquent, Append doit être utilisé comme opération transactionnelle (sans utiliser l’argument-m). Malheureusement, au cours de l’opération de sélection d’insertion finale, le mode transactionnel est actuellement environ six fois plus lent que le mode multi-transactionnel.  
  
Le mode Append charge les données en deux phases. La phase 1 charge simultanément des données à partir du fichier source dans une table de mise en lots (une fragmentation peut se produire). La phase 2 charge les données de la table de mise en lots dans la table finale. La deuxième phase effectue une **insertion into... Sélectionnez avec l’opération (TABLOCK)** . Le tableau suivant montre le comportement de verrouillage sur la table finale et le comportement de journalisation lors de l’utilisation du mode Append :  
  
|Type de table|Plusieurs transactions<br />Mode (-m)|La table est vide|Accès concurrentiel pris en charge|Journalisation|  
|--------------|-----------------------------------|------------------|-------------------------|-----------|  
|Segment de mémoire|Oui|Oui|Oui|Minimales|  
|Segment de mémoire|Oui|Non|Oui|Minimales|  
|Segment de mémoire|Non|Oui|Non|Minimales|  
|Segment de mémoire|Non|Non|Non|Minimales|  
|CL|Oui|Oui|Non|Minimales|  
|CL|Oui|Non|Oui|Complet|  
|CL|Non|Oui|Non|Minimales|  
|CL|Non|Non|Oui|Complet|  
  
Le tableau ci-dessus affiche **dwloader** en utilisant le mode Append chargé dans un segment de mémoire ou une table d’index cluster (ci), avec ou sans l’indicateur multitransactionnel, et en chargeant dans une table vide ou une table non vide. Le comportement de verrouillage et de journalisation de chaque combinaison de charge est affiché dans le tableau. Par exemple, si vous chargez (2e) la phase avec le mode Append dans un index cluster sans mode multitransactionnel et dans une table vide, PDW crée un verrou exclusif sur la table et la journalisation est minimale. Cela signifie qu’un client ne sera pas en mesure de charger (2e) la phase et la requête simultanément dans une table vide. Toutefois, lors du chargement avec la même configuration dans une table non vide, PDW n’émet pas de verrou exclusif sur la table et l’accès concurrentiel est possible. Malheureusement, la journalisation complète se produit, ce qui ralentit le processus.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-simple-dwloader-example"></a>R. Exemple de dwloader simple  
L’exemple suivant illustre l’initiation du **chargeur** avec uniquement les options requises sélectionnées. D’autres options sont extraites du fichier de configuration global, *loadparamfile. txt*.  
  
Exemple utilisant l’authentification SQL Server.  
  
```  
--Load over Ethernet  
dwloader.exe -S 10.192.63.148 -U mylogin -P 123jkl -f /configfiles/loadparamfile.txt  
  
--Load over InfiniBand to appliance named MyPDW  
dwloader.exe -S MyPDW-SQLCTL01 -U mylogin -P 123jkl -f /configfiles/loadparamfile.txt  
```  
  
Le même exemple utilise l’authentification Windows.  
  
```  
--Load over Ethernet  
dwloader.exe -S 10.192.63.148 -W -f /configfiles/loadparamfile.txt  
  
--Load over InfiniBand to appliance named MyPDW  
dwloader.exe -S MyPDW-SQLCTL01 -W -f /configfiles/loadparamfile.txt  
```  
  
Exemple utilisant des arguments pour un fichier source et un fichier d’erreur.  
  
```  
--Load over Ethernet  
dwloader.exe -U mylogin -P 123jkl -S 10.192.63.148  -i C:\SQLData\AWDimEmployees.csv -T AdventureWorksPDW2012.dbo.DimEmployees -R C:\SQLData\LoadErrors  
```  
  
### <a name="b-load-data-into-an-adventureworks-table"></a>B. Charger des données dans une table AdventureWorks  
L’exemple suivant fait partie d’un script de commandes qui charge des données dans **AdventureWorksPDW2012**.  Pour afficher le script complet, ouvrez le fichier aw_create. bat fourni avec le package d’installation **AdventureWorksPDW2012** . 

<!-- Missing link
For more information, see [Install AdventureWorksPDW2012](install-adventureworkspdw2012.md).  
-->

L’extrait de script suivant utilise dwloader pour charger des données dans les tables DimAccount et DimCurrency. Ce script utilise une adresse Ethernet. S’il utilisait InfiniBand, le serveur *<appliance_name>* `-SQLCTL01`.  
  
```  
set server=10.193.63.134  
set user=<MyUser>  
set password=<MyPassword>  
  
set schema=AdventureWorksPDW2012.dbo  
set load="C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\dwloader.exe"  
set mode=reload  
  
--Loads data into the AdventureWorksPDW2012.dbo.DimAccount table  
--Source data is stored in the file DimAccount.txt,   
--which is in the current directory.  
  
set t1=DimAccount  
%load% -S %server% -E -M %mode% -e Utf16 -i .\%t1%.txt -T %schema%.%t1% -R %t1%.bad -t "|" -r \r\n -U %user% -P %password%   
  
--Loads data from the DimCurrency.txt file into  
--AdventureWorksPDW2012.dbo.DimCurrency  
set t1=DimCurrency  
%load% -S %server% -E -M %mode% -e Utf16 -i .\%t1%.txt -T %schema%.%t1% -R %t1%.bad -t "|" -r \r\n -U %user% -P %password%  
```  
  
Voici la DDL de la table DimAccount.  
  
```  
CREATE TABLE DimAccount(  
AccountKey int NOT NULL,  
ParentAccountKey int,  
AccountCodeAlternateKey int,  
ParentAccountCodeAlternateKey int,  
AccountDescription nvarchar(50),  
AccountType nvarchar(50),  
Operator nvarchar(50),  
CustomMembers nvarchar(300),  
ValueType nvarchar(50),  
CustomMemberOptions nvarchar(200))  
with (CLUSTERED INDEX(AccountKey),  
DISTRIBUTION = REPLICATE);  
```  
  
Voici un exemple de fichier de données, DimAccount. txt, qui contient les données à charger dans la table DimAccount.  
  
```  
--Sample of data in the DimAccount.txt load file.  
  
1||1||Balance Sheet||~||Currency|  
2|1|10|1|Assets|Assets|+||Currency|  
3|2|110|10|Current Assets|Assets|+||Currency|  
4|3|1110|110|Cash|Assets|+||Currency|  
5|3|1120|110|Receivables|Assets|+||Currency|  
6|5|1130|1120|Trade Receivables|Assets|+||Currency|  
7|5|1140|1120|Other Receivables|Assets|+||Currency|  
8|3|1150|110|Allowance for Bad Debt|Assets|+||Currency|  
9|3|1160|110|Inventory|Assets|+||Currency|  
10|9|1162|1160|Raw Materials|Assets|+||Currency|  
11|9|1164|1160|Work in Process|Assets|+||Currency|  
12|9|1166|1160|Finished Goods|Assets|+||Currency|  
13|3|1170|110|Deferred Taxes|Assets|+||Currency|  
```  
  
### <a name="c-load-data-from-the-command-line"></a>C. Charger des données à partir de la ligne de commande  
Le script de l’exemple B peut être remplacé en entrant tous les paramètres sur la ligne de commande, comme indiqué dans l’exemple suivant.  
  
```  
C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\dwloader.exe -S <Control node IP> -E -M reload -e UTF16 -i .\DimAccount.txt -T AdventureWorksPDW2012.dbo.DimAccount -R DimAccount.bad -t "|" -r \r\n -U <login> -P <password>  
```  
  
Description des paramètres de ligne de commande :  
  
-   *C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\dwloader.exe* est l’emplacement d’installation de dwloader. exe.  
  
-   *-S* est suivi de l’adresse IP du nœud de contrôle.  
  
-   *-E* spécifie de charger des chaînes vides en tant que valeurs NULL.  
  
-   *-M rechargement* spécifie de tronquer la table de destination avant d’insérer les données sources.  
  
-   *-e UTF16* indique que le fichier source utilise le type d’encodage de caractères primauté des octets de poids faible (Little endian).  
  
-   *-i .\DimAccount.txt* spécifie que les données se trouvent dans un fichier appelé DimAccount. txt, qui existe dans le répertoire actif.  
  
-   *-T AdventureWorksPDW2012. dbo. DimAccount* spécifie le nom en trois parties de la table pour recevoir les données.  
  
-   *-R DimAccount. Bad* spécifie que les lignes dont le chargement a échoué seront écrites dans un fichier appelé DimAccount. Bad.  
  
-   *-t "|"* indique que les champs du fichier d’entrée, DimAccount. txt, sont séparés par un caractère de barre verticale.  
  
-   *-r \r\n* spécifie chaque ligne dans DimAccount. txt se termine par un retour chariot et un caractère de saut de ligne.  
  
-   *-U <login_name>-P <password> * spécifie la connexion et le mot de passe de la connexion qui dispose des autorisations nécessaires pour effectuer la charge.  
  

<!-- MISSING LINK

## See Also  
[Common Metadata Query Examples](metadata-query-examples.md)  

-->
  
