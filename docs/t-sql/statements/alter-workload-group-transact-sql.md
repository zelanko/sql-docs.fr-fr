---
title: ALTER WORKLOAD GROUP (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 01/19/2016
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_WORKLOAD_GROUP_TSQL
- ALTER WORKLOAD GROUP
dev_langs: TSQL
helpviewer_keywords: ALTER WORKLOAD GROUP statement
ms.assetid: 957addce-feb0-4e54-893e-5faca3cd184c
caps.latest.revision: "56"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7bfb6ca0200095860acec2b275020012e4b96284
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="alter-workload-group-transact-sql"></a>ALTER WORKLOAD GROUP (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifie une configuration de groupe de charge de travail du gouverneur de ressources existante et éventuellement l’assigne à un à un pool de ressources du gouverneur de ressources.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "icône lien de rubrique") [Conventions de syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
ALTER WORKLOAD GROUP { group_name | "default" }  
[ WITH  
    ([ IMPORTANCE = { LOW | MEDIUM | HIGH } ]  
      [ [ , ] REQUEST_MAX_MEMORY_GRANT_PERCENT = value ]  
      [ [ , ] REQUEST_MAX_CPU_TIME_SEC = value ]  
      [ [ , ] REQUEST_MEMORY_GRANT_TIMEOUT_SEC = value ]   
      [ [ , ] MAX_DOP = value ]  
      [ [ , ] GROUP_MAX_REQUESTS = value ] )  
 ]  
[ USING { pool_name | "default" } ]  
[ ; ]  
```  
  
## <a name="arguments"></a>Arguments  
 *nom_groupe* | «**par défaut**»  
 Nom d'un groupe de charge de travail existant défini par l'utilisateur ou du groupe de charge de travail par défaut du gouverneur de ressources.  
  
> [!NOTE]  
>  Le gouverneur de ressources crée les groupes « par défaut » et internes lorsque [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est installé.  
  
 L'option "default" doit être placée entre des guillemets doubles ("") ou des crochets ([]) lorsqu'elle est utilisée avec l'instruction ALTER WORKLOAD GROUP pour éviter tout conflit avec DEFAULT, qui est un mot réservé au système. Pour plus d'informations, consultez [Database Identifiers](../../relational-databases/databases/database-identifiers.md).  
  
> [!NOTE]  
>  Les groupes de charges de travail et les pools de ressources prédéfinis utilisent tous des noms en minuscule, tels que « default ». Ce facteur doit être pris en considération pour les serveurs qui utilisent un classement qui respecte la casse. Les serveurs avec un classement qui ne respecte pas la casse, tel que SQL_Latin1_General_CP1_CI_AS, traitent "default" et "Default" comme identiques.  
  
 IMPORTANCE = { LOW | MEDIUM | HIGH }  
 Spécifie l'importance relative d'une demande dans le groupe de charges de travail. Elle prend l'une des valeurs suivantes :  
  
-   LOW  
  
-   MEDIUM (valeur par défaut)  
  
-   HIGH  
  
> [!NOTE]  
>  En interne, chaque paramètre d'importance est stocké sous la forme d'un nombre utilisé pour les calculs.  
  
 Le paramètre IMPORTANCE est local par rapport au pool de ressources : les groupes de charges de travail d'importance différente à l'intérieur du même pool de ressources s'affectent mutuellement, mais n'affectent pas les groupes de charges de travail dans un autre pool de ressources.  
  
 REQUEST_MAX_MEMORY_GRANT_PERCENT =*valeur*  
 Spécifie la quantité de mémoire maximale qu'une requête unique peut prendre du pool. Ce pourcentage est relatif à la taille du pool de ressources spécifiée par MAX_MEMORY_PERCENT.  
  
> [!NOTE]  
>  La quantité spécifiée fait uniquement référence à la mémoire allouée à l'exécution de la requête.  
  
 *valeur* doit être 0 ou un entier positif. La plage autorisée pour *valeur* est comprise entre 0 et 100. La valeur par défaut *valeur* est 25.  
  
 Notez les points suivants :  
  
-   Paramètre *valeur* 0 empêche les requêtes des opérations SORT et HASH JOIN dans les groupes de charges de travail définis par l’utilisateur en cours d’exécution.  
  
-   Nous ne recommandons pas de paramètre *valeur* supérieure à 70, car le serveur peut être impossible de réserver suffisamment de mémoire si d’autres requêtes simultanées sont en cours d’exécution. Cela risque de provoquer l'erreur de délai d'attente de requête 8645.  
  
> [!NOTE]  
>  Si les besoins en mémoire de la requête dépassent la limite spécifiée par ce paramètre, le serveur effectue les opérations suivantes :  
>   
>  Pour les groupes de charges de travail définis par l'utilisateur, le serveur essaie de réduire le degré de parallélisme de la requête jusqu'à ce que ses besoins en mémoire tombent sous la limite ou jusqu'à ce que le degré de parallélisme soit égal à 1. Si les besoins en mémoire de la requête sont encore supérieurs à la limite, l'erreur 8657 se produit.  
>   
>  Pour les groupes de charges de travail internes et par défaut, le serveur autorise la requête à obtenir la mémoire requise.  
>   
>  Sachez toutefois que dans les deux cas, l'erreur de délai d'attente 8645 se produit si le serveur dispose d'une mémoire physique insuffisante.  
  
 REQUEST_MAX_CPU_TIME_SEC =*valeur*  
 Spécifie la quantité maximale de temps processeur, en secondes, qu'une demande peut utiliser. *valeur* doit être 0 ou un entier positif. La valeur par défaut *valeur* est 0, ce qui signifie illimité.  
  
> [!NOTE]  
>  Le gouverneur de ressources n'empêche pas une demande de continuer si le temps maximal est dépassé. Toutefois, un événement sera généré. Pour plus d’informations, consultez [seuil UC dépassé classe d’événements](../../relational-databases/event-classes/cpu-threshold-exceeded-event-class.md).  
  
 REQUEST_MEMORY_GRANT_TIMEOUT_SEC =*valeur*  
 Spécifie la durée maximale, en secondes, pendant laquelle une requête peut attendre que l'allocation de mémoire (mémoire tampon de travail) devienne disponible.  
  
> [!NOTE]  
>  Une requête n'échoue pas toujours lorsque le délai d'expiration d'allocation mémoire est atteint. Une requête échoue seulement si le nombre de requêtes exécutées simultanément est trop élevé. Autrement, la requête risque d'obtenir uniquement l'allocation mémoire minimale, d'où une dégradation des performances.  
  
 *valeur* doit être un entier positif. La valeur par défaut *valeur*, 0, utilise un calcul interne basé sur le coût de requête pour déterminer la durée maximale.  
  
 MAX_DOP =*valeur*  
 Spécifie le degré maximal de parallélisme (DOP) pour les demandes parallèles. *valeur* doit être 0 ou un entier positif, 1 et 255. Lorsque *valeur* est 0, le serveur choisit le degré maximal de parallélisme. Ceci est la valeur par défaut et recommandée.  
  
> [!NOTE]  
>  La valeur réelle définie par le [!INCLUDE[ssDE](../../includes/ssde-md.md)] pour MAX_DOP peut être inférieure à la valeur spécifiée. La valeur finale est déterminée par la formule min (255, *nombre d’unités centrales)*.  
  
> [!CAUTION]  
>  La modification de MAX_DOP peut affecter de façon négative les performances d'un serveur. Si vous devez modifier MAX_DOP, nous recommandons qu'il soit défini sur une valeur inférieure ou égale au nombre maximal de planificateurs matériels présents dans un nœud NUMA unique. Nous vous recommandons de ne pas affecter à MAX_DOP une valeur supérieure à 8.  
  
 MAX_DOP est géré comme suit :  
  
-   MAX_DOP en tant qu'indicateur de requête est honoré tant qu'il ne dépasse pas le groupe de charge de travail MAX_DOP.  
  
-   MAX_DOP en tant qu'indicateur de requête remplace toujours l'option « max degree of parallelism » de sp_configure.  
  
-   Le groupe de charge de travail MAX_DOP remplace le degré maximal de parallélisme sp_configure.  
  
-   Si la requête est marquée comme étant en série (MAX_DOP = 1) au moment de la compilation, elle ne peut être reconvertie en requête parallèle au moment de l'exécution, indépendamment du groupe de charge de travail ou du paramètre sp_configure.  
  
 Une fois le degré maximal de parallélisme (DOP) configuré, il ne peut être diminué que sous la sollicitation de l'allocation de mémoire. La reconfiguration du groupe de charges de travail n'est pas visible lors de l'attente dans la file d'attente d'allocation de mémoire.  
  
 GROUP_MAX_REQUESTS =*valeur*  
 Spécifie le nombre maximal de demandes simultanées autorisées à s'exécuter dans le groupe de charges de travail. *valeur* doit être 0 ou un entier positif. La valeur par défaut *valeur*(0) autorise les demandes illimités. Lorsque le nombre maximal de requêtes est atteint, un utilisateur de ce groupe peut se connecter, mais est placé dans un état d'attente jusqu'à ce que le nombre de requêtes simultanées soit inférieur à la valeur spécifiée.  
  
 À l’aide de { *pool_name* | «**par défaut**»}  
 Associe le groupe de charges de travail avec le pool de ressources définis par l’utilisateur identifié par *pool_name*, qui met en vigueur le groupe de charges de travail dans le pool de ressources. Si *pool_name* n’est pas fourni ou si l’argument USING n’est pas utilisé, le groupe de charge de travail est placé dans le pool par défaut du gouverneur de ressources prédéfini.  
  
 L'option "default" doit être placée entre des guillemets doubles ("") ou des crochets ([]) lorsqu'elle est utilisée avec l'instruction ALTER WORKLOAD GROUP pour éviter tout conflit avec DEFAULT, qui est un mot réservé au système. Pour plus d'informations, consultez [Database Identifiers](../../relational-databases/databases/database-identifiers.md).  
  
> [!NOTE]  
>  L'option "default" respecte la casse.  
  
## <a name="remarks"></a>Notes  
 L'instruction ALTER WORKLOAD GROUP est autorisée sur le groupe par défaut.  
  
 Les modifications apportées à la configuration du groupe de charge de travail ne sont pas appliquées tant que l'instruction ALTER RESOURCE GOVERNOR RECONFIGURE n'est pas exécutée. Lorsque vous modifiez un plan qui affectent les paramètres, les nouveaux paramètres prendront effet que dans les plans mis en cache précédemment après l’exécution de DBCC FREEPROCCACHE (*pool_name*), où *pool_name* est le nom d’un pool de ressources du gouverneur de ressources sur lequel le groupe de charge de travail est associé.  
  
-   Si vous modifiez MAX_DOP à 1, l’exécution de DBCC FREEPROCCACHE n’est pas requis, car des plans parallèles peuvent s’exécuter en mode série. Toutefois, il ne peut pas être aussi efficace que d’un plan compilé sous la forme d’un plan en série.  
  
-   Si vous modifiez MAX_DOP à partir de 1 à 0 ou une valeur supérieure à 1, l’exécution de DBCC FREEPROCCACHE n’est pas requise. Toutefois, les plans en série ne peut pas s’exécuter en parallèle, afin de l’effacement du cache respectif autorise de nouveaux plans potentiellement être compilé à l’aide de parallélisme.  
  
> [!CAUTION]  
>  Effacement des plans mis en cache à partir d’un pool de ressources est associé à plusieurs groupes de charges de travail affectera tous les groupes de charges de travail avec le pool de ressources définis par l’utilisateur identifié par *pool_name*.  
  
 Lorsque vous exécutez des instructions DDL, nous vous recommandons de connaître les états du gouverneur de ressources. Pour plus d’informations, consultez [du gouverneur de ressources](../../relational-databases/resource-governor/resource-governor.md).  
  
 REQUEST_MEMORY_GRANT_PERCENT : dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], la création d'index est autorisée à utiliser une mémoire d'espace de travail supérieure à celle qui lui a été initialement allouée, en vue d'améliorer les performances. Cette gestion spéciale est prise en charge par le Gouverneur de ressources dans les versions ultérieures, toutefois, l'allocation initiale et toute allocation de mémoire supplémentaire sont limitées par les paramètres du pool de ressources et du groupe de charge de travail.  
  
 **Création d’index sur une Table partitionnée**  
  
 La mémoire consommée par la création d'index sur une table partitionnée non alignée est proportionnelle au nombre de partitions impliquées.  Si la mémoire totale requise dépasse la limite par requête (REQUEST_MAX_MEMORY_GRANT_PERCENT) imposée par le paramètre du groupe de charges de travail du Gouverneur de ressources, cette création d'index peut ne pas s'exécuter. Étant donné que le groupe de charge de travail "default" permet à une requête de dépasser la limite par requête avec la mémoire minimale requise pour démarrer la compatibilité [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], l'utilisateur peut être en mesure d'exécuter la même création d'index dans le groupe de charge de travail "default", si le pool de ressources "default" possède assez de mémoire totale configurée pour exécuter cette requête.  
  
## <a name="permissions"></a>Permissions  
 Requiert l'autorisation CONTROL SERVER.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant indique comment modifier l'importance des demandes dans le groupe par défaut en remplaçant la valeur `MEDIUM` par `LOW`.  
  
```  
ALTER WORKLOAD GROUP "default"  
WITH (IMPORTANCE = LOW);  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
 L'exemple suivant indique comment déplacer un groupe de charge de travail du pool dans lequel il est contenu vers le pool par défaut.  
  
```  
ALTER WORKLOAD GROUP adHoc  
USING [default];  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Resource Governor](../../relational-databases/resource-governor/resource-governor.md)   
 [CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/create-workload-group-transact-sql.md)   
 [DROP WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/drop-workload-group-transact-sql.md)   
 [CREATE RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-resource-pool-transact-sql.md)   
 [ALTER RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-pool-transact-sql.md)   
 [DROP RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/drop-resource-pool-transact-sql.md)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md)  
  
  
