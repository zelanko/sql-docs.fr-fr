---
title: Déployer un cluster Pacemaker pour SQL Server sur Linux | Microsoft Docs
description: Ce didacticiel montre comment déployer un cluster Pacemaker pour SQL Server sur Linux.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 12/11/2017
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.openlocfilehash: 25fb50dbd858007a29d2a10a94053884620ed68b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47750587"
---
# <a name="deploy-a-pacemaker-cluster-for-sql-server-on-linux"></a>Déployer un cluster Pacemaker pour SQL Server sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Ce didacticiel décrit les tâches nécessaires pour déployer un cluster Linux Pacemaker pour un groupe de disponibilité [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] AlwaysOn ou une instance de cluster de basculement. Contrairement à la pile étroitement couplée Windows Server /[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)], la création du cluster Pacemaker et la configuration d'un groupe de disponibilité sur Linux peuvent être effectuées avant ou après l’installation de [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]. L’intégration et la configuration des ressources pour la partie Pacemaker du déploiement d’un groupe de disponibilité ou d’une instance de cluster de basculement sont effectuées une fois que le cluster est configuré.
> [!IMPORTANT]
> Un groupe de disponibilité avec un cluster de type "Aucun" ne nécessite  *pas*  de cluster Pacemaker, et il ne peut pas être géré par Pacemaker. 

> [!div class="checklist"]
> * Installer le module complémentaire de haute disponibilité et Pacemaker.
> * Préparer les nœuds pour Pacemaker (RHEL et Ubuntu uniquement).
> * Créez le cluster Pacemaker.
> * Installer les packages SQL Server à haute disponibilité et l’Agent SQL Server.
 
## <a name="prerequisite"></a>Condition préalable
[Installer SQL Server 2017](sql-server-linux-setup.md).

## <a name="install-the-high-availability-add-on"></a>Installer le module complémentaire de haute disponibilité
Utilisez la syntaxe suivante pour installer les packages qui composent le module complémentaire de haute disponibilité (HA) pour chaque distribution de Linux. 

**Red Hat Enterprise Linux (RHEL)**
1.  Inscrivez le serveur à l’aide de la syntaxe suivante. Vous êtes invité à un nom d’utilisateur valide et un mot de passe.
    
    ```bash
    sudo subscription-manager register
    ```
    
2.  Liste des pools disponibles pour l’inscription.
    
    ```bash
    sudo subscription-manager list --available
    ```

3.  Exécutez la commande suivante pour associer une haute disponibilité RHEL à l’abonnement
    
    ```bash
    sudo subscription-manager attach --pool=<PoolID>
    ```
    
    où *PoolId* est l’ID du pool pour l’abonnement de haute disponibilité de l’étape précédente.
    
4.  Activer le référentiel être en mesure d’utiliser le module complémentaire de haute disponibilité.
    
    ```bash
    sudo subscription-manager repos --enable=rhel-ha-for-rhel-7-server-rpms
    ```
    
5.  Installation de Pacemaker.
    
    ```bash
    sudo yum install pacemaker pcs fence-agents-all resource-agents
    ```

**Ubuntu**

```bash
sudo apt-get install pacemaker pcs fence-agents resource-agents
```

**SUSE Linux Enterprise Server (SLES)**

Installer le modèle de haute disponibilité dans YaST ou de le faire dans le cadre de l’installation du serveur principal. L’installation est possible avec un norme ISO/DVD en tant que source ou en obtenant d’en ligne.
> [!NOTE]
> Sur SLES, le module complémentaire de haute disponibilité est initialisé lorsque le cluster est créé.

