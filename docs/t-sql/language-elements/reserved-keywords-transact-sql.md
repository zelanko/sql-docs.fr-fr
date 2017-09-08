---
title: "Mots clés (Transact-SQL) réservés | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- ODBC function calls
- keywords [SQL Server], reserved
- reserved words [SQL Server]
- keywords [SQL Server]
ms.assetid: ed8b3e27-6796-40f0-aef3-0cac5e0e2418
caps.latest.revision: 53
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: efaa21099f422ae812168561351a359fc89f8e0d
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="reserved-keywords-transact-sql"></a>Réservé mots clés Transact-SQL
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise des mots clés réservés pour définir des bases de données, les manipuler et y accéder. Les mots clés réservés font partie de la grammaire du langage [!INCLUDE[tsql](../../includes/tsql-md.md)] utilisé par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour analyser et interpréter les lots et instructions [!INCLUDE[tsql](../../includes/tsql-md.md)]. Bien que, d'un point de vue syntaxique, il soit possible d'employer dans les scripts [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] des mots clés [!INCLUDE[tsql](../../includes/tsql-md.md)] réservés comme identificateurs et noms d'objets, ceci est réalisable uniquement en utilisant des identificateurs délimités.  
  
 Le tableau suivant répertorie les mots clés [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] réservés.  
  
||||  
|-|-|-|  
|ADD|EXTERNAL|PROCEDURE|  
|ALL|FETCH|PUBLIC|  
|ALTER|FILE|RAISERROR|  
|AND|FILLFACTOR|READ|  
|ANY|FOR|READTEXT|  
|AS|FOREIGN|RECONFIGURE|  
|ASC|FREETEXT|REFERENCES|  
|AUTHORIZATION|FREETEXTTABLE|REPLICATION|  
|BACKUP|FROM|RESTORE|  
|BEGIN|FULL|RESTRICT|  
|BETWEEN|FUNCTION|RETURN|  
|BREAK|GOTO|REVERT|  
|BROWSE|GRANT|REVOKE|  
|BULK|GROUP|RIGHT|  
|BY|HAVING|ROLLBACK|  
|CASCADE|HOLDLOCK|ROWCOUNT|  
|CASE|IDENTITY|ROWGUIDCOL|  
|CHECK|IDENTITY_INSERT|RULE|  
|CHECKPOINT|IDENTITYCOL|SAVE|  
|CLOSE|IF|SCHEMA|  
|CLUSTERED|IN|SECURITYAUDIT|  
|COALESCE|INDEX|SELECT|  
|COLLATE|INNER|SEMANTICKEYPHRASETABLE|  
|COLUMN|INSERT|SEMANTICSIMILARITYDETAILSTABLE|  
|COMMIT|INTERSECT|SEMANTICSIMILARITYTABLE|  
|COMPUTE|INTO|SESSION_USER|  
|CONSTRAINT|IS|SET|  
|CONTAINS|JOIN|SETUSER|  
|CONTAINSTABLE|KEY|SHUTDOWN|  
|CONTINUE|KILL|SOME|  
|CONVERT|LEFT|STATISTICS|  
|CREATE|LIKE|SYSTEM_USER|  
|CROSS|LINENO|TABLE|  
|CURRENT|LOAD|TABLESAMPLE|  
|CURRENT_DATE|MERGE|TEXTSIZE|  
|CURRENT_TIME|NATIONAL|THEN|  
|CURRENT_TIMESTAMP|NOCHECK|TO|  
|CURRENT_USER|NONCLUSTERED|Haut de la page|  
|CURSOR|NOT|TRAN|  
|DATABASE|NULL|TRANSACTION|  
|DBCC|NULLIF|TRIGGER|  
|DEALLOCATE|DE|TRUNCATE|  
|DECLARE|OFF|TRY_CONVERT|  
|DEFAULT|OFFSETS|TSEQUAL|  
|DELETE|ON|UNION|  
|DENY|OPEN|UNIQUE|  
|DESC|OPENDATASOURCE|UNPIVOT|  
|DISK|OPENQUERY|UPDATE|  
|DISTINCT|OPENROWSET|UPDATETEXT|  
|DISTRIBUTED|OPENXML|USE|  
|DOUBLE|OPTION|Utilisateur|  
|DROP|ou|VALUES|  
|DUMP|ORDER|VARYING|  
|ELSE|OUTER|VIEW|  
|END|OVER|WAITFOR|  
|ERRLVL|PERCENT|WHEN|  
|ESCAPE|PIVOT|WHERE|  
|EXCEPT|PLAN|WHILE|  
|EXEC|PRECISION|par|  
|Exécutez|PRIMARY|WITHIN GROUP|  
|EXISTS|PRINT|WRITETEXT|  
|EXIT|PROC||  
  
 De plus, la norme ISO définit une liste de mots clés réservés. Évitez d'utiliser des mots clés réservés ISO pour des identificateurs et des noms d'objets. La liste des mots clés réservés ODBC figurant dans le tableau ci-dessous est identique à celle des mots clés réservés ISO.  
  
