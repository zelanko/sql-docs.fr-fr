Cet article fournit une vue d’ensemble des solutions de continuité d’activité dans le cadre de la haute disponibilité et de la récupération d’urgence dans SQL Server. 

Quand vous déployez SQL Server, vous devez toujours vérifier que toutes les instances SQL Server critiques et les bases de données qu’elles contiennent sont disponibles pour l’entreprise et les utilisateurs finaux, quels que soient l’heure ou le jour. L’objectif est de maintenir l’activité avec un minimum d’interruption voire sans interruption. Ce concept est également connu sous le nom de continuité d’activité.

SQL Server 2017 introduit plusieurs nouvelles fonctionnalités ou améliorations de celles existantes, dont certaines concernent la disponibilité. La nouveauté la plus importante de SQL Server 2017 est la prise en charge de SQL Server sur les distributions Linux. Pour obtenir la liste complète des nouvelles fonctionnalités de SQL Server 2017, consultez la rubrique [Nouveautés de SQL Server](../sql-server/what-s-new-in-sql-server-2017.md).

Cet article traite en particulier des scénarios de disponibilité dans SQL Server 2017, ainsi que des fonctionnalités de disponibilité nouvelles et améliorées dans SQL Server 2017. Les scénarios étudiés sont notamment les scénarios hybrides qui couvrent les déploiements de SQL Server sur Windows Server et Linux, et les scénarios capables d’augmenter le nombre de copies accessibles en lecture d’une base de données. Bien que cet article n’aborde pas les options de disponibilité externes à SQL Server, comme celles fournies par la virtualisation, tous les sujets traités ici s’appliquent aux installations de SQL Server sur une machine virtuelle invitée, qu’elle soit dans le cloud public ou hébergée par un serveur hyperviseur local.

## <a name="sql-server-2017-scenarios-using-the-availability-features"></a>Scénarios de SQL Server 2017 utilisant les fonctionnalités de disponibilité

Les groupes de disponibilité, les instances FCI et la copie des journaux de transaction peuvent être utilisés de plusieurs façons et pas seulement à des fins de disponibilité. Les fonctionnalités de disponibilité sont utilisées dans quatre contextes principaux :

* Haute disponibilité
* Récupération d'urgence
* Les migrations et les mises à niveau
* La mise à plus haute échelle des copies accessibles en lecture d’une ou plusieurs bases de données

Chaque section traite des fonctionnalités appropriées pour un scénario en particulier. La seule fonctionnalité non abordée ici est la [Réplication SQL Server](../relational-databases/replication/sql-server-replication.md). Bien qu’elle ne soit pas officiellement désignée comme une fonctionnalité de disponibilité dans le contexte Always On, elle est souvent utilisée pour la redondance des données dans certains scénarios. La réplication sera ajoutée à SQL Server sur Linux dans une version future.

> [!IMPORTANT] 
> Les fonctionnalités de disponibilité de SQL Server ne remplacent pas le besoin d’une stratégie de sauvegarde et de restauration robuste et correctement testée, qui est le fondement de toute solution de disponibilité.

### <a name="high-availability"></a>Haute disponibilité

Les instances ou la base de données SQL Server doivent être disponibles en cas de problème local dans un centre de données ou dans une région du cloud. Cette section décrit comment les fonctionnalités de disponibilité de SQL Server peuvent aider à atteindre cet objectif. Toutes les fonctionnalités décrites sont disponibles aussi bien sur Windows Server que sur Linux. 

#### <a name="always-on-availability-groups"></a>Groupes de disponibilité Always On

Les groupes de disponibilité Always On (ou groupes de disponibilité) ont été introduits dans SQL Server 2012 pour fournir une protection au niveau de la base de données en envoyant chaque transaction de base de données à une autre instance (un réplica) qui contient une copie de cette base de données dans un état particulier. Un groupe de disponibilité peut être déployé sur les éditions Standard ou Entreprise.  Les instances qui font partie d’un groupe de disponibilité peuvent être autonomes ou des instances de cluster de basculement Always On (ou instances FCI, décrites dans la section suivante). Les transactions étant envoyées à un réplica à mesure qu’elles se produisent, les groupes de disponibilité sont recommandés quand il est nécessaire de baisser les objectifs de point de récupération et de délai de récupération. Le déplacement de données entre réplicas peut être synchrone ou asynchrone. L’édition Entreprise autorise jusqu'à trois réplicas synchrones (y compris le réplica principal). Un groupe de disponibilité contient une copie complète de la base de données accessible en écriture et en lecture qui se trouve sur le réplica principal. Les réplicas secondaires ne peuvent pas recevoir de transaction directement des utilisateurs finaux ou des applications. 

> [!NOTE] 
> Always On est un terme général qui désigne les fonctionnalités de disponibilité dans SQL Server et inclut les groupes de disponibilité et les instances FCI. Always On n’est pas le nom de la fonctionnalité de groupe de disponibilité.

Comme les groupes de disponibilité fournissent une protection uniquement au niveau de la base de données et non au niveau de l’instance, tout ce qui n’est pas capturé dans le journal des transactions ou configuré dans la base de données doit être synchronisé manuellement sur chaque réplica secondaire. Exemples d’objets devant être synchronisés manuellement : connexions au niveau de l’instance, serveurs liés et travaux de SQL Server Agent.