## <a name="prepare-the-nodes-for-pacemaker-rhel-and-ubuntu-only"></a>Préparer les nœuds pour Pacemaker (RHEL et Ubuntu uniquement)
Pacemaker lui-même utilise un utilisateur créé sur la distribution nommée *hacluster*. L’utilisateur est créé lorsque le module complémentaire de haute disponibilité est installé sur RHEL et Ubuntu.
1. Sur chaque serveur qui servira à un nœud du cluster Pacemaker, créez le mot de passe pour un utilisateur à utiliser par le cluster. Le nom utilisé dans les exemples est *hacluster*, mais n’importe quel nom peut être utilisé. Le nom et le mot de passe doivent être le même sur tous les nœuds participant au cluster Pacemaker.
   
    ```bash
    sudo passwd hacluster
    ```
    
2. Sur chaque nœud qui fera partie du cluster Pacemaker, activer et démarrer le `pcsd` service avec les commandes suivantes (RHEL et Ubuntu) :

   ```bash
   sudo systemctl enable pcsd
   sudo systemctl start pcsd
   ```
   
   Puis exécutez
   
   ```bash
   sudo systemctl status pcsd
   ```
   
   Pour vous assurer que `pcsd` est démarré.
3. Activer le service Pacemaker sur chaque nœud du cluster Pacemaker possible.
   
   ```bash
   sudo systemctl start pacemaker
   ```

   Sur Ubuntu, vous voyez une erreur :
   
   *pacemaker de démarrage par défaut ne contient aucun runlevels, abandon.*
   
   Cette erreur est un problème connu. En dépit de l’erreur, l’activation du service Pacemaker est réussie, et ce bogue à un moment donné dans le futur.
   
4. Ensuite, créez et démarrez le cluster Pacemaker. Il existe une différence entre RHEL et Ubuntu à cette étape. Tandis que sur les deux distributions, installez `pcs` configure un fichier de configuration par défaut pour le cluster Pacemaker sur RHEL, l’exécution de cette commande supprime toute configuration existante et crée un nouveau cluster.

<a id="create"></a>
## <a name="create-the-pacemaker-cluster"></a>Créer le cluster Pacemaker 
Cette section décrit comment créer et configurer le cluster pour chaque distribution de Linux.

**RHEL**

1. Autoriser les nœuds
   
   ```bash
   sudo pcs cluster auth <Node1 Node2 … NodeN> -u hacluster
   ```
   
   où *NodeX* est le nom du nœud.
2. Créer le cluster
   
   ```bash
   sudo pcs cluster setup --name <PMClusterName Nodelist> --start --all --enable
   ```
   
   où *PMClusterName* est le nom affecté au cluster Pacemaker et *Nodelist* est la liste des noms des nœuds séparés par un espace.

**Ubuntu**

La configuration d’Ubuntu est similaire à RHEL. Toutefois, il existe une différence majeure : installation des packages Pacemaker crée une configuration de base pour le cluster et active démarre `pcsd`. Si vous essayez de configurer le cluster Pacemaker en suivant les instructions de RHEL exactement, vous obtenez une erreur. Pour résoudre ce problème, procédez comme suit : 
1. Supprimer la configuration de Pacemaker par défaut de chaque nœud.
   
   ```bash
   sudo pcs cluster destroy
   ```
   
2. Suivez les étapes décrites dans la section RHEL pour créer le cluster Pacemaker.

**SLES**

Le processus de création d’un cluster Pacemaker est complètement différent sur SLES sur RHEL et Ubuntu. Les étapes suivantes expliquent comment créer un cluster avec SLES.
1. Démarrer le processus de configuration de cluster en exécutant 
   ```bash
   sudo ha-cluster-init
   ``` 
   
   sur l’un des nœuds. Vous pouvez être invité NTP n’est pas configuré et qu’aucun périphérique de l’agent de surveillance n’est trouvé. C’est parfait pour rendre les choses opérationnel et en cours d’exécution. Agent de surveillance est liée à STONITH si vous utilisez délimitation intégrée de SLES qui est basé sur le stockage. NTP et agent de surveillance peuvent être configurés plus tard.
   
2. Vous êtes invité à configurer Corosync. Vous êtes invité à entrer l’adresse réseau à lier, ainsi que l’adresse de multidiffusion et le port. L’adresse réseau est le sous-réseau que vous utilisez ; par exemple, 192.191.190.0. Vous pouvez accepter les valeurs par défaut à chaque invite, ou modifier si nécessaire.
   
3. Ensuite, vous êtes invité si vous souhaitez configurer SBD, qui est la délimitation basée sur disque. Cette configuration peut être effectuée plus tard si vous le souhaitez. Si SBD n’est pas configuré, contrairement à sur RHEL et Ubuntu, `stonith-enabled` sera par défaut défini sur false.
   
4. Enfin, vous êtes invité si vous souhaitez configurer une adresse IP pour l’administration. Cette adresse IP est facultative, mais fonctionne de façon similaire à l’adresse IP pour un cluster de basculement Windows Server (WSFC) en ce sens qu’il crée une adresse IP du cluster à utiliser pour la connexion à celui-ci par le biais de haute disponibilité Web Konsole (HAWK). Cette configuration, trop, est facultative.
   
5. Vérifiez que le cluster est en cours d’exécution en émettant 
   ```bash
   sudo crm status
   ```
   
6. Modifier le *hacluster* avec mot de passe 
   ```bash
   sudo passwd hacluster
   ```
   
7. Si vous avez configuré une adresse IP pour l’administration, vous pouvez le tester dans un navigateur, ce qui teste également la modification de mot de passe pour *hacluster*.
   ![](./media/sql-server-linux-deploy-pacemaker-cluster/image2.png)
   
8. Sur un autre serveur SLES qui sera un nœud du cluster, exécutez 
   ```bash
   sudo ha-cluster-join
   ```
   
9. Lorsque vous y êtes invité, entrez le nom ou l’adresse IP du serveur qui a été configuré comme le premier nœud du cluster dans les étapes précédentes. Le serveur est ajouté en tant que nœud au cluster existant.
   
10. Vérifier que le nœud a été ajouté à l’aide de 
   ```bash
   sudo crm status
   ```
   
11. Modifier le *hacluster* avec mot de passe 
   ```bash
   sudo passwd hacluster
   ```
   
12. Répétez les étapes 8 à 11 pour tous les autres serveurs à ajouter au cluster.

## <a name="install-the-sql-server-ha-and-sql-server-agent-packages"></a>Installer les packages SQL Server à haute disponibilité et l’Agent SQL Server
Utilisez les commandes suivantes pour installer le package SQL Server à haute disponibilité et [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Agent, s’ils ne sont pas déjà installés. Installation du package de haute disponibilité après l’installation de [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] nécessite un redémarrage de [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] pour pouvoir être utilisé. Ces instructions supposent que les référentiels pour les packages de Microsoft ont déjà été configurés, étant donné que [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] doit être installé à ce stade.
> [!NOTE]
> - Si vous ne souhaitez pas utiliser [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Agent pour l’envoi de journaux ou toute autre utilisation, il n’a pas à installer, par conséquent, le package *mssql-server-agent* peut être ignorée.
> - Les autres packages facultatifs pour [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] sur Linux, [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] recherche en texte intégral (*mssql-server-fts*) et [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Integration Services (*mssql-server est*), ne sont pas requis pour la haute disponibilité, pour une instance FCI ou un groupe de disponibilité.

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

Dans ce didacticiel, vous avez appris à déployer un cluster Pacemaker pour SQL Server sur Linux. Vous avez appris à :
> [!div class="checklist"]
> * Installer le module complémentaire de haute disponibilité et Pacemaker.
> * Préparer les nœuds pour Pacemaker (RHEL et Ubuntu uniquement).
> * Créez le cluster Pacemaker.
> * Installer les packages SQL Server à haute disponibilité et l’Agent SQL Server.

Pour créer et configurer un groupe de disponibilité pour SQL Server sur Linux, consultez :

> [!div class="nextstepaction"]
> [Créer et configurer un groupe de disponibilité pour SQL Server sur Linux](sql-server-linux-create-availability-group.md).

