---
title: "Vue d’ensemble de la s&#233;curit&#233; (SQL Server R Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/10/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8fc84754-7fbf-4c1b-9150-7d88680b3e68
caps.latest.revision: 9
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 7
---
# Vue d’ensemble de la s&#233;curit&#233; (SQL Server R Services)

Cette rubrique décrit l’architecture de sécurité globale qui est utilisé pour connecter le [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] moteur et les composants associés à l’exécution R de base de données. Exemples du processus de sécurité sont fournis pour les deux scénarios courants pour l’utilisation de R dans un environnement d’entreprise :

+ L’exécution des fonctions RevoScaleR dans [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] à partir d’un client de science des données
+ En cours d’exécution R directement à partir de [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] à l’aide de procédures stockées

## Vue d'ensemble de la sécurité

A [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] connexion ou compte d’utilisateur Windows est requise pour exécuter tous les travaux R qui utilisent [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)]. Le compte d’utilisateur ou de connexion identifie le *principal de sécurité*, qui doivent avoir l’autorisation pour accéder à la base de données, où R est exécuté, ainsi que des autorisations pour lire des données à partir d’objets sécurisés tels que des tables, ou d’écrire les nouvelles données ou ajouter de nouveaux objets si requis par le travail de R.

Par conséquent, il est strictement nécessaire que chaque personne qui exécute le code R contre [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] doit être mappée à une connexion dans la base de données, indépendamment de ce code est envoyé à partir d’un client de science des données distantes en utilisant les fonctions RevoScaleR ou démarré à l’aide d’une procédure stockée T-SQL. 

Par exemple, supposons que vous avez créé un code R qui s’exécute sur votre ordinateur portable, et vous souhaitez exécuter ce code sur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Vous devez vous assurer que les conditions suivantes sont remplies :

+ La base de données autorise les connexions à distance.
+ Une connexion SQL avec le nom et le mot de passe que vous avez utilisé dans le code R a été ajoutée à la [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] au niveau de l’instance. Ou, si vous utilisez l’authentification Windows intégrée, l’utilisateur Windows spécifié dans la chaîne de connexion doit être ajouté en tant qu’utilisateur sur l’instance.
+ La connexion SQL ou un utilisateur Windows doit disposer de l’autorisation d’exécution de scripts externes. En règle générale, cette autorisation peut être ajoutée uniquement par un administrateur de base de données.
+ L’ouverture de session SQL ou l’utilisateur de la fenêtre doit être ajouté en tant qu’utilisateur, avec les autorisations appropriées, dans chaque base de données dans laquelle le travail de R effectue une de ces opérations :
    + Récupération des données
    + Écriture ou la mise à jour des données 
    + Création d’objets, tels que des tables ou des procédures stockées

Une fois la connexion ou le compte d’utilisateur Windows a été mis en service et les autorisations nécessaires, vous pouvez exécuter le code R sur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] à l’aide d’un objet de source de données R ou en appelant des procédures stockées. Chaque fois que R est démarré à partir de [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], la sécurité du moteur de base de données obtient le contexte de sécurité de l’utilisateur qui a démarré la tâche R et gère les mappages de l’utilisateur ou la connexion à des objets sécurisables. 

Par conséquent, tous les travaux R qui sont lancées à partir d’un client distant doivent spécifier les informations de connexion ou un utilisateur dans le cadre de la chaîne de connexion.


## Interaction de [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] sécurité et la sécurité de la zone de lancement

Lorsqu’un script R est exécuté dans le contexte de la [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ordinateur, la [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] service obtient un compte de travail disponible (un compte d’utilisateur local) à partir d’un pool de comptes de travailleur établies pour le processus externe et utilise ce compte pour effectuer les tâches associées. 

Par exemple, si vous démarrez un travail R sous vos informations d’identification de domaine Windows, votre compte peut être mappé vers le compte de travail Launchpad *SQLRUser01*.

Après le mappage à un compte de travail, [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] crée un jeton d’utilisateur qui est utilisé pour démarrer le processus. 

Lorsque tous les [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] les opérations sont terminées, le compte utilisateur est marqué comme libres et retourné au pool.

Pour plus d’informations sur [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)], consultez la page [de nouveaux composants de SQL Server pour la prise en charge l’intégration R](../../advanced-analytics/r-services/new-components-in-sql-server-to-support-r-services.md).

## Sécurité des comptes de travail
Ce mappage d’un utilisateur externe de Windows ou d’une connexion SQL valide à un compte de travail est valide uniquement pour la durée de vie de la durée de vie de la requête SQL qui exécute le script R. 

Requêtes en parallèle à partir de la même connexion sont mappés au même compte d’utilisateur travailleur.

Les répertoires utilisés pour les processus sont gérés par la [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] à l’aide de RLauncher, et les répertoires sont à accès restreint. Le compte de travail ne peut pas accéder aux fichiers dans les dossiers au-dessus de son propre, mais elle peut lire, écrire ou supprimer des enfants sous le dossier de travail de session qui a été créé pour la requête SQL avec le script R.

Pour plus d’informations sur la façon de modifier le nombre de comptes de travail, des comptes ou des mots de passe, consultez [Modifier le Pool de compte d’utilisateur pour les Services de SQL Server R](../../advanced-analytics/r-services/modify-the-user-account-pool-for-sql-server-r-services.md).


## Isolation de sécurité pour plusieurs Scripts externes

Le mécanisme d’isolation repose sur les comptes d’utilisateurs physique. Processus de satellites sont lancées pour une exécution de langue spécifique, chaque tâche de satellites utilise le compte spécifié par le [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]. Si une tâche requiert plusieurs satellites, par exemple, dans le cas des requêtes en parallèle, un compte de travail unique est utilisé pour toutes les tâches associées.

Aucun compte de travail pour afficher ou manipuler les fichiers utilisés par d’autres comptes de travail.
 
Si vous êtes un administrateur sur l’ordinateur, vous pouvez afficher les répertoires créés pour chaque processus. Chaque annuaire est identifié par son GUID de session.

## Voir aussi
[Vue d'ensemble de l'architecture](../../advanced-analytics/r-services/architecture-overview-sql-server-r-services.md)