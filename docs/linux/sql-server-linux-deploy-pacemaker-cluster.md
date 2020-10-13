---
title: Déployer un cluster Pacemaker pour SQL Server sur Linux
description: Découvrez comment déployer un cluster Pacemaker Linux pour un groupe de disponibilité Always On SQL Server (AG) ou une instance de cluster de basculement(FCI).
author: VanMSFT
ms.author: vanto
ms.reviewer: vanto
ms.date: 12/11/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: b2e5c3adb5f04f3e138b1d0644a047b8a443fde7
ms.sourcegitcommit: 610e3ebe21ac6575850a29641a32f275e71557e3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2020
ms.locfileid: "91785176"
---
# <a name="deploy-a-pacemaker-cluster-for-sql-server-on-linux"></a>Déployer un cluster Pacemaker pour SQL Server sur Linux

[!INCLUDE [SQL Server - Linux](../includes/applies-to-version/sql-linux.md)]

Ce tutoriel décrit les tâches requises pour déployer un cluster Pacemaker Linux pour un groupe de disponibilité Always On [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] ou une instance de cluster de basculement(FCI). Contrairement à la pile Windows Server/[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] étroitement couplée, la création du cluster Pacemaker et la configuration du groupe de disponibilité sur Linux peuvent être effectuées avant ou après l’installation de [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]. L’intégration et la configuration des ressources pour la partie Pacemaker d’un déploiement de groupe de disponibilité ou d’instance de cluster de basculement (FCI) sont effectuées après la configuration du cluster.
> [!IMPORTANT]
> Un groupe de disponibilité avec un cluster de type Aucun *ne* requiert pas de cluster Pacemaker cluster et ne peut pas être managé par Pacemaker. 

> [!div class="checklist"]
> * Installer le module complémentaire de haute disponibilité et installer Pacemaker.
> * Préparez les nœuds pour Pacemaker (RHEL et Ubuntu uniquement).
> * Créez le cluster Pacemaker.
> * Installez les packages HA et SQL Server Agent de SQL Server.
 
## <a name="prerequisite"></a>Configuration requise
[Installer SQL Server 2017](sql-server-linux-setup.md).

## <a name="install-the-high-availability-add-on"></a>Installer le module complémentaire de haute disponibilité
Utilisez la syntaxe suivante pour installer les packages qui composent le module complémentaire de haute disponibilité (HA) pour chaque distribution de Linux. 

**Red Hat Enterprise Linux (RHEL)**
1.  Inscrivez le serveur à l’aide de la syntaxe suivante. Vous êtes invité à entrer un nom d’utilisateur et un mot de passe valides.
    
    ```bash
    sudo subscription-manager register
    ```
    
2.  Répertoriez les pools disponibles pour l’inscription.
    
    ```bash
    sudo subscription-manager list --available
    ```

3.  Exécutez la commande suivante pour associer la haute disponibilité RHEL à l’abonnement
    
    ```bash
    sudo subscription-manager attach --pool=<PoolID>
    ```
    
    ou *PoolId* est l’ID de pool pour l’abonnement de haute disponibilité de l’étape précédente.
    
4.  Activez le référentiel pour pouvoir utiliser le module complémentaire de haute disponibilité.
    
    ```bash
    sudo subscription-manager repos --enable=rhel-ha-for-rhel-7-server-rpms
    ```
    
5.  Installez Pacemaker.
    
    ```bash
    sudo yum install pacemaker pcs fence-agents-all resource-agents
    ```

**Ubuntu**

```bash
sudo apt-get install pacemaker pcs fence-agents resource-agents
```

**SUSE Linux Enterprise Server (SLES)**

Installez le modèle de haute disponibilité dans YaST ou faites-le dans le cadre de l’installation principale du serveur. L’installation peut être effectuée avec une source ISO/DVD ou en ligne.
> [!NOTE]
> Sur SLES, le module complémentaire de haute disponibilité est initialisé lors de la création du cluster.

