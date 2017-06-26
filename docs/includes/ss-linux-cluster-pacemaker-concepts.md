## <a name="pacemakerNotify"></a>Comprendre l’agent de ressources de SQL Server pour STIMULATEUR

Avant la version CTP 1.4, l’agent de ressource STIMULATEUR pour les groupes de disponibilité ne peut pas savoir si un réplica est marqué comme étant `SYNCHRONOUS_COMMIT` a réellement à jour ou non. Le réplica pouvait avoir arrêté de se synchroniser avec le principal, mais il l’ignorait. Par conséquent, l’agent pu promouvoir un réplica obsolète principal - qui, en cas de réussite, peut provoquer une perte de données. 

SQL Server 2017 CTP 1.4 ajouté `sequence_number` à `sys.availability_groups` pour résoudre ce problème. `sequence_number`est une valeur BIGINT monolithique qui représente la mise à jour le réplica de groupe de disponibilité local est en ce qui concerne le reste des réplicas du groupe de disponibilité. Effectuer des basculements, en ajoutant ou en supprimant les réplicas et les autres opérations de groupe de disponibilité, mettre à jour ce nombre. Le nombre est mis à jour sur le serveur principal, puis envoyé à des réplicas secondaires. Un réplica secondaire qui est à jour aura donc la même numéros de séquence en tant que le serveur principal. 

Lorsque STIMULATEUR décide de promouvoir un réplica principal, tout d’abord, il envoie une notification à tous les réplicas pour extraire le numéro de séquence et les stocker (nous l’appellerons le promouvoir la notification préalable). Ensuite, quand il tente réellement STIMULATEUR promouvoir un réplica principal, le réplica lui-même promeut uniquement si son numéro de séquence est le plus élevé de tous les numéros de séquence à partir de tous les réplicas et rejette l’opération de promotion dans le cas contraire. De cette façon, seul le réplica ayant le numéro de séquence le plus élevé peut être promu principal, ce qui évite toute perte de données. 

Notez que ce résultat n’est garanti que si au moins un réplica candidat à la promotion possède le même numéro de séquence que le principal précédent. Pour ce faire, le comportement par défaut est de l’agent de ressource STIMULATEUR définir automatiquement `REQUIRED_COPIES_TO_COMMIT` tel qu’au moins un synchrone valider secondaire réplica est à jour et disponibles pour être la cible d’un basculement automatique. Avec chaque action d’analyse, la valeur de `REQUIRED_COPIES_TO_COMMIT` est calculée (et mises à jour si nécessaire) en tant que ('nombre de réplicas avec validation synchrone' / 2). Ensuite, au moment du basculement, l’agent de ressource nécessitera (`total number of replicas`  -  `required_copies_to_commit` réplicas) pour répondre à la promouvoir préalable de notification pour être en mesure de promouvoir un d’eux au principal. Le réplica avec la plus grande `sequence_number` sera promu à un principal. 

Par exemple, prenons le cas d’un groupe de disponibilité avec trois réplicas synchrones - un réplica principal et deux réplicas secondaires avec validation synchrone.

- `REQUIRED_COPIES_TO_COMMIT`est de 3 / 2 = 1

- Le nombre de réplicas pour répondre aux préalable promouvoir action requis est 1-3 = 2. Par conséquent, 2 réplicas doivent être pour le basculement doit être déclenchée. Cela signifie que, dans le cas de panne principal, si un des réplicas secondaires ne répond pas et que seul l’un des serveurs secondaires répond à l’avant de promouvoir l’action, l’agent de ressource ne peut pas garantir que la base de données secondaire qui a répondu possède les numéros de séquence le plus élevé et un basculement n’est pas déclenché.

Un utilisateur peut choisir de remplacer le comportement par défaut et configurer la ressource du groupe de disponibilité ne pas définir `REQUIRED_COPIES_TO_COMMIT` automatiquement comme ci-dessus.

>[!IMPORTANT]
>Lorsque `REQUIRED_COPIES_TO_COMMIT` est 0 est risque de perte de données. En cas de panne du principal, l’agent de ressource ne déclenche pas automatiquement un basculement. L’utilisateur doit décider s’ils veulent à attendre pour récupérer ou basculer manuellement de données primaire.

