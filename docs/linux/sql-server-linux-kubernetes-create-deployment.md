---
title: Créer des scripts de déploiement pour le groupe de disponibilité Always On SQL Server sur Kubernetes
description: Cet article explique comment créer des scripts de déploiement pour le groupe de disponibilité Always On SQL Server sur Kubernetes
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 09/24/2018
ms.topic: article
ms.prod: sql
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 181773a19e87c34a1931cae05f5a329aedbc1239
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68000131"
---
# <a name="create-deployment-script-for-sql-server-always-on-availability-group"></a>Créer un script de déploiement pour le groupe de disponibilité Always On SQL Server

Cet article décrit comment déployer un groupe de disponibilité sur un cluster Kubernetes dans une commande unique avec un exemple de script de déploiement. `deploy-ag.py` est un script Python qui crée les fichiers `.yaml` pour le cluster et peut les appliquer à un cluster Kubernetes.

Téléchargez le fichier de fichiers à partir de [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-deployment-script).

## <a name="before-you-start"></a>Avant de commencer

Installez les outils suivants sur votre station de travail.

* [Python](https://www.python.org/downloads/) (3.5 ou 3.6)
* [PyYAML](https://pyyaml.org/) - Packages Python
* [Client Kubernetes](https://github.com/kubernetes-client/python) - Package Python

Ajoutez des chemins d’accès Python aux variables d’environnement (pour Windows).

### <a name="install-the-required-components"></a>Installer les composants nécessaires

Dans l’exemple suivant, le composant ci-dessus installe les packages PyYAML et Client Kubernetes pour Python.

Après avoir installé Python, téléchargez et extrayez l’exemple de dossier. 

Pour configurer les fichiers requis, exécutez la commande suivante. Remplacez `<path>` par l’emplacement des fichiers d’exemple extraits.

```cmd
pip install --user -r "C:\<path>\requirements.txt"
```

## <a name="create-cluster-and-download-config-file"></a>Créer un cluster et télécharger le fichier config

L’exemple suivant crée le cluster dans Azure Kubernetes Service (AKS).

Avant d’exécuter le script, mettez à jour les valeurs entre crochets pointus - `<>`.

```azcli
az aks create  --resource-group <GroupName> --name <ClusterName> --generate-ssh-keys --node-count 4 --kubernetes-version 1.11.1

az aks get-credentials --resource-group=<GroupName> --name=<ClusterName>
```

>[!NOTE]
>Les groupes de disponibilité requièrent Kubernetes version 1.11.0 ou ultérieure. L’exemple spécifie 1.11.1.

## <a name="run-the-deployment-script"></a>Exécuter un script de déploiement

Les exemples ci-dessous illustrent comment exécuter `deploy-ag.py`.

### <a name="help"></a>Aide

```cmd
python ./deploy-ag.py --help
```

* **Utilisation** : `deploy-ag.py [-h] {deploy | failover} ...`
* **arguments facultatifs** :
  * `-h, --help` afficher ce message d’aide et quitter
* **sous-commandes** :
  * Actions sur l’agent K8S {déployer | basculer}

  `deploy`

   Déployer un ensemble de serveurs SQL dans un groupe de disponibilité

  `failover`

   Basculer vers un réplica cible.

### <a name="deploy-help"></a>Déployer l’aide

```cmd
python ./deploy-ag.py deploy --help
```

* **utilisation** :

  ```
  python ./deploy-ag.py deploy [-h] [--verbose] [--ag AG] [-n NAMESPACE]
    [--dry-run] [-s SQL_SERVERS [SQL_SERVERS ...]]
    [-p SA_PASSWORD] [-e {ON_PREM,AKS}]
    [--skip-create-namespace]
  ```

  Déployer des agents SQL Server et K8S dans l’espace de noms (nom AG)

* **arguments facultatifs** :
  
  `-h, --help`
  
  afficher ce message d’aide et quitter
  
  `--verbose, -v`
  
  Niveau de détail de la sortie
  
  `--ag AG`
  
  nom du groupe de disponibilité. Valeur par défaut = ag1
  
  `-n NAMESPACE, --namespace NAMESPACE`
  
  nom de l’espace de noms K8S. En l'absence de toute spécification, prend le nom AG comme valeur par défaut.

  `--dry-run`
  
  Créez les manifestes, mais ne les appliquez pas.
  
  `-s SQL_SERVERS [SQL_SERVERS ...], --sql-servers SQL_SERVERS [SQL_SERVERS ...]`

  noms des instances (jusqu’à 5, séparés par des espaces) Par défaut = [« mssql1 », « mssql2 », « mssql3 »]
  
  `-p SA_PASSWORD, --sa-password SA_PASSWORD`
  
  Mot de passe de l’association de sécurité (SA). Par défaut = « SAPassword2018 »
  
  `-e {ON_PREM,AKS}, --env {ON_PREM,AKS}`
  
  `--skip-create-namespace`
  
  Ignorez la création d'espace de noms.

### <a name="failover-help"></a>Aide au basculement

```cmd
python ./deploy-ag.py failover --help
```
* **utilisation** : 

  ```cmd
  python deploy-ag.py failover [-h] [--verbose] [--ag AG]
    [--namespace NAMESPACE] [--dry-run]
    target_replica
  ```

  Basculement manuel

* **arguments positionnels** : `target_replica`

  nom du réplica SQL Server cible pour le basculement

* **arguments facultatifs** :

  `-h, --help`
  
  afficher ce message d’aide et quitter

  `--verbose, -v`
  
  Niveau de détail de la sortie

  `--ag AG`
  
  nom du groupe de disponibilité. Valeur par défaut = ag1

  `--namespace NAMESPACE`

  nom de l’espace de noms K8S. En l'absence de toute spécification, prend le nom AG comme valeur par défaut

  `--dry-run`
  
  Créez les manifestes, mais ne les appliquez pas.

### <a name="create-the-manifests---dont-apply"></a>Créer les manifestes - ne pas appliquer

Le script suivant crée les fichiers manifestes, mais ne les applique pas.

```cmd
python ./deploy-ag.py deploy --dry-run
```

L’exemple suivant crée les manifestes pour un groupe de disponibilité sous l’espace de noms `AG1` avec trois réplicas. Avant d’exécuter le script, remplacez `<MyC0m91exP@55w0r!>` par un mot de passe complexe.

```cmd
python ./deploy-ag.py deploy --ag ag1 --namespace AG1 --sa-password '<MyC0m91exP@55w0r!>' --env AKS --dry-run
```

La commande précédente génère l’exemple de répertoire de fichiers yaml.

Dans ce cas, la sortie de la commande indique où les fichiers manifestes sont créés.

![sortie du script](./media/sql-server-linux-kubernetes-create-deployment/scriptbuild-out.png)
    
### <a name="create-the-manifests-and-apply"></a>Créer les manifestes et les appliquer

L’exemple suivant crée les manifestes pour un groupe de disponibilité sous l’espace de noms `ag1` avec trois réplicas et l’applique à votre cluster Kubernetes. Le cluster crée alors le groupe de disponibilité. Avant d’exécuter le script, remplacez `<MyC0m91exP@55w0r!>` par un mot de passe complexe.

```
python ./deploy-ag.py deploy --ag ag1 --namespace ag1 --sa-password '<MyC0m91exP@55w0r!>' --env AKS --verbose
```

Une fois le script terminé, l’opérateur Kubernetes crée le stockage, les instances, les services de l’équilibreur de charge. Vous pouvez surveiller le déploiement avec le [tableau de bord Kubernetes](https://docs.microsoft.com/azure/aks/kubernetes-dashboard).

Une fois que Kubernetes a créé les conteneurs SQL Server :

1. [Connectez-vous](sql-server-linux-kubernetes-connect.md) à une instance dans le cluster.

1. Créer une base de données.

1. À partir d’une sauvegarde complète de la base de données, démarrez la séquence de journaux de transactions consécutifs.

1. Ajoutez la base de données au groupe de disponibilité.

Le groupe de disponibilité est créé avec l’amorçage automatique afin que SQL Server crée automatiquement les bases de données secondaires sur les réplicas appropriés.

### <a name="manually-failover"></a>Basculement manuel

L’exemple suivant bascule le réplica principal.

```cmd
python ./deploy-ag.py failover --ag ag1 --namespace ag1 --verbose mssql1-0
```

## <a name="next-steps"></a>Étapes suivantes

[Groupe de disponibilité SQL Server sur le cluster Kubernetes](sql-server-ag-kubernetes.md)
