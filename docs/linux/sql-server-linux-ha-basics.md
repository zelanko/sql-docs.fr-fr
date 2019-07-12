---
title: Principes fondamentaux de disponibilité de SQL Server pour les déploiements de Linux
description: ''
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
manager: jroth
ms.date: 11/27/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: 203fad6aa3c39d57446738b9c74631fe114c609e
ms.sourcegitcommit: 93d1566b9fe0c092c9f0f8c84435b0eede07019f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67833563"
---
# <a name="sql-server-availability-basics-for-linux-deployments"></a>Principes fondamentaux de disponibilité de SQL Server pour les déploiements de Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

En commençant par [!INCLUDE[sssql17-md](../includes/sssql17-md.md)], [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] est pris en charge sur Linux et Windows. Comme basée sur Windows [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] déploiements, [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] bases de données et les instances doivent être hautement disponible sous Linux. Cet article couvre les aspects techniques de planification et de déploiement à haute disponibilité basés sur Linux [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] bases de données et instances, ainsi que les différences à partir d’installations basées sur Windows. Étant donné que [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] peuvent être nouveaux pour les professionnels de Linux et Linux peuvent ne pas pour [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] professionnels, l’article parfois présente les concepts qui peuvent être familier à certaines et inconnues à d’autres personnes.

## <a name="includessnoversion-mdincludesssnoversion-mdmd-availability-options-for-linux-deployments"></a>[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] options de disponibilité pour les déploiements de Linux
Outre la sauvegarde et de restauration, les mêmes trois fonctionnalités de disponibilité sont disponibles sur Linux que pour les déploiements basés sur Windows :
-   Groupes de disponibilité Always On (groupes de disponibilité)
-   Instances de Cluster de basculement (fci) Always On
-   [Copie des journaux de transaction](sql-server-linux-use-log-shipping.md)

