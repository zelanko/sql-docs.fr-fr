---
title: Conditions préalables, Restrictions et recommandations pour les groupes de disponibilité AlwaysOn (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], server instance
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], WSFC clusters
- Availability Groups [SQL Server], about
- Availability Groups [SQL Server], prerequisites and restrictions
- Availability Groups [SQL Server], Failover Cluster Instances
- Availability Groups [SQL Server], databases
- Availability Groups [SQL Server]
ms.assetid: edbab896-42bb-4d17-8d75-e92ca11f7abb
caps.latest.revision: 146
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5dc25e9314abf9aa025f489a087fdcc8ae98be36
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37259545"
---
# <a name="prerequisites-restrictions-and-recommendations-for-alwayson-availability-groups-sql-server"></a>Conditions préalables requises, restrictions et recommandations pour les groupes de disponibilité AlwaysOn (SQL Server)
  Cette rubrique décrit les considérations relatives au déploiement de [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], notamment les conditions préalables, restrictions et recommandations concernant les ordinateurs hôtes, les clusters WSFC (clustering de basculement Windows Server), les instances de serveur et les groupes de disponibilité. Pour chacun de ces composants, les considérations relatives à la sécurité et les autorisations requises (le cas échéant) sont indiquées.  
  
> [!IMPORTANT]  
>  Avant de déployer [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], nous vous recommandons de lire les sections de cette rubrique.  
  
 
  
##  <a name="DotNetHotfixes"></a> Correctifs logiciels .net prenant en charge les groupes de disponibilité AlwaysOn  
 Selon les composants et les fonctionnalités [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] que vous allez utiliser avec [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], vous pourrez éventuellement avoir besoin d'installer des correctifs logiciels .Net supplémentaires identifiés dans le tableau suivant. Ces derniers peuvent être installés dans n'importe quel ordre.  
  
||Fonctionnalité dépendante|Correctif logiciel|Lien|  
|------|-----------------------|------------|----------|  
|![Case à cocher](../../media/checkboxemptycenterxtraspacetopandright.gif "Case à cocher")|[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]|Le correctif pour .Net 3.5 SP1 ajoute une prise en charge au client SQL concernant les fonctionnalités AlwaysOn d'intention de lecture (read-intent), de lecture seule (readonly) et de basculement à plusieurs sous-réseaux (multisubnetfailover). Le correctif doit être installé sur chaque serveur de rapports [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|Article 2654347 de la base de connaissances : [Correctif pour .Net 3.5 SP1 pour l'ajout d'une prise en charge des fonctionnalités AlwaysOn](http://go.microsoft.com/fwlink/?LinkId=242896)|  
  
##  <a name="SystemReqsForAOAG"></a> Exigences et recommandations système de Windows  
  
  
###  <a name="SystemRequirements"></a> Liste de vérification des conditions requises (système Windows)  
 Pour prendre en charge la fonctionnalité [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] , vérifiez que chaque ordinateur devant participer à un ou plusieurs groupes de disponibilité respecte les conditions requises fondamentales suivantes :  
  
||Condition requise|Lien|  
|------|-----------------|----------|  
|![Case à cocher](../../media/checkboxemptycenterxtraspacetopandright.gif "Case à cocher")|Vérifiez que ce système n'est pas un contrôleur de domaine.|Les groupes de disponibilité ne sont pas pris en charge sur les contrôleurs de domaine.|  
|![Case à cocher](../../media/checkboxemptycenterxtraspacetopandright.gif "Case à cocher")|Vérifiez que chaque ordinateur exécute soit x86 (non-WOW64), soit x64 Windows Server 2008 ou versions ultérieures.|WOW64 (Windows 32 bits sur Windows 64 bits) ne prend pas en charge [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].|  
|![Case à cocher](../../media/checkboxemptycenterxtraspacetopandright.gif "Case à cocher")|Vérifiez que chaque ordinateur est un nœud d'un cluster WSFC (clustering de basculement Windows Server).|[Clustering de basculement Windows Server &#40;WSFC&#41; avec SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md)|  
|![Case à cocher](../../media/checkboxemptycenterxtraspacetopandright.gif "Case à cocher")|Vérifiez que le cluster WSFC contient suffisamment de nœuds pour prendre en charge les groupes de disponibilité que vous avez configurés.|Un nœud WSFC ne peut héberger qu'un seul réplica de disponibilité pour un groupe de disponibilité donné. Sur un nœud WSFC donné, une ou plusieurs instances de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] peuvent héberger des réplicas de disponibilité pour de nombreux groupes de disponibilité.<br /><br /> Demandez à vos administrateurs de base de données combien de nœuds WSFC sont requis pour prendre en charge les réplicas de disponibilité des groupes de disponibilité planifiés.<br /><br /> [Vue d’ensemble des groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).|  
|![Case à cocher](../../media/checkboxemptycenterxtraspacetopandright.gif "Case à cocher")|Vérifiez que tous les correctifs logiciels Windows applicables ont été installés sur chaque nœud du cluster WSFC.|**\*\* Important \* \***  plusieurs correctifs logiciels sont requis ou recommandés pour les nœuds d’un cluster WSFC sur lequel [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] est déployé. Pour plus d'informations, consultez [Correctifs logiciels Windows qui prennent en charge les groupes de disponibilité AlwaysOn (système Windows)](#WinHotfixes), plus loin dans cette section.|  
  
> [!IMPORTANT]  
>  Vérifiez que votre environnement est correctement configuré pour se connecter à un groupe de disponibilité. Pour plus d’informations, consultez [connectivité du Client AlwaysOn (SQL Server)](always-on-client-connectivity-sql-server.md).  
  
####  <a name="WinHotfixes"></a> Correctifs logiciels Windows qui prennent en charge les groupes de disponibilité AlwaysOn (système Windows)  
 Selon la topologie de cluster, plusieurs correctifs logiciels supplémentaires Windows Server 2008 Service Pack 2 (SP2) ou Windows Server 2008 R2 peuvent s'appliquer à la prise en charge de [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]. Le tableau suivant identifie ces correctifs. Ces derniers peuvent être installés dans n'importe quel ordre.  
  
