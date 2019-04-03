---
title: Concepts de sécurité
titleSuffix: SQL Server big data clusters
description: Cet article décrit les concepts de sécurité pour SQL Server 2019 cluster de données volumineux (version préliminaire). Cela inclut les décrivant les points de terminaison de cluster et l’authentification du cluster.
author: nelgson
ms.author: negust
ms.reviewer: jroth
manager: craigg
ms.date: 12/06/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: ebe1ef0a9a0337af29a09018bcc2e0150d676879
ms.sourcegitcommit: 2de5446fbc57787f18a907dd5deb02a7831ec07d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58860110"
---
# <a name="security-concepts-for-sql-server-big-data-clusters"></a>Concepts de sécurité pour les clusters de données volumineuses de SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Un cluster de sécuriser les données big implique la prise en charge uniforme et cohérent pour les scénarios d’authentification et d’autorisation, sur SQL Server et HDFS/Spark. L’authentification est le processus de vérification de l’identité d’un utilisateur ou d’un service et garantir qu’ils sont qui ils sont prétendant être. Autorisation fait référence à l’octroi ou de refus d’accès à des ressources spécifiques en fonction de l’identité de l’utilisateur demandeur. Cette étape est effectuée une fois que l’utilisateur est identifié via l’authentification.

Autorisation dans le contexte de données volumineuses est généralement effectuée via les listes de contrôle d’accès (ACL), qui associent les identités des utilisateurs avec des autorisations spécifiques. HDFS prend en charge d’autorisation en limitant l’accès aux API de service, les fichiers HDFS et l’exécution du travail.

Cet article décrit les concepts clés relatifs à la sécurité dans le cluster de données volumineux.

## <a name="cluster-endpoints"></a>Points de terminaison de cluster

Il existe trois points d’entrée pour le cluster de données volumineux

* Passerelle HDFS/Spark (Knox) - il s’agit d’un point de terminaison HTTPS. Autres points de terminaison sont transmises via ce. Passerelle HDFS/Spark est utilisé pour accéder aux services tels que webHDFS et Livy. Là où vous voyez des références à Knox, c’est le point de terminaison.

* Point de terminaison contrôleur - service de gestion de cluster big data qui expose les API REST de gestion de cluster. Certains outils, tels que le portail d’administration, sont également accessibles via ce point de terminaison.

* Instance principale - point de terminaison TDS pour les outils de base de données et applications de se connecter à une Instance de SQL Server Master dans le cluster.

![Points de terminaison de cluster](media/concept-security/cluster_endpoints.png)

Actuellement, il n’existe aucune option de l’ouverture de ports supplémentaires pour l’accès au cluster à partir de l’extérieur.

### <a name="how-endpoints-are-secured"></a>Sécurisation des points de terminaison

Sécurisation des points de terminaison dans le cluster de données volumineux s’effectue à l’aide de mots de passe qui peuvent être jeu/mis à jour soit à l’aide de variables d’environnement ou des commandes CLI. Tous les mots de passe interne cluster sont stockés en tant que secrets de Kubernetes.  

## <a name="authentication"></a>Authentification

Lors de la configuration du cluster, un nombre de connexions est créé.

Certaines de ces connexions sont des services communiquer entre eux, et d’autres pour les utilisateurs finaux accéder au cluster.

### <a name="end-user-authentication"></a>Authentification des utilisateurs finaux
Lors de l’approvisionnement du cluster, un nombre de mots de passe de l’utilisateur final doit être définie à l’aide de variables d’environnement. Il s’agit des mots de passe des administrateurs de cluster et SQL permettent d’accéder aux services :

Nom d’utilisateur du contrôleur :
 + CONTROLLER_USERNAME = < controller_username >

Mot de passe de contrôleur :  
 + CONTROLLER_PASSWORD = < controller_password >

Mot de passe administrateur système Master de SQL : 
 + MSSQL_SA_PASSWORD=<controller_sa_password>

Mot de passe pour le point de terminaison HDFS/Spark de l’accès à :
 + KNOX_PASSWORD=<knox_password>

### <a name="intra-cluster-authentication"></a>Authentification de l’intérieur du cluster

Lors du déploiement du cluster, un nombre de connexions SQL est créé :

* Une connexion SQL spéciale est créée dans l’instance SQL de contrôleur qui est le système géré, avec le rôle sysadmin. Le mot de passe pour cette connexion est capturé en tant que K8s secret.

* Une connexion de sysadmin est créée dans toutes les instances SQL dans le cluster, ce qui contrôleur possède et gère. Il est requis pour le contrôleur effectuer des tâches administratives, telles que le programme d’installation de haute disponibilité ou de mise à niveau, sur ces instances. Ces connexions sont également utilisées pour la communication intra-cluster entre les instances SQL, telles que l’instance principale de SQL communique avec un pool de données.

> [!NOTE]
> Dans la version actuelle, seule l’authentification de base est prise en charge. Contrôle d’accès précis aux objets HDFS et SQL big cluster calcul et données pools de données, n’est pas encore disponible.

## <a name="intra-cluster-communication"></a>Communication entre les clusters

Communication avec les services non-SQL au sein du cluster de données volumineuses, telles que Livy Spark ou Spark au pool de stockage, est sécurisée à l’aide de certificats. Tous les SQL Server pour la communication de SQL Server est sécurisé à l’aide de connexions SQL.

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur les clusters de données volumineuses de SQL Server, consultez les ressources suivantes :

- [Quelles sont les clusters SQL Server 2019 big data ?](big-data-cluster-overview.md)
- [Atelier : Architecture de clusters de données volumineuses de Microsoft SQL Server](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
