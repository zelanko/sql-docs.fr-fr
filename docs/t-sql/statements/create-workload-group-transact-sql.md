---
title: CREATE WORKLOAD GROUP (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/18/2019
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- WORKLOAD GROUP
- WORKLOAD_GROUP_TSQL
- CREATE WORKLOAD GROUP
- CREATE_WORKLOAD_GROUP_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CREATE WORKLOAD GROUP statement
author: julieMSFT
ms.author: jrasnick
manager: craigg
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azure-sqldw-latest||=azuresqldb-mi-current'
ms.openlocfilehash: bed396bf39b4b621c5b333a7b13218998264675a
ms.sourcegitcommit: f018eb3caedabfcde553f9a5fc9c3e381c563f1a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2019
ms.locfileid: "74165896"
---
# <a name="create-workload-group-transact-sql"></a>CREATE WORKLOAD GROUP (Transact-SQL)

## <a name="click-a-product"></a>Cliquez sur un produit !

Dans la ligne suivante, cliquez sur le nom du produit qui vous intéresse. Le clic affiche un contenu différent ici dans cette page web, approprié pour le produit sur lequel vous cliquez.

::: moniker range=">=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current||=sqlallproducts-allversions"

> |||||
> |---|---|---|---|
> |**_\* SQL Server \*_** &nbsp;|[Instance managée<br />SQL Database](create-workload-group-transact-sql.md?view=azuresqldb-mi-current)|[SQL Data<br />Warehouse](create-workload-group-transact-sql.md?view=azure-sqldw-latest)|

&nbsp;

## <a name="sql-server-and-sql-database-managed-instance"></a>SQL Server et instance managée SQL Database

Crée un groupe de charges de travail du gouverneur de ressources et l'associe à un pool de ressources du gouverneur de ressources. Resource Governor n’est pas disponible dans toutes les éditions de [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour obtenir la liste des fonctionnalités prises en charge par les éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Fonctionnalités prise en charge par les éditions de SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).

![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).

## <a name="syntax"></a>Syntaxe

```
CREATE WORKLOAD GROUP group_name
[ WITH
    ( [ IMPORTANCE = { LOW | MEDIUM | HIGH } ]
      [ [ , ] REQUEST_MAX_MEMORY_GRANT_PERCENT = value ]
      [ [ , ] REQUEST_MAX_CPU_TIME_SEC = value ]
      [ [ , ] REQUEST_MEMORY_GRANT_TIMEOUT_SEC = value ]
      [ [ , ] MAX_DOP = value ]
      [ [ , ] GROUP_MAX_REQUESTS = value ] )
 ]
[ USING {
    [ pool_name | "default" ]
    [ [ , ] EXTERNAL external_pool_name | "default" ] ]
    } ]
[ ; ]
```

## <a name="arguments"></a>Arguments

*group_name*     
Nom défini par l'utilisateur pour le groupe de charges de travail. *group_name* est alphanumérique, peut contenir jusqu’à 128 caractères, doit être unique dans une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et doit respecter les règles applicables aux [identificateurs](../../relational-databases/databases/database-identifiers.md).

IMPORTANCE = { LOW | **MEDIUM** | HIGH }     
Spécifie l'importance relative d'une demande dans le groupe de charges de travail. Le paramètre Importance peut avoir les valeurs suivantes, MEDIUM étant la valeur par défaut :

- LOW
- MEDIUM (valeur par défaut)
- HIGH

> [!NOTE]
> En interne, chaque paramètre d'importance est stocké sous la forme d'un nombre utilisé pour les calculs.

Le paramètre IMPORTANCE est local par rapport au pool de ressources : les groupes de charges de travail d'importance différente à l'intérieur du même pool de ressources s'affectent mutuellement, mais n'affectent pas les groupes de charges de travail dans un autre pool de ressources.

REQUEST_MAX_MEMORY_GRANT_PERCENT = *value*     
Spécifie la quantité de mémoire maximale qu'une requête unique peut prendre du pool. *value* est un pourcentage relatif à la taille du pool de ressources spécifiée par MAX_MEMORY_PERCENT. 

*value* est un entier pouvant aller jusqu’à [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] et une valeur flottante commençant par [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)]. La valeur par défaut est 25. La plage autorisée pour *value* est comprise entre 1 et 100.

