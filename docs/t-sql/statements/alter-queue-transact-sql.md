---
title: "La file d’attente de ALTER (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 05/01/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_QUEUE_TSQL
- ALTER QUEUE
dev_langs:
- TSQL
helpviewer_keywords:
- number of queue readers
- modifying queues
- ALTER QUEUE statement
- queue readers [SQL Server]
- queues [Service Broker], modifying
- unavailable queues [SQL Server]
- activation stored procedures [Service Broker]
ms.assetid: d54aa325-8761-4cd4-8da7-acf33df12296
caps.latest.revision: 49
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9320e2f2af4bccd07ee8b255166b513c0b204a76
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="alter-queue-transact-sql"></a>ALTER QUEUE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifie les propriétés d'une file d'attente.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
ALTER QUEUE <object>   
   queue_settings  
   | queue_action  
[ ; ]  
  
<object> : :=  
{  
    [ database_name. [ schema_name ] . | schema_name. ]  
        queue_name  
}   
  
<queue_settings> : :=  
WITH  
   [ STATUS = { ON | OFF } [ , ] ]  
   [ RETENTION = { ON | OFF } [ , ] ]  
   [ ACTIVATION (  
       { [ STATUS = { ON | OFF } [ , ] ]   
         [ PROCEDURE_NAME = <procedure> [ , ] ]  
         [ MAX_QUEUE_READERS = max_readers [ , ] ]  
         [ EXECUTE AS { SELF | 'user_name'  | OWNER } ]  
       |  DROP }  
          ) [ , ]]  
         [ POISON_MESSAGE_HANDLING (  
          STATUS = { ON | OFF } )  
         ]   
  
<queue_action> : :=  
   REBUILD [ WITH <query_rebuild_options> ]  
   | REORGANIZE [ WITH (LOB_COMPACTION = { ON | OFF } ) ]  
   | MOVE TO { file_group | "default" }  
  
<procedure> : :=  
{  
    [ database_name. [ schema_name ] . | schema_name. ]  
        stored_procedure_name  
}  
  
<queue_rebuild_options> : :=  
{  
   ( MAXDOP = max_degree_of_parallelism )  
}  
  