## <a name="prepare-the-nodes-for-pacemaker-rhel-and-ubuntu-only"></a>Préparez les nœuds pour Pacemaker (RHEL et Ubuntu uniquement)
Pacemaker proprement dit utilise un utilisateur créé sur la distribution nommée *hacluster*. L’utilisateur est créé lorsque le module complémentaire de haute disponibilité est installé sur RHEL et Ubuntu.
1. Sur chaque serveur qui servira de nœud au cluster Pacemaker, créez le mot de passe d’un utilisateur qui sera utilisé par le cluster. Le nom utilisé dans les exemples est *hacluster*, mais vous pouvez utiliser n’importe quel nom. Le nom et le mot de passe doivent être identiques sur tous les nœuds participant au cluster Pacemaker.
   
    ```bash
    sudo passwd hacluster
    ```
    
2. Sur chaque nœud qui fera partie du cluster Pacemaker, activez et démarrez le service `pcsd` avec les commandes suivantes (RHEL et Ubuntu) :

   ```bash
   sudo systemctl enable pcsd
   sudo systemctl start pcsd
   ```
   
   Exécutez ensuite
   
   ```bash
   sudo systemctl status pcsd
   ```
   
   pour vous assure que `pcsd` a démarré.
3. Activez le service Pacemaker sur chaque nœud possible du cluster du même nom.
   
   ```bash
   sudo systemctl start pacemaker
   ```

   Sur Ubuntu, une erreur s’affiche :
   
   *Le démarrage par défaut de Pacemaker n’a pas de niveaux d’exécution, abandon en cours.*
   
   Cette erreur est un problème connu. En dépit de l’erreur, le service Pacemaker peut être activé et ce bogue sera corrigé à un moment donné dans le futur.
   
4. Ensuite, créez et démarrez le cluster Pacemaker. Il y a une différence entre RHEL et Ubuntu à ce stade. Lors des deux distributions, l'installation de `pcs` configure un fichier de configuration par défaut pour le cluster Pacemaker, sur RHEL. L’exécution de cette commande détruit toute configuration existante et crée un cluster.

<a id="create"></a>
## <a name="create-the-pacemaker-cluster"></a>Créez le cluster Pacemaker 
Cette section décrit comment créer et configurer le cluster pour chaque distribution de Linux.

**RHEL**

1. Autoriser les nœuds
   
   ```bash
   sudo pcs cluster auth <Node1 Node2 ... NodeN> -u hacluster
   ```
   
   où *NodeX* est le nom du nœud.
2. Créer le cluster
   
   ```bash
   sudo pcs cluster setup --name <PMClusterName Nodelist> --start --all --enable
   ```
   
   où *PMClusterName* est le nom attribué au cluster Pacemaker et *Nodelist* la liste des noms des nœuds séparés par une espace.

**Ubuntu**

La configuration d’Ubuntu est similaire à celle de RHEL. Toutefois, il y a une différence majeure : l’installation des packages Pacemaker crée une configuration de base pour le cluster et active et démarre `pcsd`. Si vous essayez de configurer le cluster Pacemaker en suivant à la lettre les instructions RHEL, vous recevez un message d’erreur. Pour résoudre ce problème, procédez comme suit : 
1. Supprimez la configuration par défaut de Pacemaker de chaque nœud.
   
   ```bash
   sudo pcs cluster destroy
   ```
   
2. Suivez les étapes de la section RHEL pour créer le cluster Pacemaker.

**SLES**

Le processus de création d’un cluster Pacemaker est complètement différent sur SLES par rapport à RHEL et à Ubuntu. Les étapes suivantes décrivent comment créer un cluster avec SLES.
1. Démarrez le processus de configuration du cluster en l’exécutant 
   ```bash
   sudo ha-cluster-init
   ``` 
   
   sur l’un des nœuds. Vous pouvez être informé que NTP n’est pas configuré et qu’aucun appareil de surveillance n’a été trouvé. C’est parfait pour la mise en service. L’appareil de surveillance est lié à STONITH si vous utilisez la délimitation intégrée de SLES, qui est basée sur le stockage. NTP et l’appareil de surveillance peuvent être configurés ultérieurement.
   
2. Vous êtes invité à configurer Corosync. Vous êtes invité à entrer l’adresse réseau à lier, ainsi que l’adresse et le port de multidiffusion. L’adresse réseau est le sous-réseau que vous utilisez ; par exemple, 192.191.190.0. Vous pouvez accepter les valeurs par défaut à chaque invite, ou les modifier si nécessaire.
   