> [!NOTE]  
> La quantité spécifiée fait uniquement référence à la mémoire allouée à l'exécution de la requête.  
  
> [!IMPORTANT]
> L’affectation de la valeur 0 à *value* empêche l’exécution de requêtes avec les opérations SORT et HASH JOIN dans les groupes de charges de travail définis par l’utilisateur.     
>
> Il est déconseillé d’affecter à *value* une valeur supérieure à 70, car le serveur risque de ne pas pouvoir mettre de côté suffisamment de mémoire disponible si d’autres requêtes simultanées s’exécutent. Cela risque de provoquer l'erreur de délai d'attente de requête 8645.      
  
> [!NOTE]  
> Si les besoins en mémoire de la requête dépassent la limite spécifiée par ce paramètre, le serveur effectue les opérations suivantes :  
>   
> -  Pour les groupes de charges de travail définis par l'utilisateur, le serveur essaie de réduire le degré de parallélisme de la requête jusqu'à ce que ses besoins en mémoire tombent sous la limite ou jusqu'à ce que le degré de parallélisme soit égal à 1. Si les besoins en mémoire de la requête sont encore supérieurs à la limite, l'erreur 8657 se produit.  
>   
> -  Pour les groupes de charges de travail internes et par défaut, le serveur autorise la requête à obtenir la mémoire requise.  
>   
> Sachez toutefois que dans les deux cas, l'erreur de délai d'attente 8645 se produit si le serveur dispose d'une mémoire physique insuffisante.  

REQUEST_MAX_CPU_TIME_SEC = *value*     
Spécifie la quantité maximale de temps processeur, en secondes, qu'une demande peut utiliser. *value* doit être égal à 0 ou un entier positif. La valeur par défaut de *value* est 0, ce qui signifie illimité.

> [!NOTE]
> Par défaut, Resource Governor n’empêche pas une demande de continuer si le temps maximal est dépassé. Toutefois, un événement sera généré. Pour plus d’informations, consultez [Classe d’événements CPU Threshold Exceeded](../../relational-databases/event-classes/cpu-threshold-exceeded-event-class.md).     

