---
title: Configurer le service Integration Services en tant que ressource de cluster | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 367835aa-9855-4791-a989-b3d08402ad4c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 01d572424691ae14b8c75fa594327eef3fbd9504
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85434896"
---
# <a name="configure-the-integration-services-service-as-a-cluster-resource"></a>Configurer le service Integration Services en tant que ressource de cluster
  Pour les clients concluant que les avantages de la configuration du service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] en tant que ressource de cluster compensent les inconvénients, cette section contient les instructions de configuration nécessaires. [!INCLUDE[msCoName](../includes/msconame-md.md)] ne recommande toutefois pas de configurer le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] en tant que ressource de cluster.  
  
 Pour configurer le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] en tant que ressource de cluster, vous devez effectuer les tâches suivantes.  
  
-   Installez [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sur un cluster.  
  
     Pour installer [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sur un cluster, vous devez installer [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sur chaque nœud du cluster.  
  
-   Configurez [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] en tant que ressource de cluster.  
  
     Integration Services étant installé sur chaque nœud du cluster, vous devez le configurer en tant que ressource de cluster. Lorsque vous configurez le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] en tant que ressource de cluster, vous pouvez ajouter le service au même groupe de ressources que le [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]ou à un groupe différent. Le tableau suivant présente les avantages et inconvénients possibles de la sélection d'un groupe de ressources.  
  
    |Lorsque Integration Services et SQL Server se trouvent dans le même groupe de ressources|Lorsque Integration Services et SQL Server se trouvent dans des groupes de ressources différents|  
    |-----------------------------------------------------------------------------|-------------------------------------------------------------------------------|  
    |Les ordinateurs clients peuvent utiliser [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] pour gérer des packages stockés dans la base de données msdb, car le [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] et le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] s’exécutent tous deux sur le même serveur virtuel. Cette configuration évite les problèmes de délégation du scénario double saut.|Les ordinateurs clients ne peuvent pas utiliser [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] pour gérer des packages stockés dans la base de données msdb. Le client peut se connecter au serveur virtuel sur lequel le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] s’exécute. Toutefois, cet ordinateur ne peut pas déléguer les informations d'identification de l'utilisateur au serveur virtuel sur lequel [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] s'exécute. Ce scénario est appelé scénario double saut.|  
    |Le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] est en concurrence avec d'autres services [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] pour les ressources de processeurs et d'autres ressources informatiques.|Le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] n'est pas en concurrence avec d'autres services [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] pour les ressources de processeurs et d'autres ressources informatiques, car les différents groupes de ressources sont configurés sur des nœuds différents.|  
    |Le chargement et l'enregistrement de packages dans la base de données msdb sont plus rapides et génèrent moins de trafic réseau parce que les deux services s'exécutent sur le même ordinateur.|Le chargement et l'enregistrement de packages dans la base de données msdb peuvent être plus lents et générer plus de trafic réseau.|  
    |Les deux services sont en ligne ou hors connexion en même temps.|Le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] peut être en ligne pendant que le [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] est hors connexion. Ainsi, les packages stockés dans la base de données msdb du [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] ne sont pas disponibles.|  
    |Le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ne peut pas être déplacé rapidement vers un autre nœud si nécessaire.|Le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] peut être déplacé plus rapidement vers un autre nœud si nécessaire.|  
  
     Une fois que vous avez choisi le groupe de ressources auquel vous ajouterez [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], vous devez configurer [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] en tant que ressource de cluster dans ce groupe.  
  
-   Configurez le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] et le magasin de packages.  
  
     Une fois que vous avez configuré [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] en tant que ressource de cluster, vous devez modifier l'emplacement et le contenu du fichier de configuration du service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sur chaque nœud du cluster. Grâce à ces modifications, le fichier de configuration et le magasin de packages sont à la disposition de tous les nœuds en cas de basculement. Après avoir modifié l'emplacement et le contenu du fichier de configuration, vous devez mettre le service en ligne.  
  
-   Mettez le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] en ligne en tant que ressource de cluster.  
  
 Après la configuration du service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sur un cluster ou un serveur, vous devrez peut-être configurer des autorisations DCOM pour parvenir à vous connecter au service à partir d'un ordinateur client. Pour plus d’informations, consultez [Se connecter à un serveur Integration Services distant &#40;Service SSIS&#41;](../../2014/integration-services/connect-to-a-remote-integration-services-server-ssis-service.md).  
  
 Le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ne peut pas déléguer d'informations d'identification. Par conséquent, vous ne pouvez pas utiliser [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] pour gérer les packages stockés dans la base de données msdb dans les conditions suivantes :  
  
-   Le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] et [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] s'exécutent sur des serveurs distincts ou des serveurs virtuels.  
  
