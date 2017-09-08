---
title: "Vue d’ensemble de la sécurité (SQL Server R Services) | Microsoft Docs"
ms.custom: 
ms.date: 03/10/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8fc84754-7fbf-4c1b-9150-7d88680b3e68
caps.latest.revision: 9
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 8388d7c9d22a49a49a1a45a6fa6b479107f9ccae
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="security-overview-sql-server-r-services"></a>Vue d’ensemble de la sécurité (SQL Server R Services)

Cette rubrique décrit l’architecture de sécurité globale qui est utilisée pour connecter le moteur de base de données [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] et les composants associés au runtime R. Des exemples du processus de sécurité sont fournis pour deux scénarios courants d’utilisation de R dans un environnement d’entreprise :

+ Exécution de fonctions RevoScaleR dans [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] à partir d’un client de science des données
+ Exécution de code R directement à partir de [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] à l’aide de procédures stockées

## <a name="security-overview"></a>Vue d’ensemble de la sécurité

A [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] connexion ou compte d’utilisateur Windows est requis pour exécuter des scripts R qui utilisent des données SQL Server ou qui s’exécutent avec SQL Server en tant que le contexte de calcul. Cette exigence s’applique aux deux [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] et SQL Server 2017 Machine Learning Services. 

Le compte d’utilisateur ou de connexion identifie le *principal de sécurité*, qui peut-être plusieurs niveaux d’accès, selon les besoins de script R :
+ Autorisation d’accéder à la base de données où R est activé
+ Autorisations nécessaires pour lire des données à partir des objets sécurisés tels que des tables
+ La possibilité d’écrire les nouvelles données dans une table, comme un modèle, ou d’évaluation des résultats
+ La possibilité de créer des objets, tels que des tables, des procédures stockées qui utilisent le script R, ou personnalisé fonctionne ce travail utiliser R
+ Le droit d’installer de nouveaux packages sur l’ordinateur SQL Server ou des packages d’utiliser R fournies pour un groupe d’utilisateurs. 

Par conséquent, chaque personne qui s’exécute à l’aide du code R [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] en tant que l’exécution du contexte doit être mappé à une connexion dans la base de données. Sous la sécurité de SQL Server, il est généralement plus simple créer des rôles pour gérer les jeux d’autorisations et affecter des utilisateurs à ces rôles, au lieu de définir individuellement les autorisations utilisateur. 

Par exemple, supposons que vous avez créé un code R qui s’exécute sur votre ordinateur portable et que vous souhaitez exécuter ce code [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Vous pouvez effectuer cela uniquement si ces conditions sont remplies :

+ La base de données autorise les connexions à distance.
+ Un compte de connexion SQL dont vous avez utilisé le nom et le mot de passe dans le code R a été ajouté à [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] au niveau de l’instance. Ou, si vous utilisez l’authentification intégrée de Windows, l’utilisateur Windows spécifié dans la chaîne de connexion doit être ajouté en tant qu’utilisateur au niveau de l’instance.
+ La connexion SQL ou un utilisateur Windows doit avoir l’autorisation d’exécuter des scripts externes. En règle générale, cette autorisation ne peut être ajoutée que par un administrateur de base de données.
+ Le compte d’utilisateur SQL ou l’utilisateur Windows doit être ajouté en tant qu’utilisateur, avec les autorisations appropriées, dans chaque base de données où le travail R effectue l’une de ces opérations :
    + Extraction de données
    + Écriture ou mise à jour de données 
    + Création d’objets, tels que des tables ou des procédures stockées

Une fois la connexion ou le compte d’utilisateur Windows a été configuré et possède les autorisations nécessaires, vous pouvez exécuter le code R sur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] à l’aide d’un objet de source de données R, ou en appelant une procédure stockée. Chaque fois que R est démarré à partir de [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], la sécurité du moteur de base de données obtient le contexte de sécurité de l’utilisateur qui a démarré la tâche de R ou a exécuté la procédure stockée et gère les mappages de l’utilisateur ou d’une connexion à des objets sécurisables. 