> [!IMPORTANT]
> À compter de [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]SP2 et de [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3, quand [l’indicateur de trace 2422](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) est utilisé, Resource Governor abandonne une demande en cas de dépassement de la durée maximale.

REQUEST_MEMORY_GRANT_TIMEOUT_SEC = *value*     
Spécifie la durée maximale, en secondes, pendant laquelle une requête peut attendre qu’une allocation de mémoire (mémoire tampon de travail) devienne disponible. *value* doit être égal à 0 ou un entier positif. La valeur par défaut de *value*, 0, utilise un calcul interne basé sur le coût de requête pour déterminer le délai maximal.

> [!NOTE]
> Une requête n'échoue pas toujours lorsque le délai d'expiration d'allocation mémoire est atteint. Une requête échoue seulement si le nombre de requêtes exécutées simultanément est trop élevé. Autrement, la requête risque d'obtenir uniquement l'allocation mémoire minimale, d'où une dégradation des performances.

MAX_DOP = *value*     
Spécifie le **degré maximal de parallélisme (MAXDOP)** pour l’exécution de demandes parallèles. *value* doit être égal à 0 ou un entier positif. La plage autorisée pour *value* est comprise entre 0 et 64. Le paramètre par défaut de *value*, 0, utilise le paramètre global. MAX_DOP est géré comme suit :

> [!NOTE]
> Le groupe de charge de travail MAX_DOP remplace la [configuration du serveur pour le degré maximal de parallélisme](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md) et la [configuration étendue à la base de données](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md) **MAXDOP**.

> [!TIP]
> Pour définir cette option au niveau de la requête, utilisez l’[indicateur de requête](../../t-sql/queries/hints-transact-sql-query.md) **MAXDOP**. Définir le degré maximal de parallélisme en tant qu'indicateur de requête est efficace tant qu'il ne dépasse pas le groupe de charges de travail MAX_DOP. Si la valeur d'indicateur de requête MAXDOP dépasse la valeur configurée avec Resource Governor, le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] utilise la valeur de `MAX_DOP` Resource Governor. L’[indicateur de requête](../../t-sql/queries/hints-transact-sql-query.md) MAXDOP remplace toujours la [configuration du serveur pour le degré maximal de parallélisme](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md).      
>   
> Pour le faire au niveau de la base de données, utilisez la [configuration étendue à la base de données](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md) **MAXDOP**.      
>   
> Pour ce faire au niveau du serveur, utilisez l’[option de configuration serveur](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md) du **degré maximal de parallélisme (MAXDOP)** .     

GROUP_MAX_REQUESTS = *value*     
Spécifie le nombre maximal de demandes simultanées autorisées à s'exécuter dans le groupe de charges de travail. *value* doit être égal à 0 ou un entier positif. La valeur par défaut de *value* est 0, qui autorise un nombre illimité de demandes. Lorsque le nombre maximal de requêtes est atteint, un utilisateur de ce groupe peut se connecter, mais est placé dans un état d'attente jusqu'à ce que le nombre de requêtes simultanées soit inférieur à la valeur spécifiée.

USING { *pool_name* |  **"default"** }     
Associe le groupe de charge de travail au pool de ressources défini par l’utilisateur identifié par *pool_name*. Cette opération revient en fait à placer le groupe de charges de travail dans le pool de ressources. Si *pool_name* n’est pas fourni ou si l’argument USING n’est pas utilisé, le groupe de charge de travail est placé dans le pool par défaut Resource Governor prédéfini.

"default" est un mot réservé et doit être placé entre des guillemets doubles ("") ou des crochets ([]) lorsqu'il est utilisé avec l'argument USING.

> [!NOTE]
> Les groupes de charges de travail et les pools de ressources prédéfinis utilisent tous des noms minuscules, tels que "default". Ce facteur doit être pris en considération pour les serveurs qui utilisent un classement qui respecte la casse. Les serveurs avec un classement qui ne respecte pas la casse, tel que SQL_Latin1_General_CP1_CI_AS, traitent "default" et "Default" comme identiques.

EXTERNAL external_pool_name | "default"     
**S’applique à** : [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] et versions ultérieures).

Le groupe de charge de travail peut spécifier un pool de ressources externes. Vous pouvez définir un groupe de charge de travail et l’associer à deux pools :

