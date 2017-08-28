## <a name="pacemakerNotify"></a>Présentation de l’agent de ressources SQL Server pour Pacemaker

Avant la version CTP 1.4, l’agent de ressources Pacemaker pour les groupes de disponibilité ne pouvait pas déterminer si un réplica marqué `SYNCHRONOUS_COMMIT` était ou non réellement à jour. Le réplica pouvait avoir arrêté de se synchroniser avec le principal, mais il l’ignorait. De ce fait, l’agent pouvait promouvoir un réplica obsolète en principal, ce qui pouvait occasionner une perte de données en cas de réussite. 

Pour résoudre ce problème, SQL Server 2017 CTP 1.4 a ajouté `sequence_number` à `sys.availability_groups`. `sequence_number` est une valeur de type BIGINT à croissance monotone qui représente l’état de mise à jour du réplica du groupe de disponibilité local par rapport au reste des réplicas du groupe. Les basculements, les ajouts ou les suppressions de réplicas, et les autres opérations sur les groupes de disponibilité, mettent à jour ce numéro. Le numéro est mis à jour sur le réplica principal avant d’être transmis en mode push aux réplicas secondaires. Ainsi, un réplica secondaire à jour a le même sequence_number que le réplica principal. 

Quand Pacemaker décide de promouvoir un réplica en principal, il envoie d’abord une notification à tous les réplicas pour extraire le numéro de séquence et le stocker (nous appelons ceci la notification de prépromotion). Ensuite, quand Pacemaker tente effectivement de promouvoir un réplica en principal, le réplica n’assure sa promotion que si son numéro de séquence est supérieur à tous les numéros de séquence de tous les réplicas. Autrement, il rejette l’opération de promotion. De cette façon, seul le réplica ayant le numéro de séquence le plus élevé peut être promu principal, ce qui évite toute perte de données. 

Notez que ce résultat n’est garanti que si au moins un réplica candidat à la promotion possède le même numéro de séquence que le principal précédent. Pour ce faire, le comportement par défaut est que l’agent de ressource Pacemaker définit automatiquement `REQUIRED_COPIES_TO_COMMIT` de sorte qu’au moins un réplica secondaire de validation synchrone est à jour et disponible pour être la cible d’un basculement automatique. Avec chaque action de surveillance, la valeur de `REQUIRED_COPIES_TO_COMMIT` est calculée (et mise à jour si nécessaire) selon la formule (« nombre de réplicas avec validation synchrone » / 2). Ensuite, au moment du basculement, l’agent de ressource nécessitera la réponse de (`total number of replicas` - `required_copies_to_commit` réplicas) à la notification de prépromotion pour pouvoir promouvoir un d’entre eux en principal. Le réplica avec le `sequence_number` le plus élevé sera promu en principal. 

Par exemple, prenons le cas d’un groupe de disponibilité avec trois réplicas synchrones : un réplica principal et deux réplicas secondaires avec validation synchrone.

- `REQUIRED_COPIES_TO_COMMIT` est de 3 / 2 = 1

- Le nombre de réplicas nécessaires pour répondre à l’action de prépromotion est 3-1 = 2. Ainsi, 2 réplicas doivent être actifs pour que le basculement soit déclenché. Cela signifie que, dans le cas d’une indisponibilité du réplica principal, si un des réplicas secondaires ne répond pas et que seul un des réplicas secondaires répond à l’action de prépromotion, l’agent de ressource ne peut pas garantir que le réplica secondaire qui a répondu a le sequence_number le plus élevé, et le basculement n’est pas déclenché.

Un utilisateur peut choisir de remplacer le comportement par défaut et de configurer la ressource du groupe de disponibilité pour qu’elle ne définisse pas `REQUIRED_COPIES_TO_COMMIT` automatiquement comme ci-dessus.

>[!IMPORTANT]
>Quand la valeur de `REQUIRED_COPIES_TO_COMMIT` est 0, il existe un risque de perte de données. En cas d’indisponibilité du réplica principal, l’agent de ressource ne déclenche pas automatiquement un basculement. L’utilisateur doit décider s’il veut attendre que le réplica principal soit récupéré ou basculer manuellement.

