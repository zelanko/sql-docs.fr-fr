---
title: "Groupes de disponibilit&#233; distribu&#233;s (groupes de disponibilit&#233; Always On) | Microsoft Docs"
ms.custom: ""
ms.date: "08/30/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f7c7acc5-a350-4a17-95e1-e689c78a0900
caps.latest.revision: 28
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 28
---
# Groupes de disponibilit&#233; distribu&#233;s (groupes de disponibilit&#233; Always On)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Les groupes de disponibilité distribués permettent de combiner deux groupes de disponibilité résidant sur différents clusters de basculement Windows Server (WSFC). Une des principales utilisations des groupes de disponibilité distribués est la récupération d’urgence où le site principal est géographiquement dispersé par rapport au site de récupération d’urgence. Vous souhaitez que les données soient répliquées en permanence dans le site de récupération d’urgence, mais vous ne souhaitez pas qu’un problème réseau ou au niveau du site de récupération d’urgence entraîne la défaillance de votre site principal.  
  
 Le schéma suivant illustre l’architecture d’un groupe de disponibilité distribué.  
  
 ![AlwaysOn Distributed Availability Groups](../../../database-engine/availability-groups/windows/media/alwayson-distributed-availability-groups.png "AlwaysOn Distributed Availability Groups")  
  
 Dans le schéma précédent, il existe deux clusters de basculement Windows Server distincts (WFSC 1 et 2). Chaque cluster possède son propre groupe de disponibilité avec une configuration équivalente des bases de données. Un groupe de disponibilité distribué peut être considéré comme un « groupe de disponibilité de groupes de disponibilité ». AG 1 devient le groupe de disponibilité principal dans cet exemple. Les insertions et les mises à jour sont apportées au réplica principal AG 1 avant d’être répliquées vers les réplicas secondaires associés. Mais les modifications sont également répliquées une fois sur le réseau vers le groupe de disponibilité secondaire sur WSFC 2. Le groupe de disponibilité AG 2 réplique ces modifications vers son ou ses réplicas secondaires.  
  
> [!IMPORTANT]  
>  Lorsqu’une relation entre groupes de disponibilité distribués est établie entre deux groupes de disponibilité, le deuxième groupe de disponibilité devient automatiquement en lecture seule. Les mises à jour et les insertions peuvent uniquement être apportées au réplica principal du groupe de disponibilité principal (dans cet exemple, le réplica principal de AG 1).  
  
 Les groupes de disponibilité distribués sont différents d’un groupe de disponibilité sur un cluster de basculement Windows Server unique. Voici en quoi ils sont différents :  
  
-   Chaque cluster WSFC conserve son propre mode de quorum et sa propre configuration de vote pour les nœuds. Cela signifie que l’intégrité du cluster WSFC secondaire n’affecte pas le cluster WSFC principal.  
  
-   Les données sont envoyées une fois sur le réseau vers le cluster WSFC secondaire avant d’être répliquées au sein de ce cluster. Dans un même cluster WSFC, les données sont envoyées individuellement à chaque réplica. Pour un site secondaire dispersé géographiquement, les groupes de disponibilité distribués sont plus efficaces.  
  
-   La version du système d’exploitation utilisée sur les clusters principaux et secondaires peut différer. Dans un même cluster WSFC, tous les serveurs doivent être sur la même version de système d’exploitation. Cela permet d’utiliser des groupes de disponibilité distribués avec des mises à jour/mises à niveau propagées du système d’exploitation.  
  
-   Les groupes de disponibilité principal et secondaire doivent avoir la même configuration de bases de données.  
  
-   Le basculement automatique vers le groupe de disponibilité secondaire n’est pas pris en charge.  
  
## Créer un groupe de disponibilité distribué  
 Pour créer un groupe de disponibilité distribué, vous devez créer un groupe de disponibilité et un écouteur sur chaque cluster WSFC. Vous combinez ensuite ces éléments dans un groupe de disponibilité distribué. Les étapes suivantes fournissent un exemple de base dans Transact-SQL. Cet exemple ne couvre pas tous les détails de la création des groupes de disponibilité et des écouteurs. Son but est de mettre en avant les principales exigences.  
  
### Créer le groupe de disponibilité principal sur le premier cluster  
 Créez un groupe de disponibilité sur le premier cluster WSFC.   Dans cet exemple, le groupe de disponibilité est nommé `ag1` pour la base de données `db1`.  
  