Un groupe de disponibilité a également un autre composant qui est l’écouteur. Il permet aux applications et aux utilisateurs finaux de se connecter sans avoir besoin de connaître l’instance de SQL Server qui héberge le réplica principal. Chaque groupe de disponibilité a son propre écouteur. Bien que les implémentations de l’écouteur soient légèrement différentes sur Windows Server et Linux, la fonctionnalité qu’il fournit et son utilisation sont identiques. L’image ci-dessous montre un groupe de disponibilité Windows Server qui utilise un cluster de basculement Windows Server (WSFC). La disponibilité repose sur un cluster sous-jacent au niveau de la couche du système d’exploitation, aussi bien sur Linux que sur Windows Server. L’exemple montre une configuration simple de deux serveurs, ou nœuds, où le cluster sous-jacent est un cluster WSFC. 

![Groupe de disponibilité simple](media/sql-server-ha-story/image1.png)
 
Les éditions Standard et Entreprise prennent chacune en charge un nombre maximal de réplicas différent. Un groupe de disponibilité dans l’édition Standard, appelé groupe de disponibilité de base, prend en charge deux réplicas (un réplica principal et un secondaire) et une seule base de données dans le groupe de disponibilité. L’édition Entreprise permet non seulement de configurer plusieurs bases de données dans un seul groupe de disponibilité, mais prend en charge également jusqu'à neuf réplicas au total (un réplica principal et huit secondaires). L’édition Entreprise fournit d’autres avantages comme des réplicas secondaires accessibles en lecture, la possibilité d’effectuer des sauvegardes d’un réplica secondaire, et bien plus encore.

>[!NOTE]
> La mise en miroir de bases de données, dépréciée dans SQL Server 2012, n’est pas disponible sur la version Linux de SQL Server et ne sera pas ajoutée. Les clients qui utilisent encore la mise en miroir de bases de données doivent commencer à planifier la migration vers les groupes de disponibilité, qui remplacent la mise en miroir de bases de données.

En matière de disponibilité, les groupes de disponibilité peuvent fournir un basculement automatique ou manuel. Un basculement automatique peut se produire si un déplacement de données synchrone est configuré et que la base de données est synchronisée sur les réplicas principal et secondaire. Si l’écouteur est utilisé et que l’application utilise une version plus récente du .NET (version 3.5 avec une mise à jour, ou version 4.0 ou ultérieure), le basculement doit être géré avec peu ou aucun impact sur les utilisateurs finaux. Le basculement permettant de convertir un réplica secondaire en réplica principal peut être automatique ou manuel, et est généralement mesuré en secondes.

La liste ci-dessous souligne les différences entre les groupes de disponibilité Windows Server et Linux :
* En raison du fonctionnement différent du cluster sous-jacent sur Linux et Windows Server, tous les basculements (manuels ou automatiques) des groupes de disponibilité sont effectués via le cluster sur Linux. Pour les déploiements de groupes de disponibilité de base Windows Server, les basculements manuels doivent être effectués via SQL Server. Les basculements automatiques sont gérés par le cluster sous-jacent sur Windows Server et Linux. 
* Dans SQL Server 2017, la configuration recommandée pour les groupes de disponibilité sur Linux est de trois réplicas minimum. Cela est lié au fonctionnement du clustering sous-jacent. Une meilleure solution permettant de configurer deux réplicas sera publiée après le lancement.
* Sur Linux, le nom commun utilisé par chaque écouteur est défini dans le système DNS et non dans le cluster comme sur Windows Server.

Dans SQL Server 2017, les groupes de disponibilité bénéficient de nouvelles fonctionnalités et d’améliorations :

* Types de cluster
* REQUIRED_SECONDARIES_TO_COMMIT
* Amélioration de la prise en charge de Microsoft Distributor Transaction Coordinator (DTC) pour les configurations basées sur Windows Server
* Ajout de scénarios de scale-out pour les bases de donnée en lecture seule (décrits plus loin dans cet article)

##### <a name="always-on-availability-group-cluster-types"></a>Types de cluster des groupes de disponibilité Always On

La forme de disponibilité intégrée de clustering dans Windows Server est activée via une fonctionnalité nommée Clustering de basculement. Cela vous permet de créer un cluster WSFC à utiliser avec un groupe de disponibilité ou une instance FCI. L’intégration des groupes de disponibilité et des instances FCI est fournie par des DLL de ressource adaptées aux clusters inclus dans SQL Server. 

Chaque distribution Linux prise en charge fournit sa propre version de la solution de cluster Pacemaker. SQL Server 2017 sur Linux prend en charge l’utilisation de Pacemaker. Pacemaker est une solution de pile ouverte que chaque distribution peut ensuite intégrer à sa pile. Bien que Pacemaker soit inclus dans les distributions, il n’est pas intégré comme une fonctionnalité Clustering de basculement dans Windows Server.

Il y a davantage de similitudes que de différences entre un cluster WSFC et Pacemaker. Tous deux permettent de combiner des serveurs individuels dans une configuration pour assurer la disponibilité et utilisent des concepts comme les ressources, les contraintes (même si elles sont implémentées différemment), le basculement, etc. Pour prendre en charge Pacemaker dans les configurations de groupes de disponibilité et d’instances FCI (y compris le basculement automatique), Microsoft fournit le package mssql-server-ha pour Pacemaker, qui est similaire, mais pas exactement identique, aux DLL de ressource dans un cluster WSFC. Un cluster WSFC et Pacemaker se distinguent notamment par le fait qu’aucune ressource de nom de réseau n’est incluse dans Pacemaker, car celui-ci récupère le nom de l’écouteur (ou le nom de l’instance FCI) sur un cluster WSFC. Le système DNS fournit cette résolution de nom sur Linux.