Pour définir `REQUIRED_COPIES_TO_COMMIT` sur 0, exécutez :

```bash
sudo pcs resource update <**ag_cluster**> required_copies_to_commit=0
```

Commande équivalente dans crm (sur SLES) :

```bash
sudo crm resource param <**ag_cluster**> set required_synchronized_secondaries_to_commit 0
```

Pour revenir à la valeur calculée par défaut, exécutez :

```bash
sudo pcs resource update <**ag_cluster**> required_copies_to_commit=
```

>[!NOTE]
>La mise à jour des propriétés des ressources provoque l’arrêt et le redémarrage de tous les réplicas. Cela signifie que le réplica principal sera temporairement rétrogradé puis à nouveau promu, ce qui provoquera une indisponibilité temporaire en écriture. La nouvelle valeur pour REQUIRED_COPIES_TO_COMMIT est définie seulement une fois que les réplicas sont redémarrés et non pas dès l’exécution de la commande pcs.

## <a name="balancing-high-availability-and-data-protection"></a>Équilibre entre la haute disponibilité et la protection des données 

Ce comportement par défaut s’applique également dans le cas de 2 réplicas synchrones (principal + secondaire). Pacemaker applique `REQUIRED_COPIES_TO_COMMIT = 1` par défaut de façon à garantir que le réplica secondaire est toujours à jour pour une protection maximale des données.  

>[!WARNING]
>Ceci s’accompagne d’un risque plus élevé d’indisponibilité du réplica principal en raison des indisponibilités planifiées ou imprévues sur le réplica secondaire. L’utilisateur peut choisir de modifier le comportement par défaut de l’agent de ressource et de remplacer la valeur de `REQUIRED_COPIES_TO_COMMIT` par 0 :

```bash
sudo pcs resource update <**ag1**> required_copies_to_commit=0
```

Une fois cette valeur remplacée, l’agent de ressource utilise la nouvelle valeur pour `REQUIRED_COPIES_TO_COMMIT` et cesse de la calculer. Cela signifie que les utilisateurs doivent la mettre à jour manuellement en conséquence (par exemple s’ils augmentent le nombre de réplicas).

Le tableau ci-dessous décrit le résultat d’une indisponibilité pour les réplicas principaux ou secondaires dans différentes configurations des ressources d’un groupe de disponibilité :

### <a name="availability-group---2-sync-replicas"></a>Groupe de disponibilité - 2 réplicas de synchronisation

| |Indisponibilité du réplica principal |Une indisponibilité du réplica secondaire
|:---|:--- |:--- |
|`REQUIRED_COPIES_TO_COMMIT=0`|L’utilisateur doit effectuer un BASCULEMENT manuel. <br>Perte de données possible.<br> Le nouveau réplica principal est en lecture/écriture |Le réplica principal est en lecture/écriture, il est exposé à des pertes de données
|`REQUIRED_COPIES_TO_COMMIT=1` * |Le cluster effectue automatiquement le BASCULEMENT <br>Pas de perte de données. <br> Le nouveau réplica principal rejette toutes les connexions jusqu’à la récupération du réplica principal précédent puis se joint au groupe de disponibilité comme réplica secondaire. |Le réplica principal rejette toutes les connexions jusqu’à la récupération du réplica secondaire.

\* Comportement par défaut de l’agent de ressource SQL Server pour Pacemaker

### <a name="availability-group---3-sync-replicas"></a>Groupe de disponibilité - 3 réplicas de synchronisation

| |Indisponibilité du réplica principal |Une indisponibilité du réplica secondaire
|:---|:--- |:--- |
|`REQUIRED_COPIES_TO_COMMIT=0`|L’utilisateur doit effectuer un BASCULEMENT manuel. <br>Perte de données possible. <br>Le nouveau réplica principal est en lecture/écriture |Le réplica principal est en lecture/écriture
|`REQUIRED_COPIES_TO_COMMIT=1` * |Le cluster effectue automatiquement le BASCULEMENT. <br>Pas de perte de données. <br>Le nouveau réplica principal est en lecture/écriture |Le réplica principal est en lecture/écriture 

\* Comportement par défaut de l’agent de ressource SQL Server pour Pacemaker