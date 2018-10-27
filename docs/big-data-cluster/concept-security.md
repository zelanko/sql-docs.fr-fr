---
title: Concepts de sécurité pour le cluster de données volumineux de SQL Server | Microsoft Docs
description: Cet article décrit les concepts de sécurité pour le cluster de données volumineux de SQL Server 2019.
author: nelgson
ms.author: negust
manager: craigg
ms.date: 10/01/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 77ffea6b2507bde65b914c52eaf225e1fd1dbd31
ms.sourcegitcommit: 182d77997133a6e4ee71e7a64b4eed6609da0fba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50050881"
---
# <a name="security-concepts-for-sql-server-big-data-cluster"></a>Concepts de sécurité pour le cluster de données volumineux de SQL Server

Un cluster de sécuriser les données big implique la prise en charge uniforme et cohérent pour les scénarios d’authentification et d’autorisation, sur SQL Server et HDFS/Spark. L’authentification est le processus de vérification de l’identité d’un utilisateur ou d’un service et garantir qu’ils sont qui ils sont prétendant être. Autorisation fait référence à l’octroi ou de refus d’accès à des ressources spécifiques en fonction de l’identité de l’utilisateur demandeur. Cette étape est effectuée une fois que l’utilisateur est identifié via l’authentification.

Autorisation dans le contexte de données volumineuses est généralement effectuée via les listes de contrôle d’accès (ACL), qui associent les identités des utilisateurs avec des autorisations spécifiques. HDFS prend en charge d’autorisation en limitant l’accès aux API de service, les fichiers HDFS et l’exécution du travail.

Cet article décrit les concepts clés relatifs à la sécurité dans le cluster de données volumineux.

## <a name="cluster-endpoints"></a>Points de terminaison de cluster

Il existe trois points d’entrée pour le cluster de données volumineux

* Passerelle HDFS/Spark (Knox) – il s’agit d’un point de terminaison HTTPS. Autres points de terminaison sont transmises via ce. Passerelle HDFS/Spark est utilisé pour accéder aux services tels que webHDFS et Livy. Là où vous voyez des références à Knox, c’est le point de terminaison.

* Point de terminaison contrôleur – service de gestion de cluster big data qui expose les API REST de gestion de cluster. Certains outils, tels que le portail d’administration, sont également accessibles via ce point de terminaison.

* Instance principale - point de terminaison TDS pour les outils de base de données et applications de se connecter à une Instance de SQL Server Master dans le cluster.

![Points de terminaison de cluster](media/concept-security/cluster_endpoints.png)

Actuellement, il n’existe aucune option de l’ouverture de ports supplémentaires pour l’accès au cluster à partir de l’extérieur.

### <a name="how-endpoints-are-secured"></a>Sécurisation des points de terminaison

Sécurisation des points de terminaison dans le cluster de données volumineux s’effectue à l’aide de mots de passe qui peuvent être jeu/mis à jour soit à l’aide de variables d’environnement ou des commandes CLI. Tous les mots de passe interne cluster sont stockés en tant que secrets de Kubernetes.  

# <a name="authentication"></a>Authentification

Lors de la configuration du cluster, un nombre de connexions est créé.

Certaines de ces connexions sont des services communiquer entre eux, et d’autres pour les utilisateurs finaux accéder au cluster.

## <a name="end-user-authentication"></a>Authentification des utilisateurs finaux
Lors de l’approvisionnement du cluster, un nombre de mots de passe de l’utilisateur final doit être définie à l’aide de variables d’environnement. Il s’agit des mots de passe des administrateurs de cluster et SQL permettent d’accéder aux services :

Nom d’utilisateur du contrôleur :
 + CONTROLLER_USERNAME = < controller_username >

Mot de passe de contrôleur :  
 + CONTROLLER_PASSWORD = < controller_password >

Mot de passe administrateur système Master de SQL : 
 + MSSQL_SA_PASSWORD = < controller_sa_password >

Mot de passe pour le point de terminaison HDFS/Spark de l’accès à :
 + KNOX_PASSWORD = < knox_password >

## <a name="intra-cluster-authentication"></a>Authentification du cluster intra

 Lors du déploiement du cluster, un nombre de connexions SQL est créé :

* Une connexion SQL spéciale est créée dans l’instance SQL de contrôleur qui est le système géré, avec le rôle sysadmin. Le mot de passe pour cette connexion est capturé en tant que K8s secret.

* Une connexion de sysadmin est créée dans toutes les instances SQL dans le cluster, ce qui contrôleur possède et gère. Il est requis pour le contrôleur effectuer des tâches administratives, telles que le programme d’installation de haute disponibilité ou de mise à niveau, sur ces instances. Ces connexions sont également utilisées pour la communication intra-cluster entre les instances SQL, telles que l’instance principale de SQL communique avec un pool de données.

> [!NOTE]
> CTP2.0, seule l’authentification de base est prise en charge. Contrôle d’accès précis aux objets HDFS et SQL big cluster calcul et données pools de données, n’est pas encore disponible.

## <a name="intra-cluster-communication"></a>Communication entre les clusters

Communication avec les services non-SQL au sein du cluster de données volumineuses, telles que Livy Spark ou Spark au pool de stockage, est sécurisée à l’aide de certificats. Tous les SQL Server pour la communication de SQL Server est sécurisé à l’aide de connexions SQL.

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur les clusters de données volumineuses de SQL Server, consultez les articles suivants :

- [Quelles sont les clusters SQL Server 2019 big data ?](big-data-cluster-overview.md)
- [Démarrage rapide : Déployer le cluster de données volumineux de SQL Server sur Kubernetes](quickstart-big-data-cluster-deploy.md)
