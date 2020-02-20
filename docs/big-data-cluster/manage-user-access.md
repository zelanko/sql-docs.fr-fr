---
title: Gérer l’accès à un cluster Big Data en mode Active Directory
description: Gérer l’accès au cluster Big Data
author: NelGson
ms.author: negust
ms.reviewer: mikeray
ms.date: 12/06/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 9f9cca7e761b8f8ec3f5b87e9a195a0eb8b5da6d
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "76259457"
---
# <a name="manage-big-data-cluster-access-in-active-directory-mode"></a>Gérer l’accès à un cluster Big Data en mode Active Directory

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article explique comment mettre à jour les groupes d’Active Directory fournis lors du déploiement pour clusterAdmins et clusterUsers.

## <a name="two-overarching-roles-in-the-big-data-cluster"></a>Deux rôles principaux dans le cluster Big Data

Les groupes Active Directory peuvent être fournis dans la section sécurité du profil de déploiement comme faisant partie des rôles principaux de l’autorisation dans le cluster Big Data :

* `clusterAdmins`: Ce paramètre prend un groupe Active Directory. Les membres de ce groupe obtiennent des autorisations d’administrateur pour le cluster entier. Ils possèdent des autorisations *sysadmin* dans SQL Server, des autorisations *superutilisateur* dans Hadoop Distributed File System (HDFS) et Spark et des droits *administrateur* dans le contrôleur.

* `clusterUsers`: Ces groupes Active Directory sont des utilisateurs réguliers sans autorisations administrateur dans le cluster. Ils disposent d’autorisations pour se connecter à l’instance maître SQL Server mais, par défaut, ils n’ont pas d’autorisation aux objets ni aux données.

Une façon d’octroyer des autorisations de groupes Active Directory supplémentaires au cluster Big Data après le déploiement consiste à ajouter des utilisateurs et des groupes supplémentaires aux groupes déjà désignés au cours du déploiement. 

Toutefois, les administrateurs ne peuvent pas toujours modifier les appartenances aux groupes dans Active Directory. Pour octroyer des autorisations de groupes Active Directory supplémentaires sans modifier les appartenances aux groupes dans Active Directory, effectuez les procédures décrites dans les sections suivantes.

## <a name="grant-administrator-permissions-to-additional-active-directory-groups"></a>Octoyer des autorisations d’administrateur à des groupes Active Directory supplémentaires

>[!IMPORTANT]
>Cette procédure n’octroie pas aux groupes Active Directory supplémentaires l’accès administrateur aux composants Hadoop, tels que HDFS et Spark, dans le cluster Big Data. Ces composants n’autorisent qu’un seul groupe Active Directory en tant que groupe superutilisateur. Cette restriction signifie que le groupe spécifié dans `clusterAdmins` pendant le déploiement reste le groupe superutilisateur même après cette étape.

En suivant les procédures de cette section, vous pouvez octroyer l’accès administrateur au contrôleur et à l’instance maître SQL Server.

### <a name="create-a-login-for-the-active-directory-user-or-group-in-the-sql-server-master-instance"></a>Créer une connexion pour l’utilisateur ou le groupe Active Directory dans l’instance maître SQL Server 

1. Connectez-vous au point de terminaison SQL maître à l’aide de votre client SQL préféré. Utilisez n’importe quelle connexion d’administrateur (par exemple, `AZDATA_USERNAME`, fournie pendant le déploiement). Il peut également s’agir d’un compte Active Directory qui appartient au groupe Active Directory fourni comme `clusterAdmins` dans la configuration de la sécurité.

1. Pour créer une connexion pour l’utilisateur ou le groupe Active Directory, exécutez la commande TSQL suivante :

   ```sql
   CREATE LOGIN [<domain>\<principal>] FROM WINDOWS;
   ```

   Si vous octroyez des autorisations d’administrateur dans l’instance, octroyez également l’autorisation suivante :

   ```sql
   ALTER SERVER ROLE sysadmin ADD MEMBER [<domain>\<principal>];
   GO
   ```

### <a name="add-the-active-directory-user-or-group-to-the-roles-table-in-the-controller-database"></a>Ajouter l’utilisateur ou le groupe Active Directory à la table des rôles dans la base de données du contrôleur 

1. Obtenez les informations d’identification SQL Server du contrôleur en exécutant les commandes suivantes :

   a. Exécutez cette commande en tant qu’administrateur Kubernetes :

   ```bash
   kubectl get secret controller-sa-secret -n <cluster name> -o yaml | grep password
   ```

   b. Décoder le secret au format Base64 :

   ```bash
   echo <password from kubectl command>  | base64 --decode && echo
   ```

1. Dans une fenêtre de commande distincte, exposez le port du serveur de base de données du contrôleur :

   ```bash
   kubectl port-forward controldb-0 1433:1433 --address 0.0.0.0 -n <cluster name>
   ```

1. Utilisez la connexion précédente pour insérer une ligne dans la table des rôles. Saisissez la valeur *REALM* en majuscules.

   Si vous octroyez des autorisations administrateur, utilisez le rôle *bdcAdmin* dans le *\<nom de rôle>* . Pour des utilisateurs non administrateurs, utilisez le rôle *bdcUser*.

   ```sql
   USE controller;
   GO

   INSERT INTO [controller].[auth].[roles] VALUES (N'<user or group name>@<REALM>', N'<role name>')
   GO
   ```

1. Vérifiez que les membres du groupe que vous avez ajouté disposent d’autorisations d’administrateur de cluster Big Data en vous connectant au point de terminaison du contrôleur et en exécutant la commande suivante :

   ```bash
   azdata bdc config show
   ```

1. Pour des utilisateurs non administrateurs, vous pouvez vérifier l’accès en authentifiant l’instance maître SQL ou le contrôleur à l’aide de `azdata login`.

## <a name="next-steps"></a>Étapes suivantes

- [Concepts de sécurité pour les clusters Big Data SQL Server 2019](concept-security.md)
