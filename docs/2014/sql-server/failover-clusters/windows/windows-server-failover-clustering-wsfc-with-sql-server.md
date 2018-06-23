---
title: Clustering de basculement Windows Server (WSFC) avec SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Availability Groups [SQL Server], WSFC clusters
- Windows Server Failover Clustering (WSFC), with SQL Server
- WSFC, with SQL Server
- quorum [SQL Server]
- failover clustering [SQL Server], AlwaysOn Availability Groups
ms.assetid: 79d2ea5a-edd8-4b3b-9502-96202057b01a
caps.latest.revision: 34
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 5489a7997f6b4aab1ef61226b90fe4de7cb28473
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36051433"
---
# <a name="windows-server-failover-clustering-wsfc-with-sql-server"></a>Clustering de basculement Windows Server (WSFC) avec SQL Server
  Un cluster *WSFC* (clustering de basculement Windows Server) est un groupe de serveurs indépendants qui fonctionnent conjointement afin d’augmenter la disponibilité des applications et des services. [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] tire parti des services et des fonctionnalités de WSFC afin de prendre en charge [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] et les instances de cluster de basculement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
 
  
##  <a name="TermsAndDefs"></a> Termes et définitions  
 Cluster WSFC  
 Un cluster WSFC (clustering de basculement Windows Server) est un groupe de serveurs indépendants qui fonctionnent conjointement afin d'augmenter la disponibilité des applications et des services.  
  
 Instance de cluster de basculement  
 Une instance d'un service Windows qui gère une ressource d'adresse IP, une ressource de nom réseau et des ressources supplémentaires requises pour exécuter un ou plusieurs services ou applications. Les clients peuvent utiliser le nom réseau pour accéder aux ressources du groupe, comme c'est le cas d'un nom d'ordinateur utilisé pour accéder aux services sur un serveur physique. Toutefois, comme une instance de cluster de basculement est un groupe, elle peut être basculée vers un autre nœud sans affecter le nom ou l'adresse sous-jacent.  
  
 Nœud  
 Système Microsoft Windows Server qui est membre actif ou inactif d'un cluster de serveurs.  
  
 Ressource de cluster  
 Entité physique ou logique qui peut être détenue par un nœud, être mise en ligne et hors connexion, déplacée entre des nœuds et être gérée comme un objet cluster. Une ressource de cluster ne peut appartenir qu'à un seul nœud à un moment donné.  
  
 Groupe de ressources  
 Collection de ressources de cluster gérée comme objet de cluster unique. Généralement, un groupe de ressources contient toutes les ressources de cluster nécessaires pour exécuter une application ou un service spécifique. Le basculement et la restauration automatique agissent toujours sur des groupes de ressources.  
  
 Dépendance de ressources  
 Ressource dont dépend une autre ressource. Si la ressource A dépend de la ressource B, alors B est une dépendance de A.  
  
 Ressource de nom réseau  
 Nom de serveur logique qui est géré en tant que ressource de cluster. La ressource de nom réseau doit être utilisée avec une ressource d'adresse IP.  
  
 Propriétaire favori  
 Nœud sur lequel un groupe de ressources préfère s'exécuter. Chaque groupe de ressources est associé à une liste des propriétaires favoris triés par ordre de préférence. Au cours d'un basculement automatique, le groupe de ressources est déplacé vers le nœud favori suivant dans la liste des propriétaires favoris.  
  
 Propriétaire possible  
 Nœud secondaire sur lequel une ressource peut s'exécuter. Chaque groupe de ressources est associé à une liste des propriétaires possibles. Les groupes de ressources peuvent basculer uniquement vers des nœuds répertoriés comme propriétaires possibles.  
  
 Mode de quorum  
 Configuration de quorum dans un cluster de basculement qui détermine le nombre d'échecs de nœud que le cluster peut soutenir.  
  
 Quorum forcé  
 Processus pour démarrer le cluster même si une minorité des éléments requis pour le quorum sont en communication.  
  
 Pour plus d'informations, consultez : [Glossaire relatif aux clusters de basculement](http://msdn.microsoft.com/library/aa372869\(VS.85\).aspx)  
  
