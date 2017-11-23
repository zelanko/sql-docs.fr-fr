---
title: "CRÉER un FORMAT de fichier externe (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 08/29/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, pdw, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE EXTERNAL FILE FORMAT
- CREATE_EXTERNAL_FILE_FORMAT
dev_langs: TSQL
helpviewer_keywords:
- External
- External, file format
- PolyBase, external file format
ms.assetid: abd5ec8c-1a0e-4d38-a374-8ce3401bc60c
caps.latest.revision: "25"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 037f9e0da637b872298d3859499858620570bc41
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="create-external-file-format-transact-sql"></a>CRÉER un FORMAT de fichier externe (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Crée une définition de format de fichier externe PolyBase pour données externes stockées dans Hadoop, le stockage d’objets blob Azure ou Azure Data Lake Store. Création d’un format de fichier externe est un composant requis pour la création d’une table externe PolyBase. En créant un format de fichier externe, vous spécifiez la disposition réelle des données référencées par une table externe.  
  
 PolyBase prend en charge ces formats de fichier :  
  
-   Texte délimité  
  
-   La ruche RCFile  
  
-   La ruche ORC  
  
-   Parquet  
  
 Pour créer une table externe, consultez [CREATE EXTERNAL TABLE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-external-table-transact-sql.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- Create an external file format for PARQUET files.  
CREATE EXTERNAL FILE FORMAT file_format_name  
WITH (  
    FORMAT_TYPE = PARQUET  
     [ , DATA_COMPRESSION = {  
        'org.apache.hadoop.io.compress.SnappyCodec'  
      | 'org.apache.hadoop.io.compress.GzipCodec'      }  
    ]);  
  
--Create an external file format for ORC files.  
CREATE EXTERNAL FILE FORMAT file_format_name  
WITH (  
    FORMAT_TYPE = ORC  
     [ , DATA_COMPRESSION = {  
        'org.apache.hadoop.io.compress.SnappyCodec'  
      | 'org.apache.hadoop.io.compress.DefaultCodec'      }  
    ]);  
  
--Create an external file format for RCFILE.  
CREATE EXTERNAL FILE FORMAT file_format_name  
WITH (  
    FORMAT_TYPE = RCFILE,  
    SERDE_METHOD = {  
        'org.apache.hadoop.hive.serde2.columnar.LazyBinaryColumnarSerDe'  
      | 'org.apache.hadoop.hive.serde2.columnar.ColumnarSerDe'  
    }  
    [ , DATA_COMPRESSION = 'org.apache.hadoop.io.compress.DefaultCodec' ]);  
  
--Create an external file format for DELIMITED TEXT files.  
CREATE EXTERNAL FILE FORMAT file_format_name  
WITH (  
    FORMAT_TYPE = DELIMITEDTEXT  
    [ , FORMAT_OPTIONS ( <format_options> [ ,...n  ] ) ]  
    [ , DATA_COMPRESSION = {  
           'org.apache.hadoop.io.compress.GzipCodec'  
         | 'org.apache.hadoop.io.compress.DefaultCodec'  
        }  
     ]);  
  
<format_options> ::=  
{  
    FIELD_TERMINATOR = field_terminator  
    | STRING_DELIMITER = string_delimiter  
    | DATE_FORMAT = datetime_format  
    | USE_TYPE_DEFAULT = { TRUE | FALSE } 
    | Encoding = {'UTF8' | 'UTF16'} 
}  
```  
  
## <a name="arguments"></a>Arguments  
 *file_format_name*  
 Spécifie un nom pour le format de fichier externe.  
  
 FORMAT_TYPE  
 Spécifie le format des données externes.  
  
 PARQUET  
 Spécifie un format Parquet.  
  
 ORC  
 Spécifie un format optimisé lignes en colonnes (ORC). Cette option requiert la ruche version 0,11 ou une version ultérieure sur le cluster Hadoop externe. Dans Hadoop, le format de fichier ORC offre une meilleure compression et performances que le format de fichier RCFILE.  
  
 RCFILE (en association avec SERDE_METHOD = *SERDE_method*)  
 Spécifie un format de fichier (RcFile) enregistrement en colonnes. Cette option nécessite que vous permet de spécifier un sérialiseur de la ruche et la méthode de désérialiseur (SerDe). Cette exigence est le même si vous utilisez Hive/HiveQL dans Hadoop pour interroger les fichiers RC. Notez que la méthode SerDe respecte la casse.  
  
 Exemples de spécification RCFile avec les deux méthodes de SerDe PolyBase prend en charge.  
  
-   FORMAT_TYPE = RCFILE, SERDE_METHOD = 'org.apache.hadoop.hive.serde2.columnar.LazyBinaryColumnarSerDe'  
  
-   FORMAT_TYPE = RCFILE, SERDE_METHOD = 'org.apache.hadoop.hive.serde2.columnar.ColumnarSerDe'  
  
 DELIMITEDTEXT  
 Spécifie un format de texte avec des séparateurs de colonnes, également appelés terminateurs de champ.  
  
 Indicateur_fin_de_champ = *indicateur_fin_de_champ*  
 S’applique uniquement aux fichiers texte délimités. Spécifie un ou plusieurs caractères marquant la fin de chaque champ (colonne) dans le fichier texte délimité. La valeur par défaut est le ꞌ de caractère de canal | ꞌ. Pour garantie prise en charge, nous vous recommandons d’utiliser un ou plusieurs caractères ascii.
  
  
 Exemples :  
  
-   INDICATEUR_FIN_DE_CHAMP = ' |'  
  
-   INDICATEUR_FIN_DE_CHAMP = ' '  
  
-   Indicateur_fin_de_champ = ꞌ\tꞌ  
  
-   INDICATEUR_FIN_DE_CHAMP = ' ~ | ~'  
  
 STRING_DELIMITER = *string_delimiter*  
 Spécifie l’indicateur de fin de champ pour les données de type chaîne dans le fichier texte délimité. Le délimiteur de chaîne est un ou plusieurs caractères et est encadré par des guillemets simples. La valeur par défaut est une chaîne vide « ». Pour garantie prise en charge, nous vous recommandons d’utiliser un ou plusieurs caractères ascii.
 
  
 Exemples :  

-   STRING_DELIMITER = ' » '

-   STRING_DELIMITER = '0 x 22'--hex de guillemets doubles
  
-   STRING_DELIMITER = ' *'  
  
-   STRING_DELIMITER = Ꞌ, Ꞌ  
  
-   STRING_DELIMITER = '0x7E0x7E'--deux tildas (par exemple, ~ ~)
  
 Date_format = *datetime_format*  
 Spécifie un format personnalisé pour toutes les données de date et d’heure qui peuvent apparaître dans un fichier texte délimité. Si le fichier source utilise des formats de datefime par défaut, cette option n’est pas nécessaire. Un seul format de date/heure personnalisé est autorisé par fichier. Vous ne pouvez pas spécifier plusieurs formats de date/heure personnalisé par fichier. Toutefois, vous pouvez utiliser plusieurs formats de date/heure si chacun d’eux est le format par défaut pour son type de données respectifs dans la définition de table externe.
 
 
PolyBase utilise uniquement le format de date personnalisée pour l’importation des données. Il n’utilise pas le format personnalisé pour l’écriture de données dans un fichier externe.

 Lorsque DATE_FORMAT n’est pas spécifié ou est une chaîne vide, PolyBase utilise les formats par défaut suivantes :  
  
-   Date et heure : « AAAA-MM-JJ HH : mm : »  
  
-   SmallDateTime : « AAAA-MM-JJ HH : mm'  
  
-   Date : « AAAA-MM-jj'  
  
-   DateTime2 : « AAAA-MM-JJ HH : mm : »  
  
-   DateTimeOffset : « AAAA-MM-JJ HH : mm : »  
  
-   Durée : « hh : mm : »  
  
 **Exemples de formats de date** se trouvent dans le tableau suivant.  
  
 Remarques sur la table :  
  
-   Année, mois et jour peuvent avoir une variété de formats et de commandes. Le tableau présente uniquement ymd. Mois peut avoir les chiffres de 1 ou 2 ou 3 caractères. Jour peut avoir 1 ou 2 chiffres. Année peut comporter 2 ou 4 chiffres.  
  
-   Millisecondes (fffffff) n’est pas nécessaire.  
  
-   AM, pm (tt) n’est pas obligatoire. La valeur par défaut est AM.  
  
|Type de date|Exemple| Description|  
|---------------|-------------|-----------------|  
|DateTime|Date_format = 'AAAA-MM-JJ HH:mm:ss.fff'|Outre l’année, mois et jour, cela inclut 00-24 heures, de 00 à 59 minutes, de 00 à 59 secondes et 3 chiffres pour les millisecondes.|  
|DateTime|Date_format = 'AAAA-MM-JJ hh:mm:ss.ffftt'|Outre l’année, mois et jour, cela inclut 00-12 heures, de 00 à 59 minutes, de 00 à 59 secondes, 3 chiffres pour les millisecondes et AM, am, PM ou pm.|  
|SmallDateTime|Date_format = « AAAA-MM-JJ HH : mm »|Outre l’année, mois et jour, cela inclut entre 00 et 23 heures, de 00 à 59 minutes.|  
|SmallDateTime|Date_format = 'AAAA-MM-JJ hh:mmtt'|Outre l’année, mois et jour, cela inclut 11 : 00 heures, 00 à 59 minutes, aucun secondes et AM, le am, PM ou pm.|  
|Date|Date_format = « AAAA-MM-JJ »|Année, mois et jour. Aucun élément d’heure n’est inclus.|  
|Date|Date_format = « AAAA-MMM-JJ »|Année, mois et jour. Lorsque le mois est spécifiée avec de 3 M, la valeur d’entrée est une ou les chaînes de janvier, février, Mar, avril, mai, juin, juillet, août, septembre, octobre, novembre ou décembre.|  
|datetime2|Date_format = 'AAAA-MM-JJ ss.fffffff'|Outre l’année, mois et jour, cela inclut entre 00 et 23 heures, de 00 à 59 minutes, de 00 à 59 secondes et 7 chiffres pour les millisecondes.|  
|datetime2|Date_format = 'AAAA-MM-JJ hh:mm:ss.ffffffftt'|Outre l’année, mois et jour, cela inclut 11 : 00 heures, de 00 à 59 minutes, de 00 à 59 secondes, 7 chiffres pour les millisecondes et AM, am, PM ou pm.|  
|DateTimeOffset|Date_format = 'AAAA-MM-JJ : ss.fffffff zzz'|Outre l’année, mois et jour, cela inclut entre 00 et 23 heures, de 00 à 59 minutes, de 00 à 59 secondes et 7 chiffres de millisecondes et le décalage de fuseau horaire qui vous placer dans le fichier d’entrée en tant que {+ &#124;-} HH:ss. Par exemple, depuis l’heure à Los Angeles sans l’heure d’été épargne est de 8 heures après l’heure UTC, une valeur de -08:00, dans le fichier d’entrée spécifie le fuseau horaire de Los Angeles.|  
|DateTimeOffset|Date_format = 'AAAA-MM-JJ hh:mm:ss.ffffffftt zzz'|Outre l’année, mois et jour, cela inclut 11 : 00 heures, de 00 à 59 minutes, de 00 à 59 secondes, 7 chiffres pour les millisecondes, (AM, am, PM ou pm) et le décalage de fuseau horaire. Consultez la description de la ligne précédente.|  
|Time|Date_format = 'HH : mm :'|Il n’existe aucune valeur de date, uniquement de 00 à 23 heures, de 00 à 59 minutes, de 00 à 59 secondes.|  
  
 Tous les formats de date pris en charge :  
  
|datetime|smalldatetime|date|datetime2|datetimeoffset|  
|--------------|-------------------|----------|---------------|--------------------|  
|[M [M]] M-[d] [aa] d-yy HH : mm : [.fff]|[M [M]] M-[d] [aa] d-yy HH : mm [ : 00]|[M [M]] M-[d] d-[aa] AA|[M [M]] M-[d] [aa] d-yy HH : mm : [.fffffff]|[M [M]] M-[d] [aa] d-yy HH : mm : [.fffffff] zzz|  
|[M [M]] M-[d] [aa] d-yy HH : mm : [.fff] [tt]|[M [M]] M-[d] [aa] d-yy HH : mm [ : 00] [tt]||[M [M]] M-[d] [aa] d-yy HH : mm : [.fffffff] [tt]|[M [M]] M-[d] [aa] d-yy HH : mm : [.fffffff] [tt] zzz|  
|[M [M]] M [aa] AA-[d]-d hh : mm : [.fff]|[M [M]] M [aa] AA-[d]-d hh : mm [ : 00]|[M [M]] M [aa] AA-[d]-d|[M [M]] M [aa] AA-[d]-d hh : mm : [.fffffff]|[M [M]] M [aa] AA-[d]-d hh : mm : [.fffffff] zzz|  
|[M [M]] M-[aa] AA-[d] HH : mm : d [.fff] [tt]|[M [M]] M-[aa] AA-[d] HH : mm d [ : 00] [tt]||[M [M]] M-[aa] AA-[d] HH : mm : d [.fffffff] [tt]|[M [M]] M-[aa] AA-[d] HH : mm : d [.fffffff] [tt] zzz|  
|[aa] AA-[M [M]] [d] M-d hh : mm : [.fff]|[aa] AA-[M [M]] [d] M-d hh : mm [ : 00]|[aa] AA-[M [M]] [d] M-d|[aa] AA-[M [M]] [d] M-d hh : mm : [.fffffff]|[aa] AA-[M [M]] HH : mm : d [.fffffff] zzz de M-[d]|  
|[aa] AA-[M [M]] [d] M-d hh : mm : [.fff] [tt]|[aa] AA-[M [M]] [d] M-d hh : mm [ : 00] [tt]||[aa] AA-[M [M]] [d] M-d hh : mm : [.fffffff] [tt]|[aa] AA-[M [M]] [d] M-d hh : mm : [.fffffff] [tt] zzz|  
|[aa] AA-[d] [M [M]] d-M hh : mm : [.fff]|[aa] AA-[d] [M [M]] d-M hh : mm [ : 00]|[aa] AA - d [d]-[M [M]] M|[aa] AA-[d] [M [M]] d-M hh : mm : [.fffffff]|[aa] AA-[d] M hh : mm : [.fffffff] zzz de d-[M [M]]|  
|[aa] AA-[d] [M [M]] d-M hh : mm : [.fff] [tt]|[aa] AA-[d] [M [M]] d-M hh : mm [ : 00] [tt]||[aa] AA-[d] [M [M]] d-M hh : mm : [.fffffff] [tt]|[aa] AA-[d] [M [M]] d-M hh : mm : [.fffffff] [tt] zzz|  
|[d] [M [M]] d-M-[aa] AA HH : mm : [.fff]|[d] [M [M]] d-M-[aa] AA HH : mm [ : 00]|[d] [M [M]] d-M-[aa] AA|[d] [M [M]] d-M-[aa] AA HH : mm : [.fffffff]|[d] [M [M]] d-M-[aa] AA HH : mm : [.fffffff] zzz|  
|[d] [M [M]] d-M-[aa] AA HH : mm : [.fff] [tt]|[d] [M [M]] d-M-[aa] AA HH : mm [ : 00] [tt]||[d] [M [M]] d-M-[aa] AA HH : mm : [.fffffff] [tt]|[d] [M [M]] d-M-[aa] AA HH : mm : [.fffffff] [tt] zzz|  
|d [d]-[aa] AA-[M [M]] M hh : mm : [.fff]|d [d]-[aa] AA-[M [M]] M hh : mm [ : 00]|d [d]-[aa] AA-[M [M]] M|d [d]-[aa] AA-[M [M]] M hh : mm : [.fffffff]|[d] d-[aa] AA-[M [M]] M hh : mm : [.fffffff] zzz|  
|[d] d-[aa] AA-[M [M]] M hh : mm : [.fff] [tt]|[d] d-[aa] AA-[M [M]] M hh : mm [ : 00] [tt]||[d] d-[aa] AA-[M [M]] M hh : mm : [.fffffff] [tt]|[d] d-[aa] AA-[M [M]] M hh : mm : [.fffffff] [tt] zzz|  
  
 Détails :  
  
-   Pour séparer les valeurs mois, jour et année, vous pouvez utiliser ':', '/' ou '. '. Par souci de simplicité, la table utilise uniquement le séparateur ':'.  
  
-   Pour spécifier le mois sous forme de texte utilisez trois caractères ou plus. Mois avec 1 ou 2 caractères seront interprétés comme un nombre.  
  
-   Pour séparer les valeurs d’heure, utilisez le ' : ' symbole.  
  
-   Lettres entourés crochets sont facultatifs.  
  
-   Les lettres « tt » désigner [AM | PM | am | pm]. AM est la valeur par défaut. Lorsque « tt » est spécifié, la valeur d’heure (hh) doit être dans la plage de 0 à 12.  
  
-   Les lettres « zzz » désigne le décalage de fuseau horaire pour fuseau horaire du système dans le format {+ |-} HH:ss].  
  
 USE_TYPE_DEFAULT = {TRUE | **FALSE** }  
 Spécifie comment gérer les valeurs manquantes dans les fichiers texte délimités lorsque PolyBase récupère les données à partir du fichier texte.  
  
 TRUE  
 Lors de la récupération des données à partir du fichier texte, stocker chaque valeur manquante à l’aide de la valeur par défaut pour le type de données de la colonne correspondante dans la définition de table externe. Par exemple, remplacez une valeur manquante avec :  
  
-   0 si la colonne est définie comme une colonne numérique.  
  
-   Une chaîne vide « » si la colonne est une colonne de chaîne.  
  
-   1900-01-01 si la colonne est une colonne de date.  
  
 FALSE  
 Stocker toutes les valeurs manquantes en tant que valeur NULL. Les valeurs NULL sont stockées en utilisant le mot NULL dans le fichier texte délimité seront importés en tant que la chaîne « NULL ».  
  
   Encodage = {'UTF8' | 'UTF16'}   
 Dans Azure SQL Data Warehouse PolyBase peut lire fichiers texte délimités, UTF8 et UTF16-LE encodé. Dans SQL Server et PDW, PolyBase ne prend pas en charge la lecture UTF16 fichiers codés.
  
 DATA_COMPRESSION = *data_compression_method*  
 Spécifie la méthode de compression de données pour les données externes. Lorsque DATA_COMPRESSION n’est pas spécifié, la valeur par défaut est données non compressées.  
 Afin de fonctionner correctement, les fichiers Gzip compressée doivent avoir l’extension de fichier « .gz ».
 
 Le type de format DELIMITEDTEXT prend en charge ces méthodes de compression :  
  
-   La COMPRESSION de données = 'org.apache.hadoop.io.compress.DefaultCodec'  
  
-   La COMPRESSION de données = 'org.apache.hadoop.io.compress.GzipCodec'  

 Le type de format RCFILE prend en charge cette méthode de compression :  
  
-   La COMPRESSION de données = 'org.apache.hadoop.io.compress.DefaultCodec'  
  
 Le type de format de fichier ORC prend en charge ces méthodes de compression :  
  
-   La COMPRESSION de données = 'org.apache.hadoop.io.compress.DefaultCodec'  
  
-   La COMPRESSION de données = 'org.apache.hadoop.io.compress.SnappyCodec'  
  
 Le type de format de fichier PARQUET prend en charge ces méthodes de compression :  
  
-   La COMPRESSION de données = 'org.apache.hadoop.io.compress.GzipCodec'  
  
-   La COMPRESSION de données = 'org.apache.hadoop.io.compress.SnappyCodec'  
  
## <a name="permissions"></a>Permissions  
 Nécessite l’autorisation ALTER ANY EXTERNAL FILE FORMAT.  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
 Le format de fichier externe est étendue de base de données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]. Il est à portée de serveur dans [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
  
 Les options de format sont tous facultatifs et s’appliquent uniquement aux fichiers texte délimités.  
  
 Lorsque les données sont stockées dans un des formats compressés, PolyBase sera décompresser tout d’abord les données avant de retourner les enregistrements de données.  
  
## <a name="limitations-and-restrictions"></a>Limitations et restrictions   
  
 Le séparateur de lignes dans les fichiers texte délimités doive être pris en charge par LineRecordReader de Hadoop autrement dit, il doit être soit '\r', '\n' ou '\r\n'. Ils ne sont pas configurables par l’utilisateur.  
  
 Les combinaisons de méthodes SerDe prises en charge avec RCFiles et les méthodes de compression de données pris en charge sont répertoriés précédemment dans cet article. Toutes les combinaisons ne sont pris en charge.  
  
 Le nombre maximal de requêtes simultanées de PolyBase est 32. Lorsque 32 requêtes simultanées sont en cours d’exécution, chaque requête peut lire un maximum de 33 000 fichiers à partir de l’emplacement du fichier externe. Le dossier racine et chaque sous-dossier comptent également en tant que fichier. Si le degré de concurrence est inférieure à 32, l’emplacement du fichier externe peut contenir plus de 33 000 fichiers.  
  
 En raison de la limitation sur le nombre de fichiers dans la table externe, nous vous recommandons de stockage inférieur à 30 000 fichiers à la racine et les sous-dossiers de l’emplacement de fichier externe. En outre, nous vous recommandons de conserver le nombre de sous-dossiers dans le répertoire racine pour un petit nombre. Lorsque de trop de fichiers sont référencés une exception d’insuffisance de mémoire de Machine virtuelle Java peut se produire.  
  
## <a name="locking"></a>Verrouillage  
 Acquiert un verrou partagé sur l’objet de FORMAT de fichier externe.  
  
## <a name="performance"></a>Performance  
 À l’aide de fichiers compressés toujours s’accompagne le compromis entre le transfert moins de données entre la source de données externe et SQL Server, tout en augmentant l’utilisation du processeur pour compresser et décompresser les données.  
  
 GZip compressées des fichiers texte ne sont pas partageables. Pour améliorer les performances pour les fichiers de texte Gzip compressées, nous vous recommandons de générer plusieurs fichiers sont stockés dans le même répertoire au sein de la source de données externe. Cela permet à PolyBase de lire et de décompresser les données plus rapides à l’aide de plusieurs processus du lecteur et la décompression. Le nombre idéal de fichiers compressés est le nombre maximal de processus du lecteur de données par nœud de calcul. Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], le nombre maximal de processus du lecteur de données est 8 par nœud dans la version actuelle. Dans [!INCLUDE[ssSDW](../../includes/sssdw-md.md)], le nombre maximal de processus du lecteur de données par nœud varie selon les objectifs du contrat. Consultez [Azure SQL Data Warehouse lors du chargement des modèles et stratégies](https://blogs.msdn.microsoft.com/sqlcat/2016/02/06/azure-sql-data-warehouse-loading-patterns-and-strategies/) pour plus d’informations.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-create-a-delimitedtext-external-file-format"></a>A. Créer un format de fichier externe DELIMITEDTEXT  
 Cet exemple crée un format de fichier externe nommé *textdelimited1* pour un fichier délimité par du texte. Le FORMAT_OPTIONS spécifier les champs dans le fichier seront séparés par une barre verticale « | ». Le fichier texte est également compressé avec le codec Gzip. Si DATA_COMPRESSION n’est pas spécifié, le fichier texte est décompressé.  
  
 Pour un fichier texte délimité, la méthode de compression de données peut être la valeur par défaut du Codec, 'org.apache.hadoop.io.compress.DefaultCodec' ou le Gzip Codec, 'org.apache.hadoop.io.compress.GzipCodec'.  
  
```  
CREATE EXTERNAL FILE FORMAT textdelimited1  
WITH (  
    FORMAT_TYPE = DELIMITEDTEXT,  
    FORMAT_OPTIONS (  
        FIELD_TERMINATOR = '|',  
        DATE_FORMAT = 'MM/dd/yyyy' ),  
    DATA_COMPRESSION = 'org.apache.hadoop.io.compress.GzipCodec'  
);  
```  
  
### <a name="b-create-an-rcfile-external-file-format"></a>B. Créer un format de fichier externe RCFile  
 Cet exemple crée un format de fichier externe pour un RCFile qui utilise le org.apache.hadoop.hive.serde2.columnar.LazyBinaryColumnarSerDe de méthode de sérialisation/désérialisation. Il spécifie également pour utiliser le Codec par défaut pour la méthode de compression de données. Si DATA_COMPRESSION n’est pas spécifié, la valeur par défaut n’est aucune compression.  
  
```  
CREATE EXTERNAL FILE FORMAT rcfile1  
WITH (  
    FORMAT_TYPE = RCFILE,  
    SERDE_METHOD = 'org.apache.hadoop.hive.serde2.columnar.LazyBinaryColumnarSerDe',  
    DATA_COMPRESSION = 'org.apache.hadoop.io.compress.DefaultCodec'  
);  
```  
  
### <a name="c-create-an-orc-external-file-format"></a>C. Créer un format de fichier externe ORC  
 Cet exemple crée un format de fichier externe pour un fichier ORC qui compresse les données avec la méthode de compression de données org.apache.io.compress.SnappyCodec. Si DATA_COMPRESSION n’est pas spécifié, la valeur par défaut n’est aucune compression.  
  
```  
CREATE EXTERNAL FILE FORMAT orcfile1  
WITH (  
    FORMAT_TYPE = ORC,  
    DATA_COMPRESSION = 'org.apache.hadoop.io.compress.SnappyCodec'  
);  
```  
  
### <a name="d-create-a-parquet-external-file-format"></a>D. Créer un format de fichier externe PARQUET  
 Cet exemple crée un format de fichier externe pour un fichier Parquet qui compresse les données avec la méthode de compression de données org.apache.io.compress.SnappyCodec. Si DATA_COMPRESSION n’est pas spécifié, la valeur par défaut n’est aucune compression.  
  
```  
CREATE EXTERNAL FILE FORMAT parquetfile1  
WITH (  
    FORMAT_TYPE = PARQUET,  
    DATA_COMPRESSION = 'org.apache.hadoop.io.compress.SnappyCodec'  
);  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE EXTERNAL DATA SOURCE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-data-source-transact-sql.md)   
 [CREATE EXTERNAL TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-table-transact-sql.md)   
 [CREATE EXTERNAL TABLE AS SELECT &#40; Transact-SQL &#41;](../../t-sql/statements/create-external-table-as-select-transact-sql.md)   
 [CREATE TABLE AS SELECT &#40; Entrepôt de données SQL Azure &#41;](../../t-sql/statements/create-table-as-select-azure-sql-data-warehouse.md)   
 [sys.external_file_formats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-external-file-formats-transact-sql.md)  
  
  