```tsql  
CREATE AVAILABILITY GROUP [ag1]   
FOR DATABASE db1   
REPLICA ON N'server1' WITH (ENDPOINT_URL = N'TCP://server1.contoso.com:5022',  
    FAILOVER_MODE = AUTOMATIC,  
    AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,   
    BACKUP_PRIORITY = 50,   
    SECONDARY_ROLE(ALLOW_CONNECTIONS = NO),   
    SEEDING_MODE = AUTOMATIC),   
N'server2' WITH (ENDPOINT_URL = N'TCP://server2.contoso.com:5022',   
    FAILOVER_MODE = AUTOMATIC,   
    AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,   
    BACKUP_PRIORITY = 50,   
    SECONDARY_ROLE(ALLOW_CONNECTIONS = NO),   
    SEEDING_MODE = AUTOMATIC);   
GO  
  
```  
  
 Notez que cet exemple utilise un amorçage direct, où **SEEDING_MODE** est défini sur **AUTOMATIC** pour les réplicas et le groupe de disponibilité distribué. Cela signifie qu’une fois mis en place, les réplicas secondaires et le groupe de disponibilité secondaire sont automatiquement renseignés sans qu’une sauvegarde manuelle et une restauration de base de données primaire soient nécessaires.  
  
### Joindre les réplicas secondaires au groupe de disponibilité principal  
 Les réplicas secondaires doivent être joints au groupe de disponibilité **ALTER AVAILABILITY GROUP** avec l’option **JOIN** . Étant donné que l’amorçage direct est utilisé dans cet exemple, vous devez également appeler  **ALTER AVAILABILITY GROUP** avec l’option **GRANT CREATE ANY DATABASE** . Ainsi, le groupe de disponibilité peut créer la base de données et commencer l’amorçage automatique à partir du réplica principal.  
  
 Dans cet exemple, les commandes suivantes sont exécutées sur le réplica secondaire `server2`pour rejoindre le groupe de disponibilité `ag1` . Le groupe de disponibilité est ensuite autorisé à créer des bases de données sur le réplica secondaire.  
  
```tsql  
ALTER AVAILABILITY GROUP [ag1] JOIN   
ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE  
GO  
```  
  
### Créer un écouteur pour le groupe de disponibilité principal  
 Ajoutez ensuite un écouteur pour le groupe de disponibilité principal sur le premier cluster WSFC. Dans cet exemple, l’écouteur est nommé `ag1-listener`. Pour obtenir des instructions détaillées sur la création d’un écouteur, consultez [Créer ou configurer un écouteur de groupe de disponibilité &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md).  
  
```  
ALTER AVAILABILITY GROUP [ag1]    
    ADD LISTENER 'ag1-listener' ( WITH IP ( ('2001:db88:f0:f00f::cf3c'),('2001:4898:e0:f213::4ce2') ) , PORT = 60173);    
GO  
```  
  
### Créer le groupe de disponibilité secondaire sur le deuxième cluster  
 Puis, sur le deuxième cluster WSFC, créez un deuxième groupe de disponibilité `ag2`. Dans ce cas, la base de données n’est pas spécifiée, car elle est automatiquement amorcée à partir du groupe de disponibilité principal.  
  
```tsql  
CREATE AVAILABILITY GROUP [ag2]   
FOR   
REPLICA ON N'server3' WITH (ENDPOINT_URL = N'TCP://server3.contoso.com:5022',   
    FAILOVER_MODE = MANUAL,   
    AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,   
    BACKUP_PRIORITY = 50,   
    SECONDARY_ROLE(ALLOW_CONNECTIONS = NO),   
    SEEDING_MODE = AUTOMATIC),   
N'server4' WITH (ENDPOINT_URL = N'TCP://server4.contoso.com:5022',   
    FAILOVER_MODE = MANUAL,   
    AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,   
    BACKUP_PRIORITY = 50,   
    SECONDARY_ROLE(ALLOW_CONNECTIONS = NO),   
    SEEDING_MODE = AUTOMATIC);   
GO  
```  
  
> [!NOTE]  
>  Notez que les groupes de disponibilité secondaires doivent utiliser le même point de terminaison de mise en miroir de bases de données (le port 5022 dans l’exemple). Sinon, la réplication s’arrête après un basculement local.  
  
### Joindre les réplicas secondaires au groupe de disponibilité secondaire  
 Dans cet exemple, les commandes suivantes sont exécutées sur le réplica secondaire `server4`pour rejoindre le groupe de disponibilité `ag2` . Le groupe de disponibilité est ensuite autorisé à créer des bases de données sur le réplica secondaire pour prendre en charge l’amorçage direct.  
  
```tsql  
ALTER AVAILABILITY GROUP [ag2] JOIN   
ALTER AVAILABILITY GROUP [ag2] GRANT CREATE ANY DATABASE  
GO  
```  
  