Parce que la pile de cluster est différente, les groupes de disponibilité sont modifiés, car SQL Server doit gérer une partie des métadonnées qui sont gérées en mode natif par un cluster WSFC. Le changement le plus [!IMPORTANT] est l’introduction d’un type de cluster pour un groupe de disponibilité. Il est stocké dans sys.availability_groups dans les colonnes cluster_type et cluster_type_desc. Il existe trois types de cluster :

* WSFC 
* Externe
* None

Tous les groupes de disponibilité qui ont besoin de disponibilité doivent utiliser un cluster sous-jacent. Dans le cas de SQL Server 2017, il s’agit d’un cluster WSFC ou de Pacemaker. Pour les groupes de disponibilité de base Windows Server qui utilisent un cluster WSFC sous-jacent, le type de cluster par défaut est WSFC et ne doit pas nécessairement être défini. Pour les groupes de disponibilité Linux, lors de la création du groupe de disponibilité, vous devez définir le type de cluster sur Externe. L’intégration à Pacemaker est configurée après la création du groupe de disponibilité, tandis que sur un cluster WSFC, elle est effectuée au moment de la création.

Le type de cluster Aucun peut être utilisé avec les groupes de disponibilité Windows Server et Linux. Quand vous définissez le type de cluster sur Aucun, le groupe de disponibilité n’a pas besoin de cluster sous-jacent. Cela signifie que SQL Server 2017 est la première version de SQL Server qui prend en charge les groupes de disponibilité sans cluster. Toutefois, cette configuration n’est pas prise en charge comme solution de haute disponibilité. 

> [!IMPORTANT] 
> SQL Server 2017 ne permet pas de modifier le type de cluster d’un groupe de disponibilité après sa création. Cela signifie qu’un groupe de disponibilité ne peut pas passer du type Aucun à Externe ou WSFC, et inversement. 

