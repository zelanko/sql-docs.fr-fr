---
title: "Indicateurs (Transact-SQL) de requête | Documents Microsoft"
ms.custom: 
ms.date: 08/09/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Query_Hint_TSQL
- Query_TSQL
- Query
- Query Hint
- MAX_GRANT_PERCENT
- MAX_GRANT_PERCENT_TSQL
- MIN_GRANT_PERCENT
- MIN_GRANT_PERCENT_TSQL
- EXTERNALPUSHDOWN
- EXTERNALPUSHDOWN_TSQL
- NOLOCK_TSQL
- MAXDOP_TSQL
- USE_HINT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- REPORT PLAN query hint
- FORCE ORDER query hint
- HASH JOIN query hint
- query hints [SQL Server]
- OPTIMIZE FOR query hint
- FORCESCAN query hint
- RECOMPILE query hint
- MAXRECURSION query hint
- MERGE JOIN query hint
- HASH GROUP query hint
- KEEP PLAN query hint
- UNION query hint
- FORCESEEK query hint
- ORDER GROUP query hint
- LOOP JOIN query hint
- KEEPFIXED PLAN query hint
- FAST query hint
- MAXDOP query hint
- PARAMETERIZATION query hint
- hints [SQL Server], query
- JOIN query hint
- USE PLAN query hint
- EXPAND VIEWS query hint
- MAX_GRANT_PERCENT query hint
- MIN_GRANT_PERCENT query hint
- EXTERNALPUSHDOWN query hint
- USE HINT query hint
ms.assetid: 66fb1520-dcdf-4aab-9ff1-7de8f79e5b2d
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: 0a3c74aa7b1da86c6d0ac54025d337700019465d
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="hints-transact-sql---query"></a>Indicateurs de requête (Transact-SQL) :
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Les indicateurs de requête spécifient que les indicateurs affichés doivent être utilisés dans l'ensemble de la requête. Ils affectent tous les opérateurs de l’instruction. Si une clause UNION se trouve dans la requête principale, seule la dernière requête impliquant une opération UNION peut avoir la clause OPTION. Indicateurs de requête sont spécifiés dans le cadre de la [clause OPTION](../../t-sql/queries/option-clause-transact-sql.md). Si un ou plusieurs indicateurs de requête empêchent l'optimiseur de requête de générer un plan valide, l'erreur 8622 est déclenchée.  
  
> [!CAUTION]  
>  Étant donné que l'optimiseur de requête [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sélectionne généralement le meilleur plan d'exécution pour une requête, nous recommandons de ne recourir aux indicateurs qu'en dernier ressort, et à condition d'être un développeur ou un administrateur de base de données expérimenté.  
  
 **S’applique à :**  
  
 [DELETE](../../t-sql/statements/delete-transact-sql.md)  
  
 [INSERT](../../t-sql/statements/insert-transact-sql.md)  
  
 [SELECT](../../t-sql/queries/select-transact-sql.md)  
  
 [UPDATE](../../t-sql/queries/update-transact-sql.md)  
  
 [MERGE](../../t-sql/statements/merge-transact-sql.md)  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<query_hint > ::=   
{ { HASH | ORDER } GROUP   
  | { CONCAT | HASH | MERGE } UNION   
  | { LOOP | MERGE | HASH } JOIN   
  | EXPAND VIEWS   
  | FAST number_rows   
  | FORCE ORDER   
  | { FORCE | DISABLE } EXTERNALPUSHDOWN  
  | IGNORE_NONCLUSTERED_COLUMNSTORE_INDEX  
  | KEEP PLAN   
  | KEEPFIXED PLAN  
  | MAX_GRANT_PERCENT = percent  
  | MIN_GRANT_PERCENT = percent  
  | MAXDOP number_of_processors   
  | MAXRECURSION number   
  | NO_PERFORMANCE_SPOOL   
  | OPTIMIZE FOR ( @variable_name { UNKNOWN | = literal_constant } [ , ...n ] )  
  | OPTIMIZE FOR UNKNOWN  
  | PARAMETERIZATION { SIMPLE | FORCED }  
  | RECOMPILE  
  | ROBUST PLAN   
  | USE HINT ( '<hint_name>' [ , ...n ] )
  | USE PLAN N'xml_plan'  | TABLE HINT ( exposed_object_name [ , <table_hint> [ [, ]...n ] ] )  
}  
  
