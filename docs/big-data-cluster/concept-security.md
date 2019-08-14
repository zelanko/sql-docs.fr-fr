---
title: Concepts de sécurité
titleSuffix: SQL Server big data clusters
description: Cet article décrit les concepts de sécurité des clusters Big Data SQL Server 2019 (préversion). Il aborde notamment les points de terminaison de cluster et l’authentification des clusters.
author: nelgson
ms.author: negust
ms.reviewer: mikeray
ms.date: 06/26/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 54ae86785590eb26fb8ac402f3ae8ab6c7f29a98
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2019
ms.locfileid: "67958663"
---
# <a name="security-concepts-for-sql-server-big-data-clusters"></a>Concepts de sécurité pour les clusters Big Data SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Un cluster Big Data sécurisé implique une prise en charge uniforme et cohérente des scénarios d’authentification et d’autorisation, à la fois sur SQL Server et HDFS/Spark. L’authentification est le processus qui consiste à vérifier l’identité d’un utilisateur ou d’un service et à confirmer qu’il correspond bien à ce qu’il prétend être. L’autorisation fait référence à l’octroi ou au refus de l’accès à des ressources spécifiques en fonction de l’identité de l’utilisateur à l’origine de la demande. Cette étape est effectuée après l’identification d’un utilisateur au moyens du processus d’authentification.

L’autorisation dans le contexte du Big Data est généralement effectuée par le biais de listes de contrôle d’accès (ACL) qui associent des identités d’utilisateur à des autorisations spécifiques. HDFS prend en charge l’autorisation en limitant l’accès aux API de service, aux fichiers HDFS et à l’exécution de travaux.

Cet article aborde les principaux concepts liés à la sécurité dans le cluster Big Data.

## <a name="cluster-endpoints"></a>Points de terminaison de cluster

Il existe trois points d’entrée au cluster Big Data :

* Passerelle HDFS/Spark (Knox) : point de terminaison basé sur HTTPS. Il sert à traiter par proxy les autres points de terminaison. La passerelle HDFS/Spark est utilisée pour accéder à des services tels que webHDFS et Livy. Chaque fois que vous voyez des références à Knox, il s’agit du point de terminaison.

* Point de terminaison de contrôleur : service de gestion de cluster Big Data qui expose les API REST pour gérer le cluster. Certains outils sont également accessibles par le biais de ce point de terminaison.

* Instance maître : point de terminaison TDS utilisé par les applications et outils de base de données pour se connecter à l’instance maître SQL Server dans le cluster.

![Points de terminaison de cluster](media/concept-security/cluster_endpoints.png)

Actuellement, il n’est pas possible d’ouvrir des ports supplémentaires pour accéder au cluster de l’extérieur.

### <a name="how-endpoints-are-secured"></a>Mode de sécurisation des points de terminaison

La sécurisation des points de terminaison dans le cluster Big Data s’effectue à l’aide de mots de passe qui peuvent être définis/mis à jour à l’aide de variables d’environnement ou de commandes CLI. Tous les mots de passe internes du cluster sont stockés sous la forme de secrets Kubernetes.  

## <a name="authentication"></a>Authentification

Lors du provisionnement du cluster, plusieurs connexions sont créées.

Certaines de ces connexions permettent aux services de communiquer entre eux, tandis que d’autres sont destinées aux utilisateurs finaux qui accèdent au cluster.

### <a name="end-user-authentication"></a>Authentification des utilisateurs finaux
Lors du provisionnement du cluster, un certain nombre de mots de passe d’utilisateur final doivent être définis à l’aide de variables d’environnement. Ces mots de passe sont utilisés par les administrateurs SQL et les administrateurs de cluster pour accéder aux services :

Nom d’utilisateur du contrôleur :
 + CONTROLLER_USERNAME=<nom_utilisateur_contrôleur>

Mot de passe du contrôleur :  
 + CONTROLLER_PASSWORD=<mot_de_passe_contrôleur>

Mot de passe d’administrateur système SQL Master : 
 + MSSQL_SA_PASSWORD=<mot_de_passe_administrateur_système_contrôleur>

Mot de passe pour accéder au point de terminaison HDFS/Spark :
 + KNOX_PASSWORD=<mot_de_passe_knox>

### <a name="intra-cluster-authentication"></a>Authentification intra-cluster

Lors du déploiement du cluster, plusieurs connexions SQL sont créées :

* Une connexion SQL spéciale est créée dans l’instance SQL du contrôleur qui est gérée par le système, avec le rôle sysadmin. Le mot de passe de cette connexion est capturé sous la forme d’un secret K8s.

* Une connexion sysadmin est créée dans toutes les instances SQL du cluster détenues et gérées par ce contrôleur. Elle est nécessaire pour que le contrôleur puisse effectuer des tâches d’administration sur ces instances, comme l’installation ou la mise à niveau à haute disponibilité. Ces connexions sont également utilisées pour la communication intra-cluster entre les instances SQL (par exemple, l’instance SQL Master qui communique avec un pool de données).

> [!NOTE]
> Dans la version actuelle, seule l’authentification de base est prise en charge. Le contrôle d’accès à granularité fine aux objets HDFS ainsi que les pools de calcul et de données d’un cluster Big Data SQL ne sont pas encore disponibles.

## <a name="intra-cluster-communication"></a>Communication intra-cluster

La communication avec des services non-SQL au sein du cluster Big Data, par exemple de Livy à Spark ou de Spark au pool de stockage, est sécurisée à l’aide de certificats. Toutes les communications de SQL Server à SQL Server sont sécurisées à l’aide de connexions SQL.

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur les clusters Big Data SQL Server, consultez les ressources suivantes :

- [Présentation des clusters Big Data SQL Server 2019](big-data-cluster-overview.md)
- [Atelier : Architecture des clusters Big Data Microsoft SQL Server](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
