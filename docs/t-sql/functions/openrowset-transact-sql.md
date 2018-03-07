---
title: OPENROWSET (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/09/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- OPENROWSET_TSQL
- OPENROWSET
dev_langs:
- TSQL
helpviewer_keywords:
- data sources [SQL Server]
- OPENROWSET function
- remote data access [SQL Server], OPENROWSET
- ad hoc distributed queries
- OPENROWSET function, Transact-SQL
- OPENROWSET statement
- OLE DB data sources [SQL Server]
- ad hoc connection information
ms.assetid: f47eda43-33aa-454d-840a-bb15a031ca17
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 68db78ede26c3e7f8c60ced655d89d0fc9a615ac
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2018
---
# <a name="openrowset-transact-sql"></a>OPENROWSET (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Inclut toutes les informations de connexion exigées pour accéder à des données distantes à partir d'une source de données OLE DB. Cette méthode est une autre façon d'accéder à des tables dans un serveur lié et constitue une méthode efficace pour vous connecter et accéder à des données distantes en utilisant OLE DB. Pour faire des références plus fréquentes à des sources de données OLE DB, utilisez plutôt des serveurs liés. Pour plus d’informations, consultez [Serveurs liés &#40;moteur de base de données&#41;](../../relational-databases/linked-servers/linked-servers-database-engine.md). Le `OPENROWSET` fonction peut être référencée dans la clause FROM d’une requête comme s’il s’agissait d’un nom de table. Le `OPENROWSET` fonction peut également être référencée comme table cible d’une `INSERT`, `UPDATE`, ou `DELETE` instruction, soumise aux capacités du fournisseur OLE DB. Bien que la requête peut renvoyer plusieurs jeux de résultats, `OPENROWSET` retourne uniquement le premier.  
  
 `OPENROWSET`prend également en charge les opérations en bloc via un fournisseur BULK intégré qui permet des données à partir d’un fichier à lire et retourné sous la forme d’un ensemble de lignes.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
OPENROWSET   
( { 'provider_name' , { 'datasource' ; 'user_id' ; 'password'   
   | 'provider_string' }   
   , {   [ catalog. ] [ schema. ] object   
       | 'query'   
     }   
   | BULK 'data_file' ,   
       { FORMATFILE = 'format_file_path' [ <bulk_options> ]  
       | SINGLE_BLOB | SINGLE_CLOB | SINGLE_NCLOB }  
} )   
  
<bulk_options> ::=  
   [ , CODEPAGE = { 'ACP' | 'OEM' | 'RAW' | 'code_page' } ]   
   [ , DATASOURCE = 'data_source_name' ]
   [ , ERRORFILE = 'file_name' ]  
   [ , ERRORFILE_DATASOURCE = 'data_source_name' ]   
   [ , FIRSTROW = first_row ]   
   [ , LASTROW = last_row ]   
   [ , MAXERRORS = maximum_errors ]   
   [ , ROWS_PER_BATCH = rows_per_batch ]  
   [ , ORDER ( { column [ ASC | DESC ] } [ ,...n ] ) [ UNIQUE ] ]
  
   -- bulk_options related to input file format
   [ , FORMAT = 'CSV' ]
   [ , FIELDQUOTE = 'quote_characters']
   [ , FORMATFILE = 'format_file_path' ]   
```

  
## <a name="arguments"></a>Arguments  
 '*Nom_Fournisseur*'  
 Chaîne de caractères représentant le nom convivial (ou PROGID) du fournisseur OLE DB tel que spécifié dans le Registre. *Nom_Fournisseur* n’a aucune valeur par défaut.  
  
 '*source de données*'  
 Constante de chaîne correspondant à une source de données OLE DB spécifique. *source de données* est la propriété DBPROP_INIT_DATASOURCE à transmettre à l’interface IDBProperties du fournisseur pour initialiser le fournisseur. En général, cette chaîne comporte le nom du fichier de base de données, le nom d'un serveur de base de données ou un nom que comprend le fournisseur pour retrouver la ou les bases de données.  
  
 '*user_id*'  
 Constante de chaîne représentant le nom d'utilisateur passé au fournisseur OLE DB spécifié. *USER_ID* Spécifie le contexte de sécurité pour la connexion et est passé en tant que propriété DBPROP_AUTH_USERID pour initialiser le fournisseur. *USER_ID* ne peut pas être un nom de connexion Microsoft Windows.  
  
 '*mot de passe*'  
 Constante de chaîne représentant le mot de passe utilisateur à transmettre au fournisseur OLE DB. *mot de passe* est passé en tant que propriété DBPROP_AUTH_PASSWORD au lors de l’initialisation du fournisseur. *mot de passe* ne peut pas être un mot de passe Microsoft Windows.  
  
 '*provider_string*'  
 Chaîne de connexion spécifique au fournisseur qui est passée en tant que propriété DBPROP_INIT_PROVIDERSTRING pour initialiser le fournisseur OLE DB. *provider_string* généralement encapsule toutes les informations de connexion nécessaires pour initialiser le fournisseur. Pour obtenir la liste de mots clés qui sont reconnus par le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif, consultez [propriétés d’initialisation et d’autorisation](../../relational-databases/native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md).  
  
 *catalogue*  
 Nom du catalogue ou de la base de données où réside l'objet spécifié.  
  
 *schéma*  
 Nom du propriétaire du schéma ou de l'objet pour l'objet spécifié.  
  
 *objet*  
 Nom d'objet qui identifie de façon unique l'objet à manipuler.  
  
 '*requête*'  
 Constante de chaîne envoyée au fournisseur en vue de son exécution. L'instance locale [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne traite pas cette requête, mais traite les résultats de la requête retournés par le fournisseur (requête directe). Les requêtes directes sont utiles lorsque les fournisseurs mettent leurs données tabulaires à disposition non pas par l'intermédiaire de noms de tables, mais uniquement au moyen d'un langage de commande. Requêtes directes sont prises en charge sur le serveur distant, tant que le fournisseur de requête prend en charge l’objet de commande OLE DB et ses interfaces obligatoires. Pour plus d’informations, consultez [SQL Server Native Client &#40; OLE DB &#41; Référence](../../relational-databases/native-client-ole-db-interfaces/sql-server-native-client-ole-db-interfaces.md).  
  
 BULK  
 Utilise le fournisseur d'ensembles de lignes BULK pour que OPENROWSET lise les données dans un fichier. Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], OPENROWSET peut lire un fichier de données sans charger les données dans une table cible. Cela vous permet d’utiliser OPENROWSET avec une instruction SELECT simple.  
  
 Les arguments de l'option BULK permettent un contrôle significatif sur le début et la fin de la lecture des données, sur le traitement des erreurs et sur l'interprétation des données. Par exemple, vous pouvez spécifier que le fichier de données être lu comme un ensemble de lignes seule ligne et une seule colonne de type **varbinary**, **varchar**, ou **nvarchar**. Le comportement par défaut est indiqué dans les descriptions des arguments ci-dessous.  
  
 Pour plus d'informations sur l'utilisation de l'option BULK, consultez la section « Remarques » plus loin dans cette rubrique. Pour plus d'informations sur les autorisations requises par l'option BULK, consultez la section « Autorisations » plus loin dans cette rubrique.  
  
> [!NOTE]  
>  Lorsqu'elle est utilisée pour importer des données avec le mode de récupération complète, la fonction OPENROWSET (BULK ...) n'optimise pas la journalisation.  
  
 Pour plus d’informations sur la préparation des données pour l’importation en bloc, consultez [préparer des données pour l’exportation en bloc ou une importation &#40; SQL Server &#41; ](../../relational-databases/import-export/prepare-data-for-bulk-export-or-import-sql-server.md).  
  
 '*data_file*'  
 Chemin d'accès complet au fichier dont les données doivent être copiées dans la table cible.   
 **S’applique à :** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.   
À partir de [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1, la data_file peut être dans le stockage d’objets BLOB Azure. Pour obtenir des exemples, consultez [exemples d’accès en bloc à des données dans le stockage d’objets Blob Azure](../../relational-databases/import-export/examples-of-bulk-access-to-data-in-azure-blob-storage.md).
  
 \<bulk_options >  
 Spécifie un ou plusieurs arguments pour l'option BULK.  
  
 PAGE DE CODES = {'ACP' | « OEM » | « BRUTS » | *code_page*'}  
 Indique la page de codes des données dans le fichier. Page de codes s’applique uniquement si les données contiennent **char**, **varchar**, ou **texte** colonnes avec des valeurs de caractère plus de 127 ou inférieures à 32.  
  
> [!NOTE]  
>  Nous vous recommandons de spécifier un nom de classement pour chaque colonne dans un fichier de format, sauf lorsque vous souhaitez que l’option 65001 soit ont la priorité sur la spécification de page de codes/classement.  
  
|Valeur CODEPAGE|Description|  
|--------------------|-----------------|  
|ACP|Convertit les colonnes de **char**, **varchar**, ou **texte** type de données à partir de l’ANSI /[!INCLUDE[msCoName](../../includes/msconame-md.md)] page de codes Windows (ISO 1252) à la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] page de codes.|  
|OEM (valeur par défaut)|Convertit les colonnes de **char**, **varchar**, ou **texte** type de données à partir de la page de codes OEM du système pour le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] page de codes.|  
|RAW|Aucune conversion n'a lieu d'une page de codes à une autre. Il s'agit de l'option la plus rapide.|  
|*code_page*|Indique la page de codes source sur laquelle est basé l'encodage des données caractères du fichier de données, par exemple 850.<br /><br /> **\*\*Important \* \***  Versions antérieures à [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] ne prennent pas en charge la page de codes 65001 (encodage UTF-8).|  
  
 ERRORFILE ='*nom_fichier*'  
 Fichier utilisé pour collecter les lignes comportant des erreurs de mise en forme et impossibles à convertir en un ensemble de lignes OLE DB. Ces lignes sont copiées « en l'état » du fichier de données vers ce fichier d'erreur.  
  
 Le fichier d'erreur est créé au début de l'exécution de la commande. Une erreur est signalée si le fichier existe déjà. De plus, un fichier de contrôle portant l'extension .ERROR.txt est créé. Ce fichier fait référence à chaque ligne dans le fichier d’erreur et propose un diagnostic. Lorsque les erreurs sont corrigées, les données peuvent être chargées.  
**S’applique à :** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.
À partir de [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)], le `error_file_path` peut se trouver dans le stockage d’objets BLOB Azure. 

'errorfile_data_source_name'   
**S’applique à :** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.
Une source de données externe nommé pointe vers l’emplacement de stockage d’objets Blob Azure du fichier d’erreur contenant des erreurs détectées lors de l’importation. La source de données externe doit être créée à l’aide de la `TYPE = BLOB_STORAGE` option ajoutée dans [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1. Pour plus d’informations, consultez [CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md).
  
 FIRSTROW =*first_row*  
 Numéro de la première ligne à charger. La valeur par défaut est 1. Cela indique la première ligne du fichier de données spécifié. Les numéros des lignes sont déterminés en comptant les indicateurs de fin de ligne. FIRSTROW commence à 1.  
  
 LASTROW =*last_row*  
 Numéro de la dernière ligne à charger. La valeur par défaut est 0. Cela indique la dernière ligne du fichier de données spécifié.  
  
 MAXERRORS =*maximum_errors*  
 Spécifie le nombre maximal d'erreurs de syntaxe ou de lignes non conformes (défini dans le fichier de format) qui peuvent se produire avant que OPENROWSET lève une exception. Tant que la valeur de MAXERRORS n'est pas atteinte, OPENROWSET ignore les lignes incorrectes, ne les charge pas, et les compte comme des erreurs.  
  
 La valeur par défaut pour *maximum_errors* est 10.  
  
> [!NOTE]  
>  MAX_ERRORS ne s’applique pas aux contraintes CHECK, ou à la conversion **money** et **bigint** des types de données.  
  
 ROWS_PER_BATCH =*rows_per_batch*  
 Spécifie le nombre approximatif de lignes de données que compte le fichier de données. Cette valeur doit être du même ordre que le nombre réel de lignes.  
  
 OPENROWSET importe toujours un fichier de données en un seul lot. Toutefois, si vous spécifiez *rows_per_batch* avec une valeur > 0, le processeur de requêtes utilise la valeur de *rows_per_batch* en tant qu’indicateur pour allouer les ressources dans le plan de requête.  
  
 Par défaut, ROWS_PER_BATCH est inconnu. Si vous spécifiez ROWS_PER_BATCH = 0, le résultat est le même que si vous omettez ROWS_PER_BATCH.  
  
 COMMANDE ({ *colonne* [ASC | DESC]} [,... *n*  ] [UNIQUE])  
 Indicateur facultatif qui spécifie la manière dont sont triées les données dans le fichier de données. Par défaut, le processus de chargement en masse considère que le fichier de données n'est pas trié. Il est possible que les performances soient améliorées si l'optimiseur de requête peut exploiter l'ordre spécifié pour générer un plan de requête plus efficace. Voici quelques exemples de situations dans lesquelles il peut être intéressant de spécifier un tri :  
  
-   Insertion de lignes dans une table qui a un index cluster, où les données d'un ensemble de lignes sont triées sur la clé d'index cluster.  
  
-   Jointure de l'ensemble de lignes avec une autre table, où les colonnes de tri et de jointure correspondent.  
  
-   Agrégation des données de l'ensemble de lignes en fonction des colonnes de tri.  
  
-   Utilisation de l'ensemble de lignes en tant que table source dans la clause FROM d'une requête, où les colonnes de tri et de jointure correspondent.  
  
 UNIQUE spécifie que le fichier de données n'a pas d'entrées en double.  
  
 Si les lignes réelles du fichier de données ne sont pas triées d'après l'ordre spécifié ou si l'indicateur UNIQUE est spécifié et si des clés en double sont présentes, une erreur est retournée.  
  
 Les alias de colonnes sont requis lorsque ORDER est utilisé. La liste d'alias de colonnes doit référencer la table dérivée à laquelle accède la clause BULK. Les noms de colonnes qui sont spécifiés dans la clause ORDER font référence à cette liste d'alias de colonnes. Types de valeur élevée (**varchar (max)**, **nvarchar (max)**, **varbinary (max)**, et **xml**) et les types d’objets volumineux (LOB) (**texte**, **ntext**, et **image**) les colonnes ne peuvent pas être spécifiées.  
  
 SINGLE_BLOB  
 Retourne le contenu de *data_file* comme un ensemble de lignes seule ligne et une seule colonne de type **varbinary (max)**.  
  
> [!IMPORTANT]  
>  Nous vous recommandons d'importer des données XML seulement au moyen de l'option SINGLE_BLOB, au lieu de SINGLE_CLOB et SINGLE_NCLOB, parce que seule l'option SINGLE_BLOB prend en charge toutes les conversions d'encodage de Windows.  
  
 SINGLE_CLOB  
 En lisant *data_file* en ASCII, retourne le contenu sous la forme d’un ensemble de lignes seule ligne et une seule colonne de type **varchar (max)**, à l’aide du classement de la base de données actuelle.  
  
 SINGLE_NCLOB  
 En lisant *data_file* au format UNICODE, retourne le contenu sous la forme d’un ensemble de lignes seule ligne et une seule colonne de type **nvarchar (max)**, à l’aide du classement de la base de données actuelle.  

### <a name="input-file-format-options"></a>Options de format de fichier d’entrée
  
FORMAT  **=**  « CSV »   
**S’applique à :** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.   
Spécifie un fichier de valeurs séparées par des virgules qui est conforme à la [RFC 4180](https://tools.ietf.org/html/rfc4180) standard.

 FORMATFILE ='*chemin_fichier_format*'  
 Spécifie le chemin complet au fichier de format. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge deux types de fichiers de format : XML et non XML.  
  
 Un fichier de format est requis pour définir les types des colonnes dans le jeu de résultats, excepté lorsque SINGLE_CLOB, SINGLE_BLOB ou SINGLE_NCLOB est spécifié ; dans ce cas, le fichier de format n'est pas requis.  
  
 Pour plus d’informations sur les fichiers de format, consultez [utiliser un fichier de Format pour importer en bloc des données &#40; SQL Server &#41; ](../../relational-databases/import-export/use-a-format-file-to-bulk-import-data-sql-server.md).  

**S’applique à :** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.   
À partir de [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1, la chemin_fichier_format peut être dans le stockage d’objets BLOB Azure. Pour obtenir des exemples, consultez [exemples d’accès en bloc à des données dans le stockage d’objets Blob Azure](../../relational-databases/import-export/examples-of-bulk-access-to-data-in-azure-blob-storage.md).

FIELDQUOTE  **=**  'field_quote'   
**S’applique à :** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.   
Spécifie un caractère qui sera utilisé comme le caractère de guillemet dans le fichier CSV. Si non spécifié, le caractère guillemet (") servira en tant que le caractère guillemet tel que défini dans le [RFC 4180](https://tools.ietf.org/html/rfc4180) standard.

  
## <a name="remarks"></a>Notes   
 `OPENROWSET`peut être utilisé pour accéder aux données distantes OLE DB à partir de sources de données uniquement lorsque le **DisallowAdhocAccess** option de Registre est définie sur 0 pour le fournisseur spécifié, et les requêtes distribuées Ad Hoc option de configuration avancée est activée. Lorsque ces options ne sont pas définies, le comportement par défaut n'autorise pas l'accès d'égal à égal.  
  
 Lors de l'accès à des sources de données OLE DB distantes, l'identité des connexions approuvées n'est pas automatiquement déléguée du serveur auquel le client est connecté au serveur qui est interrogé. Il est nécessaire de configurer la délégation de l'authentification.  
  
 Les noms de catalogues et de schémas sont requis si le fournisseur OLE DB prend en charge plusieurs catalogues et schémas dans la source de données spécifiée. Les valeurs pour *catalogue* et *schéma* peut être omis lorsque le fournisseur OLE DB ne les prend pas en charge. Si le fournisseur prend en charge uniquement des noms de schéma, un nom en deux parties sous la forme *schéma***.** *objet* doit être spécifié. Si le fournisseur prend en charge uniquement les noms de catalogues, un nom en trois parties sous la forme *catalogue***.** *schéma***.** *objet* doit être spécifié. Noms en trois parties doivent être spécifiés pour les requêtes directes qui utilisent le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif. Pour plus d’informations, consultez [Conventions de syntaxe Transact-SQL &#40; Transact-SQL &#41; ](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
 `OPENROWSET`n’accepte pas de variables pour ses arguments.  
  
 Tout appel à `OPENDATASOURCE`, `OPENQUERY`, ou `OPENROWSET` dans le `FROM` clause équivaut séparément et indépendamment à partir de n’importe quel appel à ces fonctions utilisé comme cible de la mise à jour, même si les arguments identiques sont fournis pour les deux appels. En particulier, les conditions de filtre ou de jointure appliquées sur le résultat de l'un de ces appels n'ont aucun effet sur les résultats de l'autre.  
  
## <a name="using-openrowset-with-the-bulk-option"></a>Utilisation de OPENROWSET avec l'option BULK  
 Les améliorations [!INCLUDE[tsql](../../includes/tsql-md.md)] suivantes prennent en charge la fonction OPENROWSET(BULK…) :  
  
-   Une clause FROM qui est utilisée avec `SELECT` peut appeler `OPENROWSET(BULK...)` au lieu d’un nom de table, avec intégral `SELECT` fonctionnalité.  
  
     `OPENROWSET`avec la `BULK` option requiert un nom de corrélation, également appelé variable de plage ou alias, dans le `FROM` clause. Vous pouvez définir des alias de colonnes. Si une liste d'alias de colonnes n'est pas spécifiée, le fichier de format doit comporter les noms des colonnes. La spécification des alias de colonnes remplace les noms de colonnes dans le fichier de format, par exemple :  
  
     `FROM OPENROWSET(BULK...) AS table_alias`  
  
     `FROM OPENROWSET(BULK...) AS table_alias(column_alias,...n)`  
>    [!IMPORTANT]  
>    Échec d’ajout de la `AS <table_alias>` génère l’erreur :    
>    Msg 491, niveau 16, état 1, ligne 20    
>    Un nom de corrélation doit être spécifié pour l'ensemble de lignes en bloc dans la clause FROM.    
  
-   A `SELECT...FROM OPENROWSET(BULK...)` interroge les données dans un fichier directement, sans les importer dans une table. `SELECT…FROM OPENROWSET(BULK...)`peuvent également énumérer les alias de colonnes en bloc à l’aide d’un fichier de format pour spécifier les noms de colonnes, ainsi que les types de données.  
  
-   À l’aide de `OPENROWSET(BULK...)` comme table source dans une `INSERT` ou `MERGE` en bloc d’instruction importe des données à partir d’un fichier de données dans un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table. Pour plus d’informations, consultez [importer en bloc des données par l’utilisation de BULK INSERT ou OPENROWSET &#40; BULK... &#41; &#40; SQL Server &#41; ](../../relational-databases/import-export/import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md) .  
  
-   Lorsque le `OPENROWSET BULK` option est utilisée avec un `INSERT` instruction, la clause BULK prend en charge les indicateurs de table. En plus de la mise à jour indicateurs de table, tel que `TABLOCK`, le `BULK` clause peut accepter les indicateurs de table spécialisés suivants : `IGNORE_CONSTRAINTS` (ignore uniquement les `CHECK` et `FOREIGN KEY` contraintes), `IGNORE_TRIGGERS`, `KEEPDEFAULTS`, et `KEEPIDENTITY`. Pour plus d’informations, consultez [Indicateurs de table &#40;Transact-SQL&#41;](../../t-sql/queries/hints-transact-sql-table.md).  
  
 Pour plus d’informations sur l’utilisation de `INSERT...SELECT * FROM OPENROWSET(BULK...)` consultez [importation et exportation de données &#40; SQL Server &#41; ](../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md). Pour savoir à quel moment les opérations d’insertion de ligne effectuées par l’importation en bloc sont consignées dans le journal des transactions, consultez [Conditions requises pour une journalisation minimale dans l’importation en bloc](../../relational-databases/import-export/prerequisites-for-minimal-logging-in-bulk-import.md).  
  
> [!NOTE]  
>  Lorsque vous utilisez `OPENROWSET`, il est important de comprendre comment [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gère l’emprunt d’identité. Pour plus d’informations sur les considérations de sécurité, consultez [importer en bloc des données par l’utilisation de BULK INSERT ou OPENROWSET &#40; BULK... &#41; &#40; SQL Server &#41; ](../../relational-databases/import-export/import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md).  
  
### <a name="bulk-importing-sqlchar-sqlnchar-or-sqlbinary-data"></a>L'importation en bloc de données SQLCHAR, SQLNCHAR ou SQLBINARY  
 OPENROWSET(BULK...) suppose que, si elle n'est pas spécifiée, la longueur maximale des données SQLCHAR, SQLNCHAR ou SQLBINARY ne dépasse pas 8 000 octets. Si les données importées se trouvent dans un champ de données LOB qui contient toutes les **varchar (max)**, **nvarchar (max)**, ou **varbinary (max)** objets qui dépassent 8 000 octets, vous devez utiliser un fichier de format XML qui définit la longueur maximale du champ de données. Pour spécifier la longueur maximale, modifiez le fichier de format et déclarez l'attribut MAX_LENGTH.  
  
> [!NOTE]  
>  Un fichier de format généré automatiquement ne spécifie pas la longueur ou la longueur maximale d'un champ LOB. Toutefois, vous pouvez modifier un fichier de format et spécifier manuellement la longueur ou la longueur maximale.  
  
### <a name="bulk-exporting-or-importing-sqlxml-documents"></a>Exportation et importation en bloc de documents SQLXML  
 Pour exporter ou importer en bloc des données SQLXML, utilisez l'un des types de données ci-dessous dans votre fichier de format.  
  
|Type de données|Effet|  
|---------------|------------|  
|SQLCHAR ou SQLVARYCHAR|Les données sont envoyées dans la page de codes du client ou dans la page de codes impliquée par le classement.|  
|SQLNCHAR ou SQLNVARCHAR|Les données sont envoyées au format Unicode.|  
|SQLBINARY ou SQLVARYBIN|Les données sont envoyées sans être converties.|  
  
## <a name="permissions"></a>Autorisations  
 `OPENROWSET`les autorisations sont déterminées par les autorisations sur le nom d’utilisateur qui est passé au fournisseur OLE DB. Pour utiliser le `BULK` nécessite l’option `ADMINISTER BULK OPERATIONS` autorisation.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-openrowset-with-select-and-the-sql-server-native-client-ole-db-provider"></a>A. Utilisation de OPENROWSET avec SELECT et le fournisseur SQL Server Native Client OLE DB  
 L’exemple suivant utilise le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur OLE DB Native Client pour accéder à la `HumanResources.Department` de table dans le [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] base de données sur le serveur distant `Seattle1`. (L'utilisation de SQLNCLI et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vous redirigera vers la version la plus récente du fournisseur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB.) Une instruction `SELECT` définit l'ensemble de lignes retourné. La chaîne de caractères du fournisseur contient les mots clés `Server` et `Trusted_Connection`. Ces mots clés sont reconnus par le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif.  
  
```sql  
SELECT a.*  
FROM OPENROWSET('SQLNCLI', 'Server=Seattle1;Trusted_Connection=yes;',  
     'SELECT GroupName, Name, DepartmentID  
      FROM AdventureWorks2012.HumanResources.Department  
      ORDER BY GroupName, Name') AS a;  
```  
  
### <a name="b-using-the-microsoft-ole-db-provider-for-jet"></a>B. Utilisation du fournisseur Microsoft OLE DB pour Jet  
 L'exemple suivant accède à la table `Customers` de la base de données [!INCLUDE[msCoName](../../includes/msconame-md.md)] Access `Northwind` via le fournisseur [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB pour Jet.  
  
> [!NOTE]  
>  L'exécution de ce code exemple suppose que Microsoft Access est installé. Pour exécuter ce code exemple, vous devez installer la base de données Northwind.  
  
```sql  
SELECT CustomerID, CompanyName  
   FROM OPENROWSET('Microsoft.Jet.OLEDB.4.0',  
      'C:\Program Files\Microsoft Office\OFFICE11\SAMPLES\Northwind.mdb';  
      'admin';'',Customers);  
GO  
```  
  
### <a name="c-using-openrowset-and-another-table-in-an-inner-join"></a>C. Utilisation de OPENROWSET avec une autre table dans une jointure interne INNER JOIN  
 L’exemple suivant sélectionne toutes les données à partir de la `Customers` table à partir de l’instance locale de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `Northwind` base de données et à partir de la `Orders` table à partir de l’accès `Northwind` base de données stockée sur le même ordinateur.  
  
> [!NOTE]  
>  L'exécution de ce code exemple suppose que Microsoft Access est installé. Pour exécuter ce code exemple, vous devez installer la base de données Northwind.  
  
```sql  
USE Northwind  ;  
GO  
SELECT c.*, o.*  
FROM Northwind.dbo.Customers AS c   
   INNER JOIN OPENROWSET('Microsoft.Jet.OLEDB.4.0',   
   'C:\Program Files\Microsoft Office\OFFICE11\SAMPLES\Northwind.mdb';'admin';'', Orders)      
   AS o   
   ON c.CustomerID = o.CustomerID ;  
GO  
```  
  
### <a name="d-using-openrowset-to-bulk-insert-file-data-into-a-varbinarymax-column"></a>D. Utilisation de OPENROWSET pour insérer en bloc un fichier de données dans une colonne de type varbinary(max)  
 Le code exemple suivant crée une petite table aux fins de démonstration et insère dans une colonne `Text1.txt` les données du fichier `C:` situé dans le répertoire racine `varbinary(max)`.  
  
```sql  
USE AdventureWorks2012;  
GO  
CREATE TABLE myTable(FileName nvarchar(60),   
  FileType nvarchar(60), Document varbinary(max));  
GO  
  
INSERT INTO myTable(FileName, FileType, Document)   
   SELECT 'Text1.txt' AS FileName,   
      '.txt' AS FileType,   
      * FROM OPENROWSET(BULK N'C:\Text1.txt', SINGLE_BLOB) AS Document;  
GO  
```  
  
### <a name="e-using-the-openrowset-bulk-provider-with-a-format-file-to-retrieve-rows-from-a-text-file"></a>E. Utilisation du fournisseur OPENROWSET BULK avec un fichier de format pour récupérer des lignes dans un fichier texte  
 Le code exemple suivant utilise un fichier de format pour extraire des lignes d'un fichier texte dont les données sont délimitées par des tabulations, `values.txt`, qui contient les données suivantes :  
  
```sql  
1     Data Item 1  
2     Data Item 2  
3     Data Item 3  
```  
  
 Le fichier de format, `values.fmt`, décrit les colonnes du fichier `values.txt` :  
  
```sql  
9.0  
2  
1  SQLCHAR  0  10 "\t"        1  ID                SQL_Latin1_General_Cp437_BIN  
2  SQLCHAR  0  40 "\r\n"      2  Description        SQL_Latin1_General_Cp437_BIN  
```  
  
 Voici la requête qui récupère ces données :  
  
```sql  
SELECT a.* FROM OPENROWSET( BULK 'c:\test\values.txt',   
   FORMATFILE = 'c:\test\values.fmt') AS a;  
```  
  
### <a name="f-specifying-a-format-file-and-code-page"></a>F. Spécification d’une page format de fichier et le code  
 L’exemple suivant montre comment utiliser à la fois les fichiers et code page options de format en même temps.  
  
```sql  
INSERT INTO MyTable SELECT a.* FROM  
OPENROWSET (BULK N'D:\data.csv', FORMATFILE =   
    'D:\format_no_collation.txt', CODEPAGE = '65001') AS a;  
```  
### <a name="g-accessing-data-from-a-csv-file-with-a-format-file"></a>G. L’accès aux données à partir d’un fichier CSV avec un fichier de format  
**S’applique à :** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.   
```sql
SELECT *
FROM OPENROWSET(BULK N'D:\XChange\test-csv.csv',
    FORMATFILE = N'D:\XChange\test-csv.fmt', 
    FIRSTROW=2, 
    FORMAT='CSV') AS cars;  
```

### <a name="h-accessing-data-from-a-csv-file-without-a-format-file"></a>H. L’accès aux données à partir d’un fichier CSV sans fichier de format

```sql
SELECT * FROM OPENROWSET(
   BULK 'C:\Program Files\Microsoft SQL Server\MSSQL14.CTP1_1\MSSQL\DATA\inv-2017-01-19.csv',
   SINGLE_CLOB) AS DATA;
```

### <a name="i-accessing-data-from-a-file-stored-on-azure-blob-storage"></a>I. L’accès aux données à partir d’un fichier stocké sur le stockage d’objets Blob Azure   
**S’applique à :** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.   
L’exemple suivant utilise une source de données externe qui pointe vers un conteneur dans un compte de stockage Azure et les informations d’identification d’une étendue de la base de données créé pour la signature d’accès partagé.     

```sql
SELECT * FROM OPENROWSET(
   BULK  'inv-2017-01-19.csv',
   DATA_SOURCE = 'MyAzureInvoices',
   SINGLE_CLOB) AS DataFile;
```   
Pour terminer `OPENROWSET` des exemples, y compris la configuration de source de données externe, les informations d’identification, consultez [exemples d’accès en bloc à des données dans le stockage d’objets Blob Azure](../../relational-databases/import-export/examples-of-bulk-access-to-data-in-azure-blob-storage.md).
 
### <a name="additional-examples"></a>Autres exemples  
 Pour obtenir des exemples supplémentaires illustrant l’utilisation `INSERT...SELECT * FROM OPENROWSET(BULK...)`, consultez les rubriques suivantes :  
  
-   [Exemples d’importation et d’exportation en bloc de documents XML &#40;SQL Server&#41;](../../relational-databases/import-export/examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)  
  
-   [Conserver des valeurs d’identité lors de l’importation de données en bloc &#40;SQL Server&#41;](../../relational-databases/import-export/keep-identity-values-when-bulk-importing-data-sql-server.md)  
  
-   [Conserver les valeurs NULL ou utiliser la valeur par défaut lors de l’importation en bloc &#40;SQL Server&#41;](../../relational-databases/import-export/keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
-   [Utiliser un fichier de format pour importer des données en bloc &#40;SQL Server&#41;](../../relational-databases/import-export/use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [Utiliser le format caractère pour importer ou exporter des données &#40;SQL Server&#41;](../../relational-databases/import-export/use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Utiliser un fichier de format pour ignorer une colonne de table &#40;SQL Server&#41;](../../relational-databases/import-export/use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
-   [Utiliser un fichier de format pour ignorer un champ de données &#40;SQL Server&#41;](../../relational-databases/import-export/use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
-   [Utiliser un fichier de format pour mapper les colonnes d’une table sur les champs d’un fichier de données &#40;SQL Server&#41;](../../relational-databases/import-export/use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
## <a name="see-also"></a>Voir aussi  
 [DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md)   
 [FROM &#40;Transact-SQL&#41;](../../t-sql/queries/from-transact-sql.md)   
 [Importation et exportation en bloc de données &#40;SQL Server&#41;](../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md)   
 [INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)   
 [OPENDATASOURCE &#40;Transact-SQL&#41;](../../t-sql/functions/opendatasource-transact-sql.md)   
 [OPENQUERY &#40; Transact-SQL &#41;](../../t-sql/functions/openquery-transact-sql.md)   
 [Fonctions rowset &#40; Transact-SQL &#41;](../../t-sql/functions/rowset-functions-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [sp_addlinkedserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)   
 [sp_serveroption &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-serveroption-transact-sql.md)   
 [UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md)   
 [OÙ &#40; Transact-SQL &#41;](../../t-sql/queries/where-transact-sql.md)  
  
  