### Créer un écouteur pour le groupe de disponibilité secondaire  
 Ajoutez ensuite un écouteur au groupe de disponibilité secondaire sur le deuxième cluster WSFC. Dans cet exemple, l’écouteur est nommé `ag2-listener`. Pour obtenir des instructions détaillées sur la création d’un écouteur, consultez [Créer ou configurer un écouteur de groupe de disponibilité &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md).  
  
```  
ALTER AVAILABILITY GROUP [ag2]    
    ADD LISTENER 'ag2-listener' ( WITH IP ( ('2001:db88:f0:f00f::cf3c'),('2001:4898:e0:f213::4ce2') ) , PORT = 60173);    
GO  
```  
  
### Créer le groupe de disponibilité distribué sur le premier cluster  
 Sur le premier cluster WSFC, créez un groupe de disponibilité distribué (nommé `distributedag` dans cet exemple). Utilisez la commande **CREATE AVAILABILITY GROUP** avec l’option **DISTRIBUTED** . Le paramètre **AVAILABILITY GROUP ON** spécifie les groupes de disponibilité membres, `ag1` et `ag2`.  
  
```tsql  
CREATE AVAILABILITY GROUP [distributedag]  
   WITH (DISTRIBUTED)   
   AVAILABILITY GROUP ON  
      'ag1' WITH    
      (   
         LISTENER_URL = 'tcp://ag1-listener:5022',    
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,   
         FAILOVER_MODE = MANUAL,   
         SEEDING_MODE = AUTOMATIC   
      ),   
      'ag2' WITH    
      (   
         LISTENER_URL = 'tcp://ag2-listener:5022',   
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,   
         FAILOVER_MODE = MANUAL,   
         SEEDING_MODE = AUTOMATIC   
      );    
GO   
```  
  
> [!NOTE]  
>  **LISTENER_URL** spécifie l’écouteur pour chaque groupe de disponibilité, ainsi que le point de terminaison de mise en miroir de bases de données du groupe de disponibilité. Dans cet exemple, il s’agit du port `5022` (et non du port `60173` qui a permis de créer l’écouteur).  
  
### Joindre le groupe de disponibilité distribué au deuxième cluster  
 Joignez ensuite le groupe de disponibilité distribué au deuxième cluster WSFC.  
  
```tsql  
ALTER AVAILABILITY GROUP [distributedag]   
   JOIN   
   AVAILABILITY GROUP ON  
      'ag1' WITH    
      (   
         LISTENER_URL = 'tcp://ag1-listener:5022',    
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,   
         FAILOVER_MODE = MANUAL,   
         SEEDING_MODE = AUTOMATIC   
      ),   
      'ag2' WITH    
      (   
         LISTENER_URL = 'tcp://ag2-listener:5022',   
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,   
         FAILOVER_MODE = MANUAL,   
         SEEDING_MODE = AUTOMATIC   
      );    
GO  
```  

  
## Basculement vers un groupe de disponibilité secondaire  
 Seul le basculement manuel est pris en charge pour l’instant. L’instruction Transact-SQL suivante force le basculement sur le groupe de disponibilité distribué nommé `distributedag` :  


1. Définissez le mode de disponibilité sur validation synchrone pour le groupe de disponibilité secondaire. 
    
      ```tsql  
      ALTER AVAILABILITY GROUP [distributedag] 
      MODIFY 
      AVAILABILITY GROUP ON
      'ag1' WITH  
         ( 
          LISTENER_URL = 'tcp://ag1-listener:5022',  
          AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT, 
          FAILOVER_MODE = MANUAL, 
          SEEDING_MODE = MANUAL 
          ), 
      'ag2' WITH  
        ( 
        LISTENER_URL = 'tcp://ag2-listener:5022', 
        AVAILABILITY_MODE = SYNCHRONOUS_COMMIT, 
        FAILOVER_MODE = MANUAL, 
        SEEDING_MODE = MANUAL 
        );  
       
      ```  
  
1. Attendez que l’état du groupe de disponibilité distribuée soit défini sur `SYNCHRONIZED`. Exécutez la requête suivante sur le serveur SQL Server qui héberge le réplica principal du groupe de disponibilité principal. 
    
      ```tsql  
      SELECT ag.name
             , drs.database_id
             , drs.group_id
             , drs.replica_id
             , drs.synchronization_state_desc
             , drs.end_of_log_lsn 
        FROM sys.dm_hadr_database_replica_states drs,
        sys.availability_groups ag
          WHERE drs.group_id = ag.group_id;      
      ```  

    Continuez une fois que le groupe de disponibilité **synchronization_state_desc** est `SYNCHRONIZED`. Si **synchronization_state_desc** n’est pas `SYNCHRONIZED`, exécutez la commande toutes les cinq secondes jusqu’à ce qu’il change. Ne continuez pas jusqu’à **synchronization_state_desc** = `SYNCHRONIZED`. 

