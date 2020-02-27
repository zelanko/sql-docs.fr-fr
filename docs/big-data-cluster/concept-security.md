---
title: Concepts de sécurité
titleSuffix: SQL Server big data clusters
description: Cet article décrit les concepts de sécurité des clusters Big Data SQL Server. Ce contenu aborde notamment les points de terminaison de cluster et l’authentification des clusters.
author: nelgson
ms.author: negust
ms.reviewer: mikeray
ms.date: 10/23/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 0fc816325d4008d1913f0e07e3032677a0eddb4d
ms.sourcegitcommit: 11691bfa8ec0dd6f14cc9cd3d1f62273f6eee885
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2020
ms.locfileid: "77074422"
---
# <a name="security-concepts-for-big-data-clusters-2019"></a>Concepts de sécurité pour les [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article aborde les principaux concepts liés à la sécurité dans le cluster Big Data

Les [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] assurent des fonctionnalités d’autorisation et d’authentification uniformes et cohérentes. Un cluster Big Data peut être intégré à Active Directory (AD) par le biais d’un déploiement entièrement automatisé qui configure l’intégration AD sur un domaine existant. Une fois qu’un cluster Big Data est configuré avec l’intégration AD, vous pouvez tirer parti des identités et des groupes d’utilisateurs existants pour un accès unifié sur tous les points de terminaison. En outre, une fois que vous avez créé des tables externes dans SQL Server, vous pouvez contrôler l’accès aux sources de données en accordant l’accès à des tables externes aux utilisateurs et groupes AD, en centralisant ainsi les stratégies d’accès aux données à un emplacement unique.

Dans cette vidéo de 14 minutes, vous obtiendrez une vue d’ensemble de la sécurité des clusters Big Data :

> [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Overview-Big-Data-Cluster-Security/player?WT.mc_id=dataexposed-c9-niner]


## <a name="authentication"></a>Authentication

Les points de terminaison de cluster externes prennent en charge l’authentification AD. Utilisez votre identité AD pour vous authentifier auprès du cluster Big Data.

### <a name="cluster-endpoints"></a>Points de terminaison de cluster

Il existe cinq points d’entrée pour le cluster Big Data

* Instance maître : point de terminaison TDS permettant d’accéder à l’instance maître SQL Server dans le cluster, à l’aide d’outils de base de données et d’applications comme SSMS ou Azure Data Studio. Lorsque vous utilisez des commandes HDFS ou SQL Server à partir d’azdata, l’outil se connecte aux autres points de terminaison, en fonction de l’opération.

* Passerelle pour accéder aux fichiers HDFS, Spark (Knox) ; point de terminaison HTTPS pour accéder à des services tels que webHDFS et Spark.

* Point de terminaison de service de gestion de cluster (contrôleur) : service de gestion de cluster Big Data qui expose les API REST pour gérer le cluster. L’outil azdata nécessite une connexion à ce point de terminaison.

* Proxy de gestion : pour accéder au tableau de bord de recherche des journaux et au tableau de bord des métriques.

* Proxy d’application : point de terminaison pour la gestion des applications déployées dans le cluster Big Data.

![Points de terminaison de cluster](media/concept-security/cluster_endpoints.png)

Actuellement, il n’est pas possible d’ouvrir des ports supplémentaires pour accéder au cluster de l’extérieur.

## <a name="authorization"></a>Autorisation

Dans l’ensemble du cluster, la sécurité intégrée entre les différents composants permet de transmettre l’identité de l’utilisateur d’origine lors de l’émission de requêtes à partir de Spark et SQL Server jusqu’à HDFS. Comme indiqué ci-dessus, les différents points de terminaison de cluster externes prennent en charge l’authentification Active Directory.

Il existe deux niveaux de contrôles d’autorisation dans le cluster pour la gestion de l’accès aux données. L’autorisation dans le contexte de Big Data s’effectue dans SQL Server, à l’aide des autorisations SQL Server traditionnelles sur les objets et dans HDFS avec des listes de contrôle (ACL), qui associent les identités des utilisateurs à des autorisations spécifiques.

Un cluster Big Data sécurisé implique une prise en charge uniforme et cohérente des scénarios d’authentification et d’autorisation, à la fois sur SQL Server et HDFS/Spark. L’authentification est le processus qui consiste à vérifier l’identité d’un utilisateur ou d’un service et à confirmer qu’il correspond bien à ce qu’il prétend être. L’autorisation fait référence à l’octroi ou au refus de l’accès à des ressources spécifiques en fonction de l’identité de l’utilisateur à l’origine de la demande. Cette étape est effectuée après l’identification d’un utilisateur au moyens du processus d’authentification.

L’autorisation dans le contexte du Big Data est généralement effectuée par le biais de listes de contrôle d’accès (ACL) qui associent des identités d’utilisateur à des autorisations spécifiques. HDFS prend en charge l’autorisation en limitant l’accès aux API de service, aux fichiers HDFS et à l’exécution de travaux.

## <a name="encryption-and-other-security-mechanisms"></a>Chiffrement et autres mécanismes de sécurité

Le chiffrement de la communication entre les clients et les points de terminaison externes, ainsi qu’entre les composants à l’intérieur du cluster, est sécurisé avec TLS/SSL, à l’aide de certificats.

Toutes les communications de SQL Server à SQL Server, telles que l’instance maître SQL communiquant avec un pool de données, sont sécurisées à l’aide de connexions SQL.

> [!IMPORTANT]
>  Les clusters Big Data utilisent etcd pour stocker les informations d’identification. En guise de bonne pratique, assurez-vous que votre cluster Kubernetes est configuré pour utiliser le chiffrement etcd au repos. Par défaut, les secrets stockés dans etcd ne sont pas chiffrés. La documentation Kubernetes fournit des détails sur cette tâche administrative : https://kubernetes.io/docs/tasks/administer-cluster/kms-provider/ et https://kubernetes.io/docs/tasks/administer-cluster/encrypt-data/.


## <a name="basic-administrator-login"></a>Connexion administrateur de base

Vous pouvez choisir de déployer le cluster en mode AD ou à l’aide d’une connexion administrateur de base uniquement. L’utilisation de la connexion administrateur de base seule n’est pas un mode de sécurité pris en charge par la production et est destinée à l’évaluation du produit.

Même si vous choisissez le mode Active Directory, les connexions de base seront créées pour l’administrateur de cluster. Cette fonctionnalité offre un accès alternatif, en cas de défaillance de la connectivité AD.

Lors du déploiement, cette connexion de base se verra accorder des autorisations d’administrateur dans le cluster. L’utilisateur de la connexion sera administrateur système dans l’instance maître SQL Server et un administrateur dans le contrôleur de cluster.
Les composants Hadoop ne prennent pas en charge l’authentification en mode mixte, ce qui signifie qu’il n’est pas possible d’utiliser une connexion administrateur de base pour l’authentification auprès de la passerelle (Knox).

Les informations d’identification de connexion que vous devez définir lors du déploiement.

Nom d’utilisateur d’administrateur de cluster :
 + `AZDATA_USERNAME=<username>`

Mot de passe d’administrateur de cluster :  
 + `AZDATA_PASSWORD=<password>`

> [!NOTE]
> Notez que, en mode non-AD, la « racine » du nom d’utilisateur doit être utilisée conjointement avec le mot de passe ci-dessus, pour l’authentification auprès de la passerelle (Knox) pour l’accès à HDFS/Spark.

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur les [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)], consultez les ressources suivantes :

- [Que sont les [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] ?](big-data-cluster-overview.md)
- [Atelier : Architecture des [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] Microsoft](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
