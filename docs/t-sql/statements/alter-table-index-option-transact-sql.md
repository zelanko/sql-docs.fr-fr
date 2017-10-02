---
title: index_option (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 09/08/2017
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
- index_option
ms.assetid: 8a14f12d-2fbf-4036-b8b2-8db3354e0eb7
caps.latest.revision: 68
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: cd1366409f9fb0af271b26fad3b8b911f99acc06
ms.openlocfilehash: e7563f9fe992dcf4f9308cccbf11f6310b7925a7
ms.contentlocale: fr-fr
ms.lasthandoff: 09/08/2017

---
# <a name="alter-table-indexoption-transact-sql"></a>ALTER TABLE index_option (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Spécifie un ensemble d’options qui peuvent être appliqués à un index qui fait partie d’une définition de contrainte qui est créée à l’aide de [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
{   
    PAD_INDEX = { ON | OFF }  
  | FILLFACTOR = fillfactor  
  | IGNORE_DUP_KEY = { ON | OFF }  
  | STATISTICS_NORECOMPUTE = { ON | OFF }  
  | ALLOW_ROW_LOCKS = { ON | OFF }  
  | ALLOW_PAGE_LOCKS = { ON | OFF }  
  | SORT_IN_TEMPDB = { ON | OFF }   
  | ONLINE = { ON | OFF }  
  | MAXDOP = max_degree_of_parallelism  
  | DATA_COMPRESSION = { NONE |ROW | PAGE | COLUMNSTORE | COLUMNSTORE_ARCHIVE }  
      [ ON PARTITIONS ( { <partition_number_expression> | <range> }   
      [ , ...n ] ) ]  
  | ONLINE = { ON [ ( <low_priority_lock_wait> ) ] | OFF }  
}  
  
<range> ::=   
<partition_number_expression> TO <partition_number_expression>  
  
<single_partition_rebuild__option> ::=  
{  
    SORT_IN_TEMPDB = { ON | OFF }  
  | MAXDOP = max_degree_of_parallelism  
  | DATA_COMPRESSION = {NONE | ROW | PAGE | COLUMNSTORE | COLUMNSTORE_ARCHIVE } }  
  | ONLINE = { ON [ ( <low_priority_lock_wait> ) ] | OFF }  
}  
  