Sur Windows, les instances fci nécessitent toujours un cluster de basculement Windows Server (WSFC) sous-jacent. Selon le scénario de déploiement, un groupe de disponibilité nécessite généralement un cluster WSFC sous-jacent, avec l’exception en cours de la nouvelle variante dans aucun [!INCLUDE[sssql17-md](../includes/sssql17-md.md)]. Un cluster WSFC n’existe pas dans Linux. Clustering d’implémentation dans Linux est abordé dans la section [Pacemaker pour les groupes de disponibilité AlwaysOn et le basculement de cluster instances sur Linux](#pacemaker-for-always-on-availability-groups-and-failover-cluster-instances-on-linux).

## <a name="a-quick-linux-primer"></a>Notions fondamentales de Linux
Bien que certaines installations Linux peuvent être installées avec une interface, la plupart ne sont pas, ce qui signifie que presque tous les éléments au niveau de la couche de système d’exploitation sont effectuée via la ligne de commande. Le terme courant utilisé pour cette ligne de commande dans le monde de Linux est un *interpréteur de commandes bash*.

Sous Linux, de nombreuses commandes doivent être exécutées avec des privilèges élevés, tout comme vous avez besoin de beaucoup de choses à faire dans Windows Server en tant qu’administrateur. Il existe deux méthodes principales pour s’exécuter avec des privilèges élevés :
1. Exécuter dans le contexte de l’utilisateur approprié. Pour basculer vers un autre utilisateur, utilisez la commande `su`. Si `su` est exécutée sur son propre sans un nom d’utilisateur, tant que vous connaissez le mot de passe, vous pourrez désormais dans un interpréteur de commandes en tant que *racine*.
   
2. Les plus courants et sécurité réfléchie pour exécuter des opérations consiste à utiliser `sudo` avant d’exécuter quoi que ce soit. La plupart des exemples dans cet article utilisent `sudo`.

Certaines commandes courantes, chacun d'entre eux ont différents commutateurs et options qui peuvent être examinées en ligne :
-   `cd` -modifier le répertoire
-   `chmod` -modifier les autorisations d’un fichier ou un répertoire
-   `chown` -modifier la propriété d’un fichier ou répertoire
-   `ls` -afficher le contenu d’un répertoire
-   `mkdir` -créer un dossier (répertoire) sur un lecteur
-   `mv` -déplacer un fichier à partir d’un emplacement vers un autre
-   `ps` -afficher tous les processus de travail
-   `rm` -supprimer un fichier local sur un serveur
-   `rmdir` -supprimer un dossier (répertoire)
-   `systemctl` -Démarrer, arrêter ou activer les services
-   Commandes de l’éditeur de texte. Sur Linux, il existe différentes options de l’éditeur de texte, telles que vi et emacs.

## <a name="common-tasks-for-availability-configurations-of-includessnoversion-mdincludesssnoversion-mdmd-on-linux"></a>Tâches courantes pour les configurations de disponibilité de [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] sur Linux
Cette section présente les tâches qui sont communes à tous les basés sur Linux [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] déploiements.

### <a name="ensure-that-files-can-be-copied"></a>Assurez-vous que les fichiers peuvent être copiés
Copie des fichiers d’un serveur vers un autre est une tâche que toute personne utilisant [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] sur Linux doit être en mesure d’effectuer. Cette tâche est très importante pour les configurations de groupe de disponibilité.

Éléments tels que les problèmes d’autorisation peuvent exister sur Linux, ainsi que sur les installations basées sur Windows. Toutefois, les personnes familières avec la copie de serveur à serveur sur Windows peut-être pas familiarisés avec le fonctionnement sur Linux. Une méthode courante consiste à utiliser l’utilitaire de ligne de commande `scp`, ce qui signifie copie sécurisée. Dans les coulisses, `scp` utilise OpenSSH. SSH est l’acronyme shell sécurisé. Selon la distribution Linux, OpenSSH lui-même ne peut pas être installé. Si elle n’est pas le cas, OpenSSH doit être installé en premier. Pour plus d’informations sur la configuration d’OpenSSH, consultez les informations sur les liens suivants pour chaque distribution :
-   [Red Hat Enterprise Linux (RHEL)](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/deployment_guide/ch-openssh)
-   [SUSE Linux Enterprise Server (SLES)](https://en.opensuse.org/SDB:Configure_openSSH)
-   [Ubuntu](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

Lorsque vous utilisez `scp`, vous devez fournir les informations d’identification du serveur si elle n’est pas la source ou la destination. Par exemple, à l’aide de

```bash
scp MyAGCert.cer username@servername:/folder/subfolder
```

copie le fichier MyAGCert.cer dans le dossier spécifié sur l’autre serveur. Notez que vous devez disposer des autorisations - et, éventuellement, la propriété - du fichier à copier, donc `chown` serez peut-être amené à être utilisées avant la copie. De même, du côté réception, l’utilisateur a besoin d’accéder pour manipuler le fichier. Par exemple, pour restaurer ce fichier de certificat, le `mssql` utilisateur doit être en mesure d’y accéder.

Samba, qui est la variante Linux de bloc de message serveur (SMB), peut également servir à créer des partages accédés par les chemins d’accès UNC tel que `\\SERVERNAME\SHARE`. Pour plus d’informations sur la configuration Samba, consultez les informations sur les liens suivants pour chaque distribution :
-   [RHEL](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Managing_Confined_Services/chap-Managing_Confined_Services-Samba.html)
-   [SLES](https://www.suse.com/documentation/sles11/book_sle_admin/data/cha_samba.html)
-   [Ubuntu](https://help.ubuntu.com/community/Samba)

Les partages SMB basée sur Windows peuvent également être utilisés ; Partages SMB n’êtes pas obligé d’être basé sur Linux, tant que la portion cliente de Samba est correctement configurée sur le serveur Linux qui héberge [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] et le partage a l’accès approprié. Pour ceux dans un environnement mixte, il s’agit d’une façon de tirer parti de l’infrastructure existante pour basés sur Linux [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] déploiements.

Un élément important est que la version de Samba déployé doit être conforme à SMB 3.0. Lorsque la prise en charge SMB a été ajoutée dans [!INCLUDE[sssql11-md](../includes/sssql11-md.md)], il requis tous les partages de la prise en charge SMB 3.0. Si vous utilisez Samba pour le partage et le pas de Windows Server, le partage de Samba doit être à l’aide de Samba 4.0 ou version ultérieure et dans l’idéal, 4.3 ou version ultérieure, qui prend en charge SMB 3.1.1. Est une bonne source d’informations sur SMB et Linux [SMB3 dans Samba](https://events.linuxfoundation.org/sites/events/files/slides/smb3-in-samba.pr__0.pdf).

Enfin, à l’aide d’un partage NFS (system) de fichiers réseau est une option. À l’aide de NFS n’est pas une option sur les déploiements Windows des [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]et peut être utilisé uniquement pour les déploiements basés sur Linux.

### <a name="configure-the-firewall"></a>Configurer le pare-feu
Comme pour Windows, les distributions Linux présentent un pare-feu intégré. Si votre entreprise utilise un pare-feu externe pour les serveurs, la désactivation du pare-feu dans Linux peut être acceptable. Toutefois, quel que soit l’endroit où le pare-feu est activé, les ports doivent être ouverts. Le tableau suivant décrit les ports courants, requis pour hautement disponible [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] déploiements sur Linux.

| Numéro de port | type     | Description                                                                                                                 |
|-------------|----------|-----------------------------------------------------------------------------------------------------------------------------|
| 111         | TCP/UDP  | NFS - `rpcbind/sunrpc`                                                                                                    |
| 135         | TCP      | Samba (si utilisé) - le mappeur de Point de terminaison                                                                                          |
| 137         | UDP      | Samba (si utilisé) - Service de nom NetBIOS                                                                                      |
| 138         | UDP      | Samba (si utilisé) - datagramme NetBIOS                                                                                          |
| 139         | TCP      | Samba (si utilisé) - NetBIOS Session                                                                                           |
| 445         | TCP      | Samba (si utilisé) - SMB sur TCP                                                                                              |
| 1433        | TCP      | [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] -port ; par défaut Si vous le souhaitez, peut changer à `mssql-conf set network.tcpport <portnumber>`                       |
| 2049        | TCP, UDP | NFS (si utilisé)                                                                                                               |
| 2224        | TCP      | Pacemaker - utilisé par `pcsd`                                                                                                |
| 3121        | TCP      | Pacemaker - requis s’il existe des nœuds distants Pacemaker                                                                    |
| 3260        | TCP      | iSCSI Initiator (si utilisé) - peut être modifié dans `/etc/iscsi/iscsid.config` (RHEL), mais doit correspondre le port de la cible iSCSI |
| 5022        | TCP      | [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] -par défaut le port utilisé pour un point de terminaison du groupe de disponibilité ; peut être modifié lors de la création du point de terminaison                                |
| 5403        | TCP      | Pacemaker                                                                                                                   |
| 5404        | UDP      | Pacemaker - requis par Corosync si vous utilisez la multidiffusion UDP                                                                     |
| 5405        | UDP      | Pacemaker - requis par Corosync                                                                                            |
| 21064       | TCP      | Pacemaker - requise par les ressources à l’aide de DLM                                                                                 |
| Variable    | TCP      | Port du point de terminaison de groupe de disponibilité ; valeur par défaut est 5022                                                                                           |
| Variable    | TCP      | NFS - port pour `LOCKD_TCPPORT` (trouvé dans `/etc/sysconfig/nfs` sur RHEL)                                              |
| Variable    | UDP      | NFS - port pour `LOCKD_UDPPORT` (trouvé dans `/etc/sysconfig/nfs` sur RHEL)                                              |
| Variable    | TCP/UDP  | NFS - port pour `MOUNTD_PORT` (trouvé dans `/etc/sysconfig/nfs` sur RHEL)                                                |
| Variable    | TCP/UDP  | NFS - port pour `STATD_PORT` (trouvé dans `/etc/sysconfig/nfs` sur RHEL)                                                 |

Pour des ports supplémentaires qui peuvent être utilisés par Samba, consultez [l’utilisation du Port Samba](https://wiki.samba.org/index.php/Samba_Port_Usage).

À l’inverse, le nom du service sous Linux peut également être ajouté en tant qu’exception au lieu du port ; par exemple, `high-availability` pour Pacemaker. Consultez votre distribution pour les noms s’il s’agit la direction que vous souhaitez poursuivre. Par exemple, la commande à ajouter dans Pacemaker est sur RHEL

```bash
sudo firewall-cmd --permanent --add-service=high-availability
```

**Documentation de pare-feu :**
-   [RHEL](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/high_availability_add-on_reference/s1-firewalls-haar)
-   [SLES](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html)

### <a name="install-includessnoversion-mdincludesssnoversion-mdmd-packages-for-availability"></a>Installer [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] packages pour la disponibilité
Sur un Windows [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] installation, certains composants sont installés même dans une installation du moteur de base, tandis que d’autres ne le sont pas. Sous Linux, uniquement le [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] moteur est installé dans le cadre du processus d’installation. Tout le reste est facultatif. Pour hautement disponible [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] instances sous Linux, les deux packages doivent être installés avec [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]: [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Agent (*mssql-server-agent*) et le package de haute disponibilité (HA) (*mssql-server-ha*). Bien que [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Agent est techniquement facultatif, il est [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]du Planificateur de tâches et est requis par l’envoi de journaux, afin de l’installation est recommandée. Sur les installations basées sur Windows, [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Agent n’est pas facultatif.

>[!NOTE]
>Pour les débutants en [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)], [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Agent est [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]du Planificateur de travaux intégrées. Il est une méthode courante pour les administrateurs de planifier des éléments tels que des sauvegardes et autres [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] maintenance. Contrairement à une installation Windows de [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] où [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Agent est un service complètement différent, sur Linux, [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Agent s’exécute dans le contexte de [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] lui-même.

Lorsque les groupes de disponibilité ou les instances fci sont configurés sur une configuration basée sur Windows, ils utilisent un cluster. Détection de cluster signifie que [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] a DLL un cluster WSFC connaît (sqagtres.dll et sqsrvres.dll pour les instances fci, hadrres.dll pour les groupes de disponibilité) de ressource spécifique et sont utilisés par le cluster WSFC pour vous assurer que le [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] fonctionnalités en cluster est, en cours d’exécution, et fonctionne correctement. Étant donné que le clustering est externe non seulement à [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] mais Linux proprement dit, Microsoft a dû coder l’équivalent d’une DLL de ressource pour les déploiements basés sur Linux le groupe de disponibilité et l’ICF. Il s’agit du *mssql-server-ha* du package, également connu sous le [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] agent de ressources pour Pacemaker. Pour installer le *mssql-server-ha* du package, consultez [installer les packages haute disponibilité et de l’Agent SQL Server](sql-server-linux-deploy-pacemaker-cluster.md#install-the-sql-server-ha-and-sql-server-agent-packages).

Les autres packages facultatifs pour [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] sur Linux, [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] recherche en texte intégral (*mssql-server-fts*) et [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Integration Services (*mssql-server est*), ne sont pas requis pour la haute disponibilité, pour une instance FCI ou un groupe de disponibilité.

## <a name="pacemaker-for-always-on-availability-groups-and-failover-cluster-instances-on-linux"></a>Pacemaker pour les groupes de disponibilité AlwaysOn et les instances de cluster de basculement sur Linux
Précédente comme indiqué, le seul mécanisme de gestion de clusters pris en charge par Microsoft pour les groupes de disponibilité et les instances fci est Pacemaker avec Corosync. Cette section décrit les informations de base pour comprendre la solution, ainsi que comment planifier et déployer pour [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] configurations.

### <a name="ha-add-onextension-basics"></a>Principes fondamentaux de haute disponibilité complémentaires / l’extension
Toutes les distributions prises en charge actuellement expédier une haute disponibilité complémentaires-on/extension, qui est basée sur la pile de clustering de Pacemaker. Cette pile intègre deux composants clés : Pacemaker et Corosync. Tous les composants de la pile sont :
-   Pacemaker - le cœur de composant, qui effectue des opérations comme coordonnée entre les ordinateurs en cluster de clustering.
-   Corosync - une infrastructure et un ensemble d’API qui fournit des éléments tels que le quorum, la possibilité de redémarrage de l’échec de processus et ainsi de suite.
-   libQB - fournit des éléments tels que la journalisation.
-   Agent de ressource - fonctionnalité spécifique fournie afin qu’une application peut s’intégrer à Pacemaker.
-   Agent - Scripts/fonctionnalités qui vous permettre d’isoler les nœuds et les traiter si elles rencontrent des problèmes de la clôture.
    
> [!NOTE]
> La pile de cluster est communément appelé Pacemaker dans le monde de Linux.

Cette solution est quelque peu similaire à, mais de nombreuses façons différentes de déployer des configurations en cluster à l’aide de Windows. Dans Windows, la forme de la disponibilité de clustering, appelée un cluster de basculement Windows Server (WSFC), est intégrée dans le système d’exploitation et la fonctionnalité qui permet la création d’un cluster WSFC, le clustering de basculement, est désactivé par défaut. Dans Windows, groupes de disponibilité fci s’appuient sur un cluster WSFC et partager une intégration étroite en raison de la ressource spécifique DLL est fournie par [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]. Cette solution étroitement couplée est généralement possible, car il est tout à partir d’un seul fournisseur.

![](./media/sql-server-linux-ha-basics/image1.png)

Sur Linux, alors que chaque distribution pris en charge a Pacemaker disponible, chaque distribution peut personnaliser et disposent des versions et des implémentations légèrement différentes. Certaines des différences apparaîtront dans les instructions fournies dans cet article. La couche de clustering est open source, même s’il est livré avec les distributions, il n’est pas étroitement intégré dans la même façon un cluster WSFC sous Windows. C’est pourquoi Microsoft propose *mssql-server-ha*, de sorte que [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] et la pile de Pacemaker peut fermer pour fournir, mais pas exactement les mêmes fonctionnalités pour les groupes de disponibilité et les instances fci dans le cadre de Windows.

Pour obtenir une documentation complète sur Pacemaker, y compris une explication plus approfondie de ce que tout est avec les informations de référence complète, pour RHEL et SLES :
-   [RHEL](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/7/html/High_Availability_Add-On_Reference/ch-overview-HAAR.html)
-   [SLES](https://www.suse.com/documentation/sle_ha/book_sleha/data/book_sleha.html)

Ubuntu n’a pas un guide pour la disponibilité.

Pour plus d’informations sur l’ensemble de la pile, consultez également le fonctionnaire [page de documentation Pacemaker](https://clusterlabs.org/doc/) sur le site Clusterlabs.

### <a name="pacemaker-concepts-and-terminology"></a>Pacemaker concepts et terminologie
Cette section décrit les concepts et la terminologie liée à une implémentation de Pacemaker courants.

#### <a name="node"></a>Nœud
Un nœud est un serveur faisant partie du cluster. Un cluster Pacemaker prend nativement en charge jusqu'à 16 nœuds. Ce nombre peut être dépassé si Corosync n’est pas en cours d’exécution sur les nœuds supplémentaires, mais Corosync est requis pour [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]. Par conséquent, le nombre maximal de nœuds d’un cluster peut avoir pour toute [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]-configuration de base est 16 ; il correspond à la limite de Pacemaker et n’a rien à voir avec les limites maximales pour les groupes de disponibilité ou les instances fci imposées par [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]. 

#### <a name="resource"></a>Resource
Un cluster WSFC et un cluster Pacemaker présentent le concept d’une ressource. Une ressource est une fonctionnalité spécifique qui s’exécute dans le contexte du cluster, comme un disque ou une adresse IP. Par exemple, sous Pacemaker ICF et le groupe de disponibilité des ressources peuvent être créés. Ce n’est pas différent de ce qui se fait dans un cluster WSFC, où vous voyez un [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] ressource pour une FCI ou un groupe de disponibilité lors de la configuration d’un groupe de disponibilité, mais n’est pas exactement les mêmes en raison des différences sous-jacentes dans la manière dont [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] s’intègre à Pacemaker.

Pacemaker dispose des ressources standard et le clone. Ressources de clone sont ceux qui s’exécutent simultanément sur tous les nœuds. Un exemple serait une adresse IP qui s’exécute sur plusieurs nœuds pour des raisons d’équilibrage de charge. N’importe quelle ressource qui est créé pour les instances fci utilise une ressource standard, dans la mesure où un seul nœud peut héberger une instance FCI à tout moment donné.

Lorsqu’un groupe de disponibilité est créé, celui-ci nécessite un formulaire spécialisé d’une ressource de clone appelé une ressource plusieurs état. Alors qu’un groupe de disponibilité a uniquement un réplica principal, le groupe de disponibilité est en cours d’exécution sur tous les nœuds qu’il est configuré pour fonctionner sur et permet à des éléments tels que les accès en lecture seule. Comme il s’agit d’une utilisation « dynamique » du nœud, les ressources présentent le concept de deux états : master et subordonné. Pour plus d’informations, consultez [ressources plusieurs États : Ressources qui ont plusieurs modes](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Configuring_the_Red_Hat_High_Availability_Add-On_with_Pacemaker/s1-multistateresource-HAAR.html).

#### <a name="resource-groupssets"></a>Groupes de ressources/haute
Similaires aux rôles dans un cluster WSFC, un cluster Pacemaker a le concept d’un groupe de ressources. Un groupe de ressources (appelé un jeu dans SLES) est une collection de ressources qui fonctionneront ensemble et peut basculer d’un nœud vers un autre comme une seule unité. Groupes de ressources ne peut pas contenir les ressources qui sont configurées en tant que maître/esclave ; Par conséquent, ils ne peuvent pas être utilisés pour les groupes de disponibilité. Si un groupe de ressources peut être utilisé pour les instances fci, il n’est pas généralement une configuration recommandée.

#### <a name="constraints"></a>Contraintes
Clusters Wsfc ont des paramètres différents pour les ressources, ainsi que des éléments tels que les dépendances, qui indiquent le cluster WSFC d’une relation parent/enfant entre deux ressources différentes. Une dépendance est simplement une règle indiquant le cluster WSFC quelle ressource doit être en ligne tout d’abord.

Un cluster Pacemaker n’a pas le concept de dépendances, mais il existe des contraintes. Il existe trois types de contraintes : colocalisation, d’emplacement et de classement.
-   Une contrainte de colocalisation applique ou non deux ressources doivent être en cours d’exécution sur le même nœud.
-   Une contrainte d’emplacement indique le cluster Pacemaker où une ressource (ou non) s’exécuter.
-   Une contrainte de classement indique le cluster Pacemaker l’ordre dans lequel les ressources doivent commencer.

> [!NOTE]
> Contraintes de colocalisation ne sont pas requis pour les ressources dans un groupe de ressources, étant donné que tous ces sont considérés comme une seule unité.

#### <a name="quorum-fence-agents-and-stonith"></a>Quorum, les agents de délimitation et STONITH
Quorum sous Pacemaker est quelque peu similaire à un cluster WSFC dans son concept. L’objectif du mécanisme de quorum d’un cluster est pour vous assurer que le cluster reste en cours d’exécution. Un cluster WSFC et les modules complémentaires de haute disponibilité pour les distributions de Linux ont le concept de vote, où chaque nœud est comptabilisée dans quorum. Vous souhaitez une majorité des voix, sinon, dans le pire des cas, le cluster va être arrêté.

Contrairement à un cluster WSFC, il n’existe aucune ressource de témoin pour travailler avec le quorum. Comme un cluster WSFC, l’objectif est de limiter le nombre d’électeurs impairs. Configuration de quorum a différentes considérations pour les groupes de disponibilité que le cluster de basculement.

Clusters Wsfc surveiller l’état des nœuds participant et les gérer lorsqu’un problème survient. Les versions ultérieures de clusters Wsfc offrent des fonctionnalités telles que la mise en quarantaine d’un nœud qui est le dysfonctionnement ou non disponible (nœud n’est pas activé, la communication réseau est vers le bas, etc.). Sur le côté de Linux, ce type de fonctionnalité est fourni par un agent de délimitation. Le concept est parfois appelé délimitation. Toutefois, ces agents de délimitation sont généralement spécifiques au déploiement et souvent fournies par les fournisseurs de matériel et de certains fournisseurs de logiciels, tels que ceux qui fournissent des hyperviseurs. Par exemple, VMware fournit un agent d’isolation qui peut être utilisé pour les machines virtuelles Linux virtualisés à l’aide de vSphere.

Quorum clôtures ties dans un autre concept appelé STONITH et dépanner le nœud autres dans la tête. STONITH est nécessaire d’avoir un cluster Pacemaker pris en charge sur toutes les distributions Linux. Pour plus d’informations, consultez [clôtures dans un Cluster de disponibilité élevée de Red Hat](https://access.redhat.com/solutions/15575) (RHEL).

#### <a name="corosyncconf"></a>corosync.conf
Le `corosync.conf` fichier contient la configuration du cluster. Il se trouve dans `/etc/corosync`. Au cours des opérations quotidiennes normales, ce fichier doit avoir jamais à être modifié si le cluster est correctement configuré.

#### <a name="cluster-log-location"></a>Emplacement des journaux de cluster
Emplacements des journaux pour les clusters Pacemaker diffèrent selon la distribution.
-   RHEL et SLES- `/var/log/cluster/corosync.log`
-   Ubuntu - `/var/log/corosync/corosync.log`

Pour modifier l’emplacement de journalisation par défaut, modifiez `corosync.conf`.

## <a name="plan-pacemaker-clusters-for-includessnoversion-mdincludesssnoversion-mdmd"></a>Planifier des clusters Pacemaker pour [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]
Cette section décrit les points importants de planification pour un cluster Pacemaker.

### <a name="virtualizing-linux-based-pacemaker-clusters-for-includessnoversion-mdincludesssnoversion-mdmd"></a>Clusters de virtualisation Pacemaker basés sur Linux pour [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]
L’utilisation de machines virtuelles pour déployer basés sur Linux [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] déploiements pour les groupes de disponibilité et les instances fci est couverte par les mêmes règles que pour leurs équivalents basée sur Windows. Il existe un ensemble de règles pour la prise en charge de base virtualisé [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] fournies par Microsoft dans les déploiements [956893 de base de connaissances de support technique Microsoft](https://support.microsoft.com/help/956893/support-policy-for-microsoft-sql-server-products-that-are-running-in-a-hardware-virtualization-environment). Les hyperviseurs différents tels que Microsoft Hyper-V et VMware ESXi peuvent ont des variances différentes en plus de cela, en raison des différences dans les plateformes eux-mêmes.

Lorsqu’il s’agit de groupes de disponibilité et les instances fci sous virtualization, assurez-vous qu’anti-affinité est définie pour les nœuds d’un cluster Pacemaker donné. Lorsque configuré pour la haute disponibilité dans une configuration de groupe de disponibilité ou une instance FCI, les machines virtuelles hébergeant [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] ne doit jamais s’exécuter sur le même hyperviseur hôte. Par exemple, si une instance FCI à deux nœuds est déployée, il doit être *au moins* trois hôtes hyperviseur afin qu’il existe quelque part pour l’une des machines virtuelles hébergeant un nœud pour accéder en cas de défaillance de l’hôte, en particulier si vous utilisez des fonctionnalités telles que Live Migration ou vMotion.

Pour plus d’informations, consultez :
-   Documentation de Hyper-V - [à l’aide du Clustering invité pour la haute disponibilité](https://technet.microsoft.com/library/dn440540(v=ws.11).aspx)
-   Livre blanc (écrit pour les déploiements basés sur Windows, mais la plupart des concepts toujours appliquer) - [planification hautement disponible, les déploiements Server SQL stratégiques avec VMware vSphere](https://www.vmware.com/content/dam/digitalmarketing/vmware/en/pdf/solutions/vmware-vsphere-highly-available-mission-critical-sql-server-deployments.pdf)

>[!NOTE]
>RHEL avec un cluster Pacemaker avec STONITH n’est pas encore pris en charge par Hyper-V. Jusqu'à ce que qui est pris en charge, pour plus d’informations et mises à jour, consultez [des stratégies de prise en charge pour les Clusters à disponibilité élevée RHEL](https://access.redhat.com/articles/29440#3physical_host_mixing).

### <a name="networking"></a>Mise en réseau
Contrairement à un cluster WSFC, Pacemaker ne nécessite pas un nom dédié ou au moins une adresse IP dédiée pour le cluster Pacemaker lui-même. Groupes de disponibilité et les instances fci nécessitent des adresses IP (consultez la documentation pour chacun d’eux pour plus d’informations), mais pas les noms, car il n’existe aucune ressource de nom de réseau. SLES n’autorise pas la configuration d’une adresse IP à des fins administratives, mais il n’est pas obligatoire, comme illustré dans [créer le cluster Pacemaker](sql-server-linux-deploy-pacemaker-cluster.md#create).

Comme un cluster WSFC, Pacemaker préférez mise en réseau redondant, ce qui signifie que les cartes réseau distinctes (cartes réseau ou pNICs pour serveur physique) ayant des adresses IP individuelles. En termes de la configuration du cluster, chaque adresse IP aurait ce que l'on appelle sa propre anneau. Toutefois, comme avec les clusters Wsfc aujourd'hui, de nombreuses implémentations sont virtualisées ou dans le cloud public où il n’existe qu’un seul virtualisé carte d’interface réseau (carte réseau virtuelle) présenté au serveur. Si tous les pNICs et les cartes réseau virtuelles sont connectés au même commutateur physique ou virtuel, il n’étant aucune véritable redondance au niveau de la couche réseau, la configuration de plusieurs cartes réseau est un peu d’une illusion à la machine virtuelle. Redondance réseau est généralement générée dans l’hyperviseur pour les déploiements virtualisés et est sans aucun doute générée dans le cloud public.

Une différence avec plusieurs cartes réseau et Pacemaker par rapport à un cluster WSFC est que Pacemaker autorise plusieurs adresses IP sur le même sous-réseau, contrairement à un cluster WSFC. Pour plus d’informations sur plusieurs sous-réseaux et les clusters Linux, consultez l’article [configurer plusieurs sous-réseaux](sql-server-linux-configure-multiple-subnet.md).

### <a name="quorum-and-stonith"></a>Quorum et STONITH
Configuration de quorum et les spécifications sont liées aux déploiements de groupe de disponibilité ou spécifiques de l’ICF de [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)].

STONITH est requis pour un cluster Pacemaker pris en charge. Utilisez la documentation à partir de la distribution pour configurer l’installation STONITH. Par exemple, à [délimitation selon le stockage](https://www.suse.com/documentation/sle_ha/book_sleha/data/sec_ha_storage_protect_fencing.html) pour SLES. Il existe également un agent STONITH pour VMware vCenter pour les solutions basées sur ESXI. Pour plus d’informations, consultez [Stonith plug-in Agent pour l’isolement de VMWare VM VCenter SOAP (Unofficial)](https://github.com/olafrv/fence_vmware_soap).

> [!NOTE]
> Au moment de la rédaction de cet article, Hyper-V ne dispose pas d’une solution pour STONITH. Cela vaut pour les déploiements et affecte également des déploiements de Pacemaker basé sur Azure à l’aide de certaines distributions tels que RHEL.

### <a name="interoperability"></a>Interopérabilité
Cette section décrit comment un cluster basé sur Linux peut interagir avec un cluster WSFC ou à d’autres distributions de Linux.

#### <a name="wsfc"></a>WSFC
Actuellement, il n’existe aucun moyen direct pour un cluster WSFC et un cluster Pacemaker fonctionner ensemble. Cela signifie qu’il n’existe aucun moyen pour créer un groupe de disponibilité ou d’une instance FCI qui fonctionne sur un cluster WSFC et le Pacemaker. Toutefois, il existe deux solutions d’interopérabilité, qui sont conçus pour les groupes de disponibilité. La seule façon de qu'une instance FCI peut participer à une configuration inter-plateformes est si elle participe en tant qu’instance dans un de ces deux scénarios :
-   Un groupe de disponibilité avec un type de cluster aucun. Pour plus d’informations, consultez le Windows [documentation des groupes de disponibilité](../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md).
-   Un groupe de disponibilité distribué, qui est un type spécial de groupe de disponibilité qui permet à deux groupes de disponibilité différents à configurer en tant que leur propre groupe de disponibilité. Pour plus d’informations sur les groupes de disponibilité distribués, consultez la documentation [groupes de disponibilité distribués](../database-engine/availability-groups/windows/distributed-availability-groups.md).

#### <a name="other-linux-distributions"></a>Autres distributions de Linux
Sur Linux, tous les nœuds d’un cluster Pacemaker doivent être sur la même distribution. Par exemple, cela signifie qu’un nœud RHEL ne peut pas faire partie d’un cluster Pacemaker qui possède un nœud SLES. La principale raison pour cela a été indiquée précédemment : les distributions peuvent avoir différentes versions et les fonctionnalités, donc les choses ne fonctionnait pas correctement. Mélange des distributions a le même article que mélange des clusters Wsfc et Linux : n’utilisez aucun ou distribué des groupes de disponibilité.

## <a name="next-steps"></a>Étapes suivantes
[Déployer un cluster STIMULATEUR pour SQL Server sur Linux](sql-server-linux-deploy-pacemaker-cluster.md)
