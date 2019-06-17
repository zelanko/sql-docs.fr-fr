---
title: dwloader du chargeur de ligne de commande - Parallel Data Warehouse | Microsoft Docs
description: dwloader est un outil de ligne de commande de Parallel Data Warehouse (PDW) qui charge des lignes de la table en bloc dans une table existante.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: df30a9b849b987b5514a1824f25736a82587da09
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66175037"
---
# <a name="dwloader-command-line-loader-for-parallel-data-warehouse"></a>dwloader du chargeur de ligne de commande pour Parallel Data Warehouse
**dwloader** est un outil de ligne de commande Parallel Data Warehouse (PDW) qui charge des lignes de la table en bloc dans une table existante. Lors du chargement de lignes, vous pouvez ajouter toutes les lignes à la fin de la table (*mode append* ou *en mode fastappend*), ajoute de nouvelles lignes et mettre à jour des lignes existantes (*mode upsert*), ou supprimer toutes les lignes avant le chargement existantes et puis insérer toutes les lignes dans une table vide (*recharger mode*).  
  
**Processus de chargement des données**  
  
1.  Préparer la source de données.  
  
    Utilisez votre propre processus ETL pour créer les données source que vous voulez charger. La source de données doit être formaté pour correspondre au schéma de la table de destination. Store de la source de données dans un ou plusieurs fichiers texte et copiez les fichiers texte dans le même répertoire sur votre serveur de chargement. Pour plus d’informations sur le serveur de chargement, consultez [obtenir et configurer un serveur de chargement](acquire-and-configure-loading-server.md)  
  
2.  Préparez les options de chargement.  
  
    Décider des options de chargement que vous allez utiliser. Store les options de chargement dans un fichier de configuration. Copiez le fichier de configuration dans un emplacement local sur votre serveur de chargement. Le **dwloader** les options de configuration sont décrites dans cette rubrique.  
  
3.  Préparer la charge des options de défaillance.  
  
    Décidez comment vous **dwloader** pour gérer les lignes qui ne parviennent pas à charger. Pour effectuer le chargement, **dwloader** charge tout d’abord les données dans une table intermédiaire, puis transfère les données à la table de destination. Comme le chargeur charge des données dans la table intermédiaire, il suit le nombre de lignes qui ne parviennent pas à charger. Par exemple, les lignes qui ne sont pas formatés correctement échoue à charger. Lignes ayant échoué sont copiées vers un fichier de rejet. Par défaut, la charge est abandonnée après le rejet du premier, sauf si vous spécifiez un seuil de rejet différents.  
  
4.  Installer **dwloader**.  
  
    Installez dwloader sur le serveur de chargement s’il n’est pas déjà installé. 

