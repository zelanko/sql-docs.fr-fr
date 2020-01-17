---
title: Haute disponibilité SQL Server pour les déploiements Linux
description: Découvrez les différentes options de haute disponibilité disponibles pour SQL Server sur Linux, telles que les groupes de disponibilité Always On, les instances de cluster de basculement et la copie des journaux de transaction.
ms.custom: seo-lt-2019
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 11/27/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: 474533a69d74512e3e305f44d96f90009aa64e00
ms.sourcegitcommit: 34d28d49e8d0910cf06efda686e2d73059569bf8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2020
ms.locfileid: "75656607"
---
# <a name="sql-server-availability-basics-for-linux-deployments"></a>Principes de base de la disponibilité SQL Server pour les déploiements Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

À partir de [!INCLUDE[sssql17-md](../includes/sssql17-md.md)], [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] est pris en charge sur Linux et sur Windows. Comme les [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]déploiements [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] basés sur Windows, les bases de données et les instances doivent être hautement disponibles sous Linux. Cet article aborde les aspects techniques de la planification et du déploiement de bases de données et d’instances [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] basées sur Linux à haut niveau de disponibilité, ainsi que certaines des différences par rapport aux installations Windows. Comme [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] peut être une nouveauté pour les professionnels Linux et que Linux peut être une nouveauté pour les professionnels [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)], l’article présente parfois des concepts pouvant être familiers aux uns et ne pas l’être aux autres.

## <a name="includessnoversion-mdincludesssnoversion-mdmd-availability-options-for-linux-deployments"></a>[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] options de disponibilité pour les déploiements Linux
Outre la sauvegarde et la restauration, les trois mêmes fonctionnalités de disponibilité sont disponibles sur Linux comme pour les déploiements basés sur Windows :
-   Groupes de disponibilité Always On
-   Instances de cluster de basculement (FCI) Always On
-   [Copie des journaux de transaction](sql-server-linux-use-log-shipping.md)