- Un pool de ressources pour les charges de travail et les requêtes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]
- Un pool de ressources externes pour les processus externes. Pour plus d’informations, consultez [sp_execute_external_script &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

## <a name="remarks"></a>Notes
Quand `REQUEST_MEMORY_GRANT_PERCENT` est utilisé, la création d’index est autorisée à utiliser une mémoire d’espace de travail supérieure à celle qui lui a été initialement allouée, afin d’améliorer les performances. Cette gestion spéciale est prise en charge par le gouverneur de ressources dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Toutefois, l'allocation initiale et toute allocation de mémoire supplémentaire sont limitées par les paramètres du pool de ressources et du groupe de charges de travail.

La limite `MAX_DOP` est définie par [tâche](../../relational-databases/system-dynamic-management-views/sys-dm-os-tasks-transact-sql.md). Il ne s’agit pas d’une limite par [requête](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md). Cela signifie que lors d’une exécution de requête parallèle, une requête unique peut générer plusieurs tâches qui sont affectées à un [planificateur](../../relational-databases/system-dynamic-management-views/sys-dm-os-tasks-transact-sql.md). Pour plus d’informations, consultez le [Guide de l’architecture des threads et des tâches](../../relational-databases/thread-and-task-architecture-guide.md).

Lorsque `MAX_DOP` est utilisé et qu’une requête est marquée comme étant en série au moment de la compilation, elle ne peut être reconvertie en requête parallèle au moment de l'exécution, indépendamment du groupe de charge de travail ou du paramètre de configuration du serveur. Après la configuration de `MAX_DOP`, il ne peut être diminué qu’en raison de la sollicitation de la mémoire. La reconfiguration du groupe de charges de travail n'est pas visible lors de l'attente dans la file d'attente d'allocation de mémoire.

### <a name="index-creation-on-a-partitioned-table"></a>Création d'un index sur une table partitionnée

La mémoire consommée par la création d'index sur une table partitionnée non alignée est proportionnelle au nombre de partitions impliquées. Si la mémoire totale requise dépasse la limite par requête (`REQUEST_MAX_MEMORY_GRANT_PERCENT`) imposée par le paramètre du groupe de charges de travail de Resource Governor, cette création d’index peut échouer. Étant donné que le groupe de charges de travail *"default"* permet à une requête de dépasser la limite par requête avec la mémoire minimale, l’utilisateur peut être en mesure d’exécuter la même création d’index dans le groupe de charges de travail *"default"* , si le pool de ressources *"default"* possède assez de mémoire totale configurée pour exécuter cette requête.

## <a name="permissions"></a>Autorisations
Nécessite l'autorisation `CONTROL SERVER`.

## <a name="example"></a>Exemple

Créez un groupe de charge de travail nommé `newReports` qui utilise les paramètres par défaut de Resource Governor et se trouve dans le pool par défaut de ce dernier. L'exemple spécifie le pool `default`, mais cela n'est pas obligatoire.

```sql
CREATE WORKLOAD GROUP newReports
    USING "default" ;
GO
```

## <a name="see-also"></a>Voir aussi

- [ALTER WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/alter-workload-group-transact-sql.md)
- [DROP WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/drop-workload-group-transact-sql.md)
- [CREATE RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-resource-pool-transact-sql.md)
- [ALTER RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-pool-transact-sql.md)
- [DROP RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/drop-resource-pool-transact-sql.md)
- [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md)

::: moniker-end
::: moniker range="=azure-sqldw-latest||=sqlallproducts-allversions"

> ||||
> |---|---|---|
> |[SQL Server](create-workload-group-transact-sql.md?view=sql-server-2017)||[Instance managée<br />SQL Database](create-workload-group-transact-sql.md?view=azuresqldb-mi-current)||**_\* SQL Data<br />Warehouse \*_** &nbsp;||||

&nbsp;

## <a name="sql-data-warehouse-preview"></a>SQL Data Warehouse (préversion)

Crée un groupe de charge de travail.  Les groupes de charge de travail sont les conteneurs d’un ensemble de requêtes. Ils déterminent la façon dont la gestion des charges de travail est configurée sur un système.  Les groupes de charge de travail permettent de réserver des ressources pour l’isolation de la charge de travail. Ils contiennent des ressources, définissent les ressources par requête et adhèrent aux règles d’exécution.  Une fois l’instruction exécutée, les paramètres sont activés.

 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md). 

```
CREATE WORKLOAD GROUP group_name  
 WITH  
 (        MIN_PERCENTAGE_RESOURCE = value  
      ,   CAP_PERCENTAGE_RESOURCE = value 
      ,   REQUEST_MIN_RESOURCE_GRANT_PERCENT = value   
  [ [ , ] REQUEST_MAX_RESOURCE_GRANT_PERCENT = value ]  
  [ [ , ] IMPORTANCE = { LOW | BELOW_NORMAL | NORMAL | ABOVE_NORMAL | HIGH }]
  [ [ , ] QUERY_EXECUTION_TIMEOUT_SEC = value ] )  
  [ ; ]
```

*group_name*</br>
Spécifie le nom qui identifie le groupe de charge de travail.  group_name est un sysname.  Il peut comporter jusqu’à 128 caractères et doit être unique dans l’instance.