<table_hint> ::=  
[ NOEXPAND ] {   
    INDEX ( index_value [ ,...n ] ) | INDEX = ( index_value )  
  | FORCESEEK [( index_value ( index_column_name [,... ] ) ) ]  
  | FORCESCAN  
  | HOLDLOCK   
  | NOLOCK   
  | NOWAIT  
  | PAGLOCK   
  | READCOMMITTED   
  | READCOMMITTEDLOCK   
  | READPAST   
  | READUNCOMMITTED   
  | REPEATABLEREAD   
  | ROWLOCK   
  | SERIALIZABLE   
  | SNAPSHOT  
  | SPATIAL_WINDOW_MAX_CELLS = integer  
  | TABLOCK   
  | TABLOCKX   
  | UPDLOCK   
  | XLOCK  
}  
```  
  
## <a name="arguments"></a>Arguments  
 { HASH | ORDER } GROUP  
 Indique que les agrégations décrites dans la clause GROUP BY ou DISTINCT de la requête doivent utiliser le hachage ou le tri.  
  
 { MERGE | HASH | CONCAT } UNION  
 Indique que toutes les opérations UNION sont effectuées par fusion, hachage ou concaténation d'ensembles UNION. Si plusieurs indicateurs UNION sont spécifiées, l'optimiseur sélectionne la stratégie la moins coûteuse parmi les indicateurs spécifiés.  
  
 { LOOP | MERGE | HASH } JOIN  
 Spécifie que toutes les opérations de jointure sont effectuées par LOOP JOIN, MERGE JOIN ou HASH JOIN dans toute la requête. Si plusieurs indicateurs de jointure sont spécifiés, l'optimiseur sélectionne la stratégie la moins coûteuse parmi celles qui sont autorisées.  
  
 Si, dans la même requête, un indicateur de jointure est également spécifié dans la clause FROM pour une paire de tables particulière, il a la priorité sur la jointure des deux tables, même s'il reste à honorer les indicateurs de requête. Ainsi, l'indicateur de jointure de la paire de tables peut seulement restreindre la sélection des méthodes de jointure autorisées dans l'indicateur de requête. Pour plus d’informations, consultez [indicateurs de jointure &#40; Transact-SQL &#41; ](../../t-sql/queries/hints-transact-sql-join.md).  
  
 EXPAND VIEWS  
 Spécifie que les vues indexées sont développées et que l'optimiseur de requête ne considère pas une vue indexée en tant que substitut d'une partie de la requête. Une vue est développée lorsque son nom est remplacé par sa définition dans le texte de la requête.  
  
 Cet indicateur de requête interdit virtuellement l'utilisation directe de vues indexées et d'index sur des vues indexées dans le plan de requête.  
  
 La vue indexée n’est pas développée uniquement si la vue est directement référencée dans la partie SELECT de la requête et de WITH (NOEXPAND) ou de WITH (NOEXPAND, INDEX ( *index_value* [**, ***.. .n* ])) est spécifié. Pour plus d’informations sur l’indicateur de requête WITH (NOEXPAND), consultez [FROM](../../t-sql/queries/from-transact-sql.md).  
  
 Seules les vues dans la partie SELECT des instructions, y compris celles figurant dans les instructions INSERT, UPDATE, MERGE et DELETE, sont affectées par l'indicateur.  
  
 FAST *number_rows*  
 Spécifie que la requête est optimisée pour la récupération rapide du premier *nombre_de_lignes.* Il s’agit d’un entier non négatif. Après la première *nombre_de_lignes* sont retournées, la requête poursuit l’exécution et génère le jeu de résultats complet.  
  
 FORCE ORDER  
 Spécifie que l'ordre de jointure spécifié dans la syntaxe de la requête est conservé au cours de l'optimisation de la requête. L'utilisation de FORCE ORDER n'a aucun effet sur une éventuelle inversion des rôles de la part de l'optimiseur de requête.  
  
> [!NOTE]  
>  Dans une instruction MERGE, il convient d'accéder à la table source avant la table cible comme ordre de jointure par défaut, à moins que la clause WHEN SOURCE NOT MATCHED ne soit spécifiée. La spécification de FORCE ORDER préserve ce comportement par défaut.  
  
 {FORCE | DÉSACTIVER} EXTERNALPUSHDOWN  
 Forcer ou désactiver la poussée vers le bas du calcul de la qualification des expressions dans Hadoop. S’applique uniquement aux requêtes à l’aide de PolyBase. Pousse pas vers le bas dans le stockage Azure.  
  
 KEEP PLAN  
 Force l'optimiseur de requête à abaisser le seuil de recompilation estimé pour une requête. Le seuil de recompilation estimé correspond au point auquel la requête est automatiquement recompilée lorsque le nombre estimé de modifications de colonnes indexées a été apporté à une table en exécutant des instructions UPDATE, DELETE, MERGE ou INSERT. La spécification de KEEP PLAN permet de garantir qu'une requête n'est pas recompilée aussi fréquemment lorsque plusieurs mises à jour sont effectuées dans une table.  
  
 KEEPFIXED PLAN  
 Force l'optimiseur de requête à ne pas recompiler une requête en raison de modifications enregistrées au niveau des statistiques. Spécification de KEEPFIXED PLAN permet de s’assurer qu’une requête est recompilée seulement si le schéma des tables sous-jacentes est modifié ou si **sp_recompile** est exécutée sur ces tables.  
  
 IGNORE_NONCLUSTERED_COLUMNSTORE_INDEX  
 **S'applique à**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] jusqu'à [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Empêche que la requête à l’aide d’un index columnstore optimisé en mémoire non cluster. Si la requête contient l'indicateur de requête pour éviter l'utilisation de l'index columnstore et un indicateur d'index pour utiliser un index columnstore, les indicateurs sont en conflit et la requête retourne une erreur.  
  
 MAX_GRANT_PERCENT = *%*  
 Taille en pourcentage d’allocation de la mémoire maximale. La requête est assurée pour ne pas dépasser cette limite. La limite réelle peut être inférieure si le gouverneur de ressources configuration est inférieur à celle-ci. Les valeurs valides sont compris entre 0,0 et 100,0.  
  
**S'applique à**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] jusqu'à [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 MIN_GRANT_PERCENT = *%*  
 Taille en pourcentage d’allocation de la mémoire minimale = % de la limite par défaut. La requête est assurée de bénéficier de MAX (mémoire requise, min grant), car il est requis au moins la mémoire nécessaire pour démarrer une requête. Les valeurs valides sont compris entre 0,0 et 100,0.  
  
**S'applique à**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] jusqu'à [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 MAXDOP *nombre*  
 **S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] jusqu'à [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Remplace le **degré maximal de parallélisme** option de configuration de **sp_configure** et le gouverneur de ressources pour la spécification de cette option de requête. L'indicateur de requête MAXDOP peut dépasser la valeur configurée avec sp_configure. Si MAXDOP dépasse la valeur configurée avec le gouverneur de ressources, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] utilise la valeur du gouverneur de ressources MAXDOP, décrite dans [ALTER WORKLOAD GROUP &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-workload-group-transact-sql.md). Toutes les règles sémantiques utilisées avec les **degré maximal de parallélisme** option de configuration s’appliquent lorsque vous utilisez l’indicateur de requête MAXDOP. Pour plus d’informations, consultez [Configurer l’option de configuration du serveur Degré maximal de parallélisme](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md).  
  
> [!WARNING]  
> Si MAXDOP est défini avec la valeur zéro, le serveur choisit le degré maximal de parallélisme.  
  
 MAXRECURSION *nombre*  
 Spécifie le nombre maximal de récursivités autorisé pour cette requête. *nombre* est un entier non négatif compris entre 0 et 32767. Lorsque 0 est spécifié, aucune limite n'est appliquée. Si cette option n'est pas spécifiée, la limite par défaut du serveur est 100.  
  
 Lorsque la limite par défaut ou spécifiée de MAXRECURSION est atteinte au cours de l'exécution d'une requête, cette requête se termine et une erreur est retournée.  
  
 À cause de cette erreur, tous les effets de l'instruction sont annulés. S'il s'agit d'une instruction SELECT, les résultats retournés sont partiels ou aucun résultat n'est retourné. Il se peut que parmi les résultats partiels éventuellement retournés ne figurent pas toutes les lignes des niveaux de récursivité supérieurs au niveau de récursivité maximal spécifié.  
  
 Pour plus d’informations, consultez [avec common_table_expression &#40; Transact-SQL &#41; ](../../t-sql/queries/with-common-table-expression-transact-sql.md).  
  
 NO_PERFORMANCE_SPOOL  
 **S'applique à**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] jusqu'à [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Un opérateur spool empêche l’ajout des plans de requête (à l’exception des plans, lors de la mise en attente est nécessaire pour garantir la sémantique de mise à jour valide). Dans certains scénarios, l’opérateur de spool peut réduire les performances. Par exemple, la file d’attente utilise tempdb et les contentions de tempdb peuvent se produire s’il existe plusieurs requêtes simultanées en cours d’exécution avec les opérations de mise en attente.  
  
 OPTIMIZE FOR (  *@variable_name*  {inconnu | = *literal_constant}* [ **,** ... *n* ] )  
 Indique à l'optimiseur de requête d'attribuer à une variable locale une valeur déterminée lors de la compilation et de l'optimisation de la requête. Cette valeur n'est utilisée que pendant l'optimisation de la requête, et non pas lors de son exécution.  
  
 *@variable_name*  
 Nom d'une variable locale utilisée dans une requête, à laquelle une valeur peut être attribuée pour être utilisée avec l'indicateur de requête OPTIMIZE FOR.  
  
 *UNKNOWN*  
 Spécifie que l'optimiseur de requête utilise des données statistiques à la place de la valeur initiale pour déterminer la valeur d'une variable locale pendant l'optimisation de requête.  
  
 *literal_constant*  
 Est une valeur de constante littérale à affecter  *@variable_name*  pour une utilisation avec l’indicateur de requête OPTIMIZE FOR. *literal_constant* est utilisée uniquement lors de l’optimisation de requête et non comme la valeur de  *@variable_name*  pendant l’exécution de requête. *literal_constant* peut être de n’importe quel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type de données système qui peut être exprimée comme une constante littérale. Type de données de *literal_constant* doit être implicitement convertible en données de type qui  *@variable_name*  références dans la requête.  
  
 OPTIMIZE FOR peut contrecarrer le comportement de détection de paramètres par défaut de l'optimiseur ou être utilisé lors de la création de repères de plan. Pour plus d’informations, consultez [recompiler une procédure stockée](../../relational-databases/stored-procedures/recompile-a-stored-procedure.md).  
  
 OPTIMIZE FOR UNKNOWN  
 Indique à l'optimiseur de requête d'utiliser des données statistiques au lieu des valeurs initiales pour toutes les variables locales lorsque la requête est compilée et optimisée, y compris les paramètres créés avec un paramétrage forcé.  
  
 Si OPTIMIZE FOR @variable_name = *literal_constant* et OPTIMIZE FOR UNKNOWN sont utilisés dans le même indicateur de requête, l’optimiseur de requête utilise le *literal_constant* qui est spécifié pour une valeur spécifique et un inconnu pour les valeurs variables restantes. Les valeurs ne sont utilisées que pendant l'optimisation de la requête, et non pas lors de son exécution.  
  
 PARAMETERIZATION { SIMPLE | FORCED }  
 Spécifie les règles de paramétrage que l'optimiseur de requête [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] applique à la requête lorsqu'elle est compilée.  
  
> [!IMPORTANT]  
> L'indicateur de requête PARAMETERIZATION ne peut être spécifié qu'à l'intérieur d'un repère de plan. Il ne peut pas être spécifié directement dans une requête.  
  
 SIMPLE indique à l'optimiseur de requête de tenter le processus de paramétrage simple. FORCED indique à l'optimiseur de tenter le processus de paramétrage forcé. L'indicateur de requête PARAMETERIZATION permet de remplacer le paramétrage actuel de l'option PARAMETERIZATION database SET à l'intérieur d'un repère de plan. Pour plus d’informations, consultez [spécifier le comportement du paramétrage requête à l’aide des repères de Plan](../../relational-databases/performance/specify-query-parameterization-behavior-by-using-plan-guides.md).  
  
 RECOMPILE  
 Indique au [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] d'ignorer le plan généré pour la requête à l'issue de son exécution, forçant ainsi l'optimiseur de requête à recompiler un plan de requête lors de la prochaine exécution de cette même requête. Sans spécifier de RECOMPILATION, la [!INCLUDE[ssDE](../../includes/ssde-md.md)] met en cache des plans de requête et les réutilise. Lors de la compilation des plans de requête, l'indicateur de requête RECOMPILE utilise les valeurs actuelles des variables locales de la requête, qui sont transmises aux paramètres si la requête se trouve à l'intérieur d'une procédure stockée.  
  
 L'indicateur de requête RECOMPILE s'avère fort utile en cela qu'il vous évite de créer une procédure stockée contenant la clause WITH RECOMPILE lorsqu'il s'agit de recompiler uniquement un sous-ensemble de requêtes à l'intérieur de la procédure stockée et non pas l'ensemble de la procédure stockée. Pour plus d’informations, consultez [recompiler une procédure stockée](../../relational-databases/stored-procedures/recompile-a-stored-procedure.md). RECOMPILE s'avère également utile pour créer des repères de guides.  
  
 ROBUST PLAN  
 Force l'optimiseur de requête à essayer un plan capable de prendre en charge la taille maximale potentielle des lignes, éventuellement aux dépens des performances. Lorsque la requête est traitée, les tables et les opérateurs intermédiaires peuvent avoir à stocker et traiter des lignes plus grandes que n'importe quelle ligne d'entrée. Parfois, les lignes peuvent être si grandes que l'opérateur particulier ne peut pas les traiter. Dans ce cas, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] génère une erreur lors de l'exécution de la requête. À l'aide de ROBUST PLAN, vous indiquez à l'optimiseur de requête de ne considérer aucun plan de requête qui pourrait avoir ce problème.  
  
 Si un tel plan n'est pas possible, l'optimiseur de requête retourne une erreur au lieu de reporter la détection de l'erreur au moment de l'exécution de la requête. Lignes peuvent contenir des colonnes de longueur variable ; le [!INCLUDE[ssDE](../../includes/ssde-md.md)] permet de définir les lignes qui ont une taille maximale potentielle au-delà de la capacité de le [!INCLUDE[ssDE](../../includes/ssde-md.md)] pour les traiter. En règle générale, en dépit de la taille maximale potentielle, une application stocke des lignes dont la taille réelle est comprise dans les limites gérées par le [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Si le [!INCLUDE[ssDE](../../includes/ssde-md.md)] trouve une ligne trop longue, il retourne une erreur d'exécution.  
 
<a name="use_hint"></a>INDICATEUR d’utilisation ( **'***hint_name***'** )  
 **S’applique aux**: s’applique aux [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (en commençant par [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]) et [!INCLUDE[ssSDS](../../includes/sssds-md.md)].
 
 Fournit un ou plusieurs indicateurs supplémentaires au processeur de requêtes comme spécifié par un nom de l’indicateur **à l’intérieur des guillemets simples**. 

 Les noms d’indicateur suivants sont pris en charge :
 
*  'DISABLE_OPTIMIZED_NESTED_LOOP'  
 Fait en sorte que le processeur de requêtes non ne pas d’utiliser une opération de tri (tri batch) pour les jointures de boucles imbriquées optimisée lors de la génération d’un plan de requête. Cela est équivalent à [indicateur de trace](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 2340.
*  'FORCE_LEGACY_CARDINALITY_ESTIMATION'  
 Force l’optimiseur de requête à utiliser [Estimation de cardinalité](../../relational-databases/performance/cardinality-estimation-sql-server.md) de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et les versions antérieures. Cela est équivalent à [indicateur de trace](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 9481 ou [Database Scoped Configuration](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md) configuration LEGACY_CARDINALITY_ESTIMATION = ON.
*  'ENABLE_QUERY_OPTIMIZER_HOTFIXES'  
 Correctifs (modifications publiées dans les Service Packs et mises à jour cumulatives de SQL Server) de l’optimiseur de requête active. Cela est équivalent à [indicateur de trace](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 4199 ou [Database Scoped Configuration](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md) paramètre QUERY_OPTIMIZER_HOTFIXES = ON.
*  'DISABLE_PARAMETER_SNIFFING'  
 Indique l’optimiseur de requête à utiliser la distribution moyenne des données lors de la compilation d’une requête avec un ou plusieurs paramètres, qui effectue le plan de requête indépendante sur la valeur du paramètre qui a été utilisée tout d’abord lorsque la requête a été compilée. Cela est équivalent à [indicateur de trace](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 4136 ou [Database Scoped Configuration](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md) paramètre PARAMETER_SNIFFING = OFF.
*  'ASSUME_MIN_SELECTIVITY_FOR_FILTER_ESTIMATES'  
 Provoque le SQL Server générer un plan à l’aide de sélectivité minimale lors de l’évaluation des prédicats et des filtres pour prendre en compte pour la corrélation. Cela est équivalent à [indicateur de trace](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 4137 lorsqu’il est utilisé avec le modèle d’estimation de cardinalité de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et les versions antérieures, et l’effet est semblable lorsque [indicateur de trace](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 9471 est utilisé avec le modèle d’estimation de cardinalité de [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] ou une version ultérieure.
*  'DISABLE_OPTIMIZER_ROWGOAL'  
 Entraîne par SQL Server génère un plan qui n’utilise pas les réglages d’objectif de ligne avec les requêtes qui contiennent TOP, OPTION (FAST N), ou il existe des mots clés. Cela est équivalent à [indicateur de trace](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 4138.
*  'ENABLE_HIST_AMENDMENT_FOR_ASC_KEYS'  
 Permet de statistiques rapides générés automatiquement (modification de l’histogramme) pour une colonne d’index au début pour la cardinalité estimation est nécessaire. L’histogramme utilisée pour estimer la cardinalité sera ajustée à la compilation de requête pour prendre en compte les valeur minimale ou maximale réelle de cette colonne. Cela est équivalent à [indicateur de trace](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 4139. 
*  'ASSUME_JOIN_PREDICATE_DEPENDS_ON_FILTERS'  
 Entraîne par SQL Server générer un plan de requête à l’aide de l’hypothèse de relation contenant-contenu Simple, au lieu de l’hypothèse de relation contenant-contenu de Base par défaut pour les jointures, sous l’optimiseur de requête [Estimation de cardinalité](../../relational-databases/performance/cardinality-estimation-sql-server.md) de [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] ou une version ultérieure. Cela est équivalent à [indicateur de trace](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 9476. 
*  'FORCE_DEFAULT_CARDINALITY_ESTIMATION'  
 Force l’optimiseur de requête à utiliser [Estimation de cardinalité](../../relational-databases/performance/cardinality-estimation-sql-server.md) modèle qui correspond à un niveau de compatibilité de base de données actuel. Utilisez cet indicateur pour remplacer [Database Scoped Configuration](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md) configuration LEGACY_CARDINALITY_ESTIMATION = ON ou [indicateur de trace](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 9481.
 
> [!TIP]
> Indicateur respectent pas la casse.
  
  La liste de tous les noms d’indicateur d’utilisation pris en charge peut être interrogée à l’aide de la vue de gestion dynamique [sys.dm_exec_valid_use_hints ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-valid-use-hints-transact-sql.md).
> [!IMPORTANT] 
> Certains indicateurs d’indicateur d’utilisation peuvent entrer en conflit avec les indicateurs de trace activés au niveau global ou au niveau de la session ou la base de données étendue des paramètres de configuration. Dans ce cas, l’indicateur de niveau de requête (indicateur USE) est toujours prioritaire. Si des conflits d’indicateur d’utilisation avec un autre indicateur de requête ou un indicateur de trace activé au niveau de la requête (par exemple par QUERYTRACEON), SQL Server génère une erreur lorsque vous tentez d’exécuter la requête. 

 USE PLAN N**'***xml_plan***'**  
 Force l’optimiseur de requête à utiliser un plan de requête existant pour une requête qui est spécifiée par **'***xml_plan***'**. USE PLAN ne peut pas être spécifié avec des instructions INSERT, UPDATE, MERGE ou DELETE.  
  
INDICATEUR de TABLE  **(*** exposed_object_name* [ **,** \<indicateur de table > [[**,**]...  *n*  ]] **)** Applique l’indicateur de table spécifié à la table ou la vue qui correspond à *exposed_object_name*. Nous recommandons d’utiliser un indicateur de table comme indicateur de requête uniquement dans le contexte d’un [repère de plan](../../relational-databases/performance/plan-guides.md).  
  
 *exposed_object_name* peut prendre l’une des références suivantes :  
  
-   Lorsqu’un alias est utilisé pour la table ou vue dans la [FROM](../../t-sql/queries/from-transact-sql.md) clause de la requête, *exposed_object_name* est l’alias.  
  
-   Lorsqu’un alias n’est pas utilisé, *exposed_object_name* est la correspondance exacte de la table ou la vue référencée dans la clause FROM. Par exemple, si la table ou la vue est référencée à l’aide d’un nom en deux parties, *exposed_object_name* est le même nom en deux parties.  
  
 Lorsque *exposed_object_name* est spécifié sans spécifier également un indicateur de table, tous les index spécifiés dans la requête comme partie d’un indicateur de table pour l’objet sont ignorées et l’utilisation des index est déterminée par l’optimiseur de requête. Vous pouvez utiliser cette technique pour éliminer l'effet d'un indicateur de table INDEX lorsque vous ne pouvez pas modifier la requête d'origine. Voir l'exemple J.  
  
**\<indicateur de table > :: =** {[NOEXPAND] {INDEX ( *index_value* [,...*n* ] ) | INDEX = ( *index_value* ) | FORCESEEK [**(***index_value***(*** index_column_name* [**,**...] **))** ]| FORCESCAN | HOLDLOCK | NOLOCK | NOWAIT | PAGLOCK | READCOMMITTED | READCOMMITTEDLOCK | READPAST | READUNCOMMITTED | REPEATABLEREAD | ROWLOCK | SÉRIALISABLE | INSTANTANÉ | SPATIAL_WINDOW_MAX_CELLS | TABLOCK | TABLOCKX | UPDLOCK | XLOCK} est l’indicateur de table à appliquer à la table ou la vue qui correspond à *exposed_object_name* comme indicateur de requête. Pour obtenir une description de ces indicateurs, consultez [indicateurs de Table &#40; Transact-SQL &#41; ](../../t-sql/queries/hints-transact-sql-table.md).  
  
 Les indicateurs de table autres que INDEX, FORCESCAN et FORCESEEK sont interdits comme indicateurs de requête, à moins que la requête n'ait déjà une clause WITH qui spécifie l'indicateur de table. Pour plus d'informations, consultez la section Notes.  
  
> [!CAUTION] 
> Le fait de spécifier FORCESEEK avec des paramètres limite davantage le nombre de plans qui peuvent être considérés par l'optimiseur que le fait de spécifier FORCESEEK sans paramètre. Cela peut provoquer une erreur « Impossible de générer le plan » dans davantage de cas. Dans une version ultérieure, il se peut que des modifications internes de l'optimiseur autorisent la prise en considération de davantage de plans.  
  
## <a name="remarks"></a>Notes  
 Il n'est pas possible de spécifier des indicateurs de requête dans une instruction INSERT sauf si celle-ci contient une clause SELECT.  
  
 Les indicateurs de requête ne peuvent être spécifiés que dans une requête de niveau supérieur et non pas dans des sous-requêtes. Lorsqu’un indicateur de table est spécifié comme un indicateur de requête, l’indicateur peut être spécifié dans la requête de niveau supérieur ou dans une sous-requête ; Toutefois, la valeur spécifiée pour *exposed_object_name* dans l’indicateur de TABLE clause doit correspondre exactement au nom exposé dans la requête ou une sous-requête.  
  
## <a name="specifying-table-hints-as-query-hints"></a>Spécification d'indicateurs de table comme indicateurs de requête  
 Nous recommandons l’utilisation de l’indicateur de table INDEX, FORCESCAN ou FORCESEEK comme indicateur de requête uniquement dans le contexte d’un [repère de plan](../../relational-databases/performance/plan-guides.md). Les repères de plan sont utiles lorsque vous ne pouvez pas modifier la requête d'origine, par exemple car il s'agit d'une application tierce. L'indicateur de requête spécifié dans le repère de plan est ajouté à la requête avant sa compilation et son optimisation. Pour les requêtes ad hoc, utilisez la clause TABLE HINT uniquement lors du test des instructions de repère de plan. Pour toutes les autres requêtes ad hoc, nous recommandons de spécifier ces indicateurs uniquement comme indicateurs de table.  
  
 Lorsqu'ils sont spécifiés comme indicateurs de requête, les indicateurs de table INDEX, FORCESCAN et FORCESEEK sont valides pour les objets suivants :  
  
-   Tables  
  
-   Vues  
  
-   Vues indexées  
  
-   Expressions de table communes (l'indicateur doit être spécifié dans l'instruction SELECT dont le jeu de résultats remplit l'expression de table commune)  
  
-   Vues de gestion dynamique  
  
-   Sous-requêtes nommées  
  
 Les indicateurs de table INDEX, FORCESCAN et FORCESEEK peuvent être spécifiés en tant qu'indicateurs de requête pour une requête sans indicateurs de table existants, ou être utilisés pour remplacer respectivement un ou plusieurs indicateurs INDEX, FORCESCAN ou FORCESEEK existants dans la requête. Les indicateurs de table autres que INDEX, FORCESCAN et FORCESEEK sont interdits comme indicateurs de requête, à moins que la requête n'ait déjà une clause WITH qui spécifie l'indicateur de table. Dans ce cas, un indicateur correspondant doit également être spécifié comme indicateur de requête en utilisant TABLE HINT dans la clause OPTION pour conserver la sémantique de la requête. Par exemple, si la requête contient l’indicateur de table NOLOCK, la clause OPTION dans le  **@hints**  paramètre du repère de plan doit également contenir l’indicateur NOLOCK. Consultez l’exemple K. Lorsqu’un indicateur de table autre que INDEX, FORCESCAN ou FORCESEEK est spécifié à l’aide d’indicateur de TABLE dans la clause OPTION sans indicateur de requête correspondant, ou vice versa ; erreur 8702 est déclenchée (indiquant que la clause OPTION peut entraîner la sémantique de la requête à modifier) et Échec de la requête.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-merge-join"></a>A. Utilisation de MERGE JOIN  
 L’exemple suivant spécifie que l’opération de jointure dans la requête est effectuée par la jointure de fusion. L'exemple utilise la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
SELECT *   
FROM Sales.Customer AS c  
INNER JOIN Sales.CustomerAddress AS ca ON c.CustomerID = ca.CustomerID  
WHERE TerritoryID = 5  
OPTION (MERGE JOIN);  
GO    
```  
  