Pour ceux qui veulent simplement ajouter des copies de base de données en lecture seule, ou qui sont intéressés par les options de migration ou de mise à niveau qu’offrent les groupes de disponibilité, mais ne veulent pas assumer la complexité de gérer un cluster sous-jacent ou la réplication, un groupe de disponibilité avec le type de cluster Aucun est la solution idéale. Pour plus d’informations, consultez les sections [Migrations et mises à niveau](#Migrations) et [Échelle lecture](#ReadScaleOut). 

La capture d’écran ci-dessous montre la prise en charge des différents types de cluster dans SSMS. Vous devez exécuter la version 17.1 ou ultérieure. La capture d’écran ci-dessous concerne la version 17.2.

![Options de groupe de disponibilité dans SSMS](media/sql-server-ha-story/image2.png)
 
##### <a name="required_synchronized_secondaries_to_commit"></a>REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT

Dans SQL Server 2016, la prise en charge du nombre de réplicas synchrones est passée de deux à trois dans l’édition Entreprise. Toutefois, si un réplica secondaire était synchronisé, mais que l’autre rencontrait un problème, il n’existait aucun moyen de contrôler le comportement pour indiquer au réplica principal d’attendre le réplica concerné ou de continuer. Cela signifie que le réplica principal à un moment donné continue de recevoir du trafic en écriture, même si le réplica secondaire n’est pas synchronisé, ce qui implique une perte de données sur le réplica secondaire.
Dans SQL Server 2017, il existe désormais une option pour contrôler le comportement en cas de réplicas synchrones : REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT. L’option fonctionne de la façon suivante :
* Il existe trois valeurs possibles : 0, 1 et 2
* La valeur est le nombre de réplicas secondaires qui doivent être synchronisés, ce qui a des implications sur la perte de données, la disponibilité du groupe de disponibilité et le basculement
* Pour les clusters WSFC et un type de cluster Aucun, la valeur par défaut est 0 et peut être définie manuellement sur 1 ou 2
* Pour un type de cluster Externe, par défaut, le mécanisme de cluster définit cette valeur qui peut être remplacée manuellement. Pour les trois réplicas synchrones, la valeur par défaut est égale à 1.
Sur Linux, la valeur de REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT est configurée sur la ressource de groupe de disponibilité dans le cluster. Sur Windows, elle est définie via Transact-SQL.

Une valeur supérieure à 0 garantit une protection de données plus élevée, car si le nombre de réplicas secondaires nécessaires n’est pas disponible, le réplica principal n’est pas disponible tant que le problème n’est pas résolu. REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT affecte également le comportement de basculement, car le basculement automatique ne peut pas se produire si le nombre nécessaire de réplicas secondaires n’est pas dans l’état approprié. Sur Linux, la valeur 0 n’autorise pas le basculement automatique, par conséquent, quand vous utilisez des réplicas synchrones avec basculement automatique, la valeur doit êtes supérieure à 0 pour obtenir le basculement automatique. Le comportement de SQL Server 2016 et des versions antérieures est une valeur 0 sur Windows Server.

##### <a name="enhanced-microsoft-distributed-transaction-coordinator-support"></a>Amélioration de la prise en charge de Microsoft Distributed Transaction Coordinator

Avant SQL Server 2016, la seule façon d’assurer la disponibilité dans SQL Server pour les applications qui nécessitent des transactions distribuées utilisant DTC en arrière-plan était de déployer des instances FCI. Une transaction distribuée peut être effectuée de deux manières :
* Une transaction qui s’étend sur plusieurs bases de données dans la même instance de SQL Server
* Une transaction qui s’étend sur plusieurs instances de SQL Server ou qui implique éventuellement une source de données non-SQL Server

SQL Server 2016 a introduit la prise en charge partielle de DTC avec les groupes de disponibilité (2ème scénario). SQL Server 2017 complète la prise en charge dans les deux scénarios avec DTC.

Autre amélioration de la prise en charge de DTC pour les groupes de disponibilité : dans SQL Server 2016, l’activation de la prise en charge de DTC sur un groupe de disponibilité pouvait être effectuée uniquement à la création du groupe de disponibilité et ne pouvait pas être ajoutée plus tard. Dans SQL Server 2017, la prise en charge de DTC peut être ajoutée à un groupe de disponibilité également après sa création.

>[!NOTE]
> La prise en charge de DTC peut uniquement être configurée pour les bases de données dans des instances SQL Server basées sur Windows Server. Si votre application nécessite DTC, vous devez utiliser le système d’exploitation Windows Server et non Linux pour votre déploiement de SQL Server. 

#### <a name="always-on-failover-cluster-instances"></a>Instances de cluster de basculement Always On
Les installations en cluster sont une fonctionnalité de SQL Server depuis la version 6.5. Les instances FCI sont une méthode testée qui permet d’assurer la disponibilité d’une installation entière de SQL Server, c’est-à-dire une instance. Cela signifie que tout ce que contient l’instance, y compris les bases de données, les travaux de SQL Server Agent, les serveurs liés, etc., est déplacé sur un autre serveur si le serveur sous-jacent rencontre un problème. Toutes les instances FCI nécessitent une sorte de stockage partagé, même s’il est fourni sur un réseau. Les ressources d’une instance FCI peuvent uniquement être exécutées et détenues par un seul nœud à un moment donné. Dans l’image ci-dessous, le premier nœud du cluster possède l’instance FCI, ce qui signifie également qu’il possède les ressources de stockage partagé associées, représenté par la ligne continue vers le stockage.

![Instance de cluster de basculement](media/sql-server-ha-story/image3.png)
 
Après un basculement, la propriété change, comme illustré dans l’image ci-dessous.

![Après le basculement](media/sql-server-ha-story/image4.png)
 
Il n’y a pas de perte de données avec une instance FCI, mais le stockage partagé sous-jacent est un point d’échec unique, car il n’y a qu’une seule copie des données. Les instances FCI sont souvent associées à une autre méthode de disponibilité, comme un groupe de disponibilité ou la copie des journaux de transaction, pour avoir des copies redondantes des bases de données. La méthode supplémentaire déployée doit utiliser un stockage séparé physiquement de l’instance FCI. Quand l’instance FCI bascule sur un autre nœud, elle s’arrête sur un nœud et démarre sur l’autre, ce qui a le même effet que si vous éteignez un serveur et le rallumez. Une instance FCI suit le processus de récupération normal, ce qui signifie que toutes les transactions qui doivent être restaurées par progression le sont, et toutes les transactions incomplètes sont annulées. Par conséquent, la base de données est cohérente par rapport à un point de données jusqu’au moment de l’échec ou du basculement manuel, il n’y a donc aucune perte de données. Les bases de données sont disponibles uniquement après la récupération, le temps de récupération dépend donc de plusieurs facteurs et est généralement plus long que le basculement sur un groupe de disponibilité. L’inconvénient est que quand vous basculez un groupe de disponibilité, des tâches supplémentaires peuvent être nécessaires pour que la base de données soit utilisable, comme l’activation d’un travail de SQL Server Agent.

Tout comme les groupes de disponibilité, les instances FCI récupèrent le nœud du cluster sous-jacent qui les héberge. Une instance FCI conserve toujours le même nom. Les applications et les utilisateurs finaux ne se connectent jamais aux nœuds, c’est le nom unique attribué à l’instance FCI qui est utilisé. Une instance FCI peut participer à un groupe de disponibilité sous la forme d’une instance hébergeant un réplica principal ou secondaire.

La liste ci-dessous souligne les différences entre les instances FCI sur Windows Server et Linux :

* Sur Windows Server, une instance FCI fait partie du processus d’installation. Une instance FCI sur Linux est configurée après l’installation de SQL Server.
* Linux prend uniquement en charge une seule installation de SQL Server par hôte, toutes les instances FCI représentent donc l’instance par défaut. Windows Server prend en charge jusqu'à 25 instances FCI par cluster WSFC.
* Le nom commun utilisé par les instances FCI dans Linux est défini dans le système DNS, et doit être identique à la ressource créée pour l’instance FCI.

#### <a name="log-shipping"></a>Copie des journaux de transaction
Si les objectifs de point de récupération et de délai de récupération sont plus flexibles, ou que les bases de données ne sont pas considérées comme très critiques, la copie des journaux de transaction est une autre fonctionnalité de disponibilité qui a fait ses preuves dans SQL Server. Basé sur les sauvegardes natives de SQL Server, le processus de copie des journaux de transaction génère automatiquement des sauvegardes de fichier journal, les copie dans une ou plusieurs instances appelées secours semi-automatique, et applique automatiquement les sauvegardes du fichier journal à ce secours. La copie des journaux de transaction utilise les travaux de SQL Server Agent pour automatiser le processus de sauvegarde, de copie et d’application des sauvegardes du fichier journal.

![Copie des journaux de transactions](media/sql-server-ha-story/image5.png)
 
Le principal avantage de l’utilisation de la copie des journaux de transaction dans une capacité est sans doute qu’elle prend en compte l’erreur humaine. L’application des journaux de transactions peut être différée. Par conséquent, si un utilisateur envoie une commande de type UPDATE sans clause WHERE, le serveur de secours peut ne pas avoir pris en compte le changement et vous pouvez donc l’utiliser pendant que vous réparez le système principal. Bien que la copie des journaux de transaction soit facile à configurer, le basculement du réplica principal sur un secours semi-automatique, appelé changement de rôle, est toujours manuel. Un changement de rôle est lancé via Transact-SQL et, tout comme pour un groupe de disponibilité, tous les objets qui ne sont pas capturés dans le journal des transactions doivent être synchronisés manuellement. Par ailleurs, la copie des journaux de transaction doit être configurée pour chaque base de données, tandis qu’un seul groupe de disponibilité peut contenir plusieurs bases de données. Contrairement au groupe de disponibilité ou à l’instance FCI, la copie des journaux de transaction ne récupère rien pour le changement de rôle. Les applications doivent être en mesure de le gérer. Des techniques comme l’alias DNS (CNAME) peuvent être utilisées, mais il existe des avantages et des inconvénients, par exemple, le temps que prend le système DNS pour l’actualisation après le basculement.

## <a name="disaster-recovery"></a>Récupération d'urgence

Quand votre emplacement de disponibilité principal subit un événement catastrophique comme un tremblement de terre ou une inondation, l’entreprise doit être préparée à mettre ses systèmes en ligne ailleurs. Cette section décrit comment les fonctionnalités de disponibilité de SQL Server peuvent aider à assurer la continuité de l’activité.

### <a name="always-on-availability-groups"></a>Groupes de disponibilité Always On

L’un des avantages des groupes de disponibilité est que la haute disponibilité et la récupération d’urgence peuvent être configurées à l’aide d’une seule fonctionnalité. S’il n’est pas nécessaire de garantir la haute disponibilité du stockage partagé, il est bien plus facile d’avoir des réplicas locaux dans un seul centre de données pour la haute disponibilité et des réplicas distants dans d’autres centres de données pour la récupération d’urgence, chacun avec un stockage séparé. La redondance entraîne en contrepartie des copies supplémentaires de la base de données. L’exemple ci-dessous illustre un groupe de disponibilité sur plusieurs centres de données. Un seul réplica principal est responsable de la synchronisation de tous les réplicas secondaires.

![Groupe de disponibilité](media/sql-server-ha-story/image6.png)
 
À l’exception des groupes de disponibilité avec un type de cluster Aucun, les groupes de disponibilité nécessitent que tous les réplicas fassent partie du même cluster sous-jacent, qu’il s’agisse d’un cluster WSFC ou de Pacemaker. Cela signifie que, dans l’illustration ci-dessus, le cluster WSFC est étiré sur deux centres de données différents, ce qui augmente la complexité, quelle que soit la plateforme (Windows Server ou Linux). Le fait d’étirer les clusters sur la distance ajoute de la complexité. À compter de SQL Server 2016, un groupe de disponibilité distribué permet à un groupe de disponibilité de configurer des groupes de disponibilité sur des clusters différents. Ceci permet de découpler l’exigence selon laquelle tous les nœuds doivent participer au même cluster et facilite donc la configuration de la récupération d’urgence. Pour plus d’informations sur les groupes de disponibilité distribués, consultez [Groupes de disponibilité distribués](../database-engine/availability-groups/windows/distributed-availability-groups.md).

![Groupe de disponibilité distribué](media/sql-server-ha-story/image11.png)
 
### <a name="always-on-failover-cluster-instances"></a>Instances de cluster de basculement Always On

Les instances FCI peuvent être utilisées pour la récupération d’urgence. Tout comme avec un groupe de disponibilité normal, le mécanisme de cluster sous-jacent doit également être étendu à tous les emplacements, ce qui augmente la complexité. Il existe un élément supplémentaire à prendre en compte pour les instances FCI : le stockage partagé. Les mêmes disques doivent être disponibles dans les sites principal et secondaires. Une méthode externe (comme les fonctionnalités fournies par le fournisseur de stockage au niveau de la couche matérielle ou le réplica de stockage dans Windows Server) est donc nécessaire pour vérifier que les disques utilisés par l’instance FCI existent ailleurs. 

![Instance FCI Always On](media/sql-server-ha-story/image8.png)
 
### <a name="log-shipping"></a>Copie des journaux de transaction
La copie des journaux de transaction est l’une des méthodes les plus anciennes pour la récupération d’urgence des bases de données SQL Server. La copie des journaux de transaction est souvent utilisée conjointement avec les groupes de disponibilité et les instances FCI pour assurer une récupération d’urgence économique et plus simple par rapport à d’autres options plus complexes en raison de l’environnement, des compétences administratives ou du budget. De la même façon que la haute disponibilité pour la copie des journaux de transaction, de nombreux environnements diffèrent le chargement d’un journal de transactions pour prendre en compte l’erreur humaine.

## <a name="migrations-and-upgrades"></a><a name = "Migrations"></a> Migrations et mises à niveau

Qu’il s’agisse de déployer de nouvelles instances ou d’en mettre à niveau des anciennes, une entreprise ne peut pas tolérer d’interruption de longue durée. Cette section décrit comment les fonctionnalités de disponibilité de SQL Server peuvent servir à réduire le temps d’arrêt quand un changement d’architecture, un basculement de serveur, un changement de plateforme (par exemple, de Windows Server à Linux, ou inversement) ou une mise à jour corrective est planifié.

> [!NOTE]
> D’autres méthodes, comme l’utilisation de sauvegardes et leur restauration ailleurs, peuvent également servir pour les migrations et les mises à niveau. Elles ne sont pas abordées dans cet article. 

### <a name="always-on-availability-groups"></a>Groupes de disponibilité Always On

Une instance existante qui contient un ou plusieurs groupes de disponibilité peut être mise à niveau sur place vers SQL Server 2017. Cette opération nécessite un certain temps d’arrêt, mais qui peut être réduit avec une planification appropriée. 

Si l’objectif est de migrer vers de nouveaux serveurs et de ne pas changer la configuration (y compris le système d’exploitation ou la version de SQL Server), ces serveurs peuvent être ajoutés sous forme de nœuds au cluster sous-jacent existant et ajoutés au groupe de disponibilité. Une fois que le ou les réplicas sont dans l’état souhaité, vous pouvez basculer manuellement sur un nouveau serveur, puis l’ancien peut être supprimé du groupe de disponibilité et désactivé. 

Les groupes de disponibilité distribués permettent eux aussi de migrer vers une nouvelle configuration ou de mettre à niveau SQL Server. Comme un groupe de disponibilité distribué prend en charge différents groupes de disponibilité sous-jacents sur différentes architectures, vous pouvez par exemple passer de SQL Server 2016 exécuté sur Windows Server 2012 R2 à SQL Server 2017 exécuté sur Windows Server 2016. 

![Groupe de disponibilité distribué](media/sql-server-ha-story/image10.png)

Enfin, les groupes de disponibilité avec un type de cluster Aucun peuvent également être utilisés pour la migration ou la mise à niveau. Comme vous ne pouvez pas mélanger et mettre en correspondance différents types de cluster dans une configuration standard de groupe de disponibilité, tous les réplicas doivent être de type Aucun. Un groupe de disponibilité distribué peut être utilisé pour englober des groupes de disponibilité configurés avec différents types de cluster. Cette méthode est également prise en charge sur différentes plateformes de système d’exploitation.

Toutes les variantes de groupes de disponibilité pour les migrations et les mises à niveau permettent d’échelonner dans le temps la partie la plus chronophage du travail : la synchronisation des données. Au moment de lancer le basculement sur la nouvelle configuration, le transfert se traduit par une courte interruption au lieu d’une longue période de temps d’arrêt pendant laquelle toutes les opérations, y compris la synchronisation des données, doivent être effectuées. 

Les groupes de disponibilité peuvent réduire au maximum le temps d’arrêt d’une mise à jour corrective du système d’exploitation sous-jacent en basculant manuellement le réplica principal sur un réplica secondaire pendant l’opération. En ce qui concerne le système d’exploitation, cette solution est plus courante sur Windows Server, car souvent, mais pas toujours, la maintenance du système d’exploitation sous-jacent nécessite un redémarrage. La mise à jour corrective de Linux nécessite parfois un redémarrage, mais cela est rare. 

La [mise à jour corrective d’instances de SQL Server faisant partie d’un groupe de disponibilité](../database-engine/availability-groups/windows/upgrading-always-on-availability-group-replica-instances.md) peut également réduire le temps d’arrêt selon la complexité de l’architecture du groupe de disponibilité. Pour appliquer une mise à jour corrective à des serveurs faisant partie d’un groupe de disponibilité, il faut d’abord l’appliquer à un réplica secondaire. Une fois que le nombre approprié de réplicas est corrigé, le réplica principal est manuellement basculé sur un autre nœud pour effectuer la mise à niveau. Tous les réplicas secondaires restants à ce stade peuvent être mis à niveau à leur tour. 

### <a name="always-on-failover-cluster-instances"></a>Instances de cluster de basculement Always On

Les instances FCI ne sont pas adaptées pour une migration ou une mise à niveau traditionnelle. Un groupe de disponibilité ou la copie des journaux de transaction doit être configuré pour les bases de données de l’instance FCI et tous les autres objets pris en compte. Toutefois, les instances FCI sur Windows Server restent une option courante quand les serveurs Windows Server sous-jacents doivent être corrigés. Vous pouvez lancer un basculement manuel qui entraîne une courte interruption au lieu d’une indisponibilité totale de l’instance tout au long de la mise à jour de Windows Server.
Une instance FCI peut être mise à niveau sur place pour SQL Server 2017. Pour plus d’informations, consultez [Mettre à niveau une instance de cluster de basculement SQL Server](../sql-server/failover-clusters/windows/upgrade-a-sql-server-failover-cluster-instance.md).

### <a name="log-shipping"></a>Copie des journaux de transaction

La copie des journaux de transaction reste une option courante pour migrer et mettre à niveau des bases de données. Comme pour les groupes de disponibilité, mais cette fois en utilisant le journal des transactions comme méthode de synchronisation, la propagation des données peut être démarrée un certain temps avant le basculement de serveur. Au moment du basculement, une fois que tout le trafic est interrompu au niveau de la source, un journal de transactions final doit être capturé, copié et appliqué à la nouvelle configuration. À ce stade, la base de données peut être mise en ligne. La copie des journaux de transaction tolère souvent mieux les réseaux plus lents et, même si le basculement peut être légèrement plus long qu’un basculement à l’aide d’un groupe de disponibilité ou d’un groupe de disponibilité distribué, il se mesure généralement en minutes et non en heures, jours ou semaines.

Tout comme pour les groupes de disponibilité, la copie des journaux de transaction vous permet de basculer sur un autre serveur en cas de mise à jour corrective.

### <a name="other-sql-server-deployment-methods-and-availability"></a>Autres méthodes de déploiement de SQL Server et disponibilité

Il existe deux autres méthodes de déploiement de SQL Server sur Linux : les conteneurs et l’utilisation d’Azure (ou d’un autre fournisseur de cloud public). Le besoin général de disponibilité telle qu’elle est présentée dans cet article existe indépendamment de la manière dont SQL Server est déployé. Ces deux méthodes ont des éléments particuliers à prendre en compte en ce qui concerne la haute disponibilité de SQL Server.

Les [conteneurs utilisant Docker](../linux/quickstart-install-connect-docker.md) sont une nouvelle façon de déployer SQL Server, à la fois pour Windows Server et Linux. Un conteneur est une image complète de SQL Server prête à exécuter. Toutefois, il n’existe actuellement aucune prise en charge native du clustering et, par conséquent, de la haute disponibilité et de la récupération d’urgence. Actuellement, les options qui permettent de rendre disponibles les bases de données SQL Server à l’aide de conteneurs sont la copie des journaux de transaction et les opérations de sauvegarde et restauration. Même s’il est possible de configurer un groupe de disponibilité avec un type de cluster Aucun, comme indiqué plus haut, cette configuration n’est pas vraiment une configuration de disponibilité. Microsoft recherche des moyens de permettre aux groupes de disponibilité ou aux instances FCI d’utiliser des conteneurs. 

Aujourd’hui, si vous utilisez un conteneur et que ce dernier est perdu, selon la plateforme sur laquelle il est déployé, il peut être redéployé et attaché au stockage partagé qui était utilisé. Une partie de ce mécanisme est fournie par l’orchestrateur de conteneurs. Malgré une certaine résilience, la récupération de la base de données est associée à un certain temps d’arrêt et la disponibilité n’est pas aussi haute qu’avec un groupe de disponibilité ou une instance FCI. 

Les machines virtuelles IaaS Linux peuvent être déployées en installant SQL Server à l’aide d’Azure. De la même façon qu’une installation locale, l’installation prise en charge nécessite le mécanisme STONITH (Shoot The Other Node In The Head), qui est externe à Pacemaker. STONITH est fourni en isolant les agents de disponibilité. Certaines distributions les incluent dans la plateforme, d’autres font appel à des fournisseurs de matériel et de logiciels externes. Vérifiez les formes de STONITH qui sont fournies par votre distribution Linux afin qu’une solution prise en charge puisse être déployée dans le cloud public.

## <a name="cross-platform-and-linux-distribution-interoperability"></a>Scénarios multiplateformes et d’interopérabilité entre distributions Linux

SQL Server étant maintenant pris en charge sur Windows Server et Linux, cette section décrit des scénarios de collaboration entre ces plateformes en matière de disponibilité et à d’autres fins, et aborde les solutions pouvant incorporer plusieurs distributions Linux.

Avant d’aborder les scénarios multiplateformes et d’interopérabilité, vous devez tenir compte des faits suivants :

* Il n’existe pas de scénario où un groupe de disponibilité/une instance FCI basé sur un cluster WSFC fonctionne directement avec un groupe de disponibilité/une instance FCI basé sur Linux. Un cluster WSFC ne peut pas être étendu par un nœud Pacemaker et inversement. 
* Le mélange des distributions Linux n’est pas pris en charge avec des instances FCI ou un groupe de disponibilité dont le type de cluster est Externe. Tous les réplicas de groupe de disponibilité dans ce scénario doivent être configurés avec la même distribution Linux et la même version. Les deux méthodes prises en charge qui permettent à SQL Server de fonctionner sur les deux plateformes ou sur plusieurs distributions de Linux sont les groupes de disponibilité et la copie des journaux de transaction.

## <a name="distributed-availability-groups"></a>Groupes de disponibilité distribués 

Les groupes de disponibilité distribués sont conçus pour englober les configurations de groupe de disponibilité, que les deux clusters sous-jacents des groupes de disponibilité soient deux clusters WSFC distincts, des distributions Linux ou un cluster WSFC et une distribution Linux. Le groupe de disponibilité distribué est la méthode principale pour une solution multiplateforme. Un groupe de disponibilité distribué constitue également la solution principale pour les migrations comme la conversion d’une infrastructure SQL Server basée sur Windows Server en infrastructure basée sur Linux si tel est le souhait de votre entreprise. Comme indiqué ci-dessus, les groupes de disponibilité et notamment les groupes de disponibilité distribués réduisent le temps d’indisponibilité d’une application. Voici un exemple de groupe de disponibilité distribué qui englobe un cluster WSFC et Pacemaker.

![Groupe de disponibilité distribué](media/sql-server-ha-story/image9.png)
 
Si un groupe de disponibilité est configuré avec un type de cluster Aucun, il peut s’étendre sur Windows Server et Linux, ainsi que sur plusieurs distributions Linux. Comme cette configuration n’est pas vraiment une configuration de haute disponibilité, elle ne doit pas être utilisée pour les déploiements critiques, mais plutôt dans des scénarios de migration/mise à jour ou d’échelle lecture.

## <a name="log-shipping"></a>Copie des journaux de transaction

La copie des journaux de transaction est uniquement basée sur la sauvegarde et la restauration, et il n’existe aucune différence entre les bases de données, les structures de fichiers, etc., entre SQL Server sur Windows Server et SQL Server sur Linux. Par conséquent, la copie des journaux de transaction peut être configurée entre des installations SQL Server Windows Server et Linux ainsi qu’entre des distributions de Linux. Rien d’autre ne change. Le seul inconvénient est que la copie des journaux de transaction, comme les groupes de disponibilité, ne peut pas fonctionner quand la source utilise une version majeure de SQL Server supérieure à celle de la cible. 

## <a name="read-scale"></a><a name = "ReadScaleOut"></a> Échelle lecture

Depuis leur introduction dans SQL Server 2012, les réplicas secondaires peuvent être utilisés pour les requêtes en lecture seule. Il existe deux manières de le faire avec un groupe de disponibilité : en autorisant un accès direct au réplica secondaire et en [configurant un routage en lecture seule](../database-engine/availability-groups/windows/configure-read-only-routing-for-an-availability-group-sql-server.md) qui nécessite l’utilisation de l’écouteur.  SQL Server 2016 a introduit la possibilité d’équilibrer la charge des connexions en lecture seule via l’écouteur à l’aide d’un algorithme de type tourniquet (Round Robin), ce qui permet aux demandes en lecture seule d’être réparties sur tous les réplicas accessibles en lecture. 

> [!NOTE]
> La fonctionnalité des réplicas secondaires accessibles en lecture est uniquement disponible dans l’édition Entreprise, et chaque instance qui héberge un réplica accessible en lecture doit disposer d’une licence SQL Server.

La possibilité de mettre à plus haute échelle des copies accessibles en lecture d’une base de données via les groupes de disponibilité a été introduite avec les groupes de disponibilité distribués dans SQL Server 2016. Cela permet aux entreprises d’avoir des copies en lecture seule de la base de données non seulement localement, mais aussi au niveau régional et mondial avec un minimum de configuration, et de réduire le trafic réseau et la latence en exécutant les requêtes localement. Chaque réplica principal d’un groupe de disponibilité peut amorcer deux autres groupes de disponibilité, même s’il ne s’agit pas d’une copie entièrement accessible en lecture/écriture, de sorte que chaque groupe de disponibilité distribué peut prendre en charge jusqu'à 27 copies des données accessibles en lecture. 

![Groupe de disponibilité distribué](media/sql-server-ha-story/image11.png)

À partir de SQL Server 2017, il est possible de créer pratiquement en temps réel une solution en lecture seule avec des groupes de disponibilité configurés avec un type de cluster Aucun. Si l’objectif est d’utiliser des groupes de disponibilité pour des réplicas secondaires accessibles en lecture et non pour la disponibilité, cette opération est plus simple que l’utilisation d’un cluster WSFC ou de Pacemaker, et donne au groupe de disponibilité l’avantage de l’accessibilité en lecture dans une méthode de déploiement plus simple. 

Le seul grand inconvénient est qu’en raison de l’absence de cluster sous-jacent avec un type de cluster Aucun, la configuration d’un routage en lecture seule est un peu différente. En ce qui concerne SQL Server, un écouteur est toujours nécessaire pour router les demandes, même en cas d’absence de cluster. Au lieu de configurer un écouteur traditionnel, vous utilisez l’adresse IP ou le nom du réplica principal. Le réplica principal est ensuite utilisé pour router les demandes en lecture seule.

Un secours semi-automatique de copie des journaux de transaction peut techniquement être configuré pour l’accessibilité en lecture en restaurant la base de données WITH STANDBY. Toutefois, parce que les journaux de transaction nécessitent l’utilisation exclusive de la base de données pour la restauration, les utilisateurs ne peuvent pas accéder à la base de données pendant l’opération. De ce fait, la copie des journaux de transaction est une solution moins idéale, en particulier si vous avez besoin des données quasiment en temps réel. 

Notez que dans tous les scénarios de mise à échelle lecture avec les groupes de disponibilité, contrairement à la réplication transactionnelle où les données ne sont pas en ligne, chaque réplica secondaire n’est pas dans un état où des index uniques peuvent être appliqués, le réplica est une copie exacte du principal. Cela signifie que si un index est nécessaire pour créer des rapports ou que les données doivent être manipulées, l’opération doit être effectuée sur la ou les bases de données du réplica principal. Si vous avez besoin de cette flexibilité, la réplication est une meilleure solution pour les données accessibles en lecture.

## <a name="summary"></a>Résumé

Les instances et les bases de données de SQL Server 2017 peuvent devenir hautement disponibles avec les mêmes fonctionnalités sur Windows Server et Linux. En plus des scénarios de disponibilité standard de haute disponibilité et de récupération d’urgence locales, le temps d’arrêt associé aux mises à niveau et aux migrations peut être réduit grâce aux fonctionnalités de disponibilité de SQL Server. Les groupes de disponibilité peuvent également fournir des copies supplémentaires d’une base de données dans le cadre de la même architecture pour effectuer un scale-out des copies accessibles en lecture. Qu’il s’agisse de déployer une nouvelle solution à l’aide de SQL Server 2017 ou d’effectuer une mise à niveau, SQL Server 2017 offre la disponibilité et la fiabilité dont vous avez besoin.
 
[SimpleAG]:media\sql-server-ha-story\image1.png
[SSMSAGOptions]:media\sql-server-ha-story\image2.png
[BasicFCI]:media\sql-server-ha-story\image3.png
[PostFailoverFCI]:media\sql-server-ha-story\image4.png
[LogShipping]:media\sql-server-ha-story\image5.png
[AG]:media\sql-server-ha-story\image6.png
[DAG]:media\sql-server-ha-story\image7.png
[AlwaysOnFCI]:media\sql-server-ha-story\image8.png
[BasicDAG]:media\sql-server-ha-story\image9.png
[image10]:media\sql-server-ha-story\image10.png
[DAG]:media\sql-server-ha-story\image11.png