<low_priority_lock_wait>::=  
{  
    WAIT_AT_LOW_PRIORITY ( MAX_DURATION = <time> [ MINUTES ] ,   
                           ABORT_AFTER_WAIT = { NONE | SELF | BLOCKERS } )   
}  
```  
  
## <a name="arguments"></a>Arguments  
 PAD_INDEX  **=**  {ON | **OFF** }  
 **S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Spécifie le remplissage de l'index. La valeur par défaut est OFF.  
  
 ON  
 Le pourcentage d'espace libre indiqué par FILLFACTOR est appliqué aux pages de niveau intermédiaire de l'index.  
  
 DÉSACTIVER ou *fillfactor* n’est pas spécifié  
 Les pages de niveau intermédiaire sont remplies jusqu'à la presque totalité de la capacité, laissant suffisamment d'espace pour au moins une ligne de la taille maximale possible de l'index, compte tenu du jeu de clés des pages intermédiaires.  
  
 Facteur de remplissage  **=**  *facteur de remplissage*  
 **S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Spécifie un pourcentage indiquant le taux de remplissage appliqué par le [!INCLUDE[ssDE](../../includes/ssde-md.md)] au niveau feuille de chaque page d'index lors de la création ou de la modification de l'index. La valeur spécifiée doit être un entier compris entre 1 et 100. La valeur par défaut est 0.  
  
> [!NOTE]  
>  Les facteurs de remplissage de valeur 0 et 100 sont en tout point identiques.  
  
 IGNORE_DUP_KEY  **=**  {ON | **OFF** }  
 Spécifie la réponse d'erreur lorsqu'une opération d'insertion essaie d'insérer des valeurs de clés en double dans un index unique. L'option IGNORE_DUP_KEY s'applique uniquement aux opérations d'insertion après la création ou la régénération de l'index. L’option n’a aucun effet lors de l’exécution [CREATE INDEX](../../t-sql/statements/create-index-transact-sql.md), [ALTER INDEX](../../t-sql/statements/alter-index-transact-sql.md), ou [mise à jour](../../t-sql/queries/update-transact-sql.md). La valeur par défaut est OFF.  
  
 ON  
 Un message d’avertissement se produit lorsque les valeurs de clé en double sont insérées dans un index unique. Uniquement les lignes qui violent la contrainte d’unicité échouent.  
  
 OFF  
 Un message d’erreur se produit lorsque les valeurs de clé en double sont insérées dans un index unique. L’opération d’insertion entière est restaurée.  
  
 IGNORE_DUP_KEY ne peut pas être activée pour les index créés sur une vue, les index non uniques, les index XML, les index spatiaux et les index filtrés.  
  
 Pour afficher IGNORE_DUP_KEY, utilisez [sys.indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md).  
  
 Dans la syntaxe de compatibilité descendante, WITH IGNORE_DUP_KEY est équivalent à WITH IGNORE_DUP_KEY = ON.  
  
 STATISTICS_NORECOMPUTE  **=**  {ON | **OFF** }  
 Indique si les statistiques sont recalculées. La valeur par défaut est OFF.  
  
 ON  
 Les statistiques obsolètes ne sont pas recalculées automatiquement.  
  
 OFF  
 La mise à jour automatique des statistiques est activée.  
  
 ALLOW_ROW_LOCKS  **=**  { **ON** | {OFF}  
 **S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Indique si les verrous de ligne sont autorisés ou non. La valeur par défaut est ON.  
  
 ON  
 Les verrous de ligne sont autorisés lors de l'accès à l'index. Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] détermine le moment où les verrous de ligne sont utilisés.  
  
 OFF  
 Les verrous de ligne ne sont pas utilisés.  
  
 ALLOW_PAGE_LOCKS  **=**  { **ON** | {OFF}  
 **S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Indique si les verrous de page sont autorisés. La valeur par défaut est ON.  
  
 ON  
 Les verrous de page sont autorisés lors de l'accès à l'index. Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] détermine le moment où les verrous de page sont utilisés.  
  
 OFF  
 Les verrous de page ne sont pas utilisés.  
  
 SORT_IN_TEMPDB  **=**  {ON | **OFF** }  
 **S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Spécifie s’il faut stocker les résultats de tri dans **tempdb**. La valeur par défaut est OFF.  
  
 ON  
 Les résultats de tri intermédiaires qui sont utilisés pour créer l’index sont stockés dans **tempdb**. Cela peut réduire le temps nécessaire pour créer un index si **tempdb** est un ensemble de disques que la base de données utilisateur. Toutefois, une plus grande quantité d'espace disque est alors utilisée lors de la création de l'index.  
  
 OFF  
 Les résultats de tri intermédiaires sont stockés dans la même base de données que l'index.  
  
 EN LIGNE  **=**  {ON | **OFF** }  
 **S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Indique si les tables sous-jacentes et les index associés sont disponibles pour les requêtes et la modification de données pendant l'opération d'index. La valeur par défaut est OFF. REBUILD peut être effectué en tant qu'opération ONLINE.  
  
> [!NOTE]  
>  Les index uniques non cluster ne peuvent pas être créés en ligne. Il s'agit des index qui sont créés en raison d'une contrainte UNIQUE ou PRIMARY KEY.  
  
 ON  
 Les verrous de table à long terme ne sont pas maintenus pendant la durée de l'opération d'index. Lors de la principale phase de l'indexation, seul le verrou de partage intentionnel (IS, Intent Share) est maintenu sur la table source. Ceci permet d'exécuter les requêtes ou les mises à jour dans la table sous-jacente et ses index. Au début de l'opération, un verrou partagé (S, Shared) est placé sur l'objet source pendant une période de temps très courte. À la fin de l'opération, pendant une période de temps très courte, un verrou partagé (S, Shared) est placé sur la source si un index non cluster est créé, ou bien un verrou de SCH-M (Modification du schéma) est placé lorsqu'un index cluster est créé ou supprimé en ligne et lorsqu'un index cluster ou non cluster est régénéré. Bien que les verrous d'index en ligne soient des verrous de métadonnées courtes, le verrou Sch-M doit notamment attendre que toutes les transactions bloquantes soient terminées sur cette table. Pendant le temps d'attente, le verrou Sch-M bloque toutes les autres transactions qui attendent derrière ce verrou en cas d'accès à la même table. ONLINE ne peut pas prendre la valeur ON si un index est en cours de création sur une table locale temporaire.  
  
> [!NOTE]  
>  Reconstruction d’index en ligne peut définir le *low_priority_lock_wait* options décrites plus loin dans cette section. *low_priority_lock_wait* gère la priorité de verrou S ou Sch-M pendant la reconstruction d’index en ligne.  
  
 OFF  
 Des verrous de table sont appliqués pendant l'opération d'indexation. Cela empêche tous les utilisateurs d'accéder à la table sous-jacente pendant la durée de l'opération. Une opération d'indexation hors ligne qui crée, régénère ou supprime un index cluster, ou régénère ou supprime un index non cluster, acquiert un verrou de modification de schéma (Sch-M) sur la table. Cela empêche tous les utilisateurs d'accéder à la table sous-jacente pendant la durée de l'opération. Une opération d'indexation hors ligne qui crée un index non cluster acquiert un verrou partagé (S, Shared) sur la table. Cela empêche la mise à jour de la table sous-jacente, mais autorise les opérations de lecture, telles que des instructions SELECT.  
  
 Pour plus d’informations, consultez [Online Index opérations fonctionnement](../../relational-databases/indexes/how-online-index-operations-work.md).  
  
> [!NOTE]  
>  Les opérations d'index en ligne ne sont pas disponibles dans toutes les éditions de [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour obtenir la liste des fonctionnalités prises en charge par les éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Fonctionnalités prise en charge par les éditions de SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
 MAXDOP  **=**  *max_degree_of_parallelism*  
 **S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Remplace le **degré maximal de parallélisme** option de configuration pour la durée de l’opération d’index. Pour plus d’informations, consultez [Configurer l’option de configuration du serveur max degree of parallelism](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md). Utilisez MAXDOP pour limiter le nombre de processeurs utilisés dans une exécution de plan parallèle. Le nombre maximal de processeurs est égal à 64.  
  
 *max_degree_of_parallelism* peut être :  
  
 - 1 - supprime la génération de plans parallèles.  
 - \>1 - limite le nombre maximal de processeurs utilisés dans une opération d’index en parallèle au nombre spécifié.  
 - 0 (par défaut) : utilise le nombre réel de processeurs ou inférieur en fonction de la charge système actuelle.  
  
 Pour plus d’informations, consultez [Configurer des opérations d’index parallèles](../../relational-databases/indexes/configure-parallel-index-operations.md).  
  
> [!NOTE]  
>  Opérations d’index parallèles ne sont pas disponibles dans toutes les éditions de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour obtenir la liste des fonctionnalités prises en charge par les éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Fonctionnalités prise en charge par les éditions de SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
 DATA_COMPRESSION  
 **S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Spécifie l'option de compression de données pour la table, le numéro de partition ou la plage de partitions spécifiés. Les options disponibles sont les suivantes :  
  
 Aucune  
 La table ou les partitions spécifiées ne sont pas compressées. S'applique uniquement aux tables rowstore ; ne s'applique pas aux tables columnstore.  
  
 ROW  
 La table ou les partitions spécifiées sont compressées au moyen de la compression de ligne. S'applique uniquement aux tables rowstore ; ne s'applique pas aux tables columnstore.  
  
 PAGE  
 La table ou les partitions spécifiées sont compressées au moyen de la compression de page. S'applique uniquement aux tables rowstore ; ne s'applique pas aux tables columnstore.  
  
 COLUMNSTORE  
 **S'applique à**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 S'applique uniquement aux tables columnstore. COLUMNSTORE spécifie qu'il faut décompresser une partition compressée à l'aide de l'option COLUMNSTORE_ARCHIVE. Lors de la restauration des données, l’index COLUMNSTORE continue à être compressées avec la compression columnstore qui est utilisée pour toutes les tables columnstore.  
  
 COLUMNSTORE_ARCHIVE  
 **S'applique à**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 S'applique uniquement aux tables columnstore, qui sont des tables stockées avec un index cluster columnstore. COLUMNSTORE_ARCHIVE davantage compresse la partition spécifiée à une taille plus petite. Peut être utilisé pour l'archivage, ou d'autres situations qui nécessitent moins de stockage et supportent plus de temps pour le stockage et la récupération.  
  
 Pour plus d’informations sur la compression, consultez [la Compression des données](../../relational-databases/data-compression/data-compression.md).  
  
SUR les PARTITIONS **(** { \<partition_number_expression > | \<plage >} [ **,**...  *n*  ] **)** **S’applique aux**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Spécifie les partitions auxquelles le paramètre DATA_COMPRESSION s'applique. Si la table n’est pas partitionnée, l’argument ON PARTITIONS génère une erreur. Si la clause ON PARTITIONS n’est pas fournie, l’option DATA_COMPRESSION s’applique à toutes les partitions d’une table partitionnée.  
  
\<partition_number_expression > peut être spécifié comme suit :  
  
-   Fournir, le numéro d’une partition, par exemple : ON PARTITIONS (2).  
-   Spécifiez des numéros de partition pour plusieurs partitions individuelles séparées par des virgules, par exemple : ON PARTITIONS (1, 5).  
-   Spécifiez à la fois des plages et des partitions individuelles, par exemple ON PARTITIONS (2, 4, 6 TO 8).  
  
\<plage > peut être spécifié en tant que numéros de partitions séparés par le mot TO, par exemple : ON PARTITIONS (6 TO 8).  
  
 Pour définir des types différents de compression de données pour des partitions différentes, spécifiez plusieurs fois l'option DATA_COMPRESSION, par exemple :  
  
```sql  
--For rowstore tables  
REBUILD WITH   
(  
DATA_COMPRESSION = NONE ON PARTITIONS (1),   
DATA_COMPRESSION = ROW ON PARTITIONS (2, 4, 6 TO 8),   
DATA_COMPRESSION = PAGE ON PARTITIONS (3, 5)  
)  
  