##  <a name="Overview"></a> Vue d'ensemble du clustering de basculement Windows Server  
 Le clustering de basculement Windows Server fournit les fonctionnalités d'infrastructure qui prennent en charge les scénarios de haute disponibilité et de récupération d'urgence pour les applications serveur hébergées telles que Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et Microsoft Exchange. Si un nœud de cluster ou un service échoue, les services qui étaient hébergés sur ce nœud peuvent être transférés automatiquement ou manuellement vers un autre nœud disponible dans un processus appelé *basculement*.  
  
 Les nœuds dans le cluster WSFC fonctionnent de concert afin de fournir collectivement ces types de fonctionnalités :  
  
-   **Métadonnées et notifications distribuées.** Le service WSFC et les métadonnées d'application hébergées sont gérés sur chaque nœud du cluster. Ces métadonnées incluent la configuration et l'état WSFC, en plus des paramètres d'application hébergés. Les modifications apportées aux métadonnées ou à l'état d'un nœud sont automatiquement propagées aux autres nœuds du cluster.  
  
-   **Gestion des ressources.** Les différents nœuds du cluster peuvent fournir des ressources physiques telles que le stockage DAS, les interfaces réseau et l'accès au stockage sur disque partagé. Les applications hébergées s'inscrivent elles-mêmes en tant que ressource de cluster et peuvent configurer les dépendances de démarrage et d'intégrité sur d'autres ressources.  
  
-   **Contrôle d'intégrité.** La détection d'intégrité du nœud principal et entre les nœuds est réalisée par une combinaison de communications réseau de type pulsations et de surveillance des ressources. L'intégrité globale du cluster est déterminée par les votes d'un quorum de nœuds du cluster.  
  
-   **Coordination du basculement.** Chaque ressource est configurée en vue d'être hébergée sur un nœud principal, et chacune peut être transférée automatiquement ou manuellement vers un ou plusieurs nœuds secondaires. Une stratégie de basculement basée sur l'intégrité contrôle le transfert automatique de la propriété des ressources entre les nœuds. Les nœuds et les applications hébergées sont informées lorsque le basculement se produit afin de pouvoir réagir correctement.  
  
 Pour plus d'informations, consultez : [Clusters de basculement dans Windows Server 2008 R2](http://technet.microsoft.com/library/ff182338\(WS.10\).aspx)  
  
##  <a name="AlwaysOnWsfcTech"></a> Technologies AlwaysOn SQL Server et WSFC  
 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] *AlwaysOn* est une nouvelle solution haute disponibilité et d’urgence récupération qui tire parti de WSFC. AlwaysOn offre une solution intégrée et souple qui augmente la disponibilité d'application, fournit de meilleurs retours sur les investissements en matériel, et simplifie le déploiement et la gestion haute disponibilité.  
  
 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] et les instances de cluster de basculement AlwaysOn utilisent WSFC comme technologie de plateforme, en enregistrant les composants en tant que ressources de cluster WSFC.  Des ressources associées sont combinées au sein d'un *groupe de ressources*, lequel peut être rendu dépendant d'autres ressources de cluster WSFC. Le service de cluster WSFC peut ensuite détecter et indiquer la nécessité de redémarrer l'instance [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ou la basculer automatiquement vers un nœud serveur différent dans le cluster WSFC.  
  
> [!IMPORTANT]  
>  Pour tirer pleinement parti des technologies [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] AlwaysOn, vous devez remplir plusieurs conditions requises en rapport avec WSFC.  
>   
>  Pour plus d’informations, consultez [Conditions préalables requises, restrictions et recommandations pour les groupes de disponibilité Always On &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability.md).  
  