> [!NOTE]  
>  La liste des mots clés réservés de norme ISO peut être parfois plus et parfois moins restrictive que la liste [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Par exemple, la liste de mots clés réservés ISO contient **INT**. que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'a pas besoin d'établir comme mot clé.  
  
 Les mots clés réservés [!INCLUDE[tsql](../../includes/tsql-md.md)] sont utilisables comme identificateurs ou comme noms de bases de données ou d'objets de base de données, tels que des tables, des colonnes, des vues, etc. Utilisez des identificateurs délimités ou entre guillemets. L'utilisation de mots clés réservés comme noms de variables et de paramètres de procédures stockées ne fait pas l'objet de restrictions.  
  
## <a name="odbc-reserved-keywords"></a>Mots clés réservés ODBC  
 Les mots suivants sont réservés et utilisés dans les appels de fonction ODBC. Ces mots ne limitent pas la grammaire minimale SQL ; cependant, pour garantir la compatibilité avec les pilotes qui gèrent la grammaire SQL de base, il est préférable que les applications ne les utilisent pas.  
  
 Voici la liste actuelle des mots clés réservés ODBC.  
  
||||  
|-|-|-|  
|**ABSOLU**|**EXEC**|**CHEVAUCHEMENTS**|  
|**ACTION**|**EXECUTE**|**REMPLISSAGE**|  
|**ADA**|**IL EXISTE**|**PARTIELLE**|  
|**AJOUTER**|**EXTERNAL**|**PASCAL**|  
|**ALL**|**EXTRAIRE**|**POSITION**|  
|**ALLOUER**|**FALSE**|**PRÉCISION**|  
|**ALTER**|**EXTRACTION**|**PRÉPARER**|  
|**AND**|**PREMIER**|**CONSERVER**|  
|**N’IMPORTE QUEL**|**FLOAT**|**PRIMARY**|  
|**SONT**|**POUR**|**PRÉCÉDENT**|  
|**AS**|**ÉTRANGÈRE**|**PRIVILÈGES**|  
|**ASC**|**FORTRAN**|**PROCÉDURE**|  
|**ASSERTION**|**TROUVÉ**|**PUBLIC**|  
|**AT**|**FROM**|**EN LECTURE**|  
|**AUTORISATION**|**FULL**|**RÉEL**|  
|**AVG**|**TÉLÉCHARGER**|**RÉFÉRENCES**|  
|**BEGIN**|**GLOBAL**|**RELATIF**|  
|**BETWEEN**|**ATTEINDRE**|**RESTREINDRE**|  
|**BITS**|**GOTO**|**REVOKE**|  
|**BIT_LENGTH**|**GRANT**|**RIGHT**|  
|**LES DEUX**|**GROUPE**|**RESTAURATION**|  
|**PAR**|**AVOIR**|**LIGNES**|  
|**CASCADE**|**HEURE**|**SCHÉMA**|  
|**MISES EN CASCADE**|**IDENTITÉ**|**DÉFILEMENT**|  
|**CAS**|**IMMÉDIATE**|**SECONDE**|  
|**CAST**|**IN**|**SECTION**|  
|**CATALOGUE**|**INCLURE**|**SELECT**|  
|**CHAR**|**INDEX**|**SESSION**|  
|**CHAR_LENGTH**|**INDICATEUR**|**SESSION_USER**|  
|**CARACTÈRE**|**AU DÉPART**|**ENSEMBLE**|  
|**CHARACTER_LENGTH**|**INTERNE**|**TAILLE**|  
|**VÉRIFICATION**|**ENTRÉE**|**SMALLINT**|  
|**FERMER**|**NON-RESPECT DE LA**|**CERTAINS**|  
|**FUSION**|**INSERT**|**ESPACE**|  
|**COPIES ASSEMBLÉES**|**INT**|**SQL**|  
|**CLASSEMENT**|**ENTIER**|**SQLCA**|  
|**COLONNE**|**INTERSECT**|**SQLCODE**|  
|**VALIDATION**|**INTERVALLE**|**SQLERROR**|  
|**SE CONNECTER**|**DANS**|**SQLSTATE**|  
|**CONNEXION**|**IS**|**SQLWARNING**|  
|**CONTRAINTE**|**ISOLATION**|**SUBSTRING**|  
|**CONTRAINTES**|**JOINDRE**|**SOMME**|  
|**CONTINUER**|**CLÉ**|**SYSTEM_USER**|  
|**CONVERTIR**|**LANGUAGE**|**TABLE**|  
|**CORRESPONDANT**|**DERNIÈRE**|**TEMPORAIRE**|  
|**NOMBRE**|**DÉBUT**|**PUIS**|  
|**CRÉER**|**LEFT**|**HEURE**|  
|**CROSS-**|**NIVEAU**|**HORODATEUR**|  
|**EN COURS**|**LIKE**|**TIMEZONE_HOUR**|  
|**CURRENT_DATE**|**LOCAL**|**TIMEZONE_MINUTE**|  
|**CURRENT_TIME**|**INFÉRIEURE**|**À**|  
|**CURRENT_TIMESTAMP**|**MATCH**|**DE FIN**|  
|**CURRENT_USER**|**MAX**|**TRANSACTION**|  
|**CURSEUR**|**MIN**|**TRADUIRE**|  
|**DATE**|**MINUTE**|**TRADUCTION**|  
|**JOUR**|**MODULE**|**LA FONCTION TRIM**|  
|**DÉSALLOUER**|**MOIS**|**TRUE**|  
|**DEC**|**NOMS**|**UNION**|  
|**DÉCIMAL**|**NATIONAL**|**UNIQUE**|  
|**DÉCLARER**|**NATURELLE**|**INCONNU**|  
|**PAR DÉFAUT**|**NCHAR**|**UPDATE**|  
|**PEUT ÊTRE DIFFÉRÉE**|**SUIVANT**|**SUPÉRIEUR**|  
|**DIFFÉRÉE**|**NO**|**UTILISATION**|  
|**DELETE**|**NONE**|**UTILISATEUR**|  
|**DESC**|**NOT**|**À L’AIDE DE**|  
|**DÉCRIRE**|**NULL**|**VALUE**|  
|**DESCRIPTEUR**|**NULLIF**|**VALEURS**|  
|**TESTS DE DIAGNOSTIC**|**NUMÉRIQUE**|**VARCHAR**|  
|**SE DÉCONNECTER**|**OCTET_LENGTH**|**VARIABLE**|  
|**DISTINCTES**|**DE**|**VUE**|  
|**DOMAINE**|**ON**|**LORSQUE**|  
|**DOUBLE**|**UNIQUEMENT**|**CHAQUE FOIS QUE**|  
|**DROP**|**OUVRIR**|**WHERE**|  
|**ELSE**|**OPTION**|**AVEC**|  
|**END**|**OR**|**TRAVAIL**|  
|**FIN-EXEC**|**COMMANDE**|**ÉCRITURE**|  
|**SÉQUENCE D’ÉCHAPPEMENT**|**EXTERNE**|**ANNÉE**|  
|**À L’EXCEPTION**|**SORTIE**|**ZONE**|  
|**(EXCEPTION)**|||  
  
## <a name="future-keywords"></a>Mots clés futurs  
 Les mots clés suivants sont susceptibles d'être réservés dans de futures versions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], lorsque de nouvelles fonctionnalités seront implémentées. Évitez d'utiliser ces mots comme identificateurs.  
  
||||  
|-|-|-|  
|ABSOLUTE|HOST|RELATIVE|  
|ACTION|HOUR|RELEASE|  
|ADMIN|IGNORE|RESULT|  
|AFTER|IMMEDIATE|RETURNS|  
|AGGREGATE|INDICATOR|ROLE|  
|ALIAS|INITIALIZE|ROLLUP|  
|ALLOCATE|INITIALLY|ROUTINE|  
|ARE|INOUT|ROW|  
|ARRAY|INPUT|ROWS|  
|ASENSITIVE|INT|SAVEPOINT|  
|ASSERTION|INTEGER|SCROLL|  
|ASYMMETRIC|INTERSECTION|SCOPE|  
|AT|INTERVAL|SEARCH|  
|ATOMIC|ISOLATION|SECOND|  
|BEFORE|ITERATE|SECTION|  
|BINARY|LANGUAGE|SENSITIVE|  
|BIT|LARGE|SEQUENCE|  
|BLOB|LAST|SESSION|  
|BOOLEAN|LATERAL|SETS|  
|BOTH|LEADING|SIMILAR|  
|BREADTH|LESS|SIZE|  
|CALL|LEVEL|SMALLINT|  
|CALLED|LIKE_REGEX|SPACE|  
|CARDINALITY|LIMIT|SPECIFIC|  
|CASCADED|LN|SPECIFICTYPE|  
|CAST|LOCAL|SQL|  
|CATALOG|LOCALTIME|SQLEXCEPTION|  
|CHAR|LOCALTIMESTAMP|SQLSTATE|  
|CHARACTER|LOCATOR|SQLWARNING|  
|CLASS|MAP|START|  
|CLOB|MATCH|STATE|  
|COLLATION|MEMBER|STATEMENT|  
|COLLECT|METHOD|STATIC|  
|COMPLETION|MINUTE|STDDEV_POP|  
|CONDITION|MOD|STDDEV_SAMP|  
|CONNECT|MODIFIES|STRUCTURE|  
|CONNECTION|MODIFY|SUBMULTISET|  
|CONSTRAINTS|MODULE|SUBSTRING_REGEX|  
|CONSTRUCTOR|MONTH|SYMMETRIC|  
|CORR|MULTISET|SYSTEM|  
|CORRESPONDING|NAMES|TEMPORARY|  
|COVAR_POP|NATURAL|TERMINATE|  
|COVAR_SAMP|NCHAR|THAN|  
|CUBE|NCLOB|TIME|  
|CUME_DIST|NEW|timestamp|  
|CURRENT_CATALOG|NEXT|TIMEZONE_HOUR|  
|CURRENT_DEFAULT_TRANSFORM_GROUP|Non|TIMEZONE_MINUTE|  
|CURRENT_PATH|Aucune|TRAILING|  
|CURRENT_ROLE|NORMALIZE|TRANSLATE_REGEX|  
|CURRENT_SCHEMA|NUMERIC|TRANSLATION|  
|CURRENT_TRANSFORM_GROUP_FOR_TYPE|OBJECT|TREAT|  
|CYCLE|OCCURRENCES_REGEX|TRUE|  
|DATA|OLD|UESCAPE|  
|DATE|ONLY|UNDER|  
|DAY|OPERATION|UNKNOWN|  
|DEC|ORDINALITY|UNNEST|  
|DECIMAL|OUT|USAGE|  
|DEFERRABLE|OVERLAY|USING|  
|DEFERRED|OUTPUT|Value|  
|DEPTH|PAD|VAR_POP|  
|DEREF|Paramètre|VAR_SAMP|  
|DESCRIBE|PARAMETERS|VARCHAR|  
|DESCRIPTOR|PARTIAL|VARIABLE|  
|DESTROY|PARTITION|WHENEVER|  
|DESTRUCTOR|PATH|WIDTH_BUCKET|  
|DETERMINISTIC|POSTFIX|WITHOUT|  
|DICTIONARY|PREFIX|WINDOW|  
|DIAGNOSTICS|PREORDER|WITHIN|  
|DISCONNECT|PREPARE|WORK|  
|DOMAIN|PERCENT_RANK|WRITE|  
|DYNAMIC|PERCENTILE_CONT|XMLAGG|  
|EACH|PERCENTILE_DISC|XMLATTRIBUTES|  
|ELEMENT|POSITION_REGEX|XMLBINARY|  
|END-EXEC|PRESERVE|XMLCAST|  
|EQUALS|PRIOR|XMLCOMMENT|  
|EVERY|PRIVILEGES|XMLCONCAT|  
|EXCEPTION|RANGE|XMLDOCUMENT|  
|FALSE|READS|XMLELEMENT|  
|FILTER|REAL|XMLEXISTS|  
|FIRST|RECURSIVE|XMLFOREST|  
|FLOAT|REF|XMLITERATE|  
|FOUND|REFERENCING|XMLNAMESPACES|  
|GRATUIT|REGR_AVGX|XMLPARSE|  
|FULLTEXTTABLE|REGR_AVGY|XMLPI|  
|FUSION|REGR_COUNT|XMLQUERY|  
|GENERAL|REGR_INTERCEPT|XMLSERIALIZE|  
|GET|REGR_R2|XMLTABLE|  
|GLOBAL|REGR_SLOPE|XMLTEXT|  
|GO|REGR_SXX|XMLVALIDATE|  
|GROUPING|REGR_SXY|YEAR|  
|HOLD|REGR_SYY|ZONE|  
  
## <a name="see-also"></a>Voir aussi  
 [SET QUOTED_IDENTIFIER &#40; Transact-SQL &#41;](../../t-sql/statements/set-quoted-identifier-transact-sql.md)   
 [Niveau de compatibilité ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)  
  
  