--For columnstore tables  
REBUILD WITH   
(  
DATA_COMPRESSION = COLUMNSTORE ON PARTITIONS (1, 3, 5),   
DATA_COMPRESSION = COLUMNSTORE_ARCHIVE ON PARTITIONS (2, 4, 6 TO 8)  
)  
```  
  
**\<single_partition_rebuild__option >**  
 Dans la plupart des cas, la reconstruction d'un index reconstruit toutes les partitions d'un index partitionné. Les options suivantes, lorsqu'elles sont appliquées à une partition unique, ne reconstruisent pas toutes les partitions.  
  
-   SORT_IN_TEMPDB  
-   MAXDOP  
-   DATA_COMPRESSION  
  
**low_priority_lock_wait**  
 **S'applique à**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 A **commutateur** ou reconstruction d’index en ligne se termine dès qu’il en existe aucune opération bloquante pour cette table. *WAIT_AT_LOW_PRIORITY* indique que si le **commutateur** ou opération de reconstruction d’index en ligne ne peut pas être effectuée immédiatement, il attend. L’opération maintient un verrou de priorité basse, laissant les autres opérations qui contiennent des verrous en conflit avec l’instruction DDL pour continuer. L’omission de la **attente basse** option est équivalente à `WAIT_AT_LOW_PRIORITY ( MAX_DURATION = 0 minutes, ABORT_AFTER_WAIT = NONE)`.  
  
MAX_DURATION = *temps* [**MINUTES** ]  
 Temps d’attente (valeur entière spécifiée en minutes) qui le **commutateur** ou attentes de verrou de reconstruction d’index en ligne qui doit être acquis, lors de l’exécution de la commande DDL. Le SWITCH ou l'opération de reconstruction de l'index en ligne tente de terminer immédiatement. Si l’opération est bloquée pendant la **MAX_DURATION** de temps, un de la **ABORT_AFTER_WAIT** actions est exécutée. **MAX_DURATION** heure est toujours en minutes et le mot **MINUTES** peut être omis.  
  
ABORT_AFTER_WAIT = [**NONE** | **SELF** | **DES BLOCAGES** }]  
 Aucune  
 Continue la **commutateur** ou des index en ligne opération de reconstruction sans modifier la priorité de verrou (avec une priorité normale).  
  
SELF  
 Quitte le **commutateur** ou opération de DDL de reconstruction d’index en ligne actuellement exécutée sans effectuer aucune action.  
  
BLOCKERS  
 Supprime toutes les transactions utilisateur qui bloquent actuellement le **commutateur** ou des index en ligne opération DDL de reconstruction afin que l’opération puisse continuer.  
 Des blocages requiert le **ALTER ANY CONNECTION** autorisation.  
  
## <a name="remarks"></a>Notes  
 Pour obtenir une description complète des options d’index, consultez [CREATE INDEX &#40; Transact-SQL &#41; ](../../t-sql/statements/create-index-transact-sql.md).  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [column_constraint &#40; Transact-SQL &#41;](../../t-sql/statements/alter-table-column-constraint-transact-sql.md)   
 [computed_column_definition &#40; Transact-SQL &#41;](../../t-sql/statements/alter-table-computed-column-definition-transact-sql.md)   
 [table_constraint &#40; Transact-SQL &#41;](../../t-sql/statements/alter-table-table-constraint-transact-sql.md)  
  
 

