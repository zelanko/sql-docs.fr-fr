---
title: Configurer Kubernetes avec kubeadm pour les déploiements de SQL Server 2019 | Microsoft Docs
description: Découvrez comment configurer Kubernetes sur plusieurs Ubuntu 16.04 ou 18.04 machines (physiques ou virtuels) pour les déploiements de cluster (version préliminaire) de SQL Server 2019 big data.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 11/06/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 842a23877290aec76f7813f27b68b4bccd7b5c9b
ms.sourcegitcommit: cb73d60db8df15bf929ca17c1576cf1c4dca1780
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2018
ms.locfileid: "51221775"
---
# <a name="configure-kubernetes-on-multiple-machines-for-sql-server-2019-deployments"></a>Configurer Kubernetes sur plusieurs ordinateurs pour les déploiements de SQL Server 2019

Cet article fournit un exemple montrant comment utiliser **kubeadm** pour configurer Kubernetes sur plusieurs ordinateurs pour les déploiements de cluster (version préliminaire) de SQL Server 2019 big data. Dans cet exemple, plusieurs Ubuntu 16.04 ou 18.04 LTS machines (physiques ou virtuels) sont la cible. Si vous déployez sur une autre plateforme Linux, vous devez modifier certaines des commandes pour correspondre à votre système.  

> [!TIP] 
> Pour plus d’exemples de scripts qui configurent Kubernetes, consultez [créer un cluster Kubernetes à l’aide de Kubeadm sur Ubuntu 16.04 LTS ou 18.04 LTS](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/deployment/kubeadm).

## <a name="prerequisites"></a>Prérequis

- Plusieurs machines physiques Linux ou les machines virtuelles à utiliser pour le cluster
- Configuration recommandée : 8 processeurs, 32 Go de mémoire et au moins 100 Go de stockage pour chaque ordinateur
- Au minimum trois machines dans le cluster

## <a name="prepare-the-machines"></a>Préparer les ordinateurs

Sur chaque ordinateur, il existe plusieurs conditions préalables requises. Dans un terminal bash, exécutez les commandes suivantes sur chaque ordinateur :

1. Ajouter l’ordinateur actuel à le `/etc/hosts` fichier :

   ```bash
   echo $(hostname -i) $(hostname) | sudo tee -a /etc/hosts
   ```

1. Désactiver le remplacement sur tous les appareils.

   ```bash
   sudo sed -i "/ swap / s/^/#/" /etc/fstab
   sudo swapoff -a
   ```

1. Importez les clés et inscrire le référentiel pour Kubernetes.

   ```bash
   sudo curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
   echo 'deb http://apt.kubernetes.io/ kubernetes-xenial main' | sudo tee -a /etc/apt/sources.list.d/kubernetes.list
   ```

1. Configurer docker et Kubernetes prérequis sur l’ordinateur.

   ```bash
   KUBE_DPKG_VERSION=1.11.3-00
   sudo apt-get update && /
   sudo apt-get install -y ebtables ethtool && /
   sudo apt-get install -y docker.io && /
   sudo apt-get install -y apt-transport-https && /
   sudo apt-get install -y kubelet=$KUBE_DPKG_VERSION kubeadm=$KUBE_DPKG_VERSION kubectl=$KUBE_DPKG_VERSION && /
   curl https://raw.githubusercontent.com/kubernetes/helm/master/scripts/get | bash
   ```
 
1. Définissez `net.bridge.bridge-nf-call-iptables=1`. Sur Ubuntu 18.04, les commandes suivantes d’abord activer `br_netfilter`.

   ```bash
   . /etc/os-release
   if [ "$VERSION_CODENAME" == "bionic" ]; then sudo modprobe br_netfilter; fi
   sudo sysctl net.bridge.bridge-nf-call-iptables=1
   ```

## <a name="configure-the-kubernetes-master"></a>Configurer le serveur maître de Kubernetes

Après avoir exécuté les commandes précédentes sur chaque ordinateur, choisissez une des machines à être votre maître de Kubernetes. Amusants ensuite les commandes suivantes sur cet ordinateur.

1. Tout d’abord, créez un fichier rbac.yaml dans votre répertoire actuel avec la commande suivante. 

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

1. Initialiser le maître de Kubernetes sur cet ordinateur. Vous devez voir la sortie que le maître de Kubernetes a été correctement initialisé.

   ```bash
   KUBE_VERSION=1.11.3
   sudo kubeadm init --pod-network-cidr=10.244.0.0/16 --kubernetes-version=$KUBE_VERSION
   ```

1. Remarque la `kubeadm join` commande que vous devez utiliser sur les autres serveurs à rejoindre le cluster Kubernetes. Copiez ceci pour une utilisation ultérieure.

   ![jointure de kubeadm](./media/deploy-with-kubeadm/kubeadm-join.png)

1. Configurer un fichier de configuration Kubernetes de votre répertoire de base.

   ```bash
   mkdir -p $HOME/.kube
   sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
   sudo chown $(id -u):$(id -g) $HOME/.kube/config
   ```

1. Configurer le cluster et le tableau de bord Kubernetes.

   ```bash
   kubectl apply -f https://raw.githubusercontent.com/coreos/flannel/master/Documentation/kube-flannel.yml
   helm init
   kubectl apply -f rbac.yaml
   kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/master/src/deploy/recommended/kubernetes-dashboard.yaml
   kubectl create clusterrolebinding kubernetes-dashboard --clusterrole=cluster-admin --serviceaccount=kube-system:kubernetes-dashboard
   ```

## <a name="configure-the-kubernetes-agents"></a>Configurer les agents Kubernetes

Les autres ordinateurs agira en tant qu’agents Kubernetes dans le cluster. 

Sur chacun des autres ordinateurs, exécutez le `kubeadm join` commande que vous avez copiée dans la section précédente.

![agents de jointure kubeadm](./media/deploy-with-kubeadm/kubeadm-join-agents.png)

## <a name="view-the-cluster-status"></a>Afficher l’état du cluster

Pour vérifier la connexion à votre cluster, utilisez le [kubectl get](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands) commande pour retourner une liste des nœuds du cluster.

```bash
kubectl get nodes
```

## <a name="next-steps"></a>Étapes suivantes

Les étapes décrites dans cet article configuré un cluster Kubernetes sur plusieurs machines Ubuntu. L’étape suivante consiste à déployer le cluster de données volumineux de SQL Server 2019. Pour obtenir des instructions, consultez l’article suivant :

[Déployer SQL Server 2019 CTP 2.1 sur Kubernetes](deployment-guidance.md#deploy)