### <a name="instance-level-high-availability-with-alwayson-failover-cluster-instances"></a>Haute disponibilité au niveau de l'instance avec des instances de cluster de basculement AlwaysOn  
 Une *instance de cluster de basculement* (FCI) AlwaysOn est une instance [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installée à travers des nœuds dans un cluster WSFC. Ce type d'instance dispose de dépendances de ressources sur le stockage sur disque partagé (via Fibre Channel ou SAN iSCSI) et sur un nom de réseau virtuel. Le nom de réseau virtuel comporte une dépendance de ressources sur une ou plusieurs adresses IP virtuelles, chacune dans un sous-réseau différent. Le service SQL Server et le service de SQL Server Agent sont enregistrés en tant que ressources et sont rendus dépendants de la ressource de nom de réseau virtuel.  
  
 En cas de basculement, le service WSFC transfère la propriété des ressources de l'instance à un nœud de basculement indiqué. L'instance [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] est ensuite redémarrée sur le nœud de basculement, et les bases de données sont récupérées comme à l'accoutumée. À un moment donné, seul un nœud dans le cluster peut héberger l'instance FCI et les ressources sous-jacentes.  
  
> [!NOTE]  
>  Une instance de cluster de basculement AlwaysOn requiert un stockage sur disque partagé symétrique, tel qu'un réseau de stockage (SAN) ou un partage de fichiers SMB.  Les volumes de stockage sur disque partagé doivent être disponibles à tous les nœuds de basculement potentiels dans le cluster WSFC.  
  
 Pour plus d’informations, consultez : [les Instances de Cluster de basculement AlwaysOn](always-on-failover-cluster-instances-sql-server.md)  
  
### <a name="database-level-high-availability-with-includesshadrincludessshadr-mdmd"></a>Haute disponibilité de niveau base de données avec [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]  
 Un *groupe de disponibilité* est un ensemble de bases de données utilisateur qui basculent de concert. Un groupe de disponibilité comprend un *réplica de disponibilité* principal et un à quatre réplicas secondaires qui sont conservés par le biais des déplacements de données enregistrés dans le journal SQL Server pour la protection des données sans qu’un stockage partagé soit requis. Chaque réplica est hébergé par une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur un autre nœud du cluster WSFC. Le groupe de disponibilité et un nom de réseau virtuel correspondant sont inscrits en tant que ressources dans le cluster WSFC.  
  
 Un *écouteur de groupe de disponibilité* sur le nœud du réplica principal répond aux requêtes client entrantes pour la connexion au nom de réseau virtuel et, selon les attributs figurant dans la chaîne de connexion, il redirige chaque requête vers l'instance appropriée de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
 En cas de basculement, au lieu de transférer la propriété des ressources physiques partagées sur un autre nœud, WSFC est utilisé pour reconfigurer un réplica secondaire sur une autre instance [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] afin d'en faire le réplica principal du groupe de disponibilité. La ressource de nom de réseau virtuel du groupe de disponibilité est ensuite transférée à cette instance.  
  
 À un moment donné, seule une instance [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] peut héberger le réplica principal des bases de données d'un groupe de disponibilité, tous les réplicas secondaires associés doivent résider sur une instance distincte et chaque instance doit résider sur des nœuds physiques distincts.  
  
> [!NOTE]  
>  [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] ne nécessite pas le déploiement d'une instance de cluster de basculement ni l'utilisation du stockage symétrique (SAN ou SMB).  
>   
>  Une instance de cluster de basculement (FCI) peut être utilisée avec un groupe de disponibilité afin d'améliorer la disponibilité d'un réplica de disponibilité. Toutefois, pour empêcher des conditions de concurrence potentielles dans le cluster WSFC, le basculement automatique du groupe de disponibilité n'est pas pris en charge dans ou à partir d'un réplica de disponibilité qui réside sur une instance FCI.  
  
 Pour plus d’informations, consultez [Vue d’ensemble des groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md).  
  
##  <a name="AlwaysOnWsfcHealth"></a> Contrôle d'intégrité de WSFC et basculement  
 La haute disponibilité d'une solution AlwaysOn tient au contrôle d'intégrité proactif des ressources de cluster WSFC physiques et logiques, ainsi qu'au basculement automatique et à la reconfiguration du matériel redondant.  Un administrateur système peut également initier un *basculement manuel* d'un groupe de disponibilité ou d'une instance [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] d'un nœud vers un autre.  
  
### <a name="failover-policies-for-nodes-failover-cluster-instances-and-availability-groups"></a>Stratégies de basculement pour les nœuds, les instances de cluster de basculement et les groupes de disponibilité  
 Une *stratégie de basculement* est configurée au niveau du nœud de cluster WSFC, de l’instance de cluster de basculement (FCI) [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et aux niveaux du groupe de disponibilité.  Ces stratégies, selon la gravité, la durée et la fréquence d'un état de ressource de cluster défectueux et la réactivité de nœud, peuvent déclencher le redémarrage d'un service ou le *basculement automatique* de ressources de cluster d'un nœud vers un autre, ou elles peuvent déclencher le déplacement d'un réplica principal de groupe de disponibilité d'une instance [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vers une autre.  
  
 Le basculement d'un réplica de groupe de disponibilité n'affecte pas l'instance [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sous-jacente.  Le basculement d'une instance FCI déplace les réplicas de groupe de disponibilité hébergés avec l'instance.  
  
 Pour plus d’informations, consultez [Stratégie de basculement pour les instances de cluster de basculement](failover-policy-for-failover-cluster-instances.md).  
  
### <a name="wsfc-resource-health-detection"></a>Détection d'intégrité des ressources WSFC  
 Chaque ressource dans un nœud de cluster WSFC peut signaler son état et son intégrité, de manière régulière ou à la demande. D'autres circonstances peuvent indiquer un échec de la ressource : par exemple, une faille de l'alimentation, des erreurs de disque ou de la mémoire, des erreurs de communication réseau ou des services non réactifs.  
  
 Les ressources de cluster WSFC telles que les réseaux, le stockage ou les services peuvent être rendues dépendantes les unes des autres. L'intégrité cumulative d'une ressource est déterminée en regroupant successivement son intégrité avec l'intégrité de chacune de ses dépendances de ressource.  
  
### <a name="wsfc-inter-node-health-detection-and-quorum-voting"></a>Détection d'intégrité entre les nœuds WSFC et vote du quorum  
 Chaque nœud d'un cluster WSFC participe à la communication périodique de pulsation pour partager l'état d'intégrité du nœud avec les autres nœuds. Les nœuds qui ne répondent pas sont considérés comme étant en état d'échec.  
  
 Un ensemble de nœuds de *quorum* est une majorité des nœuds votants et des témoins dans le cluster WSFC. L'intégrité globale et le statut d'un cluster WSFC sont déterminés par un *vote de quorum*périodique. La présence d'un quorum signifie que le cluster est intègre et en mesure d'assurer la tolérance aux pannes au niveau du nœud.  
  
 Un *mode de quorum* est configuré au niveau du cluster WSFC et dicte la méthodologie utilisée pour le vote du quorum, ainsi que le moment choisi pour effectuer un basculement automatique ou mettre le cluster hors connexion.  
  
> [!TIP]  
>  Il est recommandé de toujours avoir un nombre impair de votes de quorum dans un cluster WSFC.  Pour les besoins du vote du quorum, il n'est pas nécessaire que [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] soit installé sur tous les nœuds du cluster. Un serveur supplémentaire peut jouer le rôle de membre de quorum, ou le modèle de quorum WSFC peut être configuré pour utiliser un partage de fichiers distant comme ressource de contrôle décisive.  
>   
>  Pour plus d’informations, consultez [Modes de quorum WSFC et configuration de vote &#40;SQL Server&#41;](wsfc-quorum-modes-and-voting-configuration-sql-server.md).  
  
### <a name="disaster-recovery-through-forced-quorum"></a>Récupération d'urgence par le quorum forcé  
 En fonction des pratiques opérationnelles et de la configuration de cluster WSFC, vous pouvez procéder à des basculements automatiques et manuels, tout en conservant une solution AlwaysOn [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fiable et à tolérance de pannes. Cependant, si un quorum des nœuds de vote éligibles dans le cluster WSFC ne peut pas communiquer avec un autre, ou si le cluster WSFC échoue lors de la validation d'intégrité, le cluster WSFC peut être mis hors connexion.  
  
 Si le cluster WSFC est mis hors connexion en raison d’un problème grave non planifié, ou en raison d’un problème de matériel ou de communication persistant, une intervention administrative manuelle est nécessaire pour *forcer un quorum* et remettre les nœuds de cluster survivants en ligne dans une configuration sans tolérance de panne.  
  
 Ensuite, une série de mesures doit également être prise pour reconfigurer le cluster WSFC, récupérer les réplicas de base de données affectés et rétablir un nouveau quorum.  
  
 Pour plus d’informations, consultez [Récupération d’urgence WSFC par le quorum forcé &#40;SQL Server&#41;](wsfc-disaster-recovery-through-forced-quorum-sql-server.md).  
  
##  <a name="AlwaysOnWsfcRelationship"></a> Relation des composants AlwaysOn de SQL Server avec WSFC  
 Plusieurs couches de relations existent entre les fonctionnalités et les composants WSFC et AlwaysOn [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
 Les groupes de disponibilité AlwaysOn sont hébergés sur des instances [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
 Une requête d'un client qui spécifie un nom réseau d'écouteur de groupe de disponibilité logique pour se connecter à une base de données principale ou secondaire est acheminée vers le nom de réseau d'instance approprié de l'instance [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sous-jacente ou de l'instance de cluster de basculement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
 Les instances SQL Server sont hébergées activement sur un nœud unique.  
 Si elle est présente, une instance [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] autonome réside toujours sur un nœud unique avec un nom réseau d'instance statique.  Si elle est présente, une instance de cluster de basculement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] est active sur l'un des deux nœuds ou plus de basculement possibles avec un nom réseau d'instance virtuel unique.  
  
 Les nœuds sont membres d'un cluster WSFC.  
 Les métadonnées et l'état de la configuration WSFC pour tous les nœuds sont stockés sur chaque nœud. Chaque serveur peut fournir des volumes de stockage ou de stockage partagé asymétriques (SAN) pour les bases de données utilisateur ou système. Chaque serveur possède au moins une interface réseau physique sur un ou plusieurs sous-réseaux IP.  
  
 Le service WSFC surveille l'intégrité et gère la configuration d'un groupe de serveurs.  
 Le service WSFC (Windows Server Failover Cluster) propage les modifications apportées aux métadonnées et à l'état de la configuration WSFC à tous les nœuds du cluster. Les métadonnées partielles et l'état peuvent être stockés sur un partage de fichiers distant témoin du quorum WSFC. Deux ou plusieurs nœuds actifs ou témoins constituent un quorum de vote pour l'intégrité du cluster WSFC.  
  
 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] sont des sous-clés du cluster WSFC.  
 Si vous supprimez et recréez un cluster WSFC, vous devez désactiver puis réactiver la fonctionnalité [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] sur chaque instance de serveur pour laquelle [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] était activé sur le cluster WSFC d'origine. Pour plus d’informations, consultez [Activer et désactiver les groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md).  
  
 ![Diagramme de contexte du composant SQL Server AlwaysOn](../../../database-engine/media/alwaysoncomponentcontextdiagram.gif "Diagramme de contexte du composant SQL Server AlwaysOn")  
  
##  <a name="RelatedTasks"></a> Tâches associées  
  
-   [Afficher les paramètres NodeWeight pour le quorum de cluster](view-cluster-quorum-nodeweight-settings.md)  
  
-   [Configurer les paramètres NodeWeight pour un quorum de cluster](configure-cluster-quorum-nodeweight-settings.md)  
  
-   [Forcer un cluster WSFC à démarrer sans quorum](force-a-wsfc-cluster-to-start-without-a-quorum.md)  
  
##  <a name="RelatedContent"></a> Contenu associé  
  
-   [Technologies de Windows Server : clusters de basculement](http://technet.microsoft.com/library/cc732488\(v=WS.10\).aspx)  
  
-   [Clusters de basculement dans Windows Server 2008 R2](http://technet.microsoft.com/library/ff182338\(WS.10\).aspx)  
  
-   [Afficher les événements et journaux pour un cluster de basculement](http://technet.microsoft.com/library/cc772342\(WS.10\).aspx)  
  
-   [Applets de commande de cluster de basculement Get-ClusterLog](http://technet.microsoft.com/library/ee461045.aspx)  
  
## <a name="see-also"></a>Voir aussi  
 [Les Instances de Cluster de basculement AlwaysOn (SQL Server)](always-on-failover-cluster-instances-sql-server.md)   
 [Vue d’ensemble des groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Modes de quorum WSFC et configuration de vote &#40;SQL Server&#41;](wsfc-quorum-modes-and-voting-configuration-sql-server.md)   
 [Stratégie de basculement pour les instances de cluster de basculement](failover-policy-for-failover-cluster-instances.md)   
 [Récupération d’urgence WSFC par le quorum forcé &#40;SQL Server&#41;](wsfc-disaster-recovery-through-forced-quorum-sql-server.md)  
  
  