Par conséquent, tous les travaux R qui sont lancées à partir d’un client distant doivent spécifier les informations de connexion ou un utilisateur dans le cadre de la chaîne de connexion.

## <a name="interaction-of-includessnoversionmdincludesssnoversion-mdmd-security-and-launchpad-security"></a>Interaction de la sécurité de [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] et de la sécurité de LaunchPad

Quand un script R est exécuté dans le contexte de l’ordinateur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], le service [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] obtient un compte de travail disponible (compte d’utilisateur local) auprès d’un pool de comptes de travail établi pour le processus externe et utilise ce compte de travail pour effectuer les tâches associées. 

Par exemple, si vous lancez un travail R avec vos informations d’identification de domaine Windows, votre compte risque d’être mappé au compte de travail Launchpad *SQLRUser01*.

Après avoir effectué le mappage à un compte de travail, [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] crée un jeton utilisateur qui sert à lancer les processus. 

Quand toutes les opérations [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] sont terminées, le compte de travail utilisateur est marqué comme étant libre et réintègre le pool.

Pour plus d’informations sur [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)], consultez [Nouveaux composants de SQL Server pour prendre en charge l’intégration R](../../advanced-analytics/r-services/new-components-in-sql-server-to-support-r.md).

> [!NOTE]
Pour permettre à Launchpad de gérer les comptes de travail et d’exécuter les travaux R, le groupe qui contient les comptes de travail, SQLRUserGroup, doit disposer des autorisations « Permettre l’ouverture d’une session locale » ; dans le cas contraire, R Services risque de ne pas fonctionner. Par défaut, ce droit est attribué à tous les nouveaux utilisateurs locaux, mais dans certaines organisations, les stratégies de groupe plus strictes empêchent les comptes de travail de se connecter à SQL Server pour effectuer des travaux R.  

## <a name="security-of-worker-accounts"></a>Sécurité des comptes de travail

Le mappage d’un utilisateur Windows externe ou d’une connexion SQL valide à un compte de processus de travail est valid uniquement pour la durée de vie de la durée de vie de la requête SQL qui exécute le script R. 

Les requêtes en parallèle du même compte de connexion sont mappées au même compte de travail utilisateur.

Les répertoires utilisés pour les processus sont gérés par [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] à l’aide de RLauncher, et les répertoires ont un accès limité. Si le compte de travail ne peut accéder à aucun des fichiers contenus dans les dossiers situés au-dessus du sien, il peut en revanche lire, écrire ou supprimer les enfants situés en dessous du dossier de travail de session qui a été créé pour la requête SQL avec le script R.

Pour plus d’informations sur la modification du nombre de comptes de travail, du nom des comptes ou de leur mot de passe, consultez [Modifier le pool de comptes d’utilisateurs pour SQL Server R Services](../../advanced-analytics/r-services/modify-the-user-account-pool-for-sql-server-r-services.md).


## <a name="security-isolation-for-multiple-external-scripts"></a>Isolation de sécurité pour plusieurs scripts externes

Le mécanisme d’isolation repose sur des comptes d’utilisateurs physiques. À mesure que des processus satellites sont lancés pour un runtime de langage spécifique, chaque tâche satellite utilise le compte de travail spécifié par [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]. Si une tâche nécessite plusieurs satellites, par exemple, dans le cas de requêtes en parallèle, un même compte de travail est utilisé pour toutes les tâches associées.

Un compte de travail ne peut ni afficher ni manipuler les fichiers utilisés par d’autres comptes de travail.
 
Si vous êtes administrateur de l’ordinateur, vous pouvez afficher les répertoires créés pour chaque processus. Chaque répertoire est identifié par son GUID de session.

## <a name="see-also"></a>Voir aussi
[Vue d’ensemble de l’architecture](../../advanced-analytics/r-services/architecture-overview-sql-server-r.md)

