---
title: "MODIFIER le niveau de compatibilité de base de données (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 11/24/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- COMPATIBILITY_LEVEL_TSQL
- COMPATIBILITY_LEVEL
dev_langs: TSQL
helpviewer_keywords:
- 80 compatibility level
- ALTER DATABASE statement, compatibility levels
- 90 compatibility level
- compatibility levels [SQL Server]
- 100 compatibility level
ms.assetid: ca5fd220-d5ea-4182-8950-55d4101a86f6
caps.latest.revision: "89"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 62a9e4eec99073e63d53c2d610a7527fbe5f9c91
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2017
---
# <a name="alter-database-transact-sql-compatibility-level"></a>MODIFIER le niveau de compatibilité de base de données (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  
Définit certains comportements de base de données pour qu'ils soient compatibles avec la version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] spécifiée. Pour les autres options ALTER DATABASE, consultez [ALTER DATABASE &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-transact-sql.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
ALTER DATABASE database_name   
SET COMPATIBILITY_LEVEL = { 140 | 130 | 120 | 110 | 100 | 90 }  
```  
  
## <a name="arguments"></a>Arguments  
 *database_name*  
 Nom de la base de données à modifier.  
  
 COMPATIBILITY_LEVEL {140 | 130 | 120 | 110 | 100 | 90 | 80}  
 Version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avec laquelle la base de données doit être compatible. Les valeurs de niveau de compatibilité suivants peuvent être configurés :  
  
|Product|Version du moteur de base de données|Désignation de niveau de compatibilité|Prise en charge des valeurs de niveau de compatibilité|  
|-------------|-----------------------------|-------------------------------------|------------------------------------------|  
|[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)]|14|140|140, 130, 120, 110, 100|
|[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|12|130|140, 130, 120, 110, 100|  
|[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]|13|130|130, 120, 110, 100|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|12|120|120, 110, 100|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|11|110|110, 100, 90|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|10.5|100|100, 90, 80|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|10|100|100, 90, 80|  
|SQL Server 2005|9|90|90, 80|  
|SQL Server 2000|8|80|80|  
  
> [!NOTE]  
>  **Base de données SQL Azure** V12 a été publiée en décembre 2014. Un aspect de cette version était que les bases de données nouvellement créées sont leur niveau de compatibilité à 120. Base de données SQL 2015 compter prise en charge pour le niveau 130, bien que la valeur par défaut est restée à 120.  
> 
> À compter de **mid-juin 2016**, dans la base de données SQL Azure, le niveau de compatibilité par défaut sont 130 au lieu de 120 pour **nouvellement créé** bases de données. Bases de données existants créés avant mid-juin 2016 ne sont pas affectés et à maintenir leur niveau de compatibilité actuel (100, 110 et 120). 
> 
> Si vous souhaitez que le niveau de 130 pour votre base de données en général, mais vous avez des raisons de préférer le niveau 110 **estimation de cardinalité** algorithme, consultez [ALTER DATABASE SCOPED CONFIGURATION &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)et notamment son mot clé LEGACY_CARDINALITY_ESTIMATION = ON.  
>  
>  Pour plus d’informations sur la façon d’évaluer les différences de performances de vos requêtes importantes, entre deux niveaux de compatibilité sur la base de données SQL Azure, consultez [amélioré les performances de requête avec 130 de niveau de compatibilité de base de données SQL Azure](http://azure.microsoft.com/documentation/articles/sql-database-compatibility-level-query-performance-130/).


 Exécutez la requête suivante pour déterminer la version de le [!INCLUDE[ssDE](../../includes/ssde-md.md)] que vous êtes connecté.  
  
```tsql  
SELECT SERVERPROPERTY('ProductVersion');  
```  
  
> [!NOTE]  
>  Pas toutes les fonctionnalités qui varient selon le niveau de compatibilité sont pris en charge sur [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  

 Pour déterminer le niveau de compatibilité actuel, interrogez la **compatibility_level** colonne [sys.databases &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).  
  
```tsql  
SELECT name, compatibility_level FROM sys.databases;  
```  
  
## <a name="remarks"></a>Notes  
 Pour toutes les installations de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le niveau de compatibilité par défaut est défini à la version de la [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Bases de données sont définies à ce niveau, sauf si le **modèle** base de données a un niveau de compatibilité inférieur. Lorsqu’une base de données est mise à niveau depuis une version antérieure de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], la base de données conserve son niveau de compatibilité existant s’il est au moins minimale autorisée pour cette instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La mise à niveau une base de données avec un niveau de compatibilité inférieur au niveau autorisé, définit la base de données de compatibilité le plus bas niveau autorisé. Cela s'applique aussi bien aux bases de données système qu'aux bases de données utilisateur. Utilisez **ALTER DATABASE** pour modifier le niveau de compatibilité de la base de données. Pour afficher le niveau de compatibilité actuel d’une base de données, interrogez la **compatibility_level** colonne dans la **sys.databases** vue de catalogue.  

  
## <a name="using-compatibility-level-for-backward-compatibility"></a>Utilisation du niveau de compatibilité pour la compatibilité descendante  
 Le niveau de compatibilité affecte uniquement les comportements de la base de données spécifiée et non ceux du serveur tout entier. Le niveau de compatibilité fournit uniquement une compatibilité descendante partielle avec les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. À partir de mode de compatibilité 130, toutes les nouvelles requêtes plan affectant fonctionnalités ont été ajoutées uniquement pour le nouveau mode de compatibilité. Cela a été effectué afin de réduire le risque au cours des mises à niveau qui résultent d’une dégradation des performances en raison de changements de plan de requête. Du point de vue de l’application, l’objectif est toujours être au niveau de compatibilité plus récente pour pouvoir hériter parmi les nouvelles fonctionnalités ainsi que des améliorations de performances dans l’espace d’optimiseur de requête, mais à le faire de manière contrôlée. Utilisez le niveau de compatibilité en tant qu'aide à la migration intérimaire pour contourner les problèmes liés aux différences de version dans les comportements qui sont contrôlés par le paramètre de niveau de compatibilité correspondant. Pour plus d’informations, consultez les meilleures pratiques plus loin dans l’article de la mise à niveau.  
  
 Si existant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] applications sont affectées par les différences de comportement dans la version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], convertir en application fonctionnent de façon transparente avec le nouveau mode de compatibilité. Utilisez ensuite **ALTER DATABASE** pour modifier le niveau de compatibilité à 130. Le nouveau paramètre de compatibilité pour une base de données prend effet quand un **USE Database** émis ou une nouvelle connexion est traitée avec cette base de données en tant que la base de données par défaut.  
  
## <a name="best-practices"></a>Bonnes pratiques  
 La modification du niveau de compatibilité alors que des utilisateurs sont connectés à la base de données peut générer des jeux de résultats incorrects pour les requêtes actives. Par exemple, si le niveau de compatibilité change alors qu'un plan de requête est en cours de compilation, le plan compilé peut être basé à la fois sur l'ancien niveau de compatibilité et sur le nouveau, ce qui aboutit à un plan incorrect et à des résultats éventuellement erronés. En outre, le problème peut être aggravé si le plan est placé dans la mémoire cache du plan et réutilisé pour des requêtes ultérieures. Pour éviter que les requêtes ne donnent des résultats inexacts, nous vous recommandons d'utiliser la procédure suivante pour modifier le niveau de compatibilité d'une base de données :  
  
1.  Placez la base de données en mode d'accès mono-utilisateur en utilisant ALTER DATABASE SET SINGLE_USER.  
  
2.  Modifiez le niveau de compatibilité de la base de données.  
  
3.  Placez la base de données en mode d'accès multi-utilisateur en utilisant ALTER DATABASE SET MULTI_USER.  
  
4.  Pour plus d’informations sur le mode d’accès d’une base de données, consultez [ALTER DATABASE &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-transact-sql.md).  
  
## <a name="compatibility-levels-and-stored-procedures"></a>Niveaux de compatibilité et procédures stockées  
 Lors de l'exécution d'une procédure stockée, elle utilise le niveau de compatibilité en cours de la base de données dans laquelle elle est définie. Lors de la modification du paramètre de compatibilité d'une base de données, l'ensemble de ses procédures stockées sont automatiquement recompilées en conséquence.  

## <a name="differences-between-compatibility-level-130-and-level-140"></a>Différences entre le niveau de compatibilité 130 et niveau 140  
Cette section décrit les nouveaux comportements introduits avec le niveau de compatibilité 140.

|Paramètre de niveau de compatibilité inférieur ou égal à 130|Paramètre de niveau de compatibilité de 140|  
|--------------------------------------------------|-----------------------------------------|  
|Estimations de cardinalité pour les instructions faisant référence à des tables de plusieurs instructions fonctions utilisent une estimation de ligne fixe.|Estimations de cardinalité pour les instructions éligibles faisant référence à des tables de plusieurs instructions fonctions utilisera la cardinalité réelle de la sortie de fonction.  Cette option est activée **entrelacées de l’exécution** pour les fonctions table à instructions multiples.|
|Les requêtes en mode batch qui demandent une mémoire insuffisante accorder des tailles de résultats dans les vidages sur le disque peut continuer à avoir des problèmes sur les exécutions consécutives.|Requêtes en mode batch qui demandent des tailles de grant insuffisance de mémoire que le résultat dans les vidages sur le disque peut amélioré les performances sur des exécutions consécutives.  Cette option est activée **des commentaires d’allocation de mémoire de mode de traitement par lots** qui met à jour de la taille d’allocation de mémoire d’un plan de mise en cache si les vidages se sont produites pour les opérateurs en mode batch. |
|Taille qui entraîne des problèmes d’accès concurrentiel peut continuer à avoir des problèmes sur des exécutions consécutives d’allocation de requêtes en mode batch qui demandent une mémoire excessive.|Les requêtes en mode batch qui demandent une mémoire en excès accorder taille entraîne des problèmes d’accès concurrentiel peut ont amélioré la concurrence sur les exécutions consécutives.  Cette option est activée **des commentaires d’allocation de mémoire de mode de traitement par lots** qui met à jour de la taille d’allocation de mémoire d’un plan de mise en cache si une quantité excessive a été demandée à l’origine.|
|Les requêtes en mode batch qui contiennent des opérateurs de jointure sont éligibles pour trois algorithmes de jointures physiques, notamment des boucles imbriquées, de jointure de hachage et de jointure de fusion.  Si les estimations de cardinalité sont incorrectes pour les entrées de jointure, un algorithme de jointure inapproprié peut être sélectionné.  Si cela se produit, performances seront affectées et l’algorithme de jointure inapproprié reste en cours d’utilisation jusqu'à ce que le plan mis en cache est recompilé.|Il existe un opérateur de jointure supplémentaire appelé **jointure adaptive**. Si les estimations de cardinalité sont incorrectes pour l’entrée de jointure de génération externe, un algorithme de jointure inapproprié peut être sélectionné.  Si cela se produit et l’instruction est éligible pour une jointure adaptive, une boucle imbriquée sera utilisée pour les entrées de jointure plus petites et sera utilisée pour les entrées de jointure supérieure une jointure de hachage dynamiquement sans nécessiter de recompilation. |
|Plans triviales faisant référence à des index Columnstore ne sont pas éligibles pour une exécution en mode batch. |Un plan trivial faisant référence à des index Columnstore est ignoré en faveur d’un plan éligible pour une exécution en mode batch.|
|L’opérateur UDX sp_execute_external_script peut s’exécuter uniquement en mode ligne.|L’opérateur UDX sp_execute_external_script est éligible pour une exécution en mode batch.|  
|Fonction table à instructions multiples n’ont pas l’exécution entrelacée |Exécution entrelacée de multi-instruction améliorer la qualité du plan. |

Les correctifs qui étaient sous l’indicateur de trace 4199 dans les versions antérieures de SQL Server antérieure à SQL Server 2017 sont maintenant activés par défaut. Avec le mode de compatibilité 140. Indicateur de trace 4199 sera toujours applicable pour les nouveaux correctifs d’optimiseur de requête sont libérés après SQL Server 2017. Pour plus d’informations sur l’indicateur de Trace 4199, consultez [indicateur de Trace 4199](https://support.microsoft.com/en-us/kb/974006).  
  
## <a name="differences-between-compatibility-level-120-and-level-130"></a>Différences entre le niveau de compatibilité 120 et 130 de niveau  
Cette section décrit les nouveaux comportements introduits avec le niveau de compatibilité 130.   

  
|Paramètre de niveau de compatibilité inférieur ou égal à 120|Paramètre de niveau de compatibilité de 130|  
|--------------------------------------------------|-----------------------------------------|  
|L’insertion dans une instruction Insert select est monothread.|L’insertion dans une instruction Insert select est multithread, ou peut avoir un plan parallèle.|  
|Les requêtes sur une table optimisée en mémoire s’exécutent monothread.|Les requêtes sur une table mémoire optimisée peuvent avoir maintenant des plans parallèles.|  
|A introduit l’estimateur de cardinalité de 2014 SQL **CardinalityEstimationModelVersion = « 120 »**|Planifier des améliorations d’estimation avec le 130 de modèle d’Estimation de la cardinalité qui est visible à partir d’une requête supplémentaire cardinalité. **CardinalityEstimationModelVersion = « 130 »**|  
|Mode de traitement par lots ou en Mode ligne les modifications avec index Columnstore<br /><br /> Effectue un tri sur une table avec un index Columnstore est en mode ligne<br /><br /> Agrégats de fonction de fenêtrage fonctionnent en mode de ligne telles que le retard ou responsable<br /><br /> Requêtes sur les tables Columnstore avec plusieurs clauses distincts exploitées en mode ligne<br /><br /> Requêtes s’exécutant sous MAXDOP 1 ou avec un plan en série exécutée en mode ligne | Mode de traitement par lots ou en Mode ligne les modifications avec index Columnstore<br /><br /> Effectue un tri sur une table avec un index Columnstore est maintenant en mode batch<br /><br /> Agrégats de fenêtrage fonctionnent désormais en mode batch telles que le retard ou responsable<br /><br /> Les requêtes sur les tables Columnstore avec plusieurs clauses distinctes fonctionnent en mode Batch<br /><br /> Requêtes en cours d’exécution sous Maxdop1 ou avec un plan en série s’exécutent en Mode Batch|  
| Les statistiques peuvent être automatiquement mis à jour. | La logique qui met automatiquement à jour des statistiques est plus agressive sur des tables volumineuses.  Dans la pratique, cela doit réduire les cas où les clients ont bénéficié des problèmes de performances sur les requêtes où les lignes nouvellement insérées sont interrogés fréquemment, mais où les statistiques n'avaient pas été mis à jour pour inclure les valeurs. |  
| Trace 2371 est désactivé par défaut dans [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]. | [Trace 2371](https://blogs.msdn.microsoft.com/psssql/2016/10/04/default-auto-statistics-update-threshold-change-for-sql-server-2016/) est activé par défaut dans [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]. Indicateur de trace 2371 indique à la mise à jour des statistiques automatiques à échantillonner un sous-ensemble plus petit encore plus sage de lignes, dans une table qui comporte un grand nombre de lignes. <br/> <br/> Une amélioration consiste à inclure, dans l’exemple, plusieurs lignes qui ont été insérées récemment. <br/> <br/> Une autre amélioration consiste à laisser les requêtes à exécuter pendant le processus de mise à jour des statistiques est en cours d’exécution, plutôt que la requête de blocage. |  
| Pour le niveau 120, les statistiques sont échantillonnées par un *unique*-thread de processus. | Pour le niveau 130, les statistiques sont échantillonnées par un *multi*-thread de processus. |  
| les clés étrangères entrantes 253 est la limite. | Une table donnée peut être référencée par des clés étrangères entrantes jusqu'à 10 000 ou références similaire. Pour connaître les restrictions associées, consultez [Create Foreign Key Relationships](../../relational-databases/tables/create-foreign-key-relationships.md). |  
|Les algorithmes de hachage MD2, MD4, MD5, SHA et SHA1 déconseillées sont autorisés.|Les algorithmes de hachage SHA2_256 et SHA2_512 uniquement sont autorisés.|  
  
  
Indicateur de correctifs qui étaient inclus dans la trace 4199 dans les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] antérieures à [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] sont maintenant activés par défaut. Avec le mode de compatibilité 130. Indicateur de trace 4199 sera applicable pour les nouveaux correctifs d’optimiseur de requête sont libérés après [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]. Pour utiliser l’optimiseur de requête plus ancienne dans [!INCLUDE[ssSDS](../../includes/sssds-md.md)] vous devez sélectionner le niveau de compatibilité 110. Pour plus d’informations sur l’indicateur de Trace 4199, consultez [indicateur de Trace 4199](https://support.microsoft.com/en-us/kb/974006).  
  
## <a name="differences-between-lower-compatibility-levels-and-level-120"></a>Différences entre les niveaux de compatibilité inférieurs et le niveau 120  
 Cette section décrit les nouveaux comportements introduits avec le niveau de compatibilité 120.  
  
|Paramètre de niveau de compatibilité inférieur ou égal à 110|Paramètre de niveau de compatibilité égal à 120|  
|--------------------------------------------------|-----------------------------------------|  
|L'ancien optimiseur de requête est utilisé.|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] inclut des améliorations appréciables dans le composant qui crée et optimise les plans de requête. Cette nouvelle fonctionnalité de l'optimiseur de requête dépend de l'utilisation du niveau de compatibilité 120 de la base de données. Pour bénéficier de ces améliorations, vous devez développer des applications de base de données à l'aide d'un niveau de compatibilité de base de données 120. Les applications qui sont migrées des versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doivent être soigneusement testées pour vérifier que de bonnes performances sont conservées ou améliorées. Si les performances se dégradent, définissez le niveau de compatibilité 110 ou inférieur de base de données pour utiliser la méthodologie de l'ancien optimiseur de requête.<br /><br /> Le niveau de compatibilité 120 de la base de données utilise un nouvel estimateur de cardinalité qui est réglé pour le stockage des données et les charges de travail OLTP modernes. Avant de définir le niveau de compatibilité de base de données à 110 en raison de problèmes de performances, consultez les recommandations contenues dans la section Plans de requête de la [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] [Nouveautés du moteur de base de données](../../database-engine/configure-windows/what-s-new-in-sql-server-2016-database-engine.md) rubrique.|  
|Dans les niveaux de compatibilité inférieurs à 120, le paramètre de langue est ignoré lorsque vous convertissez un **date** à une valeur de chaîne. Notez que ce comportement est spécifique à la **date** type. Consultez l’exemple B dans la section exemples ci-dessous.|Le paramètre de langue n’est pas ignoré lors de la conversion un **date** à une valeur de chaîne.|  
|Les références récursives dans la partie droite d'une clause EXCEPT créent une boucle infinie. Exemple C dans la section exemples ci-dessous illustre ce comportement.|Les références récursives dans une clause EXCEPT génèrent une erreur conformément à la norme SQL ANSI.|  
|Une expression CTE récursive autorise les noms de colonnes en double.|Les expressions CTE récursives n'autorisent pas les noms de colonnes en double.|  
|Les déclencheurs désactivés sont activés en cas de modifications.|La modification d'un déclencheur ne modifie pas son état (activé ou désactivé).|  
|La clause de table OUTPUT INTO ignore le paramètre IDENTITY_INSERT SETTING = OFF et permet l'insertion de valeurs explicites.|Il est impossible d'insérer des valeurs explicites dans une colonne identité de table quand IDENTITY_INSERT a la valeur OFF.|  
|Lorsque la relation contenant-contenu de base de données a la valeur partielle, la validation du champ $action dans la clause OUTPUT d'une instruction MERGE peut retourner une erreur de classement.|Le classement des valeurs retournées par la clause $action d'une instruction MERGE est le classement de la base de données à la place du classement du serveur et aucune erreur de conflit de classement n'est retournée.|  
|A **SELECT INTO** instruction toujours crée une opération d’insertion monothread.|A **SELECT INTO** instruction peut créer une opération d’insertion parallèle. Lors de l'insertion d'un grand nombre de lignes, l'opération parallèle peut améliorer les performances.|  
  
## <a name="differences-between-lower-compatibility-levels-and-levels-110-and-120"></a>Différences entre les niveaux de compatibilité inférieurs et les niveaux 110 et 120  
 Cette section décrit les nouveaux comportements introduits avec le niveau de compatibilité 110.   Cette section s'applique également au niveau 120.  
  
|Paramètre de niveau de compatibilité inférieur ou égal à 100|Paramètre de niveau de compatibilité d'au moins 110|  
|--------------------------------------------------|--------------------------------------------------|  
|Les objets de base de données CLR (Common Language Runtime) sont exécutés avec la version 4 du CLR. Toutefois, quelques changements de comportement introduits dans la version 4 du CLR sont évités. Pour plus d’informations, consultez [Nouveautés de l’intégration du CLR](../../relational-databases/clr-integration/clr-integration-what-s-new.md).|Les objets de base de données CLR sont exécutés avec la version 4 du CLR.|  
|Les fonctions XQuery **longueur de chaîne** et **sous-chaîne** compte chaque caractère de substitution comme deux caractères.|Les fonctions XQuery **longueur de chaîne** et **sous-chaîne** compte chaque caractère de substitution comme un caractère.|  
|PIVOT est autorisé dans une requête d'expression de table commune récursive. Cependant, la requête retourne des résultats incorrects lorsqu'il existe plusieurs lignes par regroupement.|PIVOT n'est pas autorisé dans une requête d'expression de table commune récursive. Une erreur est retournée.|  
|L'algorithme RC4 est uniquement pris en charge pour des raisons de compatibilité descendante. Le nouveau matériel ne peut être chiffré à l'aide de RC4 ou de RC4_128 que lorsque la base de données se trouve dans le niveau de compatibilité 90 ou 100. (Non recommandé.) Dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], le matériel chiffré à l’aide de RC4 ou RC4_128 peut être déchiffré dans n’importe quel niveau de compatibilité.|Le nouveau matériel ne peut pas être chiffré à l'aide de RC4 ou RC4_128. Utilisez à la place un algorithme plus récent, tel qu'un des algorithmes AES. Dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], le matériel chiffré à l’aide de RC4 ou RC4_128 peut être déchiffré dans n’importe quel niveau de compatibilité.|  
|Le style par défaut pour les opérations CAST et CONVERT sur **temps** et **datetime2** des types de données est 121, sauf lorsque le type est utilisé dans une expression de colonne calculée. Pour les colonnes calculées, le style par défaut est 0. Ce comportement influe sur les colonnes calculées lorsqu'elles sont créées, utilisées dans des requêtes impliquant le paramétrage automatique, ou utilisées dans des définitions de contraintes.<br /><br /> Exemple D dans la section exemples ci-dessous montre la différence entre les styles 0 et 121. Il ne présente pas le comportement décrit ci-dessus. Pour plus d’informations sur les styles de date et d’heure, consultez [CAST et CONVERT &#40; Transact-SQL &#41; ](../../t-sql/functions/cast-and-convert-transact-sql.md).|Niveau de compatibilité est 110, le style par défaut pour les opérations CAST et CONVERT sur **temps** et **datetime2** des types de données est toujours 121. Si votre requête repose sur l'ancien comportement, utilisez un niveau de compatibilité inférieur à 110, ou spécifiez explicitement le style 0 dans la requête affectée.<br /><br /> La mise à niveau de la base de données vers le niveau de compatibilité 110 ne modifie pas les données utilisateur stockées sur le disque. Vous devez corriger manuellement ces données comme il convient. Par exemple, si vous avez utilisé SELECT INTO pour créer une table à partir d'une source qui contenait une expression de colonne calculée décrite ci-dessus, les données (utilisant le style 0) sont stockées à la place de la définition de colonne calculée. Vous devez mettre à jour manuellement ces données pour qu'elles correspondent au style 121.|  
|Toutes les colonnes des tables distantes du type **smalldatetime** qui sont référencées dans une vue partitionnée sont mappées en **datetime**. Les colonnes correspondantes dans les tables locales (dans la même position ordinale dans la liste de sélection) doivent être de type **datetime**.|Toutes les colonnes des tables distantes du type **smalldatetime** qui sont référencées dans une vue partitionnée sont mappées en **smalldatetime**. Les colonnes correspondantes dans les tables locales (dans la même position ordinale dans la liste de sélection) doivent être de type **smalldatetime**.<br /><br /> Après la mise à niveau en 110, la vue partitionnée distribuée échoue en raison d'une incompatibilité de type de données. Vous pouvez résoudre ce problème en modifiant le type de données sur la table distante en **datetime** ou en définissant la compatibilité au niveau de la base de données locale à 100 ou inférieure.|  
|La fonction SOUNDEX implémente les règles suivantes :<br /><br /> (1) MAJUSCULE H ou W majuscules sont ignorés lors de la séparation de deux consonnes qui ont le même numéro dans le code SOUNDEX.<br /><br /> 2) si les 2 premiers caractères de *character_expression* ont le même numéro dans le code SOUNDEX, les deux caractères sont inclus. Sinon, si un jeu de consonnes côte à côte ont le même numéro dans le code SOUNDEX, toutes sont exclues à l'exception de la première.|La fonction SOUNDEX implémente les règles suivantes :<br /><br /> (1) si les majuscules H ou W majuscules séparer deux consonnes qui ont le même numéro dans le code SOUNDEX, la consonne à droite est ignorée.<br /><br /> 2) si un jeu de consonnes de côte-à-côte ont le même numéro dans le code SOUNDEX, toutes sont exclues, sauf le premier.<br /><br /> <br /><br /> Des règles supplémentaires peuvent entraîner des disparités entre les valeurs calculées par la fonction SOUNDEX et les valeurs calculées sous des niveaux de compatibilité précédents. Après la mise à niveau vers le niveau de compatibilité 110, vous pouvez être amené à reconstruire les index, les segments de mémoire ou les contraintes CHECK qui utilisent la fonction SOUNDEX. Pour plus d’informations, consultez [SOUNDEX &#40; Transact-SQL &#41;](../../t-sql/functions/soundex-transact-sql.md)|  
  
## <a name="differences-between-compatibility-level-90-and-level-100"></a>Différences entre le niveau de compatibilité 90 et le niveau 100  
 Cette section décrit les nouveaux comportements introduits avec le niveau de compatibilité 100.  
  
|Paramètre de niveau de compatibilité égal à 90|Paramètre de niveau de compatibilité égal à 100|Possibilité d'impact|  
|----------------------------------------|-----------------------------------------|---------------------------|  
|Le paramètre QUOTED_IDENTIFER est toujours défini sur ON pour les fonctions de table à instructions multiples lorsqu'elles sont créées indépendamment du paramètre de niveau de session.|Le paramètre de session QUOTED IDENTIFIER est respecté lorsque les fonctions de table à instructions multiples sont créées.|Moyenne|  
|Lorsque vous créez ou modifiez une fonction de partition, **datetime** et **smalldatetime** littéraux dans la fonction sont évalués en supposant que US_English comme paramètre de langue.|Le paramètre de langue actuel est utilisé pour évaluer **datetime** et **smalldatetime** littéraux dans la fonction de partition.|Moyenne|  
|La clause FOR BROWSE est autorisée (et ignorée) dans les instructions INSERT et SELECT INTO.|La clause FOR BROWSE n'est pas autorisée dans les instructions INSERT et SELECT INTO.|Moyenne|  
|Les prédicats de texte intégral sont autorisés dans la clause OUTPUT.|Les prédicats de texte intégral ne sont pas autorisés dans la clause OUTPUT.|Faible|  
|Les instructions CREATE FULLTEXT STOPLIST, ALTER FULLTEXT STOPLIST et DROP FULLTEXT STOPLIST ne sont pas prises en charge. La liste de mots vides système est associée automatiquement aux nouveaux index de recherche en texte intégral.|Les instructions CREATE FULLTEXT STOPLIST, ALTER FULLTEXT STOPLIST et DROP FULLTEXT STOPLIST sont prises en charge.|Faible|  
|MERGE n'est pas appliqué comme mot clé réservé.|MERGE est un mot clé entièrement réservé. L'instruction MERGE est prise en charge sous les niveaux de compatibilité 100 et 90.|Faible|  
|À l’aide de la \<dml_table_source > argument de l’instruction INSERT déclenche une erreur de syntaxe.|Vous pouvez capturer les résultats d'une clause OUTPUT dans une instruction imbriquée INSERT, UPDATE, DELETE ou MERGE, puis les insérer dans une table ou une vue cible. Cette opération est effectuée à l’aide de la \<dml_table_source > argument de l’instruction INSERT.|Faible|
|Sauf si l'option NOINDEX est spécifiée, DBCC CHECKDB ou DBCC CHECKTABLE effectue les vérifications de la cohérence physique et logique sur une seule table ou vue indexée et sur tous ses index non cluster et XML. Les index spatiaux ne sont pas pris en charge.|DBCC CHECKDB ou DBCC CHECKTABLE effectue les vérifications de cohérence physique et logique sur une seule table et sur tous ses index non cluster, sauf si l'option NOINDEX est spécifiée. Toutefois, seules des vérifications de cohérence physique sont effectuées par défaut sur les index XML, les index spatiaux et les vues indexées.<br /><br /> Si WITH EXTENDED_LOGICAL_CHECKS est spécifié, des vérifications logiques sont effectuées sur des vues indexées, des index XML et des index spatiaux, là où ils sont présents. Par défaut, les vérifications de cohérence physique sont effectuées avant les vérifications de cohérence logique. Si l'option NOINDEX est également spécifiée, seules les vérifications logiques sont effectuées.|Faible|  
|Lorsqu'une clause OUTPUT est utilisée avec une instruction des langages de manipulation de données (DML) et une erreur d'exécution se produit pendant l'exécution d'instruction, la transaction complète est terminée et restaurée.|Lorsqu'une clause OUTPUT est utilisée avec une instruction DML (Data Manipulation Language) et qu'une erreur d'exécution se produit pendant l'exécution de l'instruction, le comportement est déterminé par le paramètre SET XACT_ABORT. Si SET XACT_ABORT a la valeur OFF, une erreur de l'abandon de l'instruction générée par l'instruction DML à l'aide de la clause OUTPUT met fin à l'instruction, mais l'exécution du lot continue et la transaction n'est pas restaurée. Si SET XACT_ABORT a la valeur ON, toutes les erreurs d'exécution générées par l'instruction DML à l'aide de la clause OUTPUT termineront le lot, et la transaction est restaurée.|Faible|  
|CUBE et ROLLUP ne sont pas appliqués comme mots clé réservés.|CUBE et ROLLUP sont des mots clé réservés dans la clause GROUP BY.|Faible|  
|Une validation stricte est appliquée aux éléments du document XML **anyType** type.|Validation de type lax est appliquée aux éléments de la **anyType** type. Pour plus d’informations, consultez [composants génériques et Validation du contenu](../../relational-databases/xml/wildcard-components-and-content-validation.md).|Faible|  
|Les attributs spéciaux **xsi : nil** et **xsi : type** ne peut pas être interrogés ou modifiés par les instructions de langage de manipulation de données.<br /><br /> Cela signifie que `/e/@xsi:nil` échoue alors que `/e/@*` ignore la **xsi : nil** et **xsi : type** attributs. Toutefois, `/e` retourne le **xsi : nil** et **xsi : type** par souci de cohérence avec les attributs `SELECT xmlCol`, même si `xsi:nil = "false"`.|Les attributs spéciaux **xsi : nil** et **xsi : type** sont stockés comme attributs réguliers et peut être interrogé et modifié.<br /><br /> Par exemple, l’exécution de la requête `SELECT x.query('a/b/@*')` retourne tous les attributs, y compris **xsi : nil** et **xsi : type**. Pour exclure ces types dans la requête, remplacez `@*` avec `@*[namespace-uri(.) != "` *insérer uri d’espace de noms xsi* `"` et non `(local-name(.) = "type"` ou`local-name(.) ="nil".`|Faible|  
|Une fonction définie par l'utilisateur qui convertit une valeur de chaîne constante XML en un type datetime [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est marquée comme déterministe.|Une fonction définie par l'utilisateur qui convertit une valeur de chaîne constante XML en un type datetime [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est marquée comme non déterministe.|Faible|  
|Les types de liste et d'union XML ne sont pas pris en charge complètement.|Les types de liste et d'union sont complètement pris en charge ainsi que les fonctionnalités suivantes :<br /><br /> Union de liste<br /><br /> Union d'union<br /><br /> Liste de types atomiques<br /><br /> Liste d'union|Faible|  
|Les options SET requises pour une méthode xQuery ne sont pas validées lorsque la méthode est contenue dans une vue ou une fonction table incluse.|Les options SET requises pour une méthode xQuery sont validées lorsque la méthode est contenue dans une vue ou une fonction table incluse. Une erreur survient si les options SET de la méthode sont définies incorrectement.|Faible|  
|Les valeurs d'attribut XML qui contiennent des caractères de fin de ligne (retour chariot et saut de ligne) ne sont pas normalisées selon la norme XML. Autrement dit, les deux caractères sont retournés à la place d'un caractère de saut de ligne unique.|Les valeurs d'attribut XML qui contiennent des caractères de fin de ligne (retour chariot et saut de ligne) sont normalisées selon la norme XML. Autrement dit, tous les sauts de ligne dans les entités analysées externes (y compris l'entité de document) sont normalisés à l'entrée en un caractère unique #xA par la traduction de la séquence de deux caractères #xD #xA et #xD qui n'est pas suivi de #xA.<br /><br /> Les applications qui utilisent des attributs pour transporter des valeurs de chaîne qui contiennent des caractères de fin de ligne ne recevront pas ces caractères en retour lorsqu'ils sont soumis. Pour éviter le processus de normalisation, utilisez les entités de caractère numérique XML pour encoder tous les caractères de fin de ligne.|Faible|  
|Les propriétés de colonne ROWGUIDCOL et IDENTITY peuvent être nommées de manière incorrecte en tant que contrainte. Par exemple, l'instruction `CREATE TABLE T (C1 int CONSTRAINT MyConstraint IDENTITY)` s'exécute, mais le nom de contrainte n'est pas conservé et n'est pas accessible à l'utilisateur.|Les propriétés de colonne ROWGUIDCOL et IDENTITY ne peuvent pas être nommées en tant que contrainte. L'erreur 156 est retournée.|Faible|  
|La mise à jour des colonnes en utilisant une affectation bidirectionnelle telle que `UPDATE T1 SET @v = column_name = <expression>` peut produire des résultats inattendus parce que la valeur vivante de la variable peut être utilisée dans d'autres clauses telles que la clause WHERE et ON pendant l'exécution d'instruction à la place de la valeur de départ de l'instruction. Cette opération peut modifier les significations des prédicats de façon imprévisible et ligne par ligne.<br /><br /> Ce comportement est applicable uniquement lorsque le niveau de compatibilité est défini à 90.|La mise à jour de colonnes en utilisant une affectation bidirectionnelle produit des résultats attendus car seule la valeur de départ d'instruction de la colonne fait l'objet d'un accès pendant l'exécution de l'instruction.|Faible|  
|Consultez l’exemple E dans la section exemples ci-dessous.|Consultez l’exemple F dans la section exemples ci-dessous.|Faible|  
|La fonction ODBC {fn CONVERT()} utilise le format de date par défaut de la langue. Pour certaines langues, le format par défaut est YDM, ce qui peut provoquer des erreurs de conversion lorsque CONVERT() est associé à d'autres fonctions, telles que {fn CURDATE ()}, qui attendent un format YMD.|La fonction ODBC {fn CONVERT()} utilise le style 121 (format YMD indépendant de la langue) lors de la conversion aux types de données ODBC SQL_TIMESTAMP, SQL_DATE, SQL_TIME, SQLDATE, SQL_TYPE_TIME et SQL_TYPE_TIMESTAMP.|Faible|  
|Les intrinsèques datetime tels que DATEPART ne requièrent pas que les valeurs d'entrée de chaîne soient des littéraux datetime valides. Par exemple, SELECT DATEPART (année, '2007/05-30') compile correctement.|Les intrinsèques datetime tels que DATEPART requièrent que les valeurs d'entrée de chaîne soient des littéraux datetime valides. L'erreur 241 est retournée lorsqu'un littéral datetime non valide est utilisé.|Faible|  
  
## <a name="reserved-keywords"></a>Mots clés réservés  
 Le paramètre de compatibilité détermine aussi les mots clés réservés par le [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Le tableau suivant illustre les mots clés réservés introduits par chacun des niveaux de compatibilité.  
  
|Paramètre de niveau de compatibilité|Mots clés réservés|  
|----------------------------------|-----------------------|  
|130|Doit être déterminé.|  
|120|Aucun.|  
|110|WITHIN GROUP, TRY_CONVERT, SEMANTICKEYPHRASETABLE, SEMANTICSIMILARITYDETAILSTABLE, SEMANTICSIMILARITYTABLE|  
|100|CUBE, MERGE, ROLLUP|  
|90|EXTERNAL, PIVOT, UNPIVOT, REVERT, TABLESAMPLE|  
  
 À un niveau de compatibilité spécifique, les mots clés réservés incluent l'ensemble des mots clés introduits à partir de ce niveau ou sous celui-ci. Ainsi, pour les applications au niveau 110, par exemple, l'ensemble des mots clés répertoriés dans le tableau précédent sont réservés. À des niveaux de compatibilité inférieurs, les mots clés de niveau 100 demeurent des noms d'objet valides, mais les fonctions de langage de niveau 110 correspondant à ces mots clés sont indisponibles.  
  
 Une fois introduit, un mot clé demeure réservé. Le mot clé réservé PIVOT, par exemple, introduit au niveau de compatibilité 90, est également réservé aux niveaux 100 et 110 et 120.  
  
 Si une application utilise un identificateur réservé en tant que mot clé pour son niveau de compatibilité, l'application échoue. Pour contourner ce problème, placez l’identificateur entre deux crochets (**[]**) ou des guillemets (**» «**), par exemple, pour mettre à niveau une application qui utilise l’identificateur **externe** au niveau de compatibilité 90, vous pouvez modifier l’identificateur soit **[EXTERNAL]** ou **« EXTERNAL »**.  
  
 Pour plus d’informations, consultez [Mots clés réservés &#40;Transact-SQL&#41;](../../t-sql/language-elements/reserved-keywords-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'autorisation ALTER sur la base de données.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-changing-the-compatibility-level"></a>A. Modification du niveau de compatibilité  
 L’exemple suivant modifie le niveau de compatibilité de la [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] à la base de données `110,` [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].  
  
```tsql  
ALTER DATABASE AdventureWorks2012  
SET COMPATIBILITY_LEVEL = 110;  
GO  
```  
  
 L’exemple suivant retourne le niveau de compatibilité de la base de données actuelle.  
  
```tsql  
SELECT name, compatibility_level   
FROM sys.databases   
WHERE name = db_name();  
```  
  
### <a name="b-ignoring--the-set-language-statement-except-under-compatibility-level-120"></a>B. En ignorant l’instruction SET LANGUAGE sauf sous le niveau de compatibilité 120  
 La requête suivante ignore l’instruction SET LANGUAGE sauf sous le niveau de compatibilité 120.  
  
```tsql  
SET DATEFORMAT dmy;   
DECLARE @t2 date = '12/5/2011' ;  
SET LANGUAGE dutch;   
SELECT CONVERT(varchar(11), @t2, 106);   
  
-- Results when the compatibility level is less than 120.   
12 May 2011   
  
-- Results when the compatibility level is set to 120).  
12 mei 2011  
```  
  
### <a name="c"></a>C.  
 Pour le paramètre de niveau de compatibilité inférieur ou égal à 110, les références récursives dans la partie droite d’une clause EXCEPT créent une boucle infinie.  
  
```tsql  
WITH   
cte AS (SELECT * FROM (VALUES (1),(2),(3)) v (a)),  
r   
AS (SELECT a FROM Table1  
UNION ALL  
(SELECT a FROM Table1 EXCEPT SELECT a FROM r) )   
SELECT a   
FROM r;  
  
```  
  
### <a name="d"></a>D.  
 Cet exemple montre la différence entre les styles 0 et 121. Pour plus d’informations sur les styles de date et d’heure, consultez [CAST et CONVERT &#40; Transact-SQL &#41; ](../../t-sql/functions/cast-and-convert-transact-sql.md).  
  
```tsql  
CREATE TABLE t1 (c1 time(7), c2 datetime2);   
  
INSERT t1 (c1,c2) VALUES (GETDATE(), GETDATE());  
  
SELECT CONVERT(nvarchar(16),c1,0) AS TimeStyle0  
       ,CONVERT(nvarchar(16),c1,121)AS TimeStyle121  
       ,CONVERT(nvarchar(32),c2,0) AS Datetime2Style0  
       ,CONVERT(nvarchar(32),c2,121)AS Datetime2Style121  
FROM t1;  
  
-- Returns values such as the following.  
TimeStyle0       TimeStyle121       
Datetime2Style0      Datetime2Style121  
---------------- ----------------   
-------------------- --------------------------  
3:15PM           15:15:35.8100000   
Jun  7 2011  3:15PM  2011-06-07 15:15:35.8130000  
```  
  
### <a name="e"></a>E.  
 L'attribution de variable est autorisée dans une instruction contenant un opérateur UNION de niveau supérieur, celle-ci produit néanmoins des résultats inattendus. Par exemple, dans les instructions suivantes, la variable locale `@v` reçoit la valeur de la colonne `BusinessEntityID` issue de l'union de deux tables. Par définition, lorsque l'instruction SELECT retourne plusieurs valeurs, la dernière valeur retournée est affectée à la variable. Dans ce cas, la dernière valeur est attribuée correctement à la variable, toutefois, le jeu de résultats de l'instruction SELECT UNION est également retourné.  
  
```tsql  
ALTER DATABASE AdventureWorks2012  
SET compatibility_level = 90;  
GO  
USE AdventureWorks2012;  
GO  
DECLARE @v int;  
SELECT @v = BusinessEntityID FROM HumanResources.Employee  
UNION ALL  
SELECT @v = BusinessEntityID FROM HumanResources.EmployeeAddress;  
SELECT @v;  
```  
  
### <a name="f"></a>F.  
 L'attribution de variable n'est pas autorisée dans une instruction contenant un opérateur UNION de niveau supérieur. L'erreur 10734 est retournée. Pour résoudre l'erreur, réécrivez la requête, comme dans l'exemple suivant.  
  
```tsql  
DECLARE @v int;  
SELECT @v = BusinessEntityID FROM   
    (SELECT BusinessEntityID FROM HumanResources.Employee  
     UNION ALL  
     SELECT BusinessEntityID FROM HumanResources.EmployeeAddress) AS Test;  
SELECT @v;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [Mots clés réservés &#40;Transact-SQL&#41;](../../t-sql/language-elements/reserved-keywords-transact-sql.md)   
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](../../t-sql/functions/databasepropertyex-transact-sql.md)   
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)  
 [Afficher ou modifier le niveau de compatibilité d'une base de données](../../relational-databases/databases/view-or-change-the-compatibility-level-of-a-database.md) 
  