### <a name="b-using-optimize-for"></a>B. Utilisation de OPTIMIZE FOR  
 L’exemple suivant indique à l’optimiseur de requête pour utiliser la valeur `'Seattle'` pour la variable locale `@city_name` et d’utiliser des données statistiques pour déterminer la valeur de la variable locale `@postal_code` lors de l’optimisation de la requête. L'exemple utilise la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
DECLARE @city_name nvarchar(30);  
DECLARE @postal_code nvarchar(15);  
SET @city_name = 'Ascheim';  
SET @postal_code = 86171;  
SELECT * FROM Person.Address  
WHERE City = @city_name AND PostalCode = @postal_code  
OPTION ( OPTIMIZE FOR (@city_name = 'Seattle', @postal_code UNKNOWN) );  
GO  
```  
  
### <a name="c-using-maxrecursion"></a>C. Utilisation de MAXRECURSION  
 MAXRECURSION peut être utilisé pour empêcher une expression de table commune récursive mal rédigée d'entrer dans une boucle infinie. L’exemple suivant crée une boucle infinie intentionnellement et utilise l’indicateur MAXRECURSION pour limiter le nombre de niveaux de récursivité à deux. L'exemple utilise la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```sql  
--Creates an infinite loop  
WITH cte (CustomerID, PersonID, StoreID) AS  
(  
    SELECT CustomerID, PersonID, StoreID  
    FROM Sales.Customer  
    WHERE PersonID IS NOT NULL  
  UNION ALL  
    SELECT cte.CustomerID, cte.PersonID, cte.StoreID  
    FROM cte   
    JOIN  Sales.Customer AS e   
        ON cte.PersonID = e.CustomerID  
)  
--Uses MAXRECURSION to limit the recursive levels to 2  
SELECT CustomerID, PersonID, StoreID  
FROM cte  
OPTION (MAXRECURSION 2);  
GO  
```  
  
 Une fois l'erreur de codage corrigée, MAXRECURSION n'est plus nécessaire.  
  
### <a name="d-using-merge-union"></a>D. Utilisation de MERGE UNION  
 L’exemple suivant utilise l’indicateur de requête MERGE UNION. L'exemple utilise la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
SELECT *  
FROM HumanResources.Employee AS e1  
UNION  
SELECT *  
FROM HumanResources.Employee AS e2  
OPTION (MERGE UNION);  
GO  
```  
  