Sur Windows, les instances de cluster de basculement (FCI) exigent une instance de cluster de basculement Windows Server (WSFC) sous-jacente. Selon le scénario de déploiement, un groupe de disponibilité requiert généralement un WSFC sous-jacent, à l’exception de la nouvelle variante None dans [!INCLUDE[sssql17-md](../includes/sssql17-md.md)]. Il n’y a pas de WSFC dans Linux. L’implémentation du clustering dans Linux est traitée dans la section [Pacemaker pour les groupes de disponibilité Always On et les instances de cluster de basculement sur Linux](#pacemaker-for-always-on-availability-groups-and-failover-cluster-instances-on-linux).

## <a name="a-quick-linux-primer"></a>Première initiation rapide à Linux
Alors que certaines installations Linux peuvent être installées avec une interface, la plupart d’entre elles ne le sont pas, ce qui signifie que presque tout ce qui se trouve au niveau du système d’exploitation est effectué via une ligne de commande. Le terme courant pour cette ligne de commande dans l’environnement Linux est *shell bash*.

Dans Linux, de nombreuses commandes doivent être exécutées avec des privilèges élevés, comme de nombreuses choses qui doivent être effectuées dans Windows Server en tant qu’administrateur. Il existe deux méthodes principales d’exécution avec des privilèges élevés :
1. Exécuter dans le contexte de l’utilisateur approprié. Pour passer à un autre utilisateur, utilisez la commande `su`. Si `su` est exécuté seul sans nom d’utilisateur, à condition que vous connaissiez le mot de passe, vous êtes maintenant dans un interpréteur de commandes en tant que *racine*.
   
2. La manière la plus courante et la plus respectueuse de la sécurité d'exécuter les choses consiste à utiliser `sudo` avant d’exécuter quoi que ce soit. De nombreux exemples dans cet article utilisent `sudo`.

Voici certaines commandes courantes, chacune ayant plusieurs commutateurs et options qui peuvent être recherchés en ligne :
-   `cd` - modifier le répertoire
-   `chmod` - modifier les autorisations d’un fichier ou d’un répertoire
-   `chown` - modifier la propriété d’un fichier ou d’un répertoire
-   `ls` - afficher le contenu d'un répertoire
-   `mkdir` - créer un dossier (répertoire) sur un lecteur
-   `mv` - déplacer un fichier d'un emplacement à un autre
-   `ps` - afficher tous les processus de travail
-   `rm` - supprimer un fichier localement sur un serveur
-   `rmdir` - supprimer un dossier (répertoire)
-   `systemctl` - démarrer, arrêter ou activer des services
-   Commandes de l’éditeur de texte. Sur Linux, il existe différentes options de l’éditeur de texte, telles que vi et emacs.

## <a name="common-tasks-for-availability-configurations-of-includessnoversion-mdincludesssnoversion-mdmd-on-linux"></a>Tâches courantes relatives aux configurations de disponibilité de [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] sur Linux
Cette section traite des tâches qui sont communes à tous les déploiements [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] basés sur Linux.

### <a name="ensure-that-files-can-be-copied"></a>Vérifiez que les fichiers peuvent être copiés
La copie de fichiers d’un serveur à un autre est une tâche que toute personne utilisant [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] sur Linux doit pouvoir effectuer. Cette tâche est très importante pour les configurations des groupes de disponibilité.

Des choses comme les problèmes d’autorisation peuvent exister sur Linux comme sur des installations basées sur Windows. Toutefois, ceux qui sont familiarisés avec la procédure de copie d’un serveur à l’autre sur Windows n’ont peut-être pas connaissance de la façon de le faire sur Linux. Une méthode courante consiste à utiliser l’utilitaire de ligne de commande `scp`, qui correspond à la copie sécurisée. En arrière-plan, `scp` utilise OpenSSH. SSH est l’acronyme de Secure Shell. Selon la distribution Linux, OpenSSH lui-même n’est peut-être pas installé. Si ce n’est pas le cas, OpenSSH doit d’abord être installé. Pour plus d’informations sur la configuration d’OpenSSH, consultez les informations sous les liens suivants pour chaque distribution :
-   [Red Hat Enterprise Linux (RHEL)](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/deployment_guide/ch-openssh)
-   [SUSE Linux Enterprise Server (SLES)](https://en.opensuse.org/SDB:Configure_openSSH)
-   [Ubuntu](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

Lorsque vous utilisez `scp`, vous devez fournir les informations d’identification du serveur s’il n’est ni la source ni la destination. Par exemple, l’utilisation de

```bash
scp MyAGCert.cer username@servername:/folder/subfolder
```

copie le fichier MyAGCert.cer dans le dossier spécifié sur l’autre serveur. Notez que vous devez disposer d’autorisations (et éventuellement de la propriété) du fichier pour le copier. Vous devrez donc peut-être également utiliser `chown` avant la copie. De même, du côté de la réception, l’utilisateur approprié a besoin d’un accès pour manipuler le fichier. Par exemple, pour restaurer ce fichier de certificat, l’utilisateur `mssql` doit pouvoir y accéder.

Samba, qui est la variante Linux du protocole SMB (Server Message Block), peut également être utilisé pour créer des partages accessibles par des chemins d’accès UNC tels que `\\SERVERNAME\SHARE`. Pour plus d’informations sur la configuration de Samba, consultez les informations sous les liens suivants pour chaque distribution :
-   [RHEL](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Managing_Confined_Services/chap-Managing_Confined_Services-Samba.html)
-   [SLES](https://www.suse.com/documentation/sles11/book_sle_admin/data/cha_samba.html)
-   [Ubuntu](https://help.ubuntu.com/community/Samba)

Les partages SMB basés sur Windows peuvent également être utilisés ; les partages SMB n’ont pas besoin d’être basés sur Linux tant que la partie cliente de Samba est configurée correctement sur le serveur Linux hébergeant [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] et que le partage dispose de l’accès approprié. Pour ceux qui se trouvent dans un environnement mixte, c’est une façon de tirer parti de l'infrastructure existante pour les déploiements [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] basés sur Linux.

Une chose importante est que la version de Samba déployée doit être compatible avec SMB 3.0. Lors de l’ajout de la prise en charge de SMB dans [!INCLUDE[sssql11-md](../includes/sssql11-md.md)], tous les partages sont nécessaires pour prendre en charge de SMB 3.0. Si Samba, et non Windows Server, est utilisé pour le partage, le partage basé sur Samba doit utiliser Samba 4.0 ou une version ultérieure, et dans l’idéal, 4.3 ou une version ultérieure qui prend en charge SMB 3.1.1. Une bonne source d’informations sur SMB et Linux est [SMB3 dans Samba](https://events.static.linuxfound.org/sites/events/files/slides/smb3-in-samba.pr__0.pdf).

Enfin, l’utilisation d’un partage de système de fichiers réseau (NFS) est une option. L’utilisation de NFS n’est pas une option sur les déploiements de [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] basés sur Windows et ne peut être utilisée que pour les déploiements basés sur Linux.

### <a name="configure-the-firewall"></a>Configurer le pare-feu
Comme les distributions Windows, les distributions Linux ont un pare-feu intégré. Si votre entreprise utilise un pare-feu externe pour les serveurs, la désactivation des pare-feu dans Linux peut être acceptable. Cependant, quel que soit l’emplacement où le pare-feu est activé, les ports doivent être ouverts. Le tableau suivant répertorie les ports courants requis pour des déploiements [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] hautement disponibles sur Linux.

| Numéro de port | Type     | Description                                                                                                                 |
|-------------|----------|-----------------------------------------------------------------------------------------------------------------------------|
| 111         | TCP/UDP  | NFS - `rpcbind/sunrpc`                                                                                                    |
| 135         | TCP      | Samba (si utilisé) - mappeur de point de terminaison                                                                                          |
| 137         | UDP      | Samba (si utilisé) - service de noms NetBIOS                                                                                      |
| 138         | UDP      | Samba (si utilisé) - datagramme NetBIOS                                                                                          |
| 139         | TCP      | Samba (si utilisé) - session NetBIOS                                                                                           |
| 445         | TCP      | Samba (si utilisé) - SMB sur TCP                                                                                              |
| 1433        | TCP      | [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] -port par défaut ; si vous le souhaitez, peut changer avec `mssql-conf set network.tcpport <portnumber>`                       |
| 2049        | TCP, UDP | NFS (si utilisé)                                                                                                               |
| 2224        | TCP      | Pacemaker - utilisé par `pcsd`                                                                                                |
| 3121        | TCP      | Pacemaker - requis s’il existe des nœuds Pacemaker distants                                                                    |
| 3260        | TCP      | Initiateur iSCSI (si utilisé) - peut être changé en `/etc/iscsi/iscsid.config` (RHEL), mais doit correspondre au port de la cible iSCSI |
| 5022        | TCP      | [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] - port par défaut utilisé pour un point de terminaison de groupe de disponibilité ; peut être modifié lors de la création du point de terminaison                                |
| 5403        | TCP      | Pacemaker                                                                                                                   |
| 5404        | UDP      | Pacemaker : requis par Corosync si vous utilisez la multidiffusion UDP                                                                     |
| 5405        | UDP      | Pacemaker : requis par Corosync                                                                                            |
| 21064       | TCP      | Pacemaker : requis par les ressources à l’aide de DLM                                                                                 |
| Variable    | TCP      | Port du point de terminaison du groupe de disponibilité ; la valeur par défaut est 5022                                                                                           |
| Variable    | TCP      | NFS : port pour `LOCKD_TCPPORT` (trouvé dans `/etc/sysconfig/nfs` sur RHEL)                                              |
| Variable    | UDP      | NFS : port pour `LOCKD_UDPPORT` (trouvé dans `/etc/sysconfig/nfs` sur RHEL)                                              |
| Variable    | TCP/UDP  | NFS : port pour `MOUNTD_PORT` (trouvé dans `/etc/sysconfig/nfs` sur RHEL)                                                |
| Variable    | TCP/UDP  | NFS : port pour `STATD_PORT` (trouvé dans `/etc/sysconfig/nfs` sur RHEL)                                                 |

Pour les ports supplémentaires qui peuvent être utilisés par Samba, consultez [ Utilisation des ports Samba](https://wiki.samba.org/index.php/Samba_Port_Usage).

À l’inverse, le nom du service sous Linux peut également être ajouté en tant qu’exception au lieu du port ; par exemple, `high-availability` pour Pacemaker. Reportez-vous à votre distribution pour les noms s’il s’agit de la direction que vous souhaitez poursuivre. Par exemple, sur RHEL, la commande à ajouter dans Pacemaker est

```bash
sudo firewall-cmd --permanent --add-service=high-availability
```

**Documentation Firewall :**
-   [RHEL](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/high_availability_add-on_reference/s1-firewalls-haar)
-   [SLES](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html)

### <a name="install-includessnoversion-mdincludesssnoversion-mdmd-packages-for-availability"></a>Installer des packages [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] pour la disponibilité
Sur une installation [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] basée sur Windows, certains composants sont installés même dans le cas d’une installation du moteur de base, tandis que d’autres ne le sont pas. Sous Linux, seul le moteur [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] est installé dans le cadre du processus d’installation. Tout le reste est facultatif. Pour les instances [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] hautement disponibles sous Linux, deux packages doivent être installés avec [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] : [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Agent (*mssql-server-agent*) et le package haute disponibilité (HA) (*mssql-server-ha*). Bien que l’agent [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] soit techniquement facultatif, c’est le planificateur de [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] pour les tâches et il est requis par la copie des journaux de transaction. Son installation est donc recommandée. Sur les installations basées sur Windows, l’agent [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] n’est pas facultatif.

>[!NOTE]
>Pour ceux qui sont nouveaux dans [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)], l’agent [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] est le planificateur de tâches intégré de [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]. Ce moyen est couramment utilisé par les administrateurs de bases de données pour planifier des opérations telles que les sauvegardes et les autres opérations de maintenance [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]. Contrairement à une installation de [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] basée sur Windows, où l’agent [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] est un service complètement différent, sur Linux, l’agent [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] s’exécute dans le contexte de [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] proprement dit.

Quand les groupes de disponibilité ou les instance de cluster de basculement (FCI) sont configurés sur une configuration basée sur Windows, ils prennent en charge les clusters. La prise en charge des clusters implique que [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] ait des DLL de ressources spécifiques qu’un WSFC connaît (sqagtres.dll et sqsrvres.dll pour les instances de cluster de basculement (FCI), hadrres.dll pour les groupes de disponibilité) et qui sont utilisées par le WSFC pour s’assurer que la fonctionnalité en cluster [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] est active, en cours d’exécution et fonctionne correctement. Étant donné que le clustering est externe non seulement à [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)], mais à Linux proprement dit, Microsoft a dû coder l’équivalent d’une DLL de ressource pour les déploiements de groupes de disponibilité et d’instances de cluster de basculement (FCI) basés sur Linux. Il s’agit du package *mssql-server-ha*, également appelé agent de ressources [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] pour Pacemaker. Pour installer le package *mssql-server-ha*, consultez [Installer les packages HA et SQL Server Agent](sql-server-linux-deploy-pacemaker-cluster.md#install-the-sql-server-ha-and-sql-server-agent-packages).

Les autres packages facultatifs pour [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] sur Linux, à savoir la recherche en texte intégral [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] (*mssql-server-fts*) et Integration Services [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] (*mssql-server-is*), ne sont pas requis pour la haute disponibilité, que ce soit pour une instance de cluster de basculement (FCI) un groupe de disponibilité.

## <a name="pacemaker-for-always-on-availability-groups-and-failover-cluster-instances-on-linux"></a>Pacemaker pour les groupes de disponibilité Always On et les instances de cluster de basculement sur Linux
Comme indiqué précédemment, le seul mécanisme de clustering actuellement pris en charge par Microsoft pour les groupes de disponibilité et les instances de cluster de basculement (FCI) est Pacemaker avec Corosync. Cette section présente les informations de base pour comprendre la solution ainsi que la façon de la planifier et de la déployer pour les configurations [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)].

### <a name="ha-add-onextension-basics"></a>Notions de base sur le module complémentaire/l’extension HA
Toutes les distributions actuellement prises en charge sont livrées avec le module complémentaire/l’extension de haute disponibilité, sur la base de la pile de clusters de Pacemaker. Cette pile intègre deux composants clés : Pacemaker et Corosync. Tous les composants de la pile sont :
-   Pacemaker : le composant de clustering de base, qui effectue des opérations telles que la coordination des machines en cluster.
-   Corosync : une infrastructure et un ensemble d’API qui fournissent des éléments tels que le quorum, la capacité à redémarrer les processus ayant échoué etc.
-   libQB : fournit des éléments tels que la journalisation.
-   Agent de ressources : fonctionnalité spécifiques fournie pour qu’une application puisse s’intégrer dans Pacemaker.
-   Agent de délimitation : les scripts/la fonctionnalité qui permettent d’isoler les nœuds et de les traiter en cas de problèmes.
    
> [!NOTE]
> La pile de clusters est communément appelée Pacemaker dans le monde de Linux.

Certains points de cette solution sont similaires au déploiement de configurations en cluster à l’aide de Windows, mais d’autres diffèrent. Dans Windows, la forme de disponibilité du clustering, appelée cluster de basculement Windows Server (WSFC), est intégrée au système d’exploitation, et la fonctionnalité qui permet la création d’un WSFC, clustering de basculement, est désactivée par défaut. Dans Windows, les groupes de disponibilité et les instances de cluster de basculement (FCI) sont basés sur un WSFC et ont en commun une intégration avancée en raison de la DLL de ressource spécifique fournie par [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]. Cette solution fortement couplée est possible dans l’ensemble parce que tout vient d’un seul fournisseur.

![](./media/sql-server-linux-ha-basics/image1.png)

Sur Linux, alors que chaque distribution prise en charge dispose d’un Pacemaker, chaque distribution peut être personnalisée et avoir des implémentations et des versions légèrement différentes. Certaines des différences sont reflétées par les instructions données dans cet article. La couche de clustering étant open source, bien qu’elle soit fournie avec les distributions, elle n’est pas fortement intégrée de la même façon qu’un WSFC sous Windows. C’est pourquoi Microsoft fournit *mssql-server-ha*, de sorte que [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] et la pile de Pacemaker peuvent fournir une expérience proche de celle de Windows, mais pas exactement identique, pour les groupes de disponibilité et les instances de cluster de basculement (FCI).

Pour obtenir une documentation complète sur Pacemaker, y compris une explication plus détaillée de tous les éléments avec des informations de référence complètes, pour RHEL et SLES :
-   [RHEL](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/7/html/High_Availability_Add-On_Reference/ch-overview-HAAR.html)
-   [SLES](https://www.suse.com/documentation/sle_ha/book_sleha/data/book_sleha.html)

Ubuntu n’a pas de guide pour la disponibilité.

Pour plus d’informations sur l’ensemble de la pile, consultez également la [page de documentation de Pacemaker](https://clusterlabs.org/doc/) sur le site Clusterlabs.

### <a name="pacemaker-concepts-and-terminology"></a>Concepts et terminologie de Pacemaker
Cette section documente les concepts et la terminologie courants pour une implémentation de Pacemaker.

#### <a name="node"></a>Nœud
Un nœud est un serveur participant au cluster. Un cluster Pacemaker prend en charge jusqu’à 16 nœuds en mode natif. Ce nombre peut être dépassé si Corosync n’est pas exécuté sur des nœuds supplémentaires, mais Corosync est requis pour [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]. Par conséquent, le nombre maximal de nœuds qu’un cluster peut avoir pour une configuration basée sur [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] est de 16 ; il s’agit de la limite de Pacemaker, qui n’a rien à voir avec les limitations maximales imposées par [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] pour les groupes de disponibilité ou les instances de cluster de basculement (FCI). 

#### <a name="resource"></a>Ressource
Un cluster WSFC et un cluster Pacemaker sont conçus pour une ressource. Une ressource est une fonctionnalité spécifique qui s’exécute dans le contexte du cluster, par exemple un disque ou une adresse IP. Par exemple, sous Pacemaker, des ressources d’instances de cluster de basculement (FCI) et de groupes de disponibilité peuvent être créées. Cela n’est pas différent de ce qui est fait dans un cluster WSFC, où vous voyez une ressource [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] pour une instance de cluster de basculement (FCI) ou pour une ressource de groupe de disponibilité lors de la configuration d’un groupe de disponibilité, mais ça n’est pas exactement la même chose, en raison des différences sous-jacentes dans la manière dont [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] s’intègre dans Pacemaker.

Pacemaker a des ressources standard et de clonage. Les ressources de clonage s’exécutent simultanément sur tous les nœuds. Par exemple, une adresse IP qui s’exécute sur plusieurs nœuds à des fins d’équilibrage de charge. Toute ressource créée pour les instances de cluster de basculement (FCI) utilise une ressource standard, car un seul nœud peut héberger une instance de cluster de basculement (FCI) à un moment donné.

Quand un groupe de disponibilité est créé, il nécessite une forme spécialisée de ressource de clonage appelée ressource à plusieurs états. Bien qu’un groupe de disponibilité n’ait qu’un seul réplica principal, le groupe de disponibilité proprement dit s’exécute sur tous les nœuds sur lesquels il est configuré pour fonctionner et peut potentiellement autoriser des opérations telles que l’accès en lecture seule. Étant donné qu’il s’agit d’une utilisation « en direct » du nœud, les ressources ont le concept de deux états : maître et esclave. Pour plus d'informations, consultez [Ressources à plusieurs états : ressources qui ont plusieurs modes](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Configuring_the_Red_Hat_High_Availability_Add-On_with_Pacemaker/s1-multistateresource-HAAR.html).

#### <a name="resource-groupssets"></a>Groupes/ensembles de ressources
À l’instar des rôles dans un WSFC, un cluster Pacemaker a le concept d’un groupe de ressources. Un groupe de ressources (appelé ensemble dans SLES) est une collection de ressources qui fonctionnent ensemble et peuvent basculer d’un nœud à un autre en tant qu’unité unique. Les groupes de ressources ne peuvent pas contenir de ressources qui sont configurées en tant que maître/esclave ; ils ne peuvent donc pas être utilisés pour des groupes de disponibilité. Bien qu’un groupe de ressources puisse être utilisé pour les instances de cluster de basculement (FCI), ce n’est généralement pas une configuration recommandée.

#### <a name="constraints"></a>Contraintes
Les clusters WSFC ont différents paramètres pour les ressources, ainsi que des éléments tels que des dépendances, qui indiquent au cluster WSFC une relation parent/enfant entre deux ressources différentes. Une dépendance est simplement une règle indiquant à WSFC quelle ressource doit d’abord être en ligne.

Bien qu’un cluster Pacemaker n’ait pas le concept de dépendances, il existe des contraintes. Il existe trois types de contraintes : colocalisation, emplacement et classement.
-   Une contrainte de colocalisation détermine si deux ressources devraient ou non être exécutées sur le même nœud.
-   Une contrainte de localisation indique au cluster Pacemaker où une ressource peut (ou ne peut pas) être exécutée.
-   Une contrainte de classement indique au cluster Pacemaker l’ordre dans lequel les ressources doivent démarrer.

> [!NOTE]
> Les contraintes de colocalisation ne sont pas requises pour les ressources d’un groupe de ressources, car elles sont toutes considérées comme une seule unité.

#### <a name="quorum-fence-agents-and-stonith"></a>Quorum, agents de délimitation et STONITH
Le concept de quorum sous Pacemaker est semblable à celui d’un WSFC. L’objectif du mécanisme d’un quorum du cluster est de garantir que le cluster soit en état de fonctionnement. Un WSFC et les modules complémentaires HA pour les distributions Linux ont le concept de vote, où chaque nœud compte dans le quorum. Vous souhaitez une majorité des votes, sinon, dans le pire des cas, le cluster est arrêté.

Contrairement à un WSFC, il n’y a aucune ressource témoin à utiliser avec le quorum. À l’instar d’un WSFC, l’objectif est de conserver un nombre d’électeurs impair. La configuration du quorum envisage de manière différente les groupes de disponibilité et les instances de cluster de basculement (FCI).

Les clusters WSFC surveillent l’état des nœuds participants et les gèrent lorsqu’un problème survient. Les versions ultérieures de clusters WSFC offrent des fonctionnalités telles que la mise en quarantaine d’un nœud qui ne fonctionne pas correctement ou qui n’est pas disponible (le nœud n’est pas activé, la communication réseau est interrompue etc.). Côté Linux, ce type de fonctionnalité est fourni par un agent de délimitation. Le concept est parfois appelé délimitation. Toutefois, ces agents de délimitation sont généralement spécifiques au déploiement et souvent fournis par des fournisseurs de matériel et certains éditeurs de logiciels comme ceux qui fournissent des hyperviseurs. Par exemple, VMware fournit un agent de délimitation qui peut être utilisé pour les machines virtuelles Linux virtualisées à l’aide de vSphere.

Le quorum et les délimitations sont liés dans un autre concept appelé STONITH (Shoot the Other Node in the Head). STONITH doit disposer d’un cluster Pacemaker pris en charge sur toutes les distributions Linux. Pour plus d’informations, consultez [Délimitation dans un cluster de haute disponibilité Red Hat](https://access.redhat.com/solutions/15575) (RHEL).

#### <a name="corosyncconf"></a>corosync.conf
Le fichier `corosync.conf` contient la configuration du cluster. Il se trouve dans `/etc/corosync`. Dans le cadre d’opérations quotidiennes normales, il n’est jamais nécessaire de modifier ce fichier si le cluster est configuré correctement.

#### <a name="cluster-log-location"></a>Emplacement du journal de cluster
Les emplacements de journal pour les clusters Pacemaker diffèrent selon la distribution.
-   RHEL et SLES - `/var/log/cluster/corosync.log`
-   Ubuntu - `/var/log/corosync/corosync.log`

Pour modifier l'emplacement de journalisation par défaut, modifiez `corosync.conf`.

## <a name="plan-pacemaker-clusters-for-includessnoversion-mdincludesssnoversion-mdmd"></a>Planifier des clusters Pacemaker pour [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]
Cette section traite des points de planification importants pour un cluster Pacemaker.

### <a name="virtualizing-linux-based-pacemaker-clusters-for-includessnoversion-mdincludesssnoversion-mdmd"></a>Virtualisation de Pacemaker basé sur Linux pour [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]
L’utilisation de machines virtuelles pour déployer [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] basé sur Linux pour des groupes de disponibilité et des instances de cluster de basculement (FCI) est régie par les mêmes règles que pour leurs équivalents Windows. Il y a un ensemble de règles de base pour la prise en charge de déploiements virtualisés de [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] fournis par Microsoft dans le [support Microsoft KB 956893](https://support.microsoft.com/help/956893/support-policy-for-microsoft-sql-server-products-that-are-running-in-a-hardware-virtualization-environment). De plus, différents hyperviseurs tels qu’Hyper-V de Microsoft et ESXi de VMware peuvent avoir des variances différentes en raison des différences entre les plateformes proprement dites.

Concernant les groupes de disponibilité et les instances de cluster de basculement (FCI) dans le cadre de la virtualisation, vérifiez que l’anti-affinité est définie pour les nœuds d’un cluster Pacemaker donné. Lorsqu’elles sont configurées pour la haute disponibilité dans une configuration de groupe de disponibilité ou d’instances de cluster de basculement (FCI), les machines virtuelles qui hébergent [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] ne doivent jamais s’exécuter sur le même hôte d’hyperviseur. Par exemple, si une instance de cluster de basculement (FCI) à deux nœuds est déployée, on a besoin d’*au moins* trois hôtes d’hyperviseur afin d’en avoir un prêt à fonctionner pour les machines virtuelles hébergeant un nœud en cas de défaillance d’un hôte, en particulier si des fonctionnalités telles que la migration dynamique ou vMotion sont utilisées.

Pour plus d’informations, consultez :
-   Documentation Hyper-V - [Utilisation du clustering invité pour la haute disponibilité](https://technet.microsoft.com/library/dn440540(v=ws.11).aspx)
-   Livre blanc (écrit pour des déploiements basés sur Windows, mais la plupart des concepts s’appliquent toujours) - [Planification de déploiements SQL Server critiques à haute disponibilité avec VMware vSphere](https://www.vmware.com/content/dam/digitalmarketing/vmware/en/pdf/solutions/vmware-vsphere-highly-available-mission-critical-sql-server-deployments.pdf)

### <a name="networking"></a>Mise en réseau
Contrairement à un WSFC, Pacemaker n’a besoin ni de nom dédié ni d’au moins une adresse IP dédiée pour le cluster Pacemaker proprement dit. Les groupes de disponibilité et les instances de cluster de basculement (FCI) ont besoin d’adresses (consultez la documentation correspondante pour plus d’informations), mais pas de noms, car il n’existe aucune ressource de nom de réseau. SLES autorise la configuration d’une adresse IP à des fins d’administration, mais ce n’est pas obligatoire, comme on peut le voir dans [Créer le cluster Pacemaker](sql-server-linux-deploy-pacemaker-cluster.md#create).

Comme un WSFC, Pacemaker préfèrerait une mise en réseau redondante, donc des cartes réseau distinctes (cartes réseau ou cartes réseau physiques) avec des adresses IP individuelles. En ce qui concerne la configuration du cluster, chaque adresse IP doit avoir ce que l’on appelle son propre anneau. Toutefois, comme avec les clusters WSFC aujourd’hui, de nombreuses implémentations sont virtualisées ou se trouvent dans le cloud public, où une seule carte réseau virtualisée (carte réseau virtuelle) est présentée au serveur. Si toutes les cartes réseau physiques et virtuelles sont connectées au même commutateur physique ou virtuel, il n’y pas de véritable redondance au niveau de la couche réseau. Par conséquent, la configuration de plusieurs cartes réseau est une sorte d’illusion pour la machine virtuelle. La redondance réseau est généralement intégrée à l’hyperviseur pour les déploiements virtualisés et est vraiment intégrée dans le cloud public.

L’une des différences entre plusieurs cartes d’interface réseau et Pacemaker d’un côté et un WSFC de l’autre est que Pacemaker autorise plusieurs adresses IP sur le même sous-réseau, contrairement à un WSFC. Pour plus d’informations sur plusieurs sous-réseaux et clusters Linux, consultez l’article [Configurer plusieurs sous-réseaux](sql-server-linux-configure-multiple-subnet.md).

### <a name="quorum-and-stonith"></a>Quorum et STONITH
La configuration et la configuration requise du quorum sont liées aux déploiements spécifiques aux groupes de disponibilité et aux instances de cluster de basculement (FCI) de [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)].

STONITH est requis pour un cluster de Pacemaker pris en charge. Utilisez la documentation de la distribution pour configurer STONITH. Un exemple se trouve au niveau de la [délimitation basée sur le stockage](https://www.suse.com/documentation/sle_ha/book_sleha/data/sec_ha_storage_protect_fencing.html) pour SLES. Il existe également un agent STONITH pour VMware vCenter pour les solutions ESXI. Pour plus d’informations, consultez [Agent de plug-in Stonith pour délimitation SOAP vCenter de machine virtuelle VMware (non officiel).](https://github.com/olafrv/fence_vmware_soap)

### <a name="interoperability"></a>Interopérabilité
Cette section décrit comment un cluster Linux peut interagir avec un WSFC ou avec d’autres distributions de Linux.

#### <a name="wsfc"></a>WSFC
Actuellement, il n’existe aucun moyen direct pour un WSFC et un cluster Pacemaker de fonctionner ensemble. Cela signifie qu’il n’existe aucun moyen de créer un groupe de disponibilité ou une instance de cluster de basculement (FCI) qui fonctionne sur un WSFC et sur Pacemaker. Toutefois, il existe deux solutions d’interopérabilité, toutes deux conçues pour les groupes de disponibilité. La seule façon dont une instance de cluster de basculement (FCI) peut participer à une configuration multiplateforme est d’y participer en tant qu’instance dans l’un de ces deux scénarios :
-   Un groupe de disponibilité avec un type de cluster de type Aucun. Pour plus d'informations, consultez la [ documentation des groupes de disponibilité](../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md).
-   Un groupe de disponibilité distribué, qui est un type spécial de groupe de disponibilité permettant à deux groupes de disponibilité différents d’être configurés comme leur propre groupe de disponibilité. Pour plus d’informations sur les groupes de disponibilité distribués, consultez la documentation [Groupes de disponibilité distribués](../database-engine/availability-groups/windows/distributed-availability-groups.md).

#### <a name="other-linux-distributions"></a>Autres distributions Linux
Sur Linux, tous les nœuds d’un cluster Pacemaker doivent se trouver sur la même distribution. Par exemple, cela signifie qu’un nœud RHEL ne peut pas faire partie d’un cluster Pacemaker doté d’un nœud SLES. La raison principale a déjà été indiquée : les distributions peuvent avoir des versions et des fonctionnalités différentes. Il est donc possible que certaines choses ne puissent pas fonctionner correctement. La combinaison de distributions a le même scénario que la combinaison de clusters WSFC et de Linux : utiliser des groupes de disponibilité de type Aucun ou distribués.

## <a name="next-steps"></a>Étapes suivantes
[Déployer un cluster Pacemaker pour SQL Server sur Linux](sql-server-linux-deploy-pacemaker-cluster.md)
