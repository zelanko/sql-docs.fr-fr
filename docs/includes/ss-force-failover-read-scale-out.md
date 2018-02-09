---
title: "Forcer le basculement pour le groupe de disponibilité de SQL Server"
description: "Forcer le basculement pour le groupe de disponibilité avec le type de cluster None"
services: 
author: MikeRayMSFT
ms.service: 
ms.topic: include
ms.date: 02/05/2018
ms.author: mikeray
ms.custom: include file
ms.openlocfilehash: 10a2af2cb5bc9e98605a3ee988439e3c3be60c1e
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
Chaque groupe de disponibilité possède uniquement un réplica principal. Le réplica principal autorise les opérations de lecture et d’écriture. Pour modifier le réplica est principal, vous pouvez basculer. Dans un groupe de disponibilité pour la haute disponibilité, le Gestionnaire du cluster automatise le processus de basculement. Dans un groupe de disponibilité avec le type de cluster NONE, le processus de basculement est manuel. 

Il existe deux façons de basculer sur le réplica principal dans un groupe de disponibilité avec le type de cluster NONE :

- Basculement manuel forcé avec une perte de données
- Basculement manuel sans perte de données

### <a name="forced-manual-failover-with-data-loss"></a>Basculement manuel forcé avec une perte de données

Utilisez cette méthode lorsque le réplica principal n’est pas disponible et ne peut pas être récupéré. 

Pour forcer le basculement avec perte de données, connectez-vous à l’instance de SQL Server qui héberge le réplica secondaire cible et l’exécuter :

```SQL
ALTER AVAILABILITY GROUP [ag1] FORCE_FAILOVER_ALLOW_DATA_LOSS;
```

### <a name="manual-failover-without-data-loss"></a>Basculement manuel sans perte de données

Utilisez cette méthode quand le réplica principal est disponible, mais que vous devez provisoirement ou définitivement changer la configuration et l’instance qui héberge le réplica principal. Avant d’émettre le basculement manuel, vérifiez que le réplica secondaire cible est à jour afin d’éviter de perdre des données. 

Pour basculer manuellement sans perte de données :

1. Le réplica secondaire cible `SYNCHRONOUS_COMMIT`.

   ```SQL
   ALTER AVAILABILITY GROUP [ag1] 
        MODIFY REPLICA ON N'<node2>' 
        WITH (AVAILABILITY_MODE = SYNCHRONOUS_COMMIT);
   ```

2. Exécutez la requête suivante pour identifier que les transactions actives sont validées dans le réplica principal et au moins un réplica secondaire synchrone : 

   ```SQL
   SELECT ag.name, 
      drs.database_id, 
      drs.group_id, 
      drs.replica_id, 
      drs.synchronization_state_desc, 
      ag.sequence_number
   FROM sys.dm_hadr_database_replica_states drs, sys.availability_groups ag
   WHERE drs.group_id = ag.group_id; 
   ```

   Le réplica secondaire est synchronisé quand `synchronization_state_desc` a pour valeur `SYNCHRONIZED`.

3. Mise à jour `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` à 1.

   Le script suivant définit `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` sur 1 pour un groupe de disponibilité nommé `ag1`. Avant d’exécuter le script suivant, remplacez `ag1` par le nom de votre groupe de disponibilité :

   ```SQL
   ALTER AVAILABILITY GROUP [ag1] 
        SET REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT = 1;
   ```

   Ce paramètre garantit que chaque transaction active est validée dans le réplica principal et au moins un réplica secondaire synchrone. 

4. Rétrograder le réplica principal vers un réplica secondaire. Une fois le réplica principal est rétrogradé, il est en lecture seule. Exécutez cette commande sur l’instance de SQL Server qui héberge le réplica principal pour mettre à jour le rôle à `SECONDARY`:

   ```SQL
   ALTER AVAILABILITY GROUP [ag1] 
        SET (ROLE = SECONDARY); 
   ```

5. Promouvez le réplica secondaire en réplica principal. 

   ```SQL
   ALTER AVAILABILITY GROUP ag1 FORCE_FAILOVER_ALLOW_DATA_LOSS; 
   ```  

   > [!NOTE] 
   > Pour supprimer un groupe de disponibilité, utilisez [DROP AVAILABILITY GROUP](https://docs.microsoft.com/en-us/sql/t-sql/statements/drop-availability-group-transact-sql). Pour un groupe de disponibilité créé avec un cluster de type NONE ou externe, la commande doit être exécutée sur tous les réplicas qui font partie de la disponibilité.