### <a name="e-using-hash-group-and-fast"></a>E. Utilisation de HASH GROUP et de FAST  
 L’exemple suivant utilise les indicateurs de requête HASH GROUP et FAST. L'exemple utilise la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
SELECT ProductID, OrderQty, SUM(LineTotal) AS Total  
FROM Sales.SalesOrderDetail  
WHERE UnitPrice < $5.00  
GROUP BY ProductID, OrderQty  
ORDER BY ProductID, OrderQty  
OPTION (HASH GROUP, FAST 10);  
GO    
```  
  
### <a name="f-using-maxdop"></a>F. Utilisation de MAXDOP  
 L’exemple suivant utilise l’indicateur de requête MAXDOP. L'exemple utilise la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
**S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] jusqu'à [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
```  
SELECT ProductID, OrderQty, SUM(LineTotal) AS Total  
FROM Sales.SalesOrderDetail  
WHERE UnitPrice < $5.00  
GROUP BY ProductID, OrderQty  
ORDER BY ProductID, OrderQty  
OPTION (MAXDOP 2);    
GO
```  
  
### <a name="g-using-index"></a>G. Utilisation de INDEX  
 Les exemples suivants utilisent l'indicateur INDEX. Le premier exemple spécifie un index unique. Le deuxième exemple spécifie plusieurs index pour une référence de table individuelle. Dans les deux exemples, étant donné que l'indicateur INDEX est appliqué à une table qui utilise un alias, la clause TABLE HINT doit également spécifier le même alias que le nom d'objet exposé. L'exemple utilise la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
EXEC sp_create_plan_guide   
    @name = N'Guide1',   
    @stmt = N'SELECT c.LastName, c.FirstName, e.Title  
              FROM HumanResources.Employee AS e   
              JOIN Person.Contact AS c ON e.ContactID = c.ContactID  
              WHERE e.ManagerID = 2;',   
    @type = N'SQL',  
    @module_or_batch = NULL,   
    @params = NULL,   
    @hints = N'OPTION (TABLE HINT(e, INDEX (IX_Employee_ManagerID)))';  
GO  
EXEC sp_create_plan_guide   
    @name = N'Guide2',   
    @stmt = N'SELECT c.LastName, c.FirstName, e.Title  
              FROM HumanResources.Employee AS e  
              JOIN Person.Contact AS c ON e.ContactID = c.ContactID  
              WHERE e.ManagerID = 2;',   
    @type = N'SQL',  
    @module_or_batch = NULL,   
    @params = NULL,   
    @hints = N'OPTION (TABLE HINT(e, INDEX(PK_Employee_EmployeeID, IX_Employee_ManagerID)))';  
GO    
```  
  