<!-- MISSING LINK
    See [Install dwloader Command-Line Loader &#40;SQL Server PDW&#41;](install-dwloader-command-line-loader-sql-server-pdw.md). 
--> 
  
5.  Exécutez **dwloader**.  
  
    Connectez-vous au serveur lors du chargement et exécutez le fichier exécutable **dwloader.exe** avec les options de ligne de commande appropriées.  
  
6.  Vérifier les résultats.  
  
    Vous pouvez vérifier les lignes du fichier (spécifié avec -R) pour voir si toutes les lignes Échec du chargement. Si ce fichier est vide, toutes les lignes est chargé avec succès. **dwloader** est transactionnelle, donc si une étape échoue (autres que les lignes rejetées), toutes les étapes reviendra à son état initial.  
  
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
Affiche des informations d’aide simples sur l’utilisation du chargeur. Aide s’affiche uniquement si aucun autre paramètre de ligne de commande n’est spécifiés.  
  
**-U** *login_name*  
Une connexion de l’authentification SQL Server valide disposant des autorisations appropriées pour effectuer le chargement.  
  
**-P** *mot de passe*  
Le mot de passe pour une authentification SQL Server *login_name*.  
  
**-W**  
Utiliser l'authentification Windows. (Non *login_name* ou *mot de passe* requis.) 

<!-- MISSING LINK
For information about configuring Windows Authentication, see [Security - Configure Domain Trusts](security-configure-domain-trusts.md).  
-->
  
**-f** *parameter_file_name*  
Utiliser un fichier de paramètres, *parameter_file_name*, à la place des paramètres de ligne de commande. *parameter_file_name* peut contenir n’importe quel paramètre de ligne de commande à l’exception *user_name* et *mot de passe*. Si un paramètre est spécifié sur la ligne de commande et dans le fichier de paramètres, la ligne de commande remplace le paramètre de fichier.  
  
Le fichier de paramètres contient un paramètre, sans le **-** préfixe, par ligne.  
  
Exemples :  
  
`rt=percentage`  
  
`rv=25`  
  
* *-S***target_appliance*  
Spécifie l’appliance SQL Server PDW qui recevra les données chargées.  
  
*Pour les connexions Infiniband*, *target_appliance* est spécifié en tant que < appliance-name >-SQLCTL01. Pour configurer ce nommé connexion, consultez [configurer des cartes réseau InfiniBand](configure-infiniband-network-adapters.md).  
  
Pour les connexions Ethernet, *target_appliance* est l’adresse IP pour le cluster de nœud de contrôle.  
  
Si omis, dwloader par défaut la valeur qui a été spécifiée lors de l’installation de dwloader. 

<!-- MISSING LINK
For more information about this install option, see [Install dwloader Command-Line Loader](install-dwloader.md).  
-->
  
**-T** *target_database_name.* [*schema*].*table_name*  
Le nom en trois parties pour la table de destination.  
  
* *-I***source_data_location*  
L’emplacement d’un ou plusieurs fichiers source à charger. Chaque fichier source doit être un fichier texte ou un fichier texte qui est compressé avec gzip. Uniquement un fichier source peut être compressé dans chaque fichier gzip.  
  
Pour mettre en forme un fichier source :  
  
-   Le fichier source doit être formaté selon les options de chargement.  
  
-   Chaque ligne dans un fichier source contient les données de ligne d’une table. La source de données doit correspondre au schéma de la table de destination. Colonne ordre et types de données doivent également correspondre. Chaque champ dans la ligne représente une colonne dans la table de destination.  
  
-   Par défaut, les champs sont de longueur variable et séparant par un délimiteur. Pour spécifier le type de délimiteur, utilisez les options de ligne de commande < variable_length_column_options >. Pour spécifier les champs de longueur fixe, utilisez les options de ligne de commande < fixed_width_column_options >.  
  
Pour spécifier l’emplacement de source de données :  
  
-   L’emplacement de données source peut être un chemin d’accès réseau ou un chemin d’accès local vers un répertoire sur le serveur de chargement.  
  
-   Pour spécifier tous les fichiers dans un répertoire, entrez le chemin du répertoire suivi de la * caractère générique.  Le chargeur ne charge pas les fichiers à partir de tous les sous-répertoires qui se trouvent dans l’emplacement de source de données. Les erreurs lorsqu’un répertoire existe dans un fichier gzip du chargeur.  
  
-   Pour spécifier certains des fichiers dans un répertoire, utilisez une combinaison de caractères et le * générique.  
  
Pour charger plusieurs fichiers avec une seule commande :  
  
-   Tous les fichiers doivent exister dans le même répertoire.  
  
-   Les fichiers doivent être tous les fichiers texte, tous les fichiers gzip ou une combinaison de fichiers texte et gzip.  
  
-   Aucun des fichiers peut contenir des informations d’en-tête.  
  
-   Tous les fichiers doivent utiliser le même caractère de type d’encodage. Consultez l’option -e.  
  
-   Tous les fichiers doivent être chargées dans la même table.  
  
-   Tous les fichiers seront concaténés et chargées comme s’ils sont un seul fichier, et les lignes rejetées ira à un fichier unique de rejet.  
  
Exemples :  
  
-   i - \\\loadserver\loads\daily\\*.gz  
  
-   i - \\\loadserver\loads\daily\\*.txt  
  
-   i - \\\loadserver\loads\daily\monday.*  
  
-   -i \\\loadserver\loads\daily\monday.txt  
  
-   i - \\\loadserver\loads\daily\\*  
  
**-R** *load_failure_file_name*  
S’il existe des échecs de chargement, **dwloader** stocke la ligne qui a échoué à la charge et la description de l’échec, les informations de défaillance dans un fichier nommé *load_failure_file_name*. Si ce fichier existe déjà, dwloader remplace le fichier existant. *load_failure_file_name* est créé lorsque le premier échec se produit. Si toutes les lignes se chargement correctement, *load_failure_file_name* n’est pas créé.  
  
**-fh** *number_header_rows*  
Le nombre de lignes à ignorer au début de *source_data_file_name*. La valeur par défaut est 0.  
  
<variable_length_column_options>  
Les options pour un *source_data_file_name* qui est délimitée par des caractères des colonnes de longueur variable. Par défaut, *source_data_file_name* contient des caractères ASCII dans les colonnes de longueur variable.  
  
Pour des fichiers ASCII, les valeurs NULL sont représentées en plaçant les délimiteurs de manière consécutive. Par exemple, dans un fichier délimitée une barre verticale (« | »), une valeur NULL est indiquée par « || ». Dans un fichier délimité par des virgules, une valeur NULL est indiquée par «,, ». En outre, le **-E** (--emptyStringAsNull) option doit être spécifiée. Pour plus d’informations sur -E, voir ci-dessous.  
  
**-e** *character_encoding*  
Spécifie un type d’encodage de caractères pour les données à charger à partir du fichier de données. Les options sont ASCII (par défaut), UTF-8, UTF16 ou UTF16BE, où UTF16 est primauté des octets et UTF16BE big endian. Ces options respectent la casse.  
  
**-t** *field_delimiter*  
Le délimiteur pour chaque champ (colonne) dans la ligne. Le délimiteur de champ est un ou plusieurs de ces caractères d’échappement de ASCII ou les valeurs hexadécimales ASCII.  
  
|Nom|Caractère d’échappement|Caractère hexadécimal|  
|--------|--------------------|-----------------|  
|Onglet|\t|0x09|  
|Retour chariot (CR)|\r|0x0d|  
|Saut de ligne (LF)|\n|0x0a|  
|CRLF|\r\n|0x0d0x0a|  
|Virgule|','|0x2c|  
|guillemet double|\\"|0x22|  
|un guillemet simple|\\'|0x27|  
  
Pour spécifier le caractère barre verticale sur la ligne de commande, mettez-le entre guillemets doubles, « | ». Cela permet d’éviter toute interprétation erronée par l’Analyseur de ligne de commande. Autres caractères sont placées entre guillemets simples.  
  
Exemples :  
  
-t "|"  
  
-t ' '  
  
-t 0x0a  
  
-t \t  
  
-t '~|~'  
  
**-r** *row_delimiter*  
Le délimiteur pour chaque ligne du fichier de données source. Le séparateur de lignes est une ou plusieurs des valeurs ASCII.  
  
Pour spécifier un retour chariot (CR), un saut de ligne (LF) ou un caractère de tabulation comme un délimiteur, vous pouvez utiliser les caractères d’échappement (\r, \n, \t) ou leurs valeurs hexadécimales (0 x, 0D, 09). Pour spécifier d’autres caractères spéciaux en tant que délimiteurs, utilisez leur valeur hexadécimale.  
  
Exemples de retour chariot + saut de ligne :  
  
-r \r\n  
  
-r 0x0d0x0a  
  
Exemples de CR :  
  
-r \r  
  
-r 0x0d  
  
Exemples de saut de ligne :  
  
-r \n  
  
-r 0x0a  
  
Un saut de ligne est requis pour Unix. Une demande de modification est requis pour Windows.  
  
**-s** *string_delimiter*  
Le délimiteur pour les données de chaîne type de champ d’un fichier d’entrée de texte délimité. Le délimiteur de chaîne est une ou plusieurs des valeurs ASCII.  Il peut être spécifié comme un caractère (par exemple, -s *) ou comme une valeur hexadécimale (par exemple, -s 0 x 22 pour les guillemets doubles).  
  
Exemples :  
  
-s *  
  
s - 0 x 22  
  
< fixed_width_column_options>  
Les options pour un fichier de données source qui a des colonnes de longueur fixe. Par défaut, *source_data_file_name* contient des caractères ASCII dans les colonnes de longueur variable.  
  
Colonnes de largeur fixe ne sont pas pris en charge -e est UTF8.  
  
**-w** *fixed_width_config_file*  
Chemin d’accès et nom du fichier de configuration qui spécifie le nombre de caractères dans chaque colonne. Chaque champ doit être spécifié.  
  
Ce fichier doit résider sur le serveur de chargement. Le chemin d’accès peut être un chemin d’accès UNC, relatif ou absolu. Chaque ligne dans *fixed_width_config_file* contient le nom d’une colonne et le nombre de caractères pour cette colonne. Il existe une ligne par colonne, comme suit, et l’ordre dans le fichier doit correspondre à l’ordre dans la table de destination :  
  
*column_name*=*num_chars*  
  
*column_name*=*num_chars*  
  
Exemple de fichier de configuration de la largeur de correction :  
  
SalesCode=3  
  
SalesID=10  
  
Exemple de lignes dans *source_data_file_name*:  
  
230Shirts0056  
  
320Towels1356  
  
Dans l’exemple précédent, la première ligne chargée aura SalesCode = '230' et SalesID = 'Shirts0056'. La ligne ensuite chargée a SalesCode = '320' et SaleID = 'Towels1356'.  
  
Pour plus d’informations sur la gestion de début et de fin de conversion de type des espaces ou des données en mode de largeur fixe, consultez [pour dwloader, les règles de conversion de type de données](dwloader-data-type-conversion-rules.md).  
  
**-e** *character_encoding*  
Spécifie un type d’encodage de caractères pour les données à charger à partir du fichier de données. Les options sont ASCII (par défaut), UTF-8, UTF16 ou UTF16BE, où UTF16 est primauté des octets et UTF16BE big endian. Ces options respectent la casse.  
  
Colonnes de largeur fixe ne sont pas pris en charge -e est UTF8.  
  
**-r** *row_delimiter*  
Le délimiteur pour chaque ligne du fichier de données source. Le séparateur de lignes est une ou plusieurs des valeurs ASCII.  
  
Pour spécifier un retour chariot (CR), un saut de ligne (LF) ou un caractère de tabulation comme un délimiteur, vous pouvez utiliser les caractères d’échappement (\r, \n, \t) ou leurs valeurs hexadécimales (0 x, 0D, 09). Pour spécifier d’autres caractères spéciaux en tant que délimiteurs, utilisez leur valeur hexadécimale.  
  
Exemples de retour chariot + saut de ligne :  
  
-r \r\n  
  
-r 0x0d0x0a  
  
Exemples de CR :  
  
-r \r  
  
-r 0x0d  
  
Exemples de saut de ligne :  
  
-r \n  
  
-r 0x0a  
  
Un saut de ligne est requis pour Unix. Une demande de modification est requis pour Windows.  
  
**-D** { **ymd** | ydm | mdy | myd |  dmy | dym | *custom_date_format* }  
Spécifie l’ordre des mois (m), jour (d) et l’année (y) pour tous les champs de date/heure dans le fichier d’entrée. L’ordre par défaut est ymd. Pour spécifier plusieurs formats de commande pour le même fichier source, utilisez l’option -dt.  
  
YMD | dmy  
ydm et dmy autorisent les mêmes formats d’entrée. Les deux permettent l’année être au début ou à la fin de la date. Par exemple, pour les deux **ydm** et **dmy** date formats, vous pourriez avoir 2013-02-03 ou 02-03-2013 dans le fichier d’entrée.  
  
ydm  
Vous pouvez uniquement charger entrée mis en forme en tant qu’ydm dans des colonnes de données type datetime et smalldatetime. Impossible de charger les valeurs ydm dans une colonne de la datetime2, date ou type de données datetimeoffset.  
  
mja  
MDY permet <month> <space> <day> <comma> <year>.  
  
Exemples de mdy des données d’entrée pour le 1er janvier 1975 :  
  
-   1er janvier 1975  
  
-   Jan 01, 75  
  
-   Jan/1/75  
  
-   01011975  
  
maj  
Entrée des exemples de fichiers pour mars 04,2010 : 03-2010-04, 3/2010/4  
  
jam  
Exemples de fichier d’entrée pour le 04 mars 2010 : 04-2010-03, 4/2010/3  
  
*custom_date_format*  
*custom_date_format* est un format de date personnalisé (par exemple, MM/jj/aaaa) et inclus pour la compatibilité descendante uniquement. dwloader n’applique pas le format de date personnalisé. Au lieu de cela, lorsque vous spécifiez un format de date personnalisé, **dwloader** convertira le paramètre correspondant d’ymd, ydm, mdy, myd, dym ou JMA.  
  
Par exemple, si vous spécifiez -D MM/jj/aaaa, dwloader attend toutes les date d’entrée doivent être classés avec mois tout d’abord, puis jour et puis année (MJA). Il n’applique pas de caractère de 2 mois, les jours à 2 chiffres et 4 chiffres, comme spécifié par le format de date personnalisé. Voici quelques exemples de dates peuvent être mis en forme dans le fichier d’entrée lorsque le format de date est -D MM/jj/aaaa : 01/02/2013, Jan.02.2013, 1/2/2013  
  
Pour obtenir des informations de mise en forme plus complètes, consultez [pour dwloader, les règles de conversion de type de données](dwloader-data-type-conversion-rules.md).  
  
**-dt** *datetime_format_file*  
Chaque format de date/heure est spécifiée dans un fichier nommé *datetime_format_file*. Contrairement aux paramètres de ligne de commande, les paramètres de fichier incluant des espaces ne doivent pas entre guillemets doubles. Vous ne pouvez pas modifier le format de date/heure que vous chargez des données. Le fichier de données source et de sa colonne correspondante dans la table de destination doivent avoir le même format.  
  
Chaque ligne contient le nom d’une colonne dans la table de destination et son format de date/heure.  
  
Exemples :  
  
`LastReceiptDate=ymd`  
  
`ModifiedDate=dym`  
  
**-d** *staging_database_name*  
Le nom de base de données qui contiendra la table intermédiaire. La valeur par défaut est la base de données spécifiée avec l’option -T, qui est la base de données pour la table de destination. Pour plus d’informations sur l’utilisation d’une base de données mise en lots, consultez [créer la base de données intermédiaire](staging-database.md).  
  
**-M** *load_mode_option*  
Spécifie s’il faut ajouter, upsert, ou de recharger les données. Le mode par défaut est d’ajouter.  
  
Ajouter  
Le chargeur insère des lignes à la fin des lignes existantes dans la table de destination.  
  
fastappend  
Le chargeur insère des lignes directement, sans utiliser une table temporaire, à la fin des lignes existantes dans la table de destination. fastappend nécessite la transaction multi (-m) option. Une base de données intermédiaire ne peut pas être spécifié lors de l’utilisation de fastappend. Il n’existe aucune restauration avec fastappend, ce qui signifie que la récupération à partir d’une charge de l’échec ou abandonnée doit être gérée par votre propre processus de chargement.  
  
upsert **-K***merge_column* [,...*n* ]  
Le chargeur utilise l’instruction de fusion SQL Server pour mettre à jour les lignes existantes et insérer de nouvelles lignes.  
  
L’option -K spécifie l’ou les colonnes de la fusion de base sur. Ces colonnes forment une clé de fusion, qui doit représenter une ligne unique. Si la clé de fusion existe dans la table de destination, la ligne est mise à jour. Si la clé de fusion n’existe pas dans la table de destination, la ligne est ajoutée.  
  
Pour les tables distribuées par hachage, la clé de fusion doit être ou inclure la colonne de distribution.  
  
Pour les tables répliquées, la clé de fusion est la combinaison d’une ou plusieurs colonnes. Ces colonnes sont spécifiées en fonction des besoins de l’application.  
  
Plusieurs colonnes doivent être séparés par une virgule sans espace, ou séparées par des virgules avec des espaces et encadrée de guillemets simples.  
  
Si deux lignes dans la table source ont des valeurs de clé de fusion, leurs lignes respectifs doivent être identiques.  
  
Recharger  
Le chargeur tronque la table de destination avant d’insérer la source de données.  
  
**-b** *batchsize*  
Recommandé uniquement pour une utilisation par le Support Microsoft, *batchsize* est la taille de lot SQL Server pour la copie en bloc qui effectue le DMS et instances SQL Server sur les nœuds de calcul.  Lorsque *batchsize* est spécifié, SQL Server PDW remplacera la taille de charge de lot est calculée dynamiquement pour chaque charge.  
  
À compter de SQL Server 2012 PDW, le nœud de contrôle calcule dynamiquement une taille de lot pour chaque chargement par défaut. Ce calcul automatique est basé sur plusieurs paramètres tels que la taille de la mémoire, type de table cible, schéma de la table cible, type de charge, taille de fichier et la classe de ressources utilisateur.  
  
Par exemple, si le mode de chargement est FASTAPPEND et la table a un index columnstore en cluster, SQL Server PDW sera par la tentative par défaut à utiliser une taille de lot de 1 048 576 afin que les rowgroups va devenir fermées et charge directement dans le columnstore sans passer par le magasin delta. Si la mémoire n’autorise pas la taille de lot de 1 048 576, dwloader choisit une valeur batchsize plus petits.  
  
Si le type de charge est FASTAPPEND, le *batchsize* s’applique au chargement de données dans la table, sinon *batchsize* s’applique au chargement de données dans la table intermédiaire.  
  
<reject_options>  
Spécifie les options pour déterminer le nombre d’échecs de chargement qui permettra du chargeur. Si les échecs de chargement dépassent le seuil, le chargeur arrêtera et pas valider toutes les lignes.  
  
**-rt** { **valeur** | pourcentage}  
Spécifie si l’option -*reject_value* dans le **-rv** *reject_value* option est un nombre de lignes (valeur) littéral ou un taux de défaillance (pourcentage). La valeur par défaut est la valeur.  
  
L’option de pourcentage est un calcul en temps réel qui se produit à intervalles en fonction de l’option - r.  
  
Par exemple, si le chargeur essaie de charger 100 lignes et 25 échoue et 75 réussisse, le taux d’échec est 25 %.  
  
**-rv** *reject_value*  
Spécifie le nombre ou le pourcentage de rejets de ligne autorisée avant l’arrêt de la charge. Le **-rt** option détermine si *reject_value* fait référence au nombre de lignes ou le pourcentage de lignes.  
  
La valeur par défaut *reject_value* est 0.  
  
Lorsqu’il est utilisé avec la valeur de -rt, le chargeur arrête la charge lorsque le nombre de lignes rejetées dépasse reject_value.  
  
Quand utiliser avec pourcentage de -rt, le chargeur calcule le pourcentage à intervalles (-option de rs). Par conséquent, le pourcentage de lignes ayant échoué peut dépasser *reject_value*.  
  
**-rs** *reject_sample_size*  
Utilisé avec le `-rt percentage` option pour spécifier les vérifications de pourcentage incrémentielle. Par exemple, si reject_sample_size est 1000, le chargeur de calculer le pourcentage de lignes ayant échoué après avoir tenté de charger les 1000 lignes. Il recalcule le pourcentage de lignes ayant échoué après avoir tenté de charger chaque 1000 lignes supplémentaires.  
  
**-c**  
Supprime les caractères d’espace blanc de gauche et droite de char, nchar, varchar et nvarchar champs. Convertit chaque champ qui contient uniquement des caractères d’espace blanc sur la chaîne vide.  
  
Exemples :  
  
« ' est tronquée à « »  
  
'abc' Obtient tronqué à 'abc'  
  
-C est utilisé avec -E, l’opération -E se produit en premier. Les champs qui contiennent uniquement des caractères d’espace blanc sont converties en une chaîne vide et pas avec la valeur NULL.  
  
**-E**  
Convertir des chaînes vides sur la valeur NULL. La valeur par défaut est à ne pas effectuer ces conversions.  
  
**-m**  
Utiliser le mode de transaction multiples pour la deuxième phase de chargement ; lors du chargement des données à partir de la table intermédiaire dans une table distribuée.  
  
Avec **-m**, SQL Server PDW effectue et valide les charges en parallèle. Beaucoup plus rapide que le mode de chargement par défaut, ce n’est pas sécurisé de la transaction.  
  
Sans **-m**, SQL Server PDW effectue et valide des charges en série sur les distributions au sein de chaque nœud de calcul et simultanément sur les nœuds de calcul. Cette méthode est plus lente que le mode de transaction multiples, mais est sûre.  
  
**-m** est facultatif pour *ajouter*, *recharger*, et *upsert*.  
  
**-m** est requis pour fastappend.  
  
**-m** ne peut pas être utilisé avec les tables répliquées.  
  
**m -** s’applique uniquement à la deuxième phase de chargement. Il ne s’applique pas à la première phase de chargement ; chargement des données dans la table intermédiaire.  
  
Il n’existe aucune restauration avec le mode de transaction multiples, ce qui signifie que la récupération à partir d’une charge de l’échec ou abandonnée doit être gérée par votre propre processus de chargement.  
  
Nous vous recommandons d’utiliser **-m** uniquement lors du chargement dans une table vide, afin que vous puissiez récupérer sans perte de données. Pour récupérer à partir d’un échec de chargement : supprimez la table de destination, résoudre le problème de chargement, recréer la table de destination, et réexécuter la charge.  
  
**-N**  
Vérifiez que l’appliance cible dispose d’un certificat de SQL Server PDW valid d’une autorité approuvée. Cela permet de garantir à vos données ne sont pas en cours détournée par un attaquant et envoyées à un emplacement non autorisé. Le certificat doit déjà être installé sur l’appliance. La seule façon d’installer le certificat est pour l’administrateur de l’appliance pour l’installer à l’aide de l’outil de Configuration Manager. Demandez à votre administrateur de matériel si vous ne savez pas si l’appliance a un certificat approuvé installé.  
  
**-se**  
Ignorer le chargement des fichiers vides. Il ignore également décompression des fichiers gzip vide.

**-l**  
Disponible avec la mise à jour CU7.4, spécifie la longueur de ligne maximale (en octets) qui peut être chargée. Les valeurs valides sont des entiers compris entre 32768 et 33554432. Utilisez uniquement lorsque nécessaire pour charger des lignes de grande taille (supérieures à 32 Ko) comme ceci alloue plus de mémoire sur le client et le serveur.
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
0 (succès) ou une autre valeur d’entier (échec)  
  
Dans un fichier batch ou de la fenêtre commande, utilisez `errorlevel` pour afficher le code de retour. Exemple :  
  
```  
dwloader  
echo ReturnCode=%errorlevel%  
if not %errorlevel%==0 echo Fail  
if %errorlevel%==0 echo Success  
```  
  
Lorsque vous utilisez PowerShell, utilisez `$LastExitCode`.  
  
## <a name="permissions"></a>Autorisations  
Nécessite une autorisation de charge et des autorisations applicables (INSERT, UPDATE, DELETE) sur la table de destination. Nécessite l’autorisation de créer (pour la création d’une table temporaire) sur la base de données intermédiaire. Si une base de données intermédiaire n’est pas utilisé, autorisation de création est nécessaire sur la base de données de destination. 

<!-- MISSING LINK
For more information, see [Grant permissions to load data](grant-permissions-to-load-data.md).  
-->
  
## <a name="general-remarks"></a>Remarques d'ordre général  
Pour plus d’informations sur les conversions de type de données lors du chargement avec dwloader, consultez [pour dwloader, les règles de conversion de type de données](dwloader-data-type-conversion-rules.md).  
  
Si un paramètre comprend un ou plusieurs espaces, placez-le entre le paramètre entre guillemets doubles.  
  
Vous devez exécuter le chargeur à partir de son emplacement d’installation. L’exécutable de dwloader est préinstallé avec l’appliance et se trouve dans le répertoire C:\Program Files\Microsoft SQL Server Data Warehouse\DWLoader.  
  
Vous pouvez remplacer un paramètre qui est spécifié dans le fichier de paramètres (-option f) en le spécifiant comme un paramètre de ligne de commande.  
  
Vous pouvez exécuter plusieurs instances du chargeur simultanément. Le nombre maximal d’instances de chargeur est préconfiguré et ne peut pas être modifié. 

<!-- MISSING LINK
For the maximum number of loads per appliance, see [Minimum and Maximum Values](minimum-maximum-values.md)  
-->
  
Données chargées peuvent nécessiter plus ou moins d’espace sur l’appliance que dans l’emplacement source. Vous pouvez effectuer des importations de test avec des sous-ensembles de données pour estimer la consommation de disque.  
  
Bien que **dwloader** est un processus de transaction et restaurera normalement en cas d’échec, il ne peut pas être annulée une fois le chargement en masse a été effectué correctement. Pour annuler un actif **dwloader** traiter, tapez CTRL + C.  
  
## <a name="limitations-and-restrictions"></a>Limitations et restrictions  
La taille totale de tous les chargements se produisent simultanément doit être inférieure à LOG_SIZE pour la base de données, et nous vous recommandons la taille totale de tous les chargements simultanés est inférieure à 50 % de la LOG_SIZE. Pour atteindre cette limite de taille, vous pouvez diviser les charges importantes en plusieurs lots. Pour plus d’informations sur LOG_SIZE, consultez [créer la base de données](../t-sql/statements/create-database-parallel-data-warehouse.md)  
  
Lors du chargement de plusieurs fichiers avec une seule charge commande, toutes les lignes rejetées sont écrits dans le même fichier de rejet. Le fichier de rejet n’affiche pas le fichier d’entrée qui contient chaque ligne rejetée.  
  
La chaîne vide ne doit pas servir comme délimiteur. Lorsqu’une chaîne vide est utilisée comme un séparateur de lignes, le chargement échoue. Lorsqu’il est utilisé en tant que délimiteur de colonne, la charge ignore le délimiteur et continue d’utiliser la valeur par défaut « | » comme délimiteur de colonne. Lorsqu’il est utilisé comme délimiteur de chaîne, la chaîne vide est ignorée et le comportement par défaut est appliqué.  
  
## <a name="locking-behavior"></a>Comportement de verrouillage  
**dwloader** comportement de verrouillage peut varier selon le *load_mode_option*.  
  
-   **ajouter** -ajouter est l’architecture recommandée et l’option la plus courante. Ajouter la charge des données dans une table intermédiaire. Le verrouillage est décrite en détail ci-dessous.  
  
-   **Ajout rapide** -Fast-append charge directement dans la table finale en prenant un verrou de table ExclusiveUpdate et est le seul mode qui n’utilise pas une table intermédiaire.  
  
-   **recharger** -rechargement charge les données dans une table intermédiaire et nécessite un verrou exclusif sur la table intermédiaire et la table finale. Rechargement n’est pas recommandé pour les opérations simultanées.  
  
-   **upsert** -Upsert charge les données dans une table intermédiaire, puis effectue une opération de fusion à partir de la table intermédiaire vers la table finale. Upsert ne nécessite pas de verrous exclusifs sur la table finale. Les performances peuvent varier lorsque vous utilisez upsert. Tester le comportement dans votre environnement.  
  
### <a name="locking-behavior"></a>Comportement de verrouillage  
**Ajouter le mode de verrouillage**  
  
Ajouter peut être exécuté en mode transactionnel multi (à l’aide de l’argument -m), mais il n’est pas sûr de la transaction. Par conséquent ajouter doit être utilisé comme une opération transactionnelle (sans utiliser l’argument -m). Malheureusement, lors de l’opération INSERT-SELECT finale, mode transactionnel est actuellement environ six fois plus lent que le mode transactionnel multiples.  
  
Le mode append charge les données en deux phases. Première phase charge les données à partir du fichier source dans une table intermédiaire simultanément (la fragmentation peut se produire). Phase 2 charge les données à partir de la table intermédiaire vers la table finale. La deuxième phase effectue un **INSERT INTO... Sélectionnez WITH (TABLOCK)** opération. Le tableau suivant montre le comportement de verrouillage sur la table finale, et comportement de journalisation lorsque vous utilisez le mode adjonction :  
  
|Type de table|Transactions multiples<br />Mode (-m)|Table est vide|Prise en charge l’accès concurrentiel|Journalisation|  
|--------------|-----------------------------------|------------------|-------------------------|-----------|  
|Segment de mémoire (heap)|Oui|Oui|Oui|Minimal|  
|Segment de mémoire (heap)|Oui|Non|Oui|Minimal|  
|Segment de mémoire (heap)|Non|Oui|Non|Minimal|  
|Segment de mémoire (heap)|Non|Non|Non|Minimal|  
|Cl|Oui|Oui|Non|Minimal|  
|Cl|Oui|Non|Oui|Complète|  
|Cl|Non|Oui|Non|Minimal|  
|Cl|Non|Non|Oui|Complète|  
  
Le tableau ci-dessus présente **dwloader** en utilisant le mode append, le chargement dans un segment de mémoire ou une table d’index cluster (CI), avec ou sans l’indicateur multi-transactionnelle et le chargement dans une table vide ou une table non vide. Le verrouillage et le comportement de chaque combinaison de charge de ce type d’enregistrement s’affiche dans la table. Par exemple, le chargement (2ème) phase avec le mode append dans un index cluster sans mode multi-transactionnelle et dans vide table aura PDW créer un verrou exclusif sur la table et journalisation est minime. Cela signifie qu’un client ne sera pas en mesure de charger (2e) phase et requête simultanément dans une table vide. Toutefois, lors du chargement avec la même configuration dans une table non vide, PDW n’émettra pas un verrou exclusif sur la table et l’accès concurrentiel est possible. Malheureusement, une journalisation complète se produit, le processus peut ralentir.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-simple-dwloader-example"></a>A. Exemple de simple dwloader  
L’exemple suivant montre l’émission de la **chargeur** avec uniquement les options requises sélectionnées. Autres options sont effectuées à partir du fichier de configuration globale, *loadparamfile.txt*.  
  
Exemple à l’aide de l’authentification SQL Server.  
  
```  
--Load over Ethernet  
dwloader.exe -S 10.192.63.148 -U mylogin -P 123jkl -f /configfiles/loadparamfile.txt  
  
--Load over InfiniBand to appliance named MyPDW  
dwloader.exe -S MyPDW-SQLCTL01 -U mylogin -P 123jkl -f /configfiles/loadparamfile.txt  
```  
  
Le même exemple en utilisant l’authentification Windows.  
  
```  
--Load over Ethernet  
dwloader.exe -S 10.192.63.148 -W -f /configfiles/loadparamfile.txt  
  
--Load over InfiniBand to appliance named MyPDW  
dwloader.exe -S MyPDW-SQLCTL01 -W -f /configfiles/loadparamfile.txt  
```  
  
Exemple à l’aide des arguments pour un fichier source et le fichier d’erreur.  
  
```  
--Load over Ethernet  
dwloader.exe -U mylogin -P 123jkl -S 10.192.63.148  -i C:\SQLData\AWDimEmployees.csv -T AdventureWorksPDW2012.dbo.DimEmployees -R C:\SQLData\LoadErrors  
```  
  
### <a name="b-load-data-into-an-adventureworks-table"></a>B. Charger des données dans une Table d’AdventureWorks  
L’exemple suivant fait partie d’un script de commandes qui charge des données dans **AdventureWorksPDW2012**.  Pour afficher le script complet, ouvrez le fichier du fichier aw_create.bat qui est fourni avec le **AdventureWorksPDW2012** package d’installation. 

<!-- Missing link
For more information, see [Install AdventureWorksPDW2012](install-adventureworkspdw2012.md).  
-->

L’extrait de script suivant utilise dwloader pour charger des données dans les tables DimAccount et DimCurrency. Ce script utilise une adresse Ethernet. Si elle utilisait InfiniBand, server serait *< nom_solution >* `-SQLCTL01`.  
  
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
  
Voici l’instruction DDL pour la DimAccount Table.  
  
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
  
Voici un exemple du fichier de données, DimAccount.txt, qui contient les données à charger dans la table DimAccount.  
  
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
Le script dans l’exemple B peut être remplacé en entrant de tous les paramètres sur la ligne de commande, comme indiqué dans l’exemple suivant.  
  
```  
C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\dwloader.exe -S <Control node IP> -E -M reload -e UTF16 -i .\DimAccount.txt -T AdventureWorksPDW2012.dbo.DimAccount -R DimAccount.bad -t "|" -r \r\n -U <login> -P <password>  
```  
  
Description des paramètres de ligne de commande :  
  
-   *C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\dwloader.exe* est l’emplacement d’installation de dwloader.exe.  
  
-   *S -* est suivi par l’adresse IP du nœud de contrôle.  
  
-   *E -* spécifie pour charger des chaînes vides comme NULL.  
  
-   *-M recharger* spécifie pour tronquer la table de destination avant d’insérer la source de données.  
  
-   *e - UTF16* indique le fichier source utilise le type d’encodage de caractères primauté peu.  
  
-   *i -.\DimAccount.txt* spécifie les données sont dans un fichier appelé DimAccount.txt qui existe dans le répertoire actif.  
  
-   *-T AdventureWorksPDW2012.dbo.DimAccount* Spécifie le nom de la partie 3 de la table à recevoir les données.  
  
-   *R - DimAccount.bad* spécifie les lignes qui ne parviennent pas à charger seront écrit dans un fichier appelé DimAccount.bad.  
  
-   *t-« | »*  indique les champs dans le fichier d’entrée, DimAccount.txt, sont séparés par le caractère barre verticale.  
  
-   *r - \r\n* spécifie chaque ligne dans DimAccount.txt se termine par un retour chariot et un retour chariot.  
  
-   *-U < login_name > -P <password>*  spécifie la connexion et le mot de passe pour la connexion qui dispose des autorisations pour effectuer le chargement.  
  

<!-- MISSING LINK

## See Also  
[Common Metadata Query Examples](metadata-query-examples.md)  

-->
  