||S'applique à Windows 2008 SP2|S'applique à Windows 2008 R2 SP1|Fourni avec Windows 2012|Pour prendre en charge...|Correctif logiciel|Lien|  
|------|---------------------------------|------------------------------------|------------------------------|-----------------|------------|----------|  
|![Case à cocher](../../media/checkboxemptycenterxtraspacetopandright.gif "Case à cocher")|√|√|Oui|**Configuration du quorum WSFC optimal**|Sur chaque nœud WSFC, assurez-vous que le correctif logiciel décrit dans l'article 2494036 de la base de connaissances est installé.<br /><br /> Ce correctif logiciel prend en charge la configuration du quorum optimal avec les cibles de basculement non automatique. Cette fonctionnalité améliore les clusters multisites en vous permettant de sélectionner les nœuds votants.|Article 2494036 de la base de connaissances :  [Un correctif est disponible pour vous permettre de configurer un nœud de cluster qui n'a pas de voix de quorum dans Windows Server 2008 et Windows Server 2008 R2](http://support.microsoft.com/kb/2494036)<br /><br /> Pour plus d’informations sur le vote du quorum, consultez [Modes de quorum WSFC et configuration de vote &#40;SQL Server&#41;](../../../sql-server/failover-clusters/windows/wsfc-quorum-modes-and-voting-configuration-sql-server.md).|  
|![Case à cocher](../../media/checkboxemptycenterxtraspacetopandright.gif "Case à cocher")|√|√|Oui|**Utilisation plus efficace de la bande passante réseau**|Sur chaque nœud WSFC, assurez-vous que le correctif logiciel décrit dans l'article 2616514 de la base de connaissances est installé.<br /><br /> Sans ce correctif, le service de cluster envoie des notifications de registre inutiles à des nœuds de cluster. Ce comportement limite la bande passante réseau, ce qui constitue un sérieux problème pour [!INCLUDE[ssHADRc](../../../includes/sshadrc-md.md)].|Article 2616514 de la base de connaissances :  [Le service de cluster envoie des notifications de changement de clé de Registre inutiles entre les nœuds de cluster dans Windows Server 2008 ou Windows Server 2008 R2](http://support.microsoft.com/kb/2616514)|  
|![Case à cocher](../../media/checkboxemptycenterxtraspacetopandright.gif "Case à cocher")||√|Non applicable|**Test sur les disques qui ne sont pas disponibles à tous les nœuds WSFC de stockage VPD**|Si un nœud WSFC exécute Windows Server 2008 R2 Service Pack 1 (SP1) et que le test de stockage Valider les données VPD (Vital Product Data) du périphérique SCSI échoue suite à une exécution incorrecte sur des disques qui sont en ligne et ne sont pas accessibles à tous les nœuds du cluster WSFC, installez le correctif décrit dans l'article KB 2531907 de la Base de connaissances.<br /><br /> Ce correctif logiciel élimine les avertissements ou erreurs incorrects dans le rapport de validation lorsque les disques sont en ligne.|Article 2531907 de la base de connaissances :  [Le test Valider les données VPD (Vital Product Data) du périphérique SCSI échoue après l'installation de Windows Server 2008 R2 SP1](http://support.microsoft.com/kb/2531907)|  
|![Case à cocher](../../media/checkboxemptycenterxtraspacetopandright.gif "Case à cocher")||√|Oui|**Basculement plus rapide sur les réplicas locaux**|Si un nœud WSFC exécute Windows Server 2008 R2 Service Pack 1 (SP1), vérifiez que le correctif logiciel décrit dans l'article 2687741 de la base de connaissances est installé.<br /><br /> Ce correctif logiciel améliore les performances du basculement [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] sur les réplicas locaux.|Article 2687741 de la base de connaissances :  [Un correctif logiciel qui améliore les performances de la fonctionnalité « Groupe de disponibilité AlwaysOn » dans SQL Server 2012 est disponible pour Windows Server 2008 R2](http://support.microsoft.com/KB/2687741)|  
|![Case à cocher](../../media/checkboxemptycenterxtraspacetopandright.gif "Case à cocher")|√|√|Oui|**Stockage asymétrique, pour les Instances de Cluster de basculement (fci)**|Si une instance de cluster de basculement (FCI) doit être activée pour [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], installez le correctif 976097 de Windows Server 2008.<br /><br /> Ce correctif logiciel permet au composant logiciel enfichable MMC (Microsoft Management Console) de gestion de cluster de basculement de prendre en charge le stockage asymétrique des disques partagés qui ne sont accessibles qu'à certains nœuds WSFC.|Article 976097 de la base de connaissances :  [Correctif logiciel pour l'ajout du stockage asymétrique au composant logiciel enfichable MMC de gestion du cluster de basculement pour un cluster de basculement exécutant Windows Server 2008 ou Windows Server 2008 R2](http://support.microsoft.com/kb/976097)<br /><br /> [Guide de l’Architecture AlwaysOn : Création d’une haute disponibilité et la Solution de récupération d’urgence à l’aide d’Instances de Cluster de basculement et groupes de disponibilité](http://technet.microsoft.com/library/jj215886.aspx)|  
|![Case à cocher](../../media/checkboxemptycenterxtraspacetopandright.gif "Case à cocher")|√|√|Non applicable|**Sécurité du protocole Internet (IPsec)**|Si votre environnement utilise des connexions IPsec, vous pouvez constater un long délai (environ deux ou trois minutes) lorsqu'un ordinateur client rétablit la connexion IPsec à un nom de réseau virtuel (dans ce contexte, pour se connecter à l'écouteur de groupe de disponibilité). Si vous utilisez des connexions IPsec, nous vous recommandons d'examiner les scénarios spécifiques détaillés dans l'article KB 980915 de la Base de connaissances.|Article 980915 de la base de connaissances :  [Un long délai se produit lorsque vous vous reconnectez à une connexion IPSec à partir d'un ordinateur qui exécute Windows Server 2003, Windows Vista, Windows Server 2008, Windows 7 ou Windows Server 2008 R2](http://support.microsoft.com/kb/980915)|  
|![Case à cocher](../../media/checkboxemptycenterxtraspacetopandright.gif "Case à cocher")|√|√|Oui|**IPv6**|Si vous utilisez IPv6, nous vous recommandons d'examiner les scénarios spécifiques détaillés dans l'article 2578103 ou 2578113 de la base de connaissances, selon votre système d'exploitation Windows Server.<br /><br /> Si votre topologie Windows Server utilise IPv6 (Internet Protocol version 6), il faut environ 30 secondes au service de cluster WSFC pour basculer vers l'adresse IP IPv6. De ce fait, les clients doivent attendre environ 30 secondes pour se reconnecter à l'adresse IP IPv6.|Article 2578103 de la base de connaissances (Windows Server 2008) :  [Il faut environ 30 secondes au service de cluster pour basculer des adresses IP IPv6 dans Windows Server 2008](http://support.microsoft.com/kb/2578103)<br /><br /> Article 2578113 de la Base de connaissances (Windows Server 2008 R2) :  **Windows Server 2008 R2 :** [Il faut environ 30 secondes au service de cluster pour basculer des adresses IP IPv6 dans Windows Server 2008 R2](http://support.microsoft.com/kb/2578113)|  
|![Case à cocher](../../media/checkboxemptycenterxtraspacetopandright.gif "Case à cocher")|√|√|Oui|**Aucun routeur entre cluster et des applications serveur**|S'il n'existe aucun routeur entre le cluster de basculement et le serveur d'applications, le service de cluster bascule lentement les ressources liées au réseau. Cela retarde les reconnexions du client après le basculement du groupe de disponibilité. En l'absence d'un routeur, nous vous recommandons d'examiner les scénarios spécifiques détaillés dans l'article KB 2582281 et d'installer le correctif logiciel, si cela s'applique à votre environnement.|Article 2582281 de la base de connaissances :  [Ralentissez l'opération de basculement s'il n'existe aucun routeur entre le cluster et un serveur d'applications](http://support.microsoft.com/kb/2582281)|  
  
###  <a name="ComputerRecommendations"></a> Recommandations pour les ordinateurs qui hébergent des réplicas de disponibilité (système Windows)  
  
-   **Systèmes comparables :**  Pour un groupe de disponibilité donné, tous les réplicas de disponibilité doivent s'exécuter sur des systèmes comparables qui peuvent gérer des charges de travail identiques.  
  
-   **Cartes réseau dédiées :**  Pour des performances optimales, utilisez une carte d’interface réseau dédiée pour [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].  
  
-   **Espace disque suffisant :**  Chaque nœud WSFC sur lequel une instance de serveur héberge un réplica de disponibilité doit posséder l'espace disque suffisant pour toutes les bases de données du groupe de disponibilité. Gardez à l'esprit qu'à mesure que le volume des bases de données primaires croît, le volume des bases de données secondaires correspondantes augmente aussi.  
  
###  <a name="PermissionsWindows"></a> Autorisations (système Windows)  
 Pour administrer un cluster WSFC, l'utilisateur doit être administrateur système sur chaque nœud de cluster.  
  
 Pour plus d’informations sur le compte permettant d’administrer le cluster, consultez [Annexe A : conditions requises pour le cluster de basculement](http://technet.microsoft.com/library/dd197454\(WS.10\).aspx).  
  
###  <a name="RelatedTasksWindows"></a> Tâches associées (système Windows)  
  
|Tâche|Lien|  
|----------|----------|  
|Définissez la valeur de HostRecordTTL.|[Modifiez HostRecordTTL (à l'aide de Windows PowerShell)](#ChangeHostRecordTTLps)|  
  
####  <a name="ChangeHostRecordTTLps"></a> Modifiez HostRecordTTL (à l'aide de Windows PowerShell)  
  
1.  Ouvrez la fenêtre PowerShell via **Exécuter en tant qu’administrateur**.  
  
2.  Importez le module FailoverClusters.  
  
3.  Utiliser le `Get-ClusterResource` applet de commande pour rechercher la ressource de nom de réseau, puis utilisez `Set-ClusterParameter` applet de commande pour définir le `HostRecordTTL` valeur, comme suit :  
  
     Get-ClusterResource "*NomRessourceRésesau>\<*" | Set-ClusterParameter HostRecordTTL *\<DuréeEnSecondes>*  
  
     L'exemple PowerShell suivant définit HostRecordTTL à 300 secondes pour une ressource de nom réseau nommée «`SQL Network Name (SQL35)`».  
  
    ```  
    Import-Module FailoverClusters  
  
    $nameResource = "SQL Network Name (SQL35)"  
    Get-ClusterResource $nameResource | Set-ClusterParameter ClusterParameter HostRecordTTL 300  
    ```  
  
    > [!TIP]  
    >  Chaque fois que vous ouvrez une nouvelle fenêtre PowerShell, vous devez importer le `FailoverClusters` module.  
  
##### <a name="related-content-powershell"></a>Contenu connexe (PowerShell)  
  
-   [Clustering and High-Availability](http://blogs.msdn.com/b/clustering/archive/2009/05/23/9636665.aspx) (Clustering et haute disponibilité) (Blog de l’équipe de clustering de basculement et d’équilibrage de la charge réseau)  
  
-   [Mise en route de Windows PowerShell sur un cluster de basculement](http://technet.microsoft.com/library/ee619762\(WS.10\).aspx)  
  
-   [Commandes de ressource de cluster et applets de commande Windows PowerShell équivalentes](http://msdn.microsoft.com/library/ee619744.aspx#BKMK_resource)  
  
###  <a name="RelatedContentWS"></a> Contenu connexe (système Windows)  
  
-   [Configurer les paramètres DNS dans un cluster de basculement multisite](http://technet.microsoft.com/library/dd197562\(WS.10\).aspx)  
  
-   [Enregistrement DNS avec ressource de nom réseau](http://blogs.msdn.com/b/clustering/archive/2009/07/17/9836756.aspx)  
  
-   [Windows 2008 R2 de basculement multisite Clustering](http://www.microsoft.com/windowsserver2008/en/us/failover-clustering-multisite.aspx)  
  
##  <a name="ServerInstance"></a> Conditions préalables requises et restrictions pour une instance de SQL Server  
 Chaque groupe de disponibilité requiert un jeu de partenaires de basculement, appelés *réplicas de disponibilité*, qui sont hébergés par les instances de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Une instance de serveur donnée peut être une *instance autonome* ou une [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]*instance de cluster de basculement* (FCI).  
  
 
  
###  <a name="PrerequisitesSI"></a> Liste de vérification : Conditions préalables requises (instance de serveur)  
  
||Condition préalable|Liens|  
|-|------------------|-----------|  
|![Case à cocher](../../media/checkboxemptycenterxtraspacetopandright.gif "Case à cocher")|L'ordinateur hôte doit se trouver sur un nœud WSFC (clustering de basculement Windows Server). Les instances de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] qui hébergent les réplicas de disponibilité d'un groupe de disponibilité donné doivent résider sur des nœuds distincts d'un même cluster WSFC. La seule exception survient lors de la migration vers un autre cluster WSFC : un groupe de disponibilité peut temporairement chevaucher deux clusters.|[Clustering de basculement Windows Server &#40;WSFC&#41; avec SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md)<br /><br /> [Clustering de basculement et groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](failover-clustering-and-always-on-availability-groups-sql-server.md)|  
|![Case à cocher](../../media/checkboxemptycenterxtraspacetopandright.gif "Case à cocher")|Si vous souhaitez qu'un groupe de disponibilité utilise Kerberos :<br /><br /> Toutes les instances de serveur qui hébergent un réplica de disponibilité pour le groupe de disponibilité doivent utiliser le même compte de service SQL Server.<br /><br /> L'administrateur de domaine doit inscrire manuellement un nom de principal de service (SPN) avec Active Directory sur le compte de service SQL Server pour le nom de réseau virtuel (VNN) de l'écouteur de groupe de disponibilité. Si le SPN est inscrit sur un compte différent du compte de service SQL Server, l'authentification échoue.<br /><br /> **\*\* Important \*\*** Si vous modifiez le compte de service SQL Server, l’administrateur de domaine devra réinscrire le SPN manuellement.|[Inscrire un nom de principal du service pour les connexions Kerberos](../../configure-windows/register-a-service-principal-name-for-kerberos-connections.md)<br /><br /> **Brève explication :**<br /><br /> Kerberos et les SPN assurent une authentification mutuelle. Le SPN est mappé au compte Windows qui démarre les services SQL Server. Si l'inscription du SPN n'est pas effectuée correctement ou échoue, la couche de sécurité Windows ne peut pas déterminer le compte associé au SPN et l'authentification Kerberos ne peut pas être utilisée.<br /><br /> Remarque : NTLM n’est pas soumis à cette condition.|  
|![Case à cocher](../../media/checkboxemptycenterxtraspacetopandright.gif "Case à cocher")|Si vous envisagez d'utiliser une instance de cluster de basculement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pour héberger un réplica de disponibilité, assurez-vous de comprendre les restrictions relatives à l'instance de cluster de basculement et de respecter les conditions préalables requises pour cette dernière.|[Restrictions et conditions préalables requises pour l’utilisation d’une instance de cluster de basculement SQL Server afin d’héberger un réplica de disponibilité](#FciArLimitations) (plus loin dans cette rubrique)|  
|![Case à cocher](../../media/checkboxemptycenterxtraspacetopandright.gif "Case à cocher")|Chaque instance de serveur doit exécuter [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]Enterprise Edition.|[Fonctionnalités prises en charge par les éditions de SQL Server 2014](../../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)|  
|![Case à cocher](../../media/checkboxemptycenterxtraspacetopandright.gif "Case à cocher")|Toutes les instances de serveur qui hébergent des réplicas de disponibilité pour un groupe de disponibilité doivent utiliser le même classement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .|[Définir ou modifier le classement du serveur](../../../relational-databases/collations/set-or-change-the-server-collation.md)|  
|![Case à cocher](../../media/checkboxemptycenterxtraspacetopandright.gif "Case à cocher")|Activez la fonctionnalité [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] sur chaque instance de serveur qui hébergera un réplica de disponibilité pour un groupe de disponibilité. Sur un ordinateur donné, vous pouvez activer autant d'instances de serveur que vous le souhaitez pour [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] , dans la limite du nombre pris en charge par votre installation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .|[Activer et désactiver les groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](enable-and-disable-always-on-availability-groups-sql-server.md)<br /><br /> **\*\* Important \*\*** Si vous supprimez et recréez un cluster WSFC, vous devez désactiver puis réactiver la fonctionnalité [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] sur chaque instance de serveur qui était activée pour les [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] sur le cluster WSFC d’origine.|  
|![Case à cocher](../../media/checkboxemptycenterxtraspacetopandright.gif "Case à cocher")|Chaque instance de serveur nécessite un point de terminaison de mise en miroir de bases de données. Notez que ce point de terminaison est partagé par tous les réplicas de disponibilité, ainsi que par tous les serveurs partenaires et témoins de mise en miroir de bases de données sur l'instance de serveur.<br /><br /> Si une instance de serveur que vous sélectionnez pour héberger un réplica de disponibilité s’exécute sous un compte d’utilisateur de domaine et n’a pas encore de point de terminaison de mise en miroir de bases de données, l’ [Assistant Nouveau groupe de disponibilité](use-the-availability-group-wizard-sql-server-management-studio.md) (ou l’ [Assistant Ajouter un réplica au groupe de disponibilité](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)) peut créer le point de terminaison et accorder l’autorisation CONNECT au compte de service de l’instance de serveur. Toutefois, si le service [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] s'exécute en tant que compte intégré, tel que Système local, Service local ou Service réseau, ou comme compte qui n'appartient pas au domaine, vous devez utiliser des certificats pour l'authentification du point de terminaison, et l'Assistant ne peut pas créer un point de terminaison de mise en miroir de bases de données sur l'instance de serveur. Dans ce cas, nous recommandons de créer les points de terminaison de mise en miroir de bases de données manuellement avant de lancer l'Assistant.<br /><br /> **\*\* Note de sécurité \*\*** La sécurité du transport pour les [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] est la même que pour la mise en miroir de bases de données.|[Point de terminaison de mise en miroir de bases de données &#40;SQL Server&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md)<br /><br /> [Sécurité du transport pour la mise en miroir de base de données et de groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](../../database-mirroring/transport-security-database-mirroring-always-on-availability.md)|  
|![Case à cocher](../../media/checkboxemptycenterxtraspacetopandright.gif "Case à cocher")|Si des bases de données utilisant FILESTREAM doivent être ajoutées à un groupe de disponibilité, vérifiez que FILESTREAM est activé sur chaque instance de serveur qui hébergera un réplica de disponibilité pour le groupe de disponibilité.|[Activer et configurer FILESTREAM](../../../relational-databases/blob/enable-and-configure-filestream.md)|  
|![Case à cocher](../../media/checkboxemptycenterxtraspacetopandright.gif "Case à cocher")|Si les bases de données de relation contenant-contenus doivent être ajoutées à un groupe de disponibilité, vérifiez que le `contained database authentication` option de serveur est définie sur `1` sur chaque instance de serveur qui hébergera un réplica de disponibilité pour le groupe de disponibilité.|[Authentification de la base de données autonome (option de configuration de serveur)](../../configure-windows/contained-database-authentication-server-configuration-option.md)<br /><br /> [Options de configuration de serveur &#40;SQL Server&#41;](../../configure-windows/server-configuration-options-sql-server.md)|  
  
###  <a name="ThreadUsage"></a> Utilisation de threads par les groupes de disponibilité  
 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] pose les conditions suivantes pour les threads de travail :  
  
-   Sur une instance [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]inactive, [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] n'utilise aucun thread.  
  
-   Le nombre maximal de threads utilisés par les groupes de disponibilité est le paramètre configuré pour le nombre maximal de threads serveur (« `max worker threads` ») moins 40.  
  
-   Les réplicas de disponibilité hébergés sur une instance de serveur spécifique partagent le même pool de threads.  
  
     Les threads sont partagés à la demande, comme suit :  
  
    -   En général, il existe 3 à 10 threads partagés, mais ce nombre peut augmenter en fonction de la charge de travail du réplica principal.  
  
    -   Si un thread donné est inactif pendant un certain temps, il est remis à disposition dans le pool de threads [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à usage général. Normalement, un thread inactif est libéré après environ 15 secondes d'inactivité. Toutefois, selon la dernière activité, un thread inactif peut être conservé plus longtemps.  
  
-   En outre, les groupes de disponibilité utilisent des threads non partagés, comme suit :  
  
    -   Chaque réplica principal utilise 1 thread de capture du journal pour chaque base de données principale. En outre, il utilise un thread d'envoi du journal pour chaque base de données secondaire. Les threads d'envoi du journal sont libérés après environ 15 secondes d'inactivité.  
  
    -   Les réplicas secondaires utilisent un thread de restauration par progression pour chaque base de données secondaire. Les threads de restauration par progression sont libérés après environ 15 secondes d'inactivité.  
  
    -   Une sauvegarde sur un réplica secondaire contient un thread sur le réplica principal pour la durée de l'opération de sauvegarde.  
  
 Pour plus d’informations, consultez [AlwaysON - HADRON Learning Series: Worker Pool Usage for HADRON Enabled Databases](http://blogs.msdn.com/b/psssql/archive/2012/05/17/alwayson-hadron-learning-series-worker-pool-usage-for-hadron-enabled-databases.aspx) (blog des ingénieurs du support technique [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]).  
  
###  <a name="PermissionsSI"></a> Autorisations (instance de serveur)  
  
|Tâche|Autorisations requises|  
|----------|--------------------------|  
|Création du point de terminaison de mise en miroir de bases de données|Requiert l'autorisation CREATE ENDPOINT ou l'appartenance au rôle serveur fixe **sysadmin** .  Requiert également l'autorisation CONTROL ON ENDPOINT. Pour plus d’informations, consultez [Autorisations de point de terminaison GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-endpoint-permissions-transact-sql).|  
|Activation de [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]|Nécessite l'appartenance au groupe **Administrateur** sur l'ordinateur local et le contrôle total sur le cluster WSFC.|  
  
###  <a name="RelatedTasksSI"></a> Tâches associées (instance de serveur)  
  
|Tâche|Rubrique|  
|----------|-----------|  
|Détermination de l'existence du point de terminaison de mise en miroir de bases de données|[sys.database_mirroring_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)|  
|Création du point de terminaison de mise en miroir de bases de données (s'il n'existe pas encore)|[Créer un point de terminaison de mise en miroir de bases de données pour l’authentification Windows &#40;Transact-SQL&#41;](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)<br /><br /> [Utiliser des certificats pour un point de terminaison de mise en miroir de bases de données &#40;Transact-SQL&#41;](../../database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)<br /><br /> [Créer une base de données mise en miroir de point de terminaison pour les groupes de disponibilité AlwaysOn &#40;SQL Server PowerShell&#41;](database-mirroring-always-on-availability-groups-powershell.md)|  
|Activation des groupes de disponibilité AlwaysOn|[Activer et désactiver les groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](enable-and-disable-always-on-availability-groups-sql-server.md)|  
  
###  <a name="RelatedContentSI"></a> Contenu connexe (instance serveur)  
  
-   [AlwaysON - HADRON Learning Series : Worker Pool Usage for HADRON Enabled Databases](http://blogs.msdn.com/b/psssql/archive/2012/05/17/alwayson-hadron-learning-series-worker-pool-usage-for-hadron-enabled-databases.aspx)  
  
##  <a name="NetworkConnect"></a> Recommandations relatives à la connectivité réseau  
 Nous vous recommandons fortement d'utiliser les mêmes liaisons réseau pour les communications entre les membres du cluster WSFC et les communications entre les réplicas de disponibilité.  L'utilisation de liaisons réseau distinctes peut provoquer des comportements inattendus en cas d'échec de certaines liaisons (et ce, même de façon intermittente).  
  
 Par exemple, pour qu'un groupe de disponibilité prenne en charge le basculement automatique, le réplica secondaire qui est le partenaire de basculement automatique doit être dans un état SYNCHRONIZED. Si la liaison réseau à ce réplica secondaire échoue (et ce, même de faon intermittente), le réplica passe à l'état UNSYNCHRONIZED et ne peut pas se resynchroniser tant que la liaison n'est pas restaurée. Si le cluster WSFC demande un basculement automatique alors que le réplica secondaire n'est pas synchronisé, le basculement automatique n'a pas lieu.  
  
##  <a name="ClientConnSupport"></a> Prise en charge de la connectivité client  
 Pour plus d’informations sur [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] prise en charge pour la connectivité client, consultez [connectivité du Client AlwaysOn (SQL Server)](always-on-client-connectivity-sql-server.md).  
  
##  <a name="FciArLimitations"></a> Conditions préalables requises et restrictions pour l'utilisation d'une instance de cluster de basculement SQL Server afin d'héberger un réplica de disponibilité  
 
  
###  <a name="RestrictionsFCI"></a> Restrictions (instances de cluster de basculement)  
  
> [!NOTE]  
>  À compter de [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)], les instances de cluster de basculement AlwaysOn prennent en charge les volumes partagés de cluster dans [!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)] et [!INCLUDE[win8srv](../../../includes/win8srv-md.md)]. Pour plus d'informations sur les volumes partagés de cluster, consultez [Présentation des volumes partagés de cluster dans un cluster de basculement](http://technet.microsoft.com/library/dd759255.aspx).  
  
-   **Les nœuds de cluster d'une instance de cluster de basculement peuvent héberger un seul réplica pour un groupe de disponibilité donné :**  Si vous ajoutez un réplica de disponibilité sur une instance de cluster de basculement, les nœuds de cluster WSFC qui sont des propriétaires d'instance de cluster de basculement potentiels ne peuvent pas héberger un autre réplica pour le même groupe de disponibilité.  
  
     En outre, chacun des autres réplicas doit être hébergé par une instance de SQL Server 2012 qui réside sur un autre nœud WSFC dans le même cluster WSFC. La seule exception survient lors de la migration vers un autre cluster WSFC : un groupe de disponibilité peut temporairement chevaucher deux clusters.  
  
-   **Les instances de cluster de basculement ne prennent pas en charge le basculement automatique par les groupes de disponibilité :**  Les instances de cluster de basculement ne prennent pas en charge le basculement automatique par les groupes de disponibilité ; par conséquent, tout réplica de disponibilité hébergé par une instance de cluster de basculement peut uniquement être configuré pour le basculement manuel.  
  
-   **Modification du nom réseau d’une instance de cluster de basculement :**  si vous devez modifier le nom réseau d’une instance de cluster de basculement qui héberge un réplica de disponibilité, vous devez supprimer le réplica de son groupe de disponibilité, puis l’ajouter de nouveau au groupe de disponibilité. Étant donné que vous ne pouvez pas supprimer le réplica principal, si vous renommez une instance de cluster de basculement qui héberge le réplica principal, vous devez basculer vers un réplica secondaire, puis supprimer le réplica principal précédent avant de l'ajouter à nouveau. Notez que l'attribution d'un nouveau nom à une instance de cluster de basculement modifie l'URL de son point de terminaison de mise en miroir de bases de données. Lorsque vous ajoutez le réplica, veillez à spécifier l'URL du point de terminaison actuel.  
  
###  <a name="PrerequisitesFCI"></a> Liste de vérification : Conditions préalables (instances de cluster de basculement)  
  
||Condition préalable|Lien|  
|-|------------------|----------|  
|![Case à cocher](../../media/checkboxemptycenterxtraspacetopandright.gif "Case à cocher")|Avant d'utiliser une instance de cluster de basculement pour héberger un réplica de disponibilité, vérifiez que votre administrateur système a installé le correctif logiciel Windows Server 2008 décrit dans l'article KB 976097 de la Base de connaissances. Ce correctif logiciel permet au composant logiciel enfichable MMC (Microsoft Management Console) de gestion de cluster de basculement de prendre en charge le stockage asymétrique des disques partagés qui ne sont accessibles qu'à certains nœuds WSFC.|Article 976097 de la base de connaissances :  [Correctif logiciel pour l'ajout du stockage asymétrique au composant logiciel enfichable MMC de gestion du cluster de basculement pour un cluster de basculement exécutant Windows Server 2008 ou Windows Server 2008 R2](http://support.microsoft.com/kb/976097)|  
|![Case à cocher](../../media/checkboxemptycenterxtraspacetopandright.gif "Case à cocher")|Vérifiez que chaque instance de cluster de basculement SQL Server dispose du stockage partagé requis, conformément à l'installation standard de l'instance de cluster de basculement SQL Server.||  
  
###  <a name="RelatedTasksFCIs"></a> Tâches associées (instances de cluster de basculement)  
  
|Tâche|Rubrique|  
|----------|-----------|  
|Installation d'un cluster de basculement SQL Server|[Créer un cluster de basculement SQL Server &#40;programme d’installation&#41;](../../../sql-server/failover-clusters/install/create-a-new-sql-server-failover-cluster-setup.md)|  
|Mise à niveau sur place de votre cluster de basculement SQL Server existant|[Mettre à niveau une instance de cluster de basculement SQL Server &#40;programme d’installation&#41;](../../../sql-server/failover-clusters/windows/upgrade-a-sql-server-failover-cluster-instance-setup.md)|  
|Maintenance de votre cluster de basculement SQL Server existant|[Ajouter ou supprimer des nœuds dans un cluster de basculement SQL Server &#40;programme d’installation&#41;](../../../sql-server/failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)|  
  
###  <a name="RelatedContentFCIs"></a> Contenu connexe (instances de cluster de basculement)  
  
-   [Clustering de basculement et groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](failover-clustering-and-always-on-availability-groups-sql-server.md)  
  
-   [Guide de l’Architecture AlwaysOn : Création d’une haute disponibilité et la Solution de récupération d’urgence à l’aide d’Instances de Cluster de basculement et groupes de disponibilité](http://technet.microsoft.com/library/jj215886.aspx)  
  
##  <a name="PrerequisitesForAGs"></a> Conditions préalables requises et restrictions pour les groupes de disponibilité  

  
###  <a name="RestrictionsAG"></a> Restrictions (groupes de disponibilité)  
  
-   **Les réplicas de disponibilité doivent être hébergés par différents nœuds d'un cluster WSFC :**  Pour un groupe de disponibilité donné, les réplicas de disponibilité doivent être hébergés par des instances de serveur qui s'exécutent sur différents nœuds du même cluster WSFC. La seule exception survient lors de la migration vers un autre cluster WSFC : un groupe de disponibilité peut temporairement chevaucher deux clusters.  
  
    > [!NOTE]  
    >  Les ordinateurs virtuels situés sur le même ordinateur physique peuvent chacun héberger un réplica de disponibilité pour le même groupe de disponibilité, étant donné que chaque ordinateur virtuel agit en tant qu'ordinateur distinct.  
  
-   **Nom de groupe de disponibilité unique :**  Chaque nom de groupe de disponibilité doit être unique sur le cluster WSFC. La longueur maximale d'un nom de groupe de disponibilité est de 128 caractères.  
  
-   **Réplicas de disponibilité :**  chaque groupe de disponibilité prend en charge un réplica principal et jusqu'à huit réplicas secondaires. Tous les réplicas peuvent s'exécuter en mode de validation asynchrone, ou au plus trois d'entre eux peuvent s'exécuter en mode de validation synchrone (un réplica principal et deux réplicas secondaires synchrones).  
  
-   **Nombre maximal de groupes de disponibilité et de bases de données de disponibilité par ordinateur :** le nombre réel de bases de données et de groupes de disponibilité que vous pouvez mettre sur un ordinateur (virtuel ou physique) dépend du matériel et de la charge de travail, mais il n’existe aucune limite imposée. Microsoft a largement testé des systèmes comportant 10 100 groupes de disponibilité et 100 bases de données par ordinateur physique. Les signes d'un système surchargé incluent, notamment, l'épuisement des threads de travail, des temps de réponse longs pour les vues système et les vues de gestion dynamique AlwaysOn et/ou des vidages de système de répartiteur bloqués. Veillez à tester soigneusement votre environnement avec une charge de travail semblable à celle de production pour vous assurer qu'il peut gérer la capacité de pointe conformément au contrat de niveau de service de l'application. Lorsque vous choisissez les contrats de niveau de service, assurez-vous de prendre en compte la charge en conditions d'échec ainsi que les temps de réponse attendus.  
  
-   **N'utilisez pas le gestionnaire du cluster de basculement pour manipuler des groupes de disponibilité :**  
  
     Exemple :  
  
    -   Ne modifiez pas les propriétés du groupe de disponibilité, telles que les propriétaires possibles.  
  
    -   N'utilisez pas le gestionnaire du cluster de basculement pour basculer des groupes de disponibilité. Vous devez utiliser [!INCLUDE[tsql](../../../includes/tsql-md.md)] ou [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].  
  
###  <a name="RequirementsAG"></a> Conditions préalables requises (groupes de disponibilité)  
 Lors de la création ou de la reconfiguration d'un groupe de disponibilité, veillez à respecter les conditions préalables requises suivantes.  
  
||Condition préalable|Description|  
|-|------------------|-----------------|  
|![Case à cocher](../../media/checkboxemptycenterxtraspacetopandright.gif "Case à cocher")|Si vous envisagez d'utiliser une instance de cluster de basculement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pour héberger un réplica de disponibilité, assurez-vous de comprendre les restrictions relatives à l'instance de cluster de basculement et de respecter les conditions préalables requises pour cette dernière.|[Conditions préalables requises et restrictions pour l’utilisation d’une instance de cluster de basculement SQL Server afin d’héberger un réplica de disponibilité](#FciArLimitations) (plus haut dans cette rubrique)|  
  
###  <a name="SecurityAG"></a> Sécurité (groupes de disponibilité)  
  
-   La sécurité est héritée du cluster WSFC (clustering de basculement Windows Server). WSFC fournit deux niveaux de sécurité utilisateur en fonction de la granularité des API de cluster entières :  
  
    -   Accès en lecture seule  
  
    -   Contrôle total  
  
         [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] nécessite un contrôle total, et l’activation de [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] sur une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] lui donne le contrôle total du cluster WSFC (par le biais du SID du service).  
  
         Vous ne pouvez pas ajouter ou supprimer directement la sécurité d'une instance de serveur dans le Gestionnaire de cluster de basculement WSFC. Pour gérer les sessions de sécurité de WSFC, utilisez le Gestionnaire de configuration de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ou le WMI équivalent de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Chaque instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] doit disposer des autorisations d'accès au Registre, cluster, etc.  
  
-   Nous vous recommandons d'utiliser le chiffrement pour les connexions entre des instances de serveur qui hébergent des réplicas de disponibilité [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] .  
  
#### <a name="permissions-availability-groups"></a>Autorisations (groupes de disponibilité)  
  
|Tâche|Autorisations requises|  
|----------|--------------------------|  
|Création d'un groupe de disponibilité|Requiert l’appartenance au rôle serveur fixe **sysadmin** et l’autorisation de serveur CREATE AVAILABILITY GROUP, l’autorisation ALTER ANY AVAILABILITY GROUP ou l’autorisation CONTROL SERVER.|  
|Modification d'un groupe de disponibilité|Requiert l'autorisation ALTER AVAILABILITY GROUP sur le groupe de disponibilité, l'autorisation CONTROL AVAILABILITY GROUP, l'autorisation ALTER ANY AVAILABILITY GROUP ou l'autorisation CONTROL SERVER.<br /><br /> En outre, la jointure d’une base de données à un groupe de disponibilité nécessite l’appartenance au rôle de base de données fixe **db_owner** .|  
|Suppression d'un groupe de disponibilité|Requiert l'autorisation ALTER AVAILABILITY GROUP sur le groupe de disponibilité, l'autorisation CONTROL AVAILABILITY GROUP, l'autorisation ALTER ANY AVAILABILITY GROUP ou l'autorisation CONTROL SERVER. Pour supprimer un groupe de disponibilité qui n'est pas hébergé à l'emplacement du réplica local, vous avez besoin de l'autorisation CONTROL SERVER ou CONTROL sur ce groupe de disponibilité.|  
  
###  <a name="RelatedTasksAGs"></a> Tâches associées (groupes de disponibilité)  
  
|Tâche|Rubrique|  
|----------|-----------|  
|Création d'un groupe de disponibilité|[Utiliser le groupe de disponibilité (Assistant Nouveau groupe de disponibilité)](use-the-availability-group-wizard-sql-server-management-studio.md)<br /><br /> [Créer un groupe de disponibilité (Transact-SQL)](create-an-availability-group-transact-sql.md)<br /><br /> [Créer un groupe de disponibilité (SQL Server PowerShell)](../../../powershell/sql-server-powershell.md)<br /><br /> [Spécifier l’URL de point de terminaison lors de l’ajout ou lors de la modification d’un réplica de disponibilité &#40;SQL Server&#41;](specify-endpoint-url-adding-or-modifying-availability-replica.md)|  
|Modification du nombre de réplicas de disponibilité|[Ajouter un réplica secondaire à un groupe de disponibilité &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md)<br /><br /> [Joindre un réplica secondaire à un groupe de disponibilité &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)<br /><br /> [Supprimer un réplica secondaire d’un groupe de disponibilité &#40;SQL Server&#41;](remove-a-secondary-replica-from-an-availability-group-sql-server.md)|  
|Création d'un écouteur de groupe de disponibilité|[Créer ou configurer un écouteur de groupe de disponibilité &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)|  
|Suppression d'un groupe de disponibilité|[Supprimer un groupe de disponibilité &#40;SQL Server&#41;](remove-an-availability-group-sql-server.md)|  
  
##  <a name="PrerequisitesForDbs"></a> Conditions préalables requises et restrictions pour les bases de données de disponibilité  
 Pour pouvoir être ajoutée à un groupe de disponibilité, une base de données doit respecter les Conditions préalables requises et restrictions suivantes.  
  
 
  
###  <a name="RequirementsDb"></a> Liste de vérification : Conditions préalables requises (bases de données de disponibilité)  
 Pour pouvoir être ajoutée à un groupe de disponibilité, une base de données :  
  
||Spécifications|Lien|  
|-|------------------|----------|  
|![Case à cocher](../../media/checkboxemptycenterxtraspacetopandright.gif "Case à cocher")|doit être une base de données utilisateur. Les bases de données système ne peuvent pas appartenir à un groupe de disponibilité ;||  
|![Case à cocher](../../media/checkboxemptycenterxtraspacetopandright.gif "Case à cocher")|doit résider sur l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] où vous créez le groupe de disponibilité et être accessible à l'instance de serveur ;||  
|![Case à cocher](../../media/checkboxemptycenterxtraspacetopandright.gif "Case à cocher")|doit être une base de données en lecture/écriture. Les bases de données en lecture seule ne peuvent pas être ajoutées à un groupe de disponibilité ;|[sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) (**is_read_only** = 0)|  
|![Case à cocher](../../media/checkboxemptycenterxtraspacetopandright.gif "Case à cocher")|doit être une base de données multi-utilisateur ;|[sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) (**user_access** = 0)|  
|![Case à cocher](../../media/checkboxemptycenterxtraspacetopandright.gif "Case à cocher")|ne doit pas utiliser AUTO_CLOSE ;|[sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) (**is_auto_close_on** = 0)|  
|![Case à cocher](../../media/checkboxemptycenterxtraspacetopandright.gif "Case à cocher")|Utilisez le mode de récupération complète (également appelé modèle de récupération complète).|[sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) (**recovery_model** = 1)|  
|![Case à cocher](../../media/checkboxemptycenterxtraspacetopandright.gif "Case à cocher")|Possédez au moins une sauvegarde complète de base de données.<br /><br /> Remarque : une fois que vous avez défini une base de données en mode de récupération complète, une sauvegarde complète est requise pour initialiser la séquence de journaux de récupération complète.|[Créer une sauvegarde complète de base de données &#40;SQL Server&#41;](../../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)|  
|![Case à cocher](../../media/checkboxemptycenterxtraspacetopandright.gif "Case à cocher")|ne doit pas appartenir à un groupe de disponibilité existant ;|[sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) (**group_database_id** = NULL)|  
|![Case à cocher](../../media/checkboxemptycenterxtraspacetopandright.gif "Case à cocher")|ne doit pas être configurée pour la mise en miroir de base de données.|[sys.database_mirroring](/sql/relational-databases/system-catalog-views/sys-database-mirroring-transact-sql) (Si la base de données ne participe pas à la mise en miroir, toutes les colonnes qui utilisent le préfixe « mirroring » ont la valeur NULL.)|  
|![Case à cocher](../../media/checkboxemptycenterxtraspacetopandright.gif "Case à cocher")|Avant d'ajouter une base de données qui utilise FILESTREAM à un groupe de disponibilité, vérifiez que FILESTREAM est activé sur chaque instance de serveur qui héberge ou hébergera un réplica de disponibilité pour le groupe de disponibilité.|[Activer et configurer FILESTREAM](../../../relational-databases/blob/enable-and-configure-filestream.md)|  
|![Case à cocher](../../media/checkboxemptycenterxtraspacetopandright.gif "Case à cocher")|Avant d’ajouter une relation contenant-contenu de la base de données à un groupe de disponibilité, vérifiez que le `contained database authentication` option de serveur est définie sur `1` sur chaque serveur de l’instance qui héberge ou hébergera un réplica de disponibilité pour le groupe de disponibilité.|[Authentification de la base de données autonome (option de configuration de serveur)](../../configure-windows/contained-database-authentication-server-configuration-option.md)<br /><br /> [Options de configuration de serveur &#40;SQL Server&#41;](../../configure-windows/server-configuration-options-sql-server.md)|  
  
> [!NOTE]  
>  [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] fonctionne avec tous les niveaux de compatibilité de base de données pris en charge.  
  
###  <a name="RestrictionsDb"></a> Restrictions (bases de données de disponibilité)  
  
-   Si le chemin d'accès du fichier (notamment la lettre de lecteur) d'une base de données secondaire diffère du chemin d'accès de la base de données primaire correspondante, les restrictions suivantes s'appliquent :  
  
    -   **[!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)]/[!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)]:**  L’option **Complète** n’est pas prise en charge (dans la page[Sélectionner la synchronisation de données initiale](select-initial-data-synchronization-page-always-on-availability-group-wizards.md) ).  
  
    -   **RESTORE WITH MOVE :**  Pour créer les bases de données secondaires, les fichiers de base de données doivent avoir l'état RESTORED WITH MOVE sur chaque instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] qui héberge un réplica secondaire.  
  
    -   **Incidence sur les opérations d’ajout de fichier :**  Une opération d’ajout de fichier ultérieure sur le réplica principal peut échouer sur les bases de données secondaires. Cet échec peut entraîner l'interruption des bases de données secondaires. Par voie de conséquence, les réplicas secondaires passent à l'état NOT SYNCHRONIZING.  
  
        > [!NOTE]  
        >  Pour plus d’informations sur la marche à suivre en cas d’échec d’une opération d’ajout de fichier, consultez [Résoudre une opération d’ajout de fichier ayant échoué &#40;groupes de disponibilité AlwaysOn&#41;](troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md).  
  
-   Vous ne pouvez pas supprimer une base de données qui appartient à un groupe de service.  
  
###  <a name="TDEdbs"></a> Suivi des bases de données protégées par le chiffrement transparent des données  
 Si vous utilisez le chiffrement transparent des données (TDE), le certificat ou la clé asymétrique pour la création et le déchiffrement d'autres clés doit être identique sur chaque instance de serveur qui héberge un réplica de disponibilité pour le groupe de disponibilité. Pour plus d’informations, consultez [Déplacer une base de données protégée par le chiffrement transparent des données vers un autre serveur SQL Server](../../../relational-databases/security/encryption/move-a-tde-protected-database-to-another-sql-server.md).  
  
###  <a name="PermissionsDbs"></a> Autorisations (bases de données de disponibilité)  
 Nécessite l'autorisation ALTER sur la base de données.  
  
###  <a name="RelatedTasksADb"></a> Tâches associées (bases de données de disponibilité)  
  
|Tâche|Rubrique|  
|----------|-----------|  
|Préparation d'une base de données secondaire (manuellement)|[Préparer manuellement une base de données secondaire pour un groupe de disponibilité &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)|  
|Jointure d'une base de données secondaire à un groupe de disponibilité (manuellement)|[Joindre une base de données secondaire à un groupe de disponibilité &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)|  
|Modification du nombre de bases de données de disponibilité|[Ajouter une base de données à un groupe de disponibilité &#40;SQL Server&#41;](availability-group-add-a-database.md)<br /><br /> [Supprimer une base de données secondaire d’un groupe de disponibilité &#40;SQL Server&#41;](remove-a-secondary-database-from-an-availability-group-sql-server.md)<br /><br /> [Supprimer une base de données primaire d’un groupe de disponibilité &#40;SQL Server&#41;](remove-a-primary-database-from-an-availability-group-sql-server.md)|  
  
##  <a name="RelatedContent"></a> Contenu associé  
  
-   [Guide de Solutions Microsoft SQL Server AlwaysOn pour une haute disponibilité et récupération d’urgence](http://go.microsoft.com/fwlink/?LinkId=227600)  
  
-   [Blog de l’équipe AlwaysOn SQL Server : Le Blog officiel de SQL Server AlwaysOn Team](http://blogs.msdn.com/b/sqlalwayson/)  
  
-   [AlwaysON - HADRON Learning Series : Worker Pool Usage for HADRON Enabled Databases](http://blogs.msdn.com/b/psssql/archive/2012/05/17/alwayson-hadron-learning-series-worker-pool-usage-for-hadron-enabled-databases.aspx)  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Clustering de basculement et groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](failover-clustering-and-always-on-availability-groups-sql-server.md)   
 [Connectivité Client AlwaysOn (SQL Server)](always-on-client-connectivity-sql-server.md)  
  
  