### <a name="h-using-forceseek"></a>H. Utilisation de FORCESEEK  
 L'exemple suivant utilise l'indicateur de table FORCESEEK. Dans la mesure où l'indicateur INDEX est appliqué à une table qui utilise un nom en deux parties, la clause TABLE HINT doit également spécifier le même nom en deux parties que le nom d'objet exposé. L'exemple utilise la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
EXEC sp_create_plan_guide   
    @name = N'Guide3',   
    @stmt = N'SELECT c.LastName, c.FirstName, HumanResources.Employee.Title  
              FROM HumanResources.Employee  
              JOIN Person.Contact AS c ON HumanResources.Employee.ContactID = c.ContactID  
              WHERE HumanResources.Employee.ManagerID = 3  
              ORDER BY c.LastName, c.FirstName;',   
    @type = N'SQL',  
    @module_or_batch = NULL,   
    @params = NULL,   
    @hints = N'OPTION (TABLE HINT( HumanResources.Employee, FORCESEEK))';  
GO    
```  
  
### <a name="i-using-multiple-table-hints"></a>I. Utilisation de plusieurs indicateurs de table  
 L'exemple suivant applique l'indicateur INDEX à une table et l'indicateur FORCESEEK à une autre. L'exemple utilise la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
EXEC sp_create_plan_guide   
    @name = N'Guide4',   
    @stmt = N'SELECT e.ManagerID, c.LastName, c.FirstName, e.Title  
              FROM HumanResources.Employee AS e   
              JOIN Person.Contact AS c ON e.ContactID = c.ContactID  
              WHERE e.ManagerID = 3;',   
    @type = N'SQL',  
    @module_or_batch = NULL,   
    @params = NULL,   
    @hints = N'OPTION (TABLE HINT (e, INDEX( IX_Employee_ManagerID))   
                       , TABLE HINT (c, FORCESEEK))';  
GO  
```  
  