```  
  
## <a name="arguments"></a>Arguments  
 *database_name* (objet)  
 Nom de la base de données contenant la file d'attente à modifier. Lorsqu’aucun *nom_base_de_données* est fourni, l’emplacement par défaut pour la base de données actuelle.  
  
 *schema_name* (objet)  
 Nom du schéma auquel la nouvelle file d'attente appartient. Lorsqu’aucun *schema_name* est fourni, l’emplacement par défaut pour le schéma par défaut pour l’utilisateur actuel.  
  
 *nom_file_attente*  
 Nom de la file d'attente à modifier.  
  
 STATUS (File d'attente)  
 Indique si la file d'attente est disponible (ON) ou indisponible (OFF). Lorsque la file d'attente est indisponible, aucun message ne peut y être ajouté ou supprimé.  
  
 RETENTION  
 Spécifie le paramètre de rétention pour la file d'attente. Si le paramètre RETENTION = ON (activé), tous les messages des conversations qui ont été envoyés ou reçus sont conservés dans la file d'attente jusqu'à ce que les conversations s'achèvent. Vous pouvez ainsi conserver les messages pour effectuer des audits ou procéder à des transactions de compensation si une erreur se produit.  
  
> [!NOTE]  
>  Si RETENTION = ON peut réduire les performances. Ce paramètre doit être utilisé seulement s'il est nécessaire pour satisfaire au contrat de niveau de service pour l'application.  
  
 ACTIVATION  
 Spécifie des informations sur la procédure stockée qui est activée pour traiter les messages arrivant dans cette file d'attente.  
  
 STATUS (Activation)  
 Spécifie si la file d'attente active ou non la procédure stockée. Lorsque STATUS = ON, la file d'attente lance la procédure stockée spécifiée avec PROCEDURE_NAME, quand le nombre de procédures actuellement en cours d'exécution est inférieur à la valeur de MAX_QUEUE_READERS et que la réception des messages dans la file d'attente est plus rapide que la réception des messages par les procédures stockées. Lorsque STATUS = OFF, la file d'attente n'active pas la procédure stockée.  
  
 RECONSTRUIRE [WITH \<queue_rebuild_options >]  
 **S'applique à**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Reconstruit tous les index sur la table interne de file d’attente. Utilisez cette fonction lorsque vous rencontrez des problèmes de fragmentation en raison d’une charge élevée. MAXDOP est l’option rebuild de la file d’attente pris en charge uniquement. RECONSTRUCTION est toujours une opération hors connexion.  
  
 RÉORGANISER [AVEC (LOB_COMPACTION = {ON | OFF})]  
 **S'applique à**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Réorganiser tous les index sur la table interne de file d’attente.   
Contrairement à RÉORGANISER dans les tables utilisateur, RÉORGANISER sur une file d’attente est toujours effectuée comme une opération hors connexion, car les verrous de page sont explicitement désactivés sur les files d’attente.  
  
> [!TIP]  
>  Pour obtenir des instructions générales concernant la fragmentation des index, lors de la fragmentation est comprise entre 5 et 30 %, réorganiser l’index. Lors de la fragmentation est supérieure à 30 %, reconstruisez l’index. Toutefois, ces numéros sont uniquement pour des conseils généraux en tant que point de départ pour votre environnement. Pour déterminer la quantité de fragmentation d’index, utilisez [sys.dm_db_index_physical_stats &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md) -voir exemple G dans cet article pour obtenir des exemples.  
  
 DÉPLACER vers { *file_group* | « default »}  
 **S'applique à**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Déplace la table interne de la file d’attente (avec ses index) à un groupe de fichiers spécifié par l’utilisateur.  Le nouveau groupe de fichiers ne doit pas être en lecture seule.  
  
 Nom_procédure = \<procédure >  
 Spécifie le nom de la procédure stockée à activer lorsque la file d'attente contient des messages à traiter. Cette valeur doit être un identificateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 *database_name* (procédure)  
 Nom de la base de données contenant la procédure stockée.  
  
 *schema_name* (procédure)  
 Nom du schéma propriétaire de la procédure stockée.  
  
 *nom_procédure_stockée*  
 Est le nom de la procédure stockée.  
  
 Valeur de MAX_QUEUE_READERS =*max_reader*  
 Précise le nombre maximal d'instances de la procédure stockée d'activation lancées simultanément par la file d'attente. La valeur de *max_readers* doit être un nombre compris entre 0 et 32 767.  
  
 EXECUTE AS  
 Spécifie le compte d'utilisateur de la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sous lequel la procédure stockée d'activation s'exécute. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit être en mesure de contrôler les autorisations de cet utilisateur au moment où la file d'attente active la procédure stockée. Pour un utilisateur de domaine Windows, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit être connecté au domaine et pouvoir valider les autorisations de l'utilisateur spécifié lorsque la procédure est activée ou que l'activation échoue. Pour un utilisateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le serveur peut toujours vérifier les autorisations.  
  
 SELF  
 Spécifie que la procédure stockée s'exécute en tant qu'utilisateur actuel. (Principal de la base de données exécutant cette instruction ALTER QUEUE.)  
  
 '*nom_utilisateur*'  
 Est le nom de l’utilisateur qui exécute la procédure stockée. *user_name* doit être un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilisateur spécifié comme un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] identificateur. L’utilisateur actuel doit avoir l’autorisation IMPERSONATE pour la *nom_utilisateur* spécifié.  
  
 OWNER  
 Spécifie que la procédure stockée s'exécute en tant que propriétaire de la file d'attente.  
  
 DROP  
 Supprime toutes les informations d'activation associées à la file d'attente.  
  
 POISON_MESSAGE_HANDLING  
 Spécifie si la gestion des messages incohérents est activée. La valeur par défaut est ON.  
  
 Une file d'attente dont la gestion des messages incohérents a la valeur OFF ne sera pas désactivée après cinq restaurations de transactions consécutives. L'application peut ainsi définir un système personnalisé de gestion des messages incohérents.  
  
## <a name="remarks"></a>Notes  
 Si une file d'attente dotée d'une procédure stockée d'activation spécifiée contient des messages, le fait de basculer l'état d'activation de OFF (désactivé) en ON (activé) déclenche immédiatement la procédure stockée d'activation. Le fait de repasser l'état d'activation de ON à OFF arrête l'activation d'instances de la procédure stockée par le broker, mais n'arrête pas les instances de la procédure stockée en cours d'exécution à ce moment-là.  
  
 La modification d'une file d'attente pour ajouter une procédure stockée d'activation ne change pas l'état d'activation de la file d'attente. La modification de la procédure stockée d'activation pour la file d'attente n'a pas d'incidence sur les instances de la procédure stockée en cours d'exécution à ce moment-là.  
  
 [!INCLUDE[ssSB](../../includes/sssb-md.md)] vérifie le nombre maximal d'agents de lecture pour une file d'attente dans le cadre du processus d'activation. Ainsi, la modification d'une file d'attente en vue d'augmenter le nombre maximal d'agents de lecture la file d'attente permet à [!INCLUDE[ssSB](../../includes/sssb-md.md)] de lancer immédiatement davantage d'instances de la procédure stockée d'activation. La modification d'une file d'attente pour diminuer le nombre maximal de lecteurs de file d'attente n'a pas d'incidence sur les instances de la procédure stockée d'activation en cours d'exécution à ce moment-là. [!INCLUDE[ssSB](../../includes/sssb-md.md)] ne lance cependant pas de nouvelles instances de la procédure stockée tant que le nombre d'instances de la procédure stockée d'activation ne retombe pas en-dessous de la limite maximale configurée.  
  
 Lorsqu'une file d'attente est indisponible, [!INCLUDE[ssSB](../../includes/sssb-md.md)] conserve les messages destinés aux services qui utilisent cette file dans la file d'attente de transmission de la base de données. Le [sys.transmission_queue](../../relational-databases/system-catalog-views/sys-transmission-queue-transact-sql.md) affichage catalogue fournit une vue de la file d’attente de transmission.  
  
 Si une instruction RECEIVE ou GET CONVERSATION GROUP spécifie une file d'attente indisponible, cette instruction échoue et une erreur [!INCLUDE[tsql](../../includes/tsql-md.md)] se produit.  
  
## <a name="permissions"></a>Permissions  
 L'autorisation de modification d'une file d'attente est accordée par défaut au propriétaire de la file d'attente, aux membres du rôle de base de données fixe db_ddladmin ou db_owner et aux membres du rôle serveur fixe sysadmin.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-making-a-queue-unavailable"></a>A. Mise en indisponibilité d'une file d'attente  
 L'exemple suivant indique comment rendre la file d'attente `ExpenseQueue` indisponible pour la réception des messages.  
  
```  
ALTER QUEUE ExpenseQueue WITH STATUS = OFF ;  
```  
  
### <a name="b-changing-the-activation-stored-procedure"></a>B. Modification de la procédure stockée d'activation  
 L'exemple suivant modifie la procédure stockée lancée par la file d'attente. La procédure stockée s'exécute sous l'utilisateur qui a lancé l'instruction `ALTER QUEUE`.  
  
```  
ALTER QUEUE ExpenseQueue  
    WITH ACTIVATION (  
        PROCEDURE_NAME = new_stored_proc,  
        EXECUTE AS SELF) ;  