*MIN_PERCENTAGE_RESOURCE* = valeur</br>
Pour ce groupe de charge de travail, spécifie une allocation de ressources minimale garantie qui n’est pas partagée avec d’autres groupes de charge de travail.  La valeur est une plage d’entiers comprise entre 0 et 100.  La somme des min_percentage_resource de tous les groupes de charge de travail ne peut pas dépasser 100.  La valeur de min_percentage_resource ne peut pas être supérieure à cap_percentage_resource.  Il existe des valeurs minimales effectives autorisées pour chaque niveau de service.  Pour plus d’informations, consultez [Valeurs effectives](#effective-values).

*CAP_PERCENTAGE_RESOURCE* = valeur</br>
Spécifie l’utilisation maximale des ressources pour toutes les requêtes d’un groupe de charge de travail.  La plage d’entiers autorisée pour la valeur est comprise entre 1 et 100.  La valeur de cap_percentage_resource ne peut pas être supérieure à min_percentage_resource.  La valeur effective de cap_percentage_resource peut être réduite si min_percentage_resource est supérieur à zéro dans d’autres groupes de charge de travail.

*REQUEST_MIN_RESOURCE_GRANT_PERCENT* = valeur</br>
Définit le nombre minimal de ressources allouées par requête.  La valeur est un paramètre obligatoire avec une plage décimale comprise entre 0,75 et 100,00.  La valeur de request_min_resource_grant_percent doit être un multiple de 0,25, être un facteur de min_percentage_resource et être inférieur à cap_percentage_resource.  Il existe des valeurs minimales effectives autorisées pour chaque niveau de service.  Pour plus d’informations, consultez [Valeurs effectives](#effective-values).

Par exemple :

```sql
CREATE WORKLOAD GROUP wgSample WITH  
( MIN_PERCENTAGE_RESOURCE = 26              -- integer value
 ,REQUEST_MIN_RESOURCE_GRANT_PERCENT = 3.25 -- factor of 26 (guaranteed a minimum of 8 concurrency)
 ,CAP_PERCENTAGE_RESOURCE = 100 )
```

Aidez-vous des valeurs utilisées avec les classes de ressources pour request_min_resource_grant_percent.  Le tableau ci-dessous contient les allocations des ressources pour Gen2.

|Classe de ressource|Pourcentage de ressources|
|---|---|
|Smallrc|3 %|
|Mediumrc|10 %|
|Largerc|22 %|
|Xlargerc|70 %|
|||

*REQUEST_MAX_RESOURCE_GRANT_PERCENT* = valeur</br>
Définit le nombre maximal de ressources allouées par requête.  La valeur est un paramètre décimal facultatif avec une valeur par défaut égale à celle de request_min_resource_grant_percent.  La valeur doit être supérieure ou égale à request_min_resource_grant_percent.  Lorsque la valeur de request_max_resource_grant_percent est supérieure à request_min_resource_grant_percent et que des ressources système sont disponibles, des ressources supplémentaires sont allouées à une requête.

*IMPORTANCE* = { LOW | BELOW_NORMAL | NORMAL | ABOVE_NORMAL | HIGH }</br>
Spécifie l’importance par défaut d’une requête pour le groupe de charge de travail.  Le paramètre Importance peut avoir les valeurs suivantes, NORMAL étant la valeur par défaut :
- LOW
- BELOW_NORMAL
- NORMAL (valeur par défaut)
- ABOVE_NORMAL
- HIGH  

L’importance définie pour le groupe de charge de travail est l’importance par défaut de toutes les requêtes du groupe de charge de travail.  Un utilisateur peut également définir l’importance au niveau du classifieur, ce qui peut remplacer le paramètre d’importance du groupe de charge de travail.  Cela permet de différencier l’importance des requêtes au sein d’un groupe de charge de travail afin d’accéder plus rapidement aux ressources non réservées.  Lorsque la somme des min_percentage_resource des différents groupes de charge de travail est inférieure à 100, des ressources non réservées sont affectées selon l’importance.

*QUERY_EXECUTION_TIMEOUT_SEC* = valeur</br>
Spécifie la durée maximale (en secondes) pendant laquelle une requête peut s’exécuter avant d’être annulée.  La valeur doit être égale à 0 ou être un entier positif.  Le paramètre par défaut de la valeur est 0, ce qui signifie que la requête n’expire jamais.  Le délai QUERY_EXECUTION_TIMEOUT_SEC démarre une fois que la requête est en cours d’exécution, pas quand elle est mise en file d’attente.

## <a name="remarks"></a>Notes
Les groupes de charge de travail correspondant aux classes de ressources sont créés automatiquement pour permettre une compatibilité descendante.  Ces groupes de charge de travail définis par le système ne peuvent pas être supprimés.  Il est possible de créer 8 autres groupes de charge de travail définis par l’utilisateur.

Si un groupe de charge de travail est créé avec une valeur min_percentage_resource supérieure à zéro, l’instruction `CREATE WORKLOAD GROUP` est mise en file d’attente tant qu’il n’y a pas suffisamment de ressources pour créer le groupe de charge de travail.

## <a name="effective-values"></a>Valeurs effectives

Les paramètres min_percentage_resource, cap_percentage_resource, request_min_resource_grant_percent et request_max_resource_grant_percent ont des valeurs effectives qui sont ajustées dans le contexte du niveau de service actuel et de la configuration des autres groupes de charge de travail.

La concurrence prise en charge par chaque niveau de service est la même que lorsque les classes de ressources ont été utilisées pour définir des allocations de ressources par requête. Par conséquent, les valeurs prises en charge pour request_min_resource_grant_percent dépendent du niveau de service qui a été défini pour l’instance.  Au niveau de service le plus bas, DW100c, un minimum de 25 % des ressources par demande est nécessaire.  Au niveau DW100c, la valeur request_min_resource_grant_percent effective pour un groupe de charge de travail configuré peut s’élever à 25 % ou plus.  Pour plus d’informations sur la façon dont les valeurs effectives sont dérivées, consultez le tableau ci-dessous.

|Niveau de service|Valeur effective la plus faible pour REQUEST_MIN_RESOURCE_GRANT_PERCENT|Nombre maximal de requêtes simultanées|
|---|---|---|
|DW100c|25 %|4|
|DW200c|12,5 %|8|
|DW300c|8 %|12|
|DW400c|6,25 %|16|
|DW500c|5 %|20|
|DW1000c|3 %|32|
|DW1500c|3 %|32|
|DW2000c|2 %|48|
|DW2500c|2 %|48|
|DW3000c|1,5 %|64|
|DW5000c|1,5 %|64|
|DW6000c|0,75 %|128|
|DW7500c|0,75 %|128|
|DW10000c|0,75 %|128|
|DW15000c|0,75 %|128|
|DW30000c|0,75 %|128|
||||

De même, request_min_resource_grant_percent et min_percentage_resource doivent être supérieurs ou égaux à la valeur effective de request_min_resource_grant_percent.  Un groupe de charge de travail avec un min_percentage_resource inférieur à la valeur effective de min_percentage_resource voit sa valeur définie sur zéro au moment de l’exécution.  Dans ce cas, les ressources configurées pour min_percentage_resource peuvent être partagées entre tous les groupes de charge de travail.  Par exemple, le groupe de charge de travail wgAdHoc avec un min_percentage_resource de 10 % exécuté avec DW1000c aura un min_percentage_resource effectif de 10 % (3,25 % est la valeur minimale prise en charge par DW1000c).  wgAdhoc avec DW100c aura un min_percentage_resource effectif de 0 %.  Les 10 % configurés pour wgAdhoc seront partagés entre tous les groupes de charge de travail.

Cap_percentage_resource a également une valeur effective.  Si un groupe de charge de travail wgAdhoc est configuré avec un cap_percentage_resource de 100 %, et si un autre groupe de charge de travail wgDashboards est créé avec un min_percentage_resource de 25 %, la valeur effective de cap_percentage_resource pour wgAdhoc devient 75 %.

Le moyen le plus simple de comprendre les valeurs d’exécution de vos groupes de charge de travail consiste à interroger la vue système [sys.dm_workload_management_workload_groups_stats](../../relational-databases/system-dynamic-management-views/sys-dm-workload-management-workload-group-stats-transact-sql.md).


## <a name="permissions"></a>Autorisations

Exige l’autorisation CONTROL DATABASE

## <a name="see-also"></a>Voir aussi
[DROP WORKLOAD GROUP (Transact-SQL)](drop-workload-group-transact-sql.md) <br>
[sys.workload_management_workload_groups](../../relational-databases/system-catalog-views/sys-workload-management-workload-groups-transact-sql.md) <br>
[sys.dm_workload_management_workload_groups_stats](../../relational-databases/system-dynamic-management-views/sys-dm-workload-management-workload-group-stats-transact-sql.md) <br>
Démarrage rapide de la création et de l’utilisation d’un [groupe de charge de travail](https://docs.microsoft.com/azure/sql-data-warehouse/quickstart-configure-workload-isolation-tsql)

::: moniker-end