### <a name="j-using-table-hint-to-override-an-existing-table-hint"></a>J. Utilisation de TABLE HINT pour substituer un indicateur de table existant  
 L'exemple suivant montre comment utiliser l'indicateur TABLE HINT sans spécifier d'indicateur pour substituer le comportement de l'indicateur de table INDEX spécifié dans la clause FROM de la requête. L'exemple utilise la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
EXEC sp_create_plan_guide   
    @name = N'Guide5',   
    @stmt = N'SELECT e.ManagerID, c.LastName, c.FirstName, e.Title  
              FROM HumanResources.Employee AS e WITH (INDEX (IX_Employee_ManagerID))  
              JOIN Person.Contact AS c ON e.ContactID = c.ContactID  
              WHERE e.ManagerID = 3;',   
    @type = N'SQL',  
    @module_or_batch = NULL,   
    @params = NULL,   
    @hints = N'OPTION (TABLE HINT(e))';  
GO    
```  
  
### <a name="k-specifying-semantics-affecting-table-hints"></a>K. Spécification d'indicateurs de table affectant la sémantique  
 L'exemple suivant contient deux indicateurs de table dans la requête : NOLOCK, qui affecte la sémantique, et INDEX, qui n'affecte pas la sémantique. Pour préserver la sémantique de la requête, l'indicateur NOLOCK est spécifié dans la clause OPTIONS du repère de plan. Outre l'indicateur NOLOCK, les indicateurs INDEX et FORCESEEK sont spécifiés et remplacent l'indicateur INDEX n'affectant pas la sémantique dans la requête lorsque l'instruction est compilée et optimisée. L'exemple utilise la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
EXEC sp_create_plan_guide   
    @name = N'Guide6',   
    @stmt = N'SELECT c.LastName, c.FirstName, e.Title  
              FROM HumanResources.Employee AS e   
                   WITH (NOLOCK, INDEX (PK_Employee_EmployeeID))  
              JOIN Person.Contact AS c ON e.ContactID = c.ContactID  
              WHERE e.ManagerID = 3;',  
    @type = N'SQL',  
    @module_or_batch = NULL,   
    @params = NULL,   
    @hints = N'OPTION (TABLE HINT (e, INDEX(IX_Employee_ManagerID), NOLOCK, FORCESEEK))';  
GO    
```  
  
 L'exemple suivant indique une autre méthode pour préserver la sémantique de la requête et permettre à l'optimiseur de choisir un index autre que l'index spécifié dans l'indicateur de table. Pour ce faire, il convient de spécifier l'indicateur NOLOCK dans la clause OPTIONS (car il affecte la sémantique) et le mot clé TABLE HINT avec uniquement une référence de table et aucun indicateur INDEX. L'exemple utilise la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