```  
  
### <a name="c-changing-the-number-of-queue-readers"></a>C. Modification du nombre de lecteurs de file d'attente  
 L'exemple suivant définit à `7` le nombre maximal d'instances de la procédure stockée que [!INCLUDE[ssSB](../../includes/sssb-md.md)] lance pour cette file d'attente.  
  
```  
ALTER QUEUE ExpenseQueue WITH ACTIVATION (MAX_QUEUE_READERS = 7) ;  
```  
  
### <a name="d-changing-the-activation-stored-procedure-and-the-execute-as-account"></a>D. Modification de la procédure stockée d'activation et du compte EXECUTE AS  
 L'exemple suivant modifie la procédure stockée lancée par [!INCLUDE[ssSB](../../includes/sssb-md.md)]. Cette procédure stockée s'exécute en tant qu'utilisateur `SecurityAccount`.  
  
```  
ALTER QUEUE ExpenseQueue  
    WITH ACTIVATION (  
        PROCEDURE_NAME = AdventureWorks2012.dbo.new_stored_proc ,  
        EXECUTE AS 'SecurityAccount') ;  
```  
  
### <a name="e-setting-the-queue-to-retain-messages"></a>E. Configuration de la file d'attente pour la conservation des messages  
 L'exemple suivant configure la file d'attente pour qu'elle conserve les messages. La file d'attente conserve tous les messages envoyés ou reçus des services utilisant cette file d'attente, jusqu'à ce que la conversation contenant le message s'achève.  
  
```  
ALTER QUEUE ExpenseQueue WITH RETENTION = ON ;  
```  
  
### <a name="f-removing-activation-from-a-queue"></a>F. Suppression de l'activation d'une file d'attente  
 L'exemple suivant supprime toutes les informations d'activation de la file d'attente.  
  
```  
ALTER QUEUE ExpenseQueue WITH ACTIVATION (DROP) ;  
```  
  
### <a name="g-rebuilding-queue-indexes"></a>G. La reconstruction des index de la file d’attente  
  
**S'applique à**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 L’exemple suivant reconstruit des index de la file d’attente  
  
```  
ALTER QUEUE ExpenseQueue REBUILD WITH (MAXDOP = 2)   
```  
  
### <a name="h-reorganizing-queue-indexes"></a>H. Réorganisation des index de la file d’attente  
  
**S'applique à**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 L’exemple suivant réorganise les index de la file d’attente  
  
```  
ALTER QUEUE ExpenseQueue REORGANIZE   
```  
  
### <a name="i-moving-queue-internal-table-to-another-filegroup"></a>Faire : déplacer la table interne de file d’attente à un autre groupe de fichiers  
  
**S'applique à**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
```  
ALTER QUEUE ExpenseQueue MOVE TO [NewFilegroup]   
```  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE QUEUE &#40;Transact-SQL&#41;](../../t-sql/statements/create-queue-transact-sql.md)   
 [SUPPRIMER la file d’attente &#40; Transact-SQL &#41;](../../t-sql/statements/drop-queue-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)  
  
  

