Chaque groupe de disponibilité contient un seul réplica principal. Le réplica principal autorise les opérations de lecture et d’écriture. Pour changer de réplica principal, vous pouvez effectuer un basculement. Dans un groupe de disponibilité pour la haute disponibilité, le gestionnaire de cluster automatise le processus de basculement. Dans un groupe de disponibilité avec échelle lecture, le processus de basculement est manuel. Il existe deux façons de basculer le réplica principal dans un groupe de disponibilité avec échelle lecture.

- Basculement manuel forcé avec perte de données

- Basculement manuel sans perte de données

### <a name="forced-fail-over-with-data-loss"></a>Basculement forcé avec perte de données

Utilisez cette méthode quand le réplica principal n’est pas disponible et qu’il ne peut pas être récupéré. 

Pour forcer le basculement avec perte de données, connectez-vous à l’instance SQL qui héberge le réplica secondaire cible et exécutez la commande suivante :

```SQL
ALTER AVAILABILITY GROUP [ag1] FORCE_FAILOVER_ALLOW_DATA_LOSS;
```

### <a name="manual-fail-over-without-data-loss"></a>Basculement manuel sans perte de données

Utilisez cette méthode quand le réplica principal est disponible, mais que vous devez provisoirement ou définitivement changer la configuration et l’instance qui héberge le réplica principal. Avant d’émettre le basculement manuel, vérifiez que le réplica secondaire cible est à jour afin d’éviter toute perte de données. 

Les étapes suivantes montrent comment effectuer un basculement manuel sans perte de données :

1. Associez au réplica secondaire cible le mode de validation synchrone.

   ```SQL
   ALTER AVAILABILITY GROUP [ag1] 
        MODIFY REPLICA ON N'**<node2>*' 
        WITH (AVAILABILITY_MODE = SYNCHRONOUS_COMMIT);
   ```

1. Exécutez la requête suivante pour vérifier que les transactions actives sont validées sur le réplica principal et sur au moins un réplica secondaire synchrone. 

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

1. Définissez `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` sur 1.

   Le script suivant définit `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` sur 1 sur un groupe de disponibilité nommé `ag1`. Avant de l’exécuter, remplacez `ag1` par le nom de votre groupe de disponibilité.

   ```SQL
   ALTER AVAILABILITY GROUP [ag1] 
        SET REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT = 1;
   ```

   Ce paramétrage garantit que chaque transaction active est validée sur le réplica principal et sur au moins un réplica synchrone secondaire. 

1. Rétrogradez le réplica principal en réplica secondaire. Une fois le réplica principal rétrogradé, il est en lecture seule. Exécutez cette commande sur l’instance SQL hébergeant le réplica principal pour définir le rôle sur SECONDARY :

   ```SQL
   ALTER AVAILABILITY GROUP [ag1] 
        SET (ROLE = SECONDARY); 
   ```

1. Promouvez le réplica secondaire en réplica principal. 

   ```SQL
   ALTER AVAILABILITY GROUP ag1 FORCE_FAILOVER_ALLOW_DATA_LOSS; 
   ```  

   > [!NOTE] 
   > Pour supprimer un groupe de disponibilité, utilisez [DROP AVAILABILITY GROUP](https://docs.microsoft.com/en-us/sql/t-sql/statements/drop-availability-group-transact-sql). Pour un groupe de disponibilité créé avec CLUSTER_TYPE NONE ou EXTERNAL, vous devez exécuter la commande sur tous les réplicas faisant partie du groupe de disponibilité.