EXEC sp_create_plan_guide   
    @name = N'Guide7',   
    @stmt = N'SELECT c.LastName, c.FirstName, e.Title  
              FROM HumanResources.Employee AS e   
                   WITH (NOLOCK, INDEX (PK_Employee_EmployeeID))  
              JOIN Person.Contact AS c ON e.ContactID = c.ContactID  
              WHERE e.ManagerID = 2;',  
    @type = N'SQL',  
    @module_or_batch = NULL,   
    @params = NULL,   
    @hints = N'OPTION (TABLE HINT (e, NOLOCK))';  
GO  
```  
### <a name="l-using-use-hint"></a>L. À l’aide d’indicateur d’utilisation  
 L’exemple suivant utilise les indicateurs de requête RECOMPILE et une indication de l’utilisation. L'exemple utilise la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
**S’applique aux**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)].  
  
```  
SELECT * FROM Person.Address  
WHERE City = 'SEATTLE' AND PostalCode = 98104
OPTION (RECOMPILE, USE HINT ('ASSUME_MIN_SELECTIVITY_FOR_FILTER_ESTIMATES', 'DISABLE_PARAMETER_SNIFFING')); 
GO  
```  
    
## <a name="see-also"></a>Voir aussi  
 [Hints &#40;Transact-SQL&#41;](../../t-sql/queries/hints-transact-sql.md)   
 [sp_create_plan_guide &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)   
 [sp_control_plan_guide &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-control-plan-guide-transact-sql.md)  
 [Indicateurs de trace](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)
  
  