3. Ensuite, on vous demande si vous souhaitez configurer SBD, qui est la délimitation basée sur le disque. Cette configuration peut être effectuée ultérieurement si vous le souhaitez. Si SBD n’est pas configuré, contrairement à ce qui est le cas pour RHEL et pour Ubuntu , `stonith-enabled` est défini par défaut sur false.
   
4. Enfin, on vous demande si vous souhaitez configurer une adresse IP pour l’administration. Cette adresse IP est facultative, mais elle fonctionne de manière similaire à l’adresse IP d’un cluster de basculement Windows Server (WSFC), dans la mesure où elle crée une adresse IP dans le cluster à utiliser pour s’y connecter via la haute disponibilité Web Konsole (HAWK). Cette configuration est également facultative.
   
5. Assurez-vous que le cluster est opérationnel en émettant 
   ```bash
   sudo crm status
   ```
   
6. Modifier le mot de passe *hacluster* avec 
   ```bash
   sudo passwd hacluster
   ```
   
7. Si vous avez configuré une adresse IP pour l’administration, vous pouvez la tester dans un navigateur, ce qui permet également de tester la modification du mot de passe pour *hacluster*.
   ![hacLuster](./media/sql-server-linux-deploy-pacemaker-cluster/image2.png)
   
8. Sur un autre serveur SLES qui sera un nœud du cluster, exécutez 
   ```bash
   sudo ha-cluster-join
   ```
   
9. Lorsque vous y êtes invité, entrez le nom ou l’adresse IP du serveur qui a été configuré en tant que premier nœud du cluster lors des étapes précédentes. Le serveur est ajouté en tant que nœud au cluster existant.
   
10. Vérifiez que le nœud a été ajouté en émettant 
   ```bash
   sudo crm status
   ```
   
11. Modifier le mot de passe *hacluster* avec 
   ```bash
   sudo passwd hacluster
   ```
   
12. Répétez les étapes 8 à 11 pour tous les autres serveurs à ajouter au cluster.

## <a name="install-the-sql-server-ha-and-sql-server-agent-packages"></a>Installez les packages HA et SQL Server Agent de SQL Server
Utilisez les commandes suivantes pour installer le package SQL Server de haute disponibilité et l’agent [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] s’ils ne sont pas encore installés. L’installation du package de haute disponibilité après l’installation de [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] requiert un redémarrage de [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] pour pouvoir être utilisé. Ces instructions supposent que les référentiels des packages Microsoft ont déjà été configurés, car [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] doit être installé à ce stade.
> [!NOTE]
> - Si vous n’utilisez pas l’agent [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] pour la copie des journaux de transaction ou pour toute autre utilisation, il n’est pas nécessaire de l’installer, de sorte que le package *mssql-server-agent* peut être ignoré.
> - Les autres packages facultatifs pour [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] sur Linux, à savoir la recherche en texte intégral [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] (*mssql-server-fts*) et Integration Services [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] (*mssql-server-is*), ne sont pas requis pour la haute disponibilité, que ce soit pour une instance de cluster de basculement (FCI) un groupe de disponibilité.

**RHEL**

```bash
sudo yum install mssql-server-ha mssql-server-agent
sudo systemctl restart mssql-server
```

**Ubuntu**

```bash
sudo apt-get install mssql-server-ha mssql-server-agent
sudo systemctl restart mssql-server
```

**SLES**

```bash
sudo zypper install mssql-server-ha mssql-server-agent
sudo systemctl restart mssql-server
```

## <a name="next-steps"></a>Étapes suivantes

Dans ce tutoriel, vous avez appris comment déployer un cluster Pacemaker pour SQL Server sur Linux. Vous avez appris à :
> [!div class="checklist"]
> * Installer le module complémentaire de haute disponibilité et installer Pacemaker.
> * Préparez les nœuds pour Pacemaker (RHEL et Ubuntu uniquement).
> * Créez le cluster Pacemaker.
> * Installez les packages HA et SQL Server Agent de SQL Server.

Pour créer et configurer un groupe de disponibilité pour SQL Server sur Linux, consultez :

> [!div class="nextstepaction"]
> [Créer et configurer un groupe de disponibilité pour SQL Server sur Linux](sql-server-linux-create-availability-group.md).

