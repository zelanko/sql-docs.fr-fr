---
title: Configurer Kubernetes avec kubeadm
titleSuffix: SQL Server big data clusters
description: Découvrez comment configurer Kubernetes sur plusieurs ordinateurs Ubuntu 16,04 ou 18,04 (physique ou virtuel) pour les déploiements SQL Server 2019 Big Data cluster (version préliminaire).
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: ea79503869e7d403e4d3f4f960de9c95760eda0f
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419448"
---
# <a name="configure-kubernetes-on-multiple-machines-for-sql-server-big-data-cluster-deployments"></a>Configurer Kubernetes sur plusieurs ordinateurs pour SQL Server les déploiements de cluster Big Data

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article fournit un exemple d’utilisation de **kubeadm** pour configurer Kubernetes sur plusieurs ordinateurs pour les déploiements de cluster SQL Server 2019 Big Data (version préliminaire). Dans cet exemple, plusieurs machines Ubuntu 16,04 ou 18,04 LTS (physique ou virtuel) sont la cible. Si vous effectuez un déploiement sur une autre plateforme Linux, vous devez modifier certaines des commandes pour qu’elles correspondent à votre système.  

> [!TIP] 
> Pour obtenir des exemples de scripts qui configurent Kubernetes, consultez [créer un cluster Kubernetes à l’aide de Kubeadm sur Ubuntu 16,04 LTS ou 18,04 LTS](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/deployment/kubeadm).

## <a name="prerequisites"></a>Prérequis

- Au minimum 3 machines physiques Linux ou machines virtuelles
- Configuration recommandée par ordinateur:
   - 8 UC
   - 64 Go de mémoire
   - 100 Go de stockage

## <a name="prepare-the-machines"></a>Préparer les machines

Sur chaque ordinateur, plusieurs conditions préalables sont requises. Dans un terminal bash, exécutez les commandes suivantes sur chaque ordinateur:

1. Ajoutez l’ordinateur actuel au `/etc/hosts` fichier:

   ```bash
   echo $(hostname -i) $(hostname) | sudo tee -a /etc/hosts
   ```

1. Désactivez l’échange sur tous les appareils.

   ```bash
   sudo sed -i "/ swap / s/^/#/" /etc/fstab
   sudo swapoff -a
   ```

1. Importez les clés et enregistrez le référentiel pour Kubernetes.

   ```bash
   sudo curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
   echo 'deb http://apt.kubernetes.io/ kubernetes-xenial main' | sudo tee -a /etc/apt/sources.list.d/kubernetes.list
   ```

1. Configurez les conditions préalables de dockr et Kubernetes sur l’ordinateur.

   ```bash
   KUBE_DPKG_VERSION=1.11.3-00
   sudo apt-get update && /
   sudo apt-get install -y ebtables ethtool && /
   sudo apt-get install -y docker.io && /
   sudo apt-get install -y apt-transport-https && /
   sudo apt-get install -y kubelet=$KUBE_DPKG_VERSION kubeadm=$KUBE_DPKG_VERSION kubectl=$KUBE_DPKG_VERSION && /
   curl https://raw.githubusercontent.com/kubernetes/helm/master/scripts/get | bash
   ```
 
1. Définissez `net.bridge.bridge-nf-call-iptables=1`. Sur Ubuntu 18,04, les commandes suivantes activent `br_netfilter`d’abord.

   ```bash
   . /etc/os-release
   if [ "$VERSION_CODENAME" == "bionic" ]; then sudo modprobe br_netfilter; fi
   sudo sysctl net.bridge.bridge-nf-call-iptables=1
   ```

## <a name="configure-the-kubernetes-master"></a>Configurer le maître Kubernetes

Après avoir exécuté les commandes précédentes sur chaque ordinateur, choisissez l’une des machines à utiliser comme maître Kubernetes. Exécutez ensuite les commandes suivantes sur cet ordinateur.

1. Tout d’abord, créez un fichier RBAC. YAML dans votre répertoire actuel à l’aide de la commande suivante. 

   ```bash
   cat <<EOF > rbac.yaml
   apiVersion: rbac.authorization.k8s.io/v1beta1
   kind: ClusterRoleBinding
   metadata:
     name: default-rbac
   subjects:
   - kind: ServiceAccount
     name: default
     namespace: default
   roleRef:
     kind: ClusterRole
     name: cluster-admin
     apiGroup: rbac.authorization.k8s.io
   EOF
   ```

1. Initialisez le maître Kubernetes sur cet ordinateur. Vous devez voir une sortie indiquant que le maître Kubernetes a été initialisé avec succès.

   ```bash
   KUBE_VERSION=1.11.3
   sudo kubeadm init --pod-network-cidr=10.244.0.0/16 --kubernetes-version=$KUBE_VERSION
   ```

1. Notez la `kubeadm join` commande que vous devez utiliser sur les autres serveurs pour rejoindre le cluster Kubernetes. Copiez ceci pour une utilisation ultérieure.

   ![kubeadm Join](./media/deploy-with-kubeadm/kubeadm-join.png)

1. Configurez un fichier de configuration Kubernetes dans votre répertoire de départ.

   ```bash
   mkdir -p $HOME/.kube
   sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
   sudo chown $(id -u):$(id -g) $HOME/.kube/config
   ```

1. Configurez le cluster et le tableau de bord Kubernetes.

   ```bash
   kubectl apply -f https://raw.githubusercontent.com/coreos/flannel/master/Documentation/kube-flannel.yml
   helm init
   kubectl apply -f rbac.yaml
   kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/master/src/deploy/recommended/kubernetes-dashboard.yaml
   kubectl create clusterrolebinding kubernetes-dashboard --clusterrole=cluster-admin --serviceaccount=kube-system:kubernetes-dashboard
   ```

## <a name="configure-the-kubernetes-agents"></a>Configurer les agents Kubernetes

Les autres machines agiront en tant qu’agents Kubernetes dans le cluster. 

Sur chaque autre machine, exécutez la `kubeadm join` commande que vous avez copiée dans la section précédente.

![agents de jointure kubeadm](./media/deploy-with-kubeadm/kubeadm-join-agents.png)

## <a name="view-the-cluster-status"></a>Afficher l’état du cluster

Pour vérifier la connexion à votre cluster, utilisez la commande [kubectl obtenir](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands) pour retourner une liste des nœuds de cluster.

```bash
kubectl get nodes
```

## <a name="next-steps"></a>Étapes suivantes

Les étapes décrites dans cet article configurent un cluster Kubernetes sur plusieurs ordinateurs Ubuntu. L’étape suivante consiste à déployer le cluster SQL Server 2019 Big Data. Pour obtenir des instructions, consultez l’article suivant:

[Déployer SQL Server sur Kubernetes](deployment-guidance.md#deploy)
