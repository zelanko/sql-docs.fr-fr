---
title: Forcer le basculement SQL Server pour des groupes de disponibilité
description: Forcer le basculement pour des groupes de disponibilité avec le type de cluster AUCUN
services: ''
author: MikeRayMSFT
ms.topic: include
ms.date: 02/05/2018
ms.author: mikeray
ms.custom: include file
ms.openlocfilehash: 90c7c7863228ce210e56e76ab3e12c77e7ccc902
ms.sourcegitcommit: fc5b757bb27048a71bb39755648d5cefe25a8bc6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80407973"
---
Chaque groupe de disponibilité contient un seul réplica principal. Le réplica principal autorise les opérations de lecture et d’écriture. Pour changer de réplica principal, vous pouvez effectuer un basculement. Dans un groupe de disponibilité pour la haute disponibilité, le gestionnaire de cluster automatise le processus de basculement. Dans un groupe de disponibilité avec le type de cluster AUCUN, le processus de basculement est manuel. 

Il existe deux façons de basculer le réplica principal dans un groupe de disponibilité avec le type de cluster AUCUN :

- Basculement manuel forcé avec perte de données
- Basculement manuel sans perte de données

### <a name="forced-manual-failover-with-data-loss"></a>Basculement manuel forcé avec perte de données

Utilisez cette méthode quand le réplica principal n’est pas disponible et ne peut pas être récupéré. 

Pour forcer le basculement avec perte de données, connectez-vous à l’instance de SQL Server qui héberge le réplica secondaire cible et exécutez la commande suivante :

```SQL
ALTER AVAILABILITY GROUP [ag1] FORCE_FAILOVER_ALLOW_DATA_LOSS;
```

Quand le réplica principal précédent récupère, il assume également le rôle principal. Pour garantir que le réplica principal précédent passe à un rôle secondaire, exécutez la commande suivante sur le réplica principal précédent.

```SQL
ALTER AVAILABILITY GROUP [ag1]  SET (ROLE = SECONDARY);
```

### <a name="manual-failover-without-data-loss"></a>Basculement manuel sans perte de données

Utilisez cette méthode quand le réplica principal est disponible, mais que vous devez provisoirement ou définitivement changer la configuration et l’instance qui héberge le réplica principal. Pour éviter toute perte de données, avant d’effectuer le basculement manuel, vérifiez que le réplica secondaire cible est à jour. 

Pour effectuer un basculement manuel sans perte de données :

1. Associez au réplica secondaire cible le mode `SYNCHRONOUS_COMMIT`.

   ```SQL
   ALTER AVAILABILITY GROUP [ag1] 
        MODIFY REPLICA ON N'<node2>' 
        WITH (AVAILABILITY_MODE = SYNCHRONOUS_COMMIT);
   ```

2. Pour vérifier que les transactions actives sont validées sur le réplica principal et sur au moins un réplica secondaire synchrone, exécutez la requête suivante : 

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

3. Affectez la valeur 1 à `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT`.

   Le script suivant définit `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` sur 1 sur un groupe de disponibilité nommé `ag1`. Avant d’exécuter le script suivant, remplacez `ag1` par le nom de votre groupe de disponibilité :

   ```SQL
   ALTER AVAILABILITY GROUP [ag1] 
        SET (REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT = 1);
   ```

   Ce paramétrage garantit que chaque transaction active est validée sur le réplica principal et sur au moins un réplica secondaire synchrone. 
   >[!NOTE]
   >Ce paramètre n’est pas propre au basculement et doit être défini en fonction des exigences de l’environnement.
   
4. Mettez hors connexion le réplica principal en vue des changements de rôle.
   ```SQL
   ALTER AVAILABILITY GROUP [ag1] OFFLINE
   ```

5. Promouvez le réplica secondaire en réplica principal. 

   ```SQL
   ALTER AVAILABILITY GROUP ag1 FORCE_FAILOVER_ALLOW_DATA_LOSS; 
   ``` 

6. Changez le rôle de l’ancien réplica principal en `SECONDARY`, et exécutez cette commande sur l’instance de SQL Server hébergeant le réplica principal :

   ```SQL
   ALTER AVAILABILITY GROUP [ag1] 
        SET (ROLE = SECONDARY); 
   ```

   > [!NOTE] 
   > Pour supprimer un groupe de disponibilité, utilisez [DROP AVAILABILITY GROUP](https://docs.microsoft.com/sql/t-sql/statements/drop-availability-group-transact-sql). Pour un groupe de disponibilité créé avec le type de cluster NONE ou EXTERNAL, exécutez la commande sur tous les réplicas faisant partie du groupe de disponibilité.