Pour définir `REQUIRED_COPIES_TO_COMMIT` à 0, exécutez :

```bash
sudo pcs resource update <**ag_cluster**> required_copies_to_commit=0
```

Commande équivalente dans crm (sur SLES) :

```bash
sudo crm resource param <**ag_cluster**> set required_synchronized_secondaries_to_commit 0
```

Pour revenir à la valeur par défaut valeur calculée, exécutez :

```bash
sudo pcs resource update <**ag_cluster**> required_copies_to_commit=
```

>[!NOTE]
>Tous les réplicas arrêter et redémarrer provoque la mise à jour des propriétés de ressource. Cela signifie primaire est temporairement rétrogradé à une base de données secondaire, puis promu à nouveau qui services temporaire écrira indisponibilité. La nouvelle valeur pour REQUIRED_COPIES_TO_COMMIT aura uniquement valeur une fois que les réplicas sont redémarrés, il ne sera pas instantanée avec la commande PC en cours d’exécution.

## <a name="balancing-high-availability-and-data-protection"></a>L’équilibrage de la haute disponibilité et protection des données 

Ce comportement par défaut s’applique également au cas de 2 réplicas synchrones (principales + secondaire). Par défaut, sera STIMULATEUR `REQUIRED_COPIES_TO_COMMIT = 1` pour vous assurer de la base de données secondaire réplica n’est toujours à jour pour la protection de données maximale.  

>[!WARNING]
>Il est fourni avec des risques plus élevés d’indisponibilité du réplica principal en raison de l’arrêt, planifié ou sur le serveur secondaire. L’utilisateur peut choisir Modifier le comportement par défaut de l’agent de la ressource et remplacer le `REQUIRED_COPIES_TO_COMMIT` 0 :

```bash
sudo pcs resource update <**ag1**> required_copies_to_commit=0
```

Une fois le remplacement, l’agent de ressource utilisera le nouveau paramètre pour `REQUIRED_COPIES_TO_COMMIT` et arrêter informatique il. Cela signifie que les utilisateurs devront manuellement mettre à jour en conséquence (par exemple, si elles augmentent le nombre de réplicas).

Le tableau ci-dessous décrit le résultat d’une interruption de réplicas principaux ou secondaires dans les configurations de ressources de groupe de disponibilité différents :

### <a name="availability-group---2-sync-replicas"></a>Groupe de disponibilité - 2 réplicas de synchronisation

| |Panne principal |Une panne de réplica secondaire
|:---|:--- |:--- |
|`REQUIRED_COPIES_TO_COMMIT=0`|Utilisateur doit émettre un basculement manuel. <br>Peut avoir une perte de données.<br> Nouveau réplica principal est en lecture/écriture |Principal est en lecture/écriture, exécution exposée à des pertes de données
|`REQUIRED_COPIES_TO_COMMIT=1` * |Cluster délivre automatiquement le basculement <br>Aucune perte de données. <br> Nouveau réplica principal rejette toutes les connexions jusqu'à ce que le réplica principal précédent récupère et joint le groupe de disponibilité comme base de données secondaire. |Principal rejette toutes les connexions jusqu'à ce que celle-ci est résolue secondaire.

\*Agent de ressources SQL Server STIMULATEUR comportement par défaut.

### <a name="availability-group---3-sync-replicas"></a>Groupe de disponibilité - 3 réplicas de synchronisation

| |Panne principal |Une panne de réplica secondaire
|:---|:--- |:--- |
|`REQUIRED_COPIES_TO_COMMIT=0`|Utilisateur doit émettre un basculement manuel. <br>Peut avoir une perte de données. <br>Nouveau réplica principal est en lecture/écriture |Principal est en lecture/écriture
|`REQUIRED_COPIES_TO_COMMIT=1` * |Cluster de basculement automatiquement émet. <br>Aucune perte de données. <br>Nouveau réplica principal est RW |Principal est en lecture/écriture 

\*Agent de ressources SQL Server STIMULATEUR comportement par défaut.