-   Le client qui exécute [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] est un troisième ordinateur.  
  
 Le client peut se connecter au serveur virtuel sur lequel le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] s’exécute. Toutefois, cet ordinateur ne peut pas déléguer les informations d'identification de l'utilisateur au serveur virtuel sur lequel [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] s'exécute. Ce scénario est appelé scénario double saut.  
  
### <a name="to-install-integration-services-on-a-cluster"></a>Pour installer Integration Services sur un cluster  
  
1.  Installez et configurez un cluster avec un ou plusieurs nœuds.  
  
2.  (Facultatif) Installez des services cluster, par exemple le [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)].  
  
3.  Installez [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sur chaque nœud du cluster.  
  
### <a name="to-configure-integration-services-as-a-cluster-resource"></a>Pour configurer Integration Services en tant que ressource de cluster  
  
1.  Ouvrez l' **Administrateur de clusters**.  
  
2.  Dans l'arborescence de la console, sélectionnez le dossier Groupes.  
  
3.  Dans le volet de résultats, sélectionnez le groupe auquel vous prévoyez d'ajouter [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]:  
  
    -   Pour ajouter Integration Services en tant que ressource de cluster au même groupe de ressources que [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], sélectionnez le groupe auquel [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] appartient.  
  
    -   Pour ajouter Integration Services en tant que ressource de cluster à un groupe différent de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], sélectionnez un groupe autre que le groupe auquel [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] appartient.  
  
4.  Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Ressource**.  
  
5.  Dans la page **Nouvelle ressource** de l’Assistant Ressource, tapez un nom et sélectionnez **Service générique** comme **Type de service**. Ne modifiez pas la valeur de **Groupe**. Cliquez sur **Suivant**.  
  
6.  Dans la page **Propriétaires possibles** , ajoutez ou supprimez les nœuds du cluster en tant que propriétaires possibles de la ressource. Cliquez sur **Suivant**.  
  
7.  Pour ajouter des dépendances, dans la page **Dépendances** , sélectionnez une ressource sous **Ressources disponibles**, puis cliquez sur **Ajouter**. En cas de basculement, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et le disque partagé qui stocke les packages [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] doivent être de nouveau en ligne avant la mise en ligne d' [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Après avoir sélectionné les dépendances, cliquez sur **Suivant**.  
  
     Pour en savoir plus, voir [Add Dependencies to a SQL Server Resource](../sql-server/failover-clusters/windows/add-dependencies-to-a-sql-server-resource.md).  
  
8.  Sur la page **Paramètres de service générique** , saisissez **MsDtsServer** dans la zone du nom de service. Cliquez sur **Suivant**.  
  
9. Dans la page **Réplication du Registre** , cliquez sur **Ajouter** pour ajouter la clé de Registre qui identifie l'emplacement du fichier de configuration du service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Ce fichier doit se trouver sur un disque partagé situé dans le même groupe de ressources que le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
10. Dans la boîte de dialogue **Clé de Registre** , tapez **SOFTWARE\Microsoft\Microsoft SQL Server\100\SSIS\ServiceConfigFile**. Cliquez sur **OK**, puis sur **Terminer**.  
  
     Le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] a maintenant été ajouté en tant que ressource de cluster.  
  
### <a name="to-configure-the-integration-services-service-and-package-store"></a>Pour configurer le service Integration Services et le magasin de packages  
  
1.  Localisez le fichier de configuration à l'emplacement %ProgramFiles%\Microsoft SQL Server\100\DTS\Binn\MsDtsSrvr.ini.xml. Copiez-le sur le disque partagé du groupe auquel vous avez ajouté le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
2.  Sur le disque partagé, créez un dossier nommé **Packages** , qui doit servir de magasin de packages. Accordez aux groupes et utilisateurs appropriés des autorisations en écriture et pour répertorier des dossiers sur le nouveau dossier.  
  
3.  Sur le disque partagé, ouvrez le fichier de configuration dans un éditeur de texte ou XML. Remplacez la valeur de l'élément `ServerName` par le nom du serveur virtuel [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] qui se trouve dans le même groupe de ressources.  
  
4.  Remplacez la valeur de l' `StorePath` élément par le chemin d’accès complet du dossier **packages** créé sur le disque partagé lors d’une étape précédente.  
  
5.  Mettez à jour la valeur de la clé **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\SSIS\ServiceConfigFile** dans le Registre en indiquant le nom et le chemin complet du fichier de configuration du service sur le disque partagé.  
  
### <a name="to-bring-the-integration-services-service-online"></a>Pour mettre le service Integration Services en ligne  
  
-   Dans **l’Administrateur de clusters**, sélectionnez le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , cliquez avec le bouton droit et sélectionnez **Mettre en ligne** dans le menu contextuel. Le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] est maintenant en ligne en tant que ressource de cluster.  
  
  