1. Sur le serveur SQL Server hébergeant le réplica principal pour le groupe de disponibilité principal, définissez la valeur du rôle du groupe de disponibilité distribué sur `SECONDARY`. 

      ```tsql
      ALTER AVAILABILITY GROUP distributedag SET (ROLE = SECONDARY); 
      ```  

    Remarque : à ce stade, le groupe de disponibilité distribuée n’est pas disponible.

1. Testez la disponibilité du basculement. Exécutez la requête suivante :

      ```tsql
      SELECT ag.name, 
             drs.database_id, 
             drs.group_id, 
             drs.replica_id, 
             drs.synchronization_state_desc, 
             drs.end_of_log_lsn 
      FROM sys.dm_hadr_database_replica_states drs, sys.availability_groups ag
      WHERE drs.group_id = ag.group_id; 
      ```  
    Le groupe de disponibilité est prêt pour le basculement lorsque **synchronization_state_desc** est `SYNCHRONIZED` et **end_of_log_lsn** est le même pour les deux groupes de disponibilité. 

1. Basculement du groupe de disponibilité principal vers le groupe de disponibilité secondaire. Exécutez la commande suivante sur le serveur SQL Server qui héberge le réplica principal du groupe de disponibilité secondaire. 

      ```tsql
      ALTER AVAILABILITY GROUP distributedag FORCE_FAILOVER_ALLOW_DATA_LOSS; 
      ```  
      Remarque : à ce stade, le groupe de disponibilité distribuée est disponible.
      
Après avoir effectué les étapes ci-dessus, le groupe de disponibilité distribué bascule sans perte de données. Microsoft vous recommande de définir le mode de disponibilité sur ASYNCHRONOUS_COMMIT si les groupes de disponibilité sont à une distance géographique qui provoque des temps de latence. 
  
## Supprimer un groupe de disponibilité distribué  
 L’instruction Transact-SQL suivante supprime un groupe de disponibilité distribué nommé `distributedag` :  
  
```tsql  
DROP AVAILABILITY GROUP [distributedag]  
```  

## Créer un groupe de disponibilité distribué avec des instances de cluster de basculement

Vous pouvez créer un groupe de disponibilité distribué à l’aide d’un groupe de disponibilité sur une instance de cluster de basculement (FCI). Dans ce cas, vous n’avez pas besoin d’écouteur de groupe de disponibilité. Utilisez le nom de réseau virtuel pour le réplica principal de l’instance FCI. L’exemple suivant montre un groupe de disponibilité distribué appelé SQLFCIDAG. Un des groupes de disponibilité est SQLFCIAG. SQLFCIAG possède 2 réplicas FCI. Le VNN pour le réplica FCI principal est SQLFCIAG-1, et celui du réplica FCI secondaire est SQLFCIAG-2. Le groupe de disponibilité distribué inclut également SQLAG-DR pour la récupération d’urgence.

![Groupe de disponibilité distribué Always On](../../../database-engine/availability-groups/windows/media/always-on-availability-group-distributed.png)

 
 
 Le DDL suivant crée ce groupe de disponibilité distribué. 

```tsql  
CREATE AVAILABILITY GROUP [SQLFCIDAG]  
   WITH (DISTRIBUTED)   
   AVAILABILITY GROUP ON  
  'SQLFCIAG' WITH    
    (   
        LISTENER_URL = 'tcp://SQLFCIAG-1:5022',    
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,   
         FAILOVER_MODE = MANUAL,   
         SEEDING_MODE = AUTOMATIC
      ),   
  'SQLAG-DR' WITH    
       (   
         LISTENER_URL = 'tcp://SQLAG-DR:5022',   
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,   
         FAILOVER_MODE = MANUAL,   
         SEEDING_MODE = AUTOMATIC
      );   
```  

Notez que l’URL de l’écouteur est le VNN de l’instance FCI principale.

## Basculement manuel du FCI dans le groupe de disponibilité distribué

Pour basculer manuellement le groupe de disponibilité FCI, mettez à jour le groupe de disponibilité distribué pour refléter la modification de l’URL de l’écouteur. Par exemple, exécutez le DDL suivant sur le groupe de disponibilité principal et le groupe de disponibilité secondaire de SQLFCIAG :

```tsql  
ALTER AVAILABILITY GROUP [SQLFCIDAG]  
   MODIFY AVAILABILITY GROUP ON  
 'SQLFCIAG' WITH    
    (   
        LISTENER_URL = 'tcp://SQLFCIAG-2:5022'
    )
```  
  
## Voir aussi  
 [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../../t-sql/statements/create-availability-group-transact-sql.md)   
 [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-availability-group-transact-sql.md)  
  
  