---
title: Créer des scripts de déploiement pour SQL Server groupe de disponibilité AlwaysOn sur Kubernetes
description: Cet article explique comment créer des scripts de déploiement pour un SQL Server groupe de disponibilité AlwaysOn sur Kubernetes
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 09/24/2018
ms.topic: article
ms.prod: sql
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 70a83efa128d8d58776907541fef9d6888af51e1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66705676"
---
# <a name="create-deployment-script-for-sql-server-always-on-availability-group"></a>Créer un script de déploiement pour SQL Server groupe de disponibilité AlwaysOn

Cet article décrit comment déployer un groupe de disponibilité sur un cluster Kubernetes dans une seule commande avec un exemple de script de déploiement. `deploy-ag.py` est un script Python qui crée le `.yaml` fichiers pour le cluster et les appliquer à un cluster Kubernetes.

Télécharger les fichiers à partir du fichier [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-deployment-script).

## <a name="before-you-start"></a>Avant de commencer

Installez les outils suivants sur votre station de travail.

* [Python](https://www.python.org/downloads/) (3.5 ou 3.6)
* [PyYAML](https://pyyaml.org/) -Packages Python
* [Client Kubernetes](https://github.com/kubernetes-client/python) -Package Python

Ajouter des chemins d’accès de python pour les variables d’environnement (pour Windows).

### <a name="install-the-required-components"></a>Installer les composants requis

L’exemple suivant, la méthode ci-dessus installe les packages PyYAML et Kubernetes Client pour Python.

Après avoir installé Python, téléchargez et extrayez le dossier d’exemples. 

Pour configurer les fichiers requis, exécutez la commande suivante. Remplacez `<path>` avec l’emplacement des fichiers d’exemple extrait.

```cmd
pip install --user -r "C:\<path>\requirements.txt"
```

## <a name="create-cluster-and-download-config-file"></a>Créer le Cluster et de télécharger le fichier de configuration

L’exemple suivant crée le cluster dans Azure Kubernetes Service (ACS).

Avant d’exécuter le script, mettez à jour les valeurs figurant entre crochets - `<>`.

```azcli
az aks create  --resource-group <GroupName> --name <ClusterName> --generate-ssh-keys --node-count 4 --kubernetes-version 1.11.1

az aks get-credentials --resource-group=<GroupName> --name=<ClusterName>
```

>[!NOTE]
>Groupes de disponibilité nécessite Kubernetes version 1.11.0 ou une version ultérieure. L’exemple spécifie 1.11.1.

## <a name="run-the-deployment-script"></a>Exécutez le script de déploiement

Les exemples suivants montrent comment exécuter `deploy-ag.py`.

### <a name="help"></a>Aide

```cmd
python ./deploy-ag.py --help
```

* **utilisation**: `deploy-ag.py [-h] {deploy | failover} ...`
* **arguments facultatifs**:
  * `-h, --help` afficher ce message d’aide et de sortie
* **sous-commandes**:
  * Actions sur l’agent k8s {déployer | basculement}

  `deploy`

   Déployer un ensemble de serveurs SQL dans un groupe de disponibilité

  `failover`

   Basculer vers un réplica cible.

### <a name="deploy-help"></a>Déployer aide

```cmd
python ./deploy-ag.py deploy --help
```

* **utilisation**:

  ```
  python ./deploy-ag.py deploy [-h] [--verbose] [--ag AG] [-n NAMESPACE]
    [--dry-run] [-s SQL_SERVERS [SQL_SERVERS ...]]
    [-p SA_PASSWORD] [-e {ON_PREM,AKS}]
    [--skip-create-namespace]
  ```

  Déployer SQL Server et les Agents k8s dans namespace(AG name)

* **arguments facultatifs**:
  
  `-h, --help`
  
  afficher ce message d’aide et de sortie
  
  `--verbose, -v`
  
  Niveau de détail de sortie
  
  `--ag AG`
  
  nom du groupe de disponibilité. Par défaut = ag1
  
  `-n NAMESPACE, --namespace NAMESPACE`
  
  nom de l’espace de noms k8s. La valeur par défaut est nom de groupe de disponibilité si non spécifié.

  `--dry-run`
  
  Créer les manifestes, mais ne s’appliquent pas les.
  
  `-s SQL_SERVERS [SQL_SERVERS ...], --sql-servers SQL_SERVERS [SQL_SERVERS ...]`

  noms des instances de SQL Server (jusqu'à 5, séparés par des espaces) par défaut = [« mssql1 », 'mssql2', 'mssql3']
  
  `-p SA_PASSWORD, --sa-password SA_PASSWORD`
  
  Mot de passe SA. Default='SAPassword2018'
  
  `-e {ON_PREM,AKS}, --env {ON_PREM,AKS}`
  
  `--skip-create-namespace`
  
  Ignorer la création de l’espace de noms.

### <a name="failover-help"></a>Aide de basculement

```cmd
python ./deploy-ag.py failover --help
```
* **utilisation**: 

  ```cmd
  python deploy-ag.py failover [-h] [--verbose] [--ag AG]
    [--namespace NAMESPACE] [--dry-run]
    target_replica
  ```

  Basculez manuellement

* **arguments de position**: `target_replica`

  nom du réplica de SQL Server cible pour le basculement

* **arguments facultatifs**:

  `-h, --help`
  
  afficher ce message d’aide et de sortie

  `--verbose, -v`
  
  Niveau de détail de sortie

  `--ag AG`
  
  nom du groupe de disponibilité. Par défaut = ag1

  `--namespace NAMESPACE`

  nom de l’espace de noms k8s. Valeurs par défaut au nom du groupe de disponibilité si non spécifié

  `--dry-run`
  
  Créer, mais ne s’appliquent pas les manifestes.

### <a name="create-the-manifests---dont-apply"></a>Créer les manifestes : ne s’appliquent pas

Le script suivant crée les fichiers manifeste, mais ne s’applique pas les.

```cmd
python ./deploy-ag.py deploy --dry-run
```

L’exemple suivant crée les manifestes pour un groupe de disponibilité sous l’espace de noms `AG1` avec trois réplicas. Avant d’exécuter le script, remplacez `<MyC0m91exP@55w0r!>` avec un mot de passe complexe.

```cmd
python ./deploy-ag.py deploy --ag ag1 --namespace AG1 --sa-password '<MyC0m91exP@55w0r!>' --env AKS --dry-run
```

La commande précédente génère le répertoire des fichiers yaml exemple.

Dans ce cas, la sortie de commande indique où les fichiers manifestes sont créés.

![sortie du script](./media/sql-server-linux-kubernetes-create-deployment/scriptbuild-out.png)
    
### <a name="create-the-manifests-and-apply"></a>Créer les manifestes et appliquer

L’exemple suivant crée les manifestes pour un groupe de disponibilité sous l’espace de noms `ag1` avec trois réplicas et s’applique à votre cluster Kubernetes. Le cluster crée ensuite le groupe de disponibilité. Avant d’exécuter le script, remplacez `<MyC0m91exP@55w0r!>` avec un mot de passe complexe.

```
python ./deploy-ag.py deploy --ag ag1 --namespace ag1 --sa-password '<MyC0m91exP@55w0r!>' --env AKS --verbose
```

Une fois le script terminé, l’opérateur Kubernetes crée le stockage, les instances de SQL Server, les services d’équilibrage de charge. Vous pouvez surveiller le déploiement avec [tableau de bord Kubernetes](https://docs.microsoft.com/azure/aks/kubernetes-dashboard).

Une fois que Kubernetes crée les conteneurs de SQL Server :

1. [Se connecter](sql-server-linux-kubernetes-connect.md) à une instance de SQL Server dans le cluster.

1. Créer une base de données.

1. Effectuez une sauvegarde complète de la base de données pour démarrer la séquence de journaux.

1. Ajouter la base de données au groupe de disponibilité.

Le groupe de disponibilité est créé avec l’amorçage automatique pour SQL Server crée automatiquement les bases de données secondaire sur les réplicas appropriés.

### <a name="manually-failover"></a>Basculez manuellement

L’exemple suivant bascule le réplica principal.

```cmd
python ./deploy-ag.py failover --ag ag1 --namespace ag1 --verbose mssql1-0
```

## <a name="next-steps"></a>Étapes suivantes

[Groupe de disponibilité de SQL Server sur un cluster Kubernetes](sql-server-ag-kubernetes.md)
