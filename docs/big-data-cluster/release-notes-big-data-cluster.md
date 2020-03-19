---
title: Notes de publication des clusters Big Data SQL Server
titleSuffix: SQL Server big data clusters
description: Cet article décrit les dernières mises à jour et les problèmes connus relatifs aux clusters Big Data SQL Server.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 03/12/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 136665cbe354ce0fdbbc575d2e97759f35cb3444
ms.sourcegitcommit: 4baa8d3c13dd290068885aea914845ede58aa840
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79286223"
---
# <a name="sql-server-2019-big-data-clusters-release-notes"></a>Notes de publication des clusters Big Data SQL Server 2019

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Les notes de publication suivantes s’appliquent à [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]. Cet article est divisé en sections pour chaque mise en production. Chaque version a un lien vers un article de support décrivant les modifications CU, ainsi que des liens de téléchargement des packages Linux. L’article répertorie également les [problèmes connus](#known-issues) pour les versions les plus récentes de [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] (BDC).

## <a name="supported-platforms"></a>Plateformes prises en charge

Cette section explique les plateformes qui sont prises en charge avec les [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] (clusters BDC).

### <a name="kubernetes-platforms"></a>Plateformes Kubernetes

|Plateforme|Versions prises en charge|
|---------|---------|
|Kubernetes|Le cluster BDC requiert la version minimale Kubernetes 1.13. Consultez [Version de Kubernetes et stratégie de prise en charge des décalages de version](https://kubernetes.io/docs/setup/release/version-skew-policy/) pour découvrir la stratégie de prise en charge des versions de Kubernetes.|
|Azure Kubernetes Service (AKS)|Le cluster BDC requiert la version minimale AKS 1.13.<br/>Consultez [Versions Kubernetes prises en charge dans AKS](/azure/aks/supported-kubernetes-versions) pour découvrir la stratégie de prise en charge des versions.|

### <a name="host-os-for-kubernetes"></a>Système d’exploitation hôte pour Kubernetes

|Plateforme|Versions prises en charge|
|---------|---------|
|Red Hat Enterprise Linux|7.3, 7.4, 7.5, 7.6|
|Ubuntu|16.04|

### <a name="sql-server-editions"></a>Éditions de SQL Server

|Édition|Notes|
|---------|---------|
|Entreprise<br/>standard<br/>Développeur| L’édition du cluster Big Data est déterminée par l’édition de l’instance principale SQL Server. Au moment du déploiement, l’édition Développeur est déployée par défaut. Vous pouvez changer l’édition après le déploiement. Consultez [Configurer l’instance principale SQL Server](../big-data-cluster/configure-sql-server-master-instance.md). |

## <a name="tools"></a>Outils

|Plateforme|Versions prises en charge|
|---------|---------|
|`azdata`|La même version mineure que le serveur doit être utilisée (identique à l’instance principale SQL Server).<br/><br/>Exécutez `azdata –-version` pour valider la version.<br/><br/>À compter de SQL Server 2019 CU3, cette version est `15.0.4023`.|
|Azure Data Studio|Procurez-vous la dernière version d’[Azure Data Studio](https://aka.ms/getazuredatastudio).|

## <a name="release-history"></a>Historique des mises en production

La table suivante énumère l’historique des mises en production pour [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)].

| Libérer               | Version       | Date de publication |
|-----------------------|---------------|--------------|
| [CU3](#cu3)           | 15.0.4023.6    | 2020-03-12   |
| [CU2](#cu2)           | 15.0.4013.40    | 2020-02-13   |
| [CU1](#cu1)           | 15.0.4003.23   | 2020-01-07   |
| [GDR1](#rtm)            | 15.0.2070.34  | 04-11-2019   |

## <a name="how-to-install-updates"></a>Comment installer les mises à jour

Pour installer les mises à jour, consultez [Comment mettre à niveau [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]](deployment-upgrade.md).

## <a id="cu3"></a> CU3 (mars 2020)

Mise à jour cumulative 3 (CU3) pour SQL Server 2019. La version du moteur de base de données SQL Server pour cette version est 15.0.4023.6.

|Version du package | Balise d'image |
|-----|-----|
|15.0.4023.6 |[2019-CU3-ubuntu-16.04]

### <a name="resolved-issues"></a>Problèmes résolus

SQL Server 2019 CU3 résout les problèmes suivants des versions précédentes.

- [Déploiement avec référentiel privé](#deployment-with-private-repository)
- [La mise à niveau peut échouer en raison du délai d’expiration](#upgrade-may-fail-due-to-timeout)

## <a id="cu2"></a> CU2 (Fév 2020)

Mise à jour cumulative 2 (CU2) pour SQL Server 2019. La version du moteur de base de données SQL Server pour cette version est 15.0.4013.40.

|Version du package | Balise d'image |
|-----|-----|
|15.0.4013.40 |[2019-CU2-ubuntu-16.04]

## <a id="cu1"></a> CU1 (Jan 2020)

Mise à jour cumulative 1 (CU1) pour SQL Server 2019. La version du moteur de base de données SQL Server pour cette version est 15.0.4003.23.

|Version du package | Balise d'image |
|-----|-----|
|15.0.4003.23|[2019-CU1-ubuntu-16.04]

## <a id="rtm"></a> GDR1 (Nov 2019)

SQL Server 2019 GDR1 (General Distribution Release 1) : offre une disponibilité générale pour [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-nover.md)]. La version du moteur de base de données SQL Server pour cette version est 15.0.2070.34.

|Version du package | Balise d'image |
|-----|-----|
|15.0.2070.34|[2019-GDR1-ubuntu-16.04]

[!INCLUDE [sql-server-servicing-updates-version-15](../includes/sql-server-servicing-updates-version-15.md)]

## <a name="known-issues"></a>Problèmes connus

### <a name="deployment-with-private-repository"></a>Déploiement avec dépôt privé

- **Versions concernées** : GDR1, CU1, CU2. Résolu pour CU3.

- **Problème et impact sur le client** : La mise à niveau à partir d’un dépôt privé a des exigences spécifiques

- **Solution de contournement** : Si vous utilisez un dépôt privé pour pré-extraire les images pour le déploiement ou la mise à niveau de BDC, assurez-vous que les images de build actuelles et les images de build cibles se trouvent dans le dépôt privé. Cela permet une restauration réussie, si nécessaire. En outre, si vous avez modifié les informations d’identification du dépôt privé depuis le déploiement d’origine, mettez à jour le secret correspondant dans Kubernetes avant de procéder à la mise à niveau. `azdata` ne prend pas en charge la mise à jour des informations d’identification via les variables d’environnement `AZDATA_PASSWORD` et `AZDATA_USERNAME`. Mettez à jour le secret à l’aide de [`kubectl edit secrets`](https://kubernetes.io/docs/concepts/configuration/secret/#editing-a-secret). 

La mise à niveau à l’aide de dépôts différents pour les builds actuels et cibles n’est pas prise en charge.

### <a name="upgrade-may-fail-due-to-timeout"></a>La mise à niveau peut échouer en raison du délai d’expiration

- **Versions concernées** : GDR1, CU1, CU2. Résolu pour CU 3.

- **Problème et impact sur le client** : Une mise à niveau peut échouer en raison du délai d’expiration.

   Le code suivant montre à quoi peut ressembler l’échec :

   ```
   >azdata.EXE bdc upgrade --name <mssql-cluster>
   Upgrading cluster to version 15.0.4003

   NOTE: Cluster upgrade can take a significant amount of time depending on
   configuration, network speed, and the number of nodes in the cluster.

   Upgrading Control Plane.
   Control plane upgrade failed. Failed to upgrade controller.
   ```

   Cette erreur est plus susceptible de se produire lorsque vous mettez à niveau BDC dans Azure Kubernetes Service (AKS).

- **Solution de contournement** : Augmentez le délai d’expiration de la mise à niveau. 

   Pour augmenter les délais d’attente pour une mise à niveau, modifiez le mappage de configuration de mise à niveau. Pour modifier le mappage de configuration de mise à niveau :

   1. Exécutez la commande suivante :

      ```bash
      kubectl edit configmap controller-upgrade-configmap
      ```

   2. Modifiez les champs suivants :

       **`controllerUpgradeTimeoutInMinutes`** Spécifie le nombre de minutes à attendre avant la fin de la mise à niveau du contrôleur ou de la base de données du contrôleur. La valeur par défaut est 5. Mettez à jour vers au moins 20.

       **`totalUpgradeTimeoutInMinutes`**  : Désigne la durée combinée du contrôleur et de la base de données du contrôleur pour terminer la mise à niveau (contrôleur + base de données contrôleur). La valeur par défaut est 10. Mettez à jour vers au moins 40.

       **`componentUpgradeTimeoutInMinutes`**  : Désigne la durée d’exécution de chaque phase suivante de la mise à niveau.  La valeur par défaut est 30. Mettez à jour vers 45.

   3. Enregistrez et quittez

   Le script Python ci-dessous est une autre façon de définir le délai d’expiration :

   ```python
   from kubernetes import client, config
   import json

   def set_upgrade_timeouts(namespace, controller_timeout=20, controller_total_timeout=40, component_timeout=45):
       """ Set the timeouts for upgrades

       The timeout settings are as follows

       controllerUpgradeTimeoutInMinutes: sets the max amount of time for the controller
           or controllerdb to finish upgrading

       totalUpgradeTimeoutInMinutes: sets the max amount of time to wait for both the
           controller and controllerdb to complete their upgrade

       componentUpgradeTimeoutInMinutes: sets the max amount of time allowed for
           subsequent phases of the upgrade to complete
       """
       config.load_kube_config()

       upgrade_config_map = client.CoreV1Api().read_namespaced_config_map("controller-upgrade-configmap", namespace)

       upgrade_config = json.loads(upgrade_config_map.data["controller-upgrade"])

       upgrade_config["controllerUpgradeTimeoutInMinutes"] = controller_timeout

       upgrade_config["totalUpgradeTimeoutInMinutes"] = controller_total_timeout

       upgrade_config["componentUpgradeTimeoutInMinutes"] = component_timeout

       upgrade_config_map.data["controller-upgrade"] = json.dumps(upgrade_config)

       client.CoreV1Api().patch_namespaced_config_map("controller-upgrade-configmap", namespace, upgrade_config_map)
   ```

### <a name="livy-job-submission-from-azure-data-studio-ads-or-curl-fail-with-500-error"></a>Échec de l’envoi de tâches Livy à partir d’Azure Data Studio (ADS) ou de curl avec l’erreur 500

- **Problème et impact sur le client** : Dans une configuration à haute disponibilité, les ressources partagées Spark `sparkhead` sont configurées avec plusieurs réplicas. Dans ce cas, vous pouvez rencontrer des échecs lors de l’envoi de tâches Livy à partir d’Azure Data Studio (ADS) ou de `curl`. Pour vérifier, une opération `curl` vers n’importe quel pod `sparkhead` entraîne un refus de connexion. Par exemple, `curl https://sparkhead-0:8998/` ou `curl https://sparkhead-1:8998` retourne l’erreur 500.

   Ceci est le cas dans les scénarios suivants :

   - Les pods ou les processus Zookeeper pour chaque instance Zookeeper sont redémarrés plusieurs fois.
   - Lorsque la connectivité réseau n’est pas fiable entre le pod `sparkhead` et les pods Zookeeper.

- **Solution de contournement** : Redémarrage des deux serveurs Livy.

   ```bash
   kubectl -n <clustername> exec sparkhead-0 -c hadoop-livy-sparkhistory supervisorctl restart livy
   ```

   ```bash
   kubectl -n <clustername> exec sparkhead-1 -c hadoop-livy-sparkhistory supervisorctl restart livy
   ```

### <a name="create-memory-optimized-table-when-master-instance-in-an-availability-group"></a>Créer une table à mémoire optimisée lorsque l’instance principale est dans un groupe de disponibilité

- **Problème et impact sur le client** : Vous ne pouvez pas utiliser le point de terminaison principal exposé pour la connexion aux bases de données du groupe de disponibilité (écouteur) pour créer des tables à mémoire optimisée.

- **Solution de contournement** : Pour créer des tables à mémoire optimisée lorsque l’instance principale SQL Server est une configuration de groupe de disponibilité, [connectez-vous à l’instance SQL Server](deployment-high-availability.md#instance-connect), exposez un point de terminaison, connectez-vous à la base de données SQL Server et créez les tables optimisées en mémoire dans le session créée avec la nouvelle connexion.

### <a name="insert-to-external-tables-active-directory-authentication-mode"></a>Insérer dans des tables externes en mode d’authentification Active Directory

- **Problème et impact sur le client** : Lorsque l’instance principale SQL Server est en mode d’authentification Active Directory, une requête qui sélectionne uniquement à partir de tables externes où au moins l’une des tables externes figure dans un pool de stockage, et insère dans une autre table externe, retourne :

   ```
   Msg 7320, Level 16, State 102, Line 1
   Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "SQLNCLI11". Only domain logins can be used to query Kerberized storage pool.
   ```

- **Solution de contournement** : Modifiez la requête de l’une des manières suivantes. Joignez d’abord la table de pool de stockage à une table locale, ou insérez dans la table locale, puis lisez la table locale pour l’insérer dans le pool de données.

### <a name="transparent-data-encryption-capabilities-can-not-be-used-with-databases-that-are-part-of-the-availability-group-in-the-sql-server-master-instance"></a>Les fonctionnalités de Transparent Data Encryption ne peuvent pas être utilisées avec des bases de données qui font partie du groupe de disponibilité dans l’instance maître SQL Server

- **Problème et impact sur le client** : Dans une configuration à haute disponibilité, les bases de données pour lesquelles le chiffrement est activé ne peuvent pas être utilisées après un basculement, car la clé principale utilisée pour le chiffrement est différente sur chaque réplica. 

- **Solution de contournement** : Il n’existe aucune solution de contournement pour ce problème. Nous vous recommandons de ne pas activer le chiffrement dans cette configuration tant qu’un correctif n’est pas en place.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)], consultez [Que sont les [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] ?](big-data-cluster-overview.md)
