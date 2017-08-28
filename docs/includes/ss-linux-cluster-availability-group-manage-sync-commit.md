## <a name="managing-synchronous-commit-mode"></a>Gestion du mode de validation synchrone

>[!WARNING]
>Dans certains cas, un groupe de disponibilité SQL Server en mode de validation synchrone sur Linux peut être exposé à une perte de données. Vous trouverez ci-dessous des informations sur la racine du problème, ainsi que la solution de contournement pour éviter toute perte de données. Ce problème sera résolu dans les prochaines versions.

###<a name="pacemaker-notification-for-availability-group-resource-promotion"></a>Notification Pacemaker pour la promotion des ressources de groupe de disponibilité

Avant CTP 1.4, l’agent de ressources Pacemaker pour les groupes de disponibilité ne pouvait pas déterminer si un réplica marqué `SYNCHRONOUS_COMMIT` était ou non réellement à jour. Le réplica pouvait avoir arrêté de se synchroniser avec le principal, mais il l’ignorait. De ce fait, l’agent pouvait promouvoir un réplica obsolète en principal, ce qui pouvant occasionner une perte de données en cas de réussite. 

Pour résoudre ce problème, SQL Server 2017 CTP 1.4 ajoute `sequence_number` à `sys.availability_groups`. `sequence_number` est une valeur de type BIGINT à croissance monotone qui représente l’état de mise à jour du réplica de groupe de disponibilité local par rapport au reste du système. Les basculements, ajouts et/ou suppressions de réplicas et les autres opérations sur les groupes de disponibilité ont pour effet de mettre à jour ce numéro. Le numéro est mis à jour sur le principal avant d’être transmis en mode push aux secondaires. Un secondaire à jour aura-t-il ainsi le même numéro que le principal.

Quand Pacemaker décide de promouvoir un réplica en principal, il envoie dans un premier temps une notification à tous les réplicas pour extraire le numéro de séquence et le stocker. Ensuite, quand Pacemaker tente effectivement de promouvoir un réplica en principal, le réplica n’assure sa promotion que si son numéro de séquence est supérieur à tous les numéros de séquence. Autrement, il rejette l’opération de promotion. De cette façon, seul le réplica ayant le numéro de séquence le plus élevé peut être promu principal, ce qui évite toute perte de données.

Notez que ce résultat n’est garanti que si au moins un réplica candidat à la promotion possède le même numéro de séquence que le principal précédent. Sachant que l’agent de ressources attend de Pacemaker qu’il envoie des notifications à tous les réplicas, la ressource de disponibilité doit être configurée avec `notify=true`. Pour chaque ressource `ocf:mssql:ag` existante, l’utilisateur doit mettre à jour la configuration de ressource avec `notify=true` avant de mettre à jour le package `mssql-server-ha` vers CTP 1.4, sinon la ressource passe à l’état d’erreur. 

### <a name="how-to-avoid-potential-for-data-loss"></a>Comment éviter le risque de perte de données 

Dans le cas suivant, un groupe de disponibilité peut toujours être exposé à une perte de données. Dans un cluster qui comprend cinq nœuds, si un groupe de disponibilité possède des réplicas sur trois instances de SQL Server, il est possible que le réplica principal et l’un des deux réplicas secondaires devancent l’autre réplica secondaire. En pareil cas, `sequence_number` dans `sys.availability_groups` est supérieur à celui des autres réplicas. Dans ces conditions, si les deux réplicas perdent la connectivité avec le reste du cluster, Pacemaker peut considérer que les trois nœuds restants forment un quorum et autoriser le réplica latent à se promouvoir en principal. Cette situation constitue un risque potentiel de perte de données.

sql2017 introduit une nouvelle fonctionnalité pour forcer un certain nombre de réplicas secondaires à être disponibles avant que des transactions puissent être validées sur le réplica principal. `REQUIRED_COPIES_TO_COMMIT` vous permet de définir le nombre de réplicas qui doivent être validés dans les journaux de transactions de base de données de réplicas secondaires avant qu’une transaction puisse se poursuivre. Vous pouvez utiliser cette option avec `CREATE AVAILABILITY GROUP` ou `ALTER AVAILABILITY GROUP`. Consultez [CREATE AVAILABILITY GROUP](http://msdn.microsoft.com/library/ff878399.aspx).

Pour éviter le risque de perte de données décrit ci-dessus, attribuez à `REQUIRED_COPIES_TO_COMMIT` le nombre maximal de réplicas synchronisés. Les versions à venir intégreront la logique permettant de gérer automatiquement le paramètre `REQUIRED_COPIES_TO_COMMIT`.
Dès lors que `REQUIRED_COPIES_TO_COMMIT` est défini, les transactions au niveau des bases de données de réplicas principaux sont mises en attente tant qu’elles ne sont pas validées sur le nombre requis de journaux de transactions de bases de données de réplicas secondaires synchrones. S’il n’y a pas suffisamment de réplicas secondaires synchrones en ligne, les transactions sont mises en suspens jusqu’à ce que soit rétablie la communication avec un nombre suffisant de réplicas secondaires.

L’exemple suivant affecte au groupe de disponibilité [ag1] la valeur `REQUIRED_COPIES_TO_COMMIT = 2`. 

```Transact-SQL
ALTER AVAILABILITY GROUP [ag1]
SET (REQUIRED_COPIES_TO_COMMIT = 2)
```

Dans l’exemple ci-dessus, si le groupe de disponibilité contient deux réplicas secondaires, il attend que les deux réplicas secondaires reconnaissent les validations. Si l’un d’eux ne répond pas, les transactions sont bloquées.
