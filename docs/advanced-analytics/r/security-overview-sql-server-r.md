---
title: Sécurité pour l’apprentissage de SQL Server et R | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: c04670464d23f0951a957df945a2e81b817ae134
ms.sourcegitcommit: 2666ca7660705271ec5b59cc5e35f6b35eca0a96
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43889185"
---
# <a name="security-for-sql-server-machine-learning-and-r"></a>Sécurité pour l’apprentissage de SQL Server et R
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article décrit l’architecture de sécurité globale qui permet de connecter le [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] moteur et des composants associés au runtime R de base de données. Exemples du processus de sécurité sont fournis pour ces scénarios courants d’utilisation de R dans un environnement d’entreprise :

+ Exécution de fonctions RevoScaleR dans [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] à partir d’un client de science des données
+ Exécution de code R directement à partir de [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] à l’aide de procédures stockées

## <a name="security-overview"></a>Vue d’ensemble de la sécurité

A [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] connexion ou compte d’utilisateur Windows est requis pour exécuter des scripts R qui utilisent des données SQL Server ou qui s’exécutent avec SQL Server comme contexte de calcul. Cette exigence s’applique aux deux [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] et SQL Server 2017 [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)].

Le compte d’utilisateur ou de connexion identifie le *principal de sécurité*, qui ont peut-être besoin de plusieurs niveaux d’accès, selon les besoins de script R :

+ Autorisation d’accéder à la base de données où R est activé
+ Autorisations nécessaires pour lire des données à partir des objets sécurisés tels que des tables
+ La capacité d’écrire de nouvelles données à une table, tels qu’un modèle, ou résultats d’évaluation
+ La possibilité de créer de nouveaux objets, tels que des tables, des procédures stockées qui utilisent le script R, ou custom fonctions ce travail de l’utilisation de R
+ Droit d’installer de nouveaux packages sur l’ordinateur de SQL Server, ou les packages d’utilisation de R fournis à un groupe d’utilisateurs. 

Par conséquent, chaque personne qui s’exécute à l’aide du code R [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] en tant que l’exécution du contexte doit être mappé à une connexion dans la base de données. Sous la sécurité de SQL Server, il est généralement plus facile de créer des rôles pour gérer des ensembles d’autorisations et affecter des utilisateurs à ces rôles, au lieu de définir individuellement les autorisations utilisateur. 

Par exemple, supposons que vous avez créé un code R qui s’exécute sur votre ordinateur portable, et que vous souhaitez exécuter ce code sur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Vous pouvez effectuer cela uniquement si ces conditions sont remplies :

+ La base de données autorise les connexions à distance.
+ Un compte de connexion SQL dont vous avez utilisé le nom et le mot de passe dans le code R a été ajouté à [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] au niveau de l’instance. Ou, si vous utilisez l’authentification intégrée de Windows, l’utilisateur Windows spécifié dans la chaîne de connexion doit être ajouté en tant qu’utilisateur au niveau de l’instance.
+ Le compte de connexion SQL ou l’utilisateur de Windows doit avoir l’autorisation d’exécuter des scripts externes. En règle générale, cette autorisation ne peut être ajoutée que par un administrateur de base de données.
+ Le compte d’utilisateur SQL ou l’utilisateur Windows doit être ajouté en tant qu’utilisateur, avec les autorisations appropriées, dans chaque base de données où le travail R effectue l’une de ces opérations :
    + Extraction de données
    + Écriture ou mise à jour de données 
    + Création d’objets, tels que des tables ou des procédures stockées

Une fois la connexion ou un compte d’utilisateur Windows a été mis en service et les autorisations nécessaires, vous pouvez exécuter le code R sur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] à l’aide d’un objet de source de données R ou en appelant une procédure stockée. Chaque fois que R est lancé à partir de [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], la sécurité du moteur de base de données obtient le contexte de sécurité de l’utilisateur qui a démarré le travail R ou a exécuté la procédure stockée et gère les mappages de l’utilisateur ou d’une connexion à des objets sécurisables. 

Par conséquent, tous les travaux R qui sont lancées à partir d’un client distant doivent spécifier les informations de connexion ou un utilisateur dans le cadre de la chaîne de connexion.

## <a name="interaction-of-includessnoversionmdincludesssnoversion-mdmd-security-and-launchpad-security"></a>Interaction de [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] sécurité et la sécurité de Launchpad

Quand un script R est exécuté dans le contexte de l’ordinateur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], le service [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] obtient un compte de travail disponible (compte d’utilisateur local) auprès d’un pool de comptes de travail établi pour le processus externe et utilise ce compte de travail pour effectuer les tâches associées. 

Par exemple, si vous lancez un travail R avec vos informations d’identification de domaine Windows, votre compte risque d’être mappé au compte de travail Launchpad *SQLRUser01*.

Après avoir effectué le mappage à un compte de travail, [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] crée un jeton utilisateur qui sert à lancer les processus. 

Quand toutes les opérations [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] sont terminées, le compte de travail utilisateur est marqué comme étant libre et réintègre le pool.

Pour plus d’informations sur le service, consultez [Extensibility framework](../concepts/extensibility-framework.md). 

### <a name="implied-authentication"></a>Authentification implicite

**L’authentification implicite** est le terme utilisé pour le processus sous lequel SQL Server obtient l’utilisateur des informations d’identification, puis exécute toutes les tâches de script externe au profit des utilisateurs, en supposant que l’utilisateur dispose des autorisations appropriées dans la base de données. L’authentification implicite est particulièrement importante si le script R a besoin effectuer un appel ODBC en dehors de la base de données SQL Server. Par exemple, le code peut récupérer une liste plus courte des facteurs à partir d’une feuille de calcul ou une autre source.

Pour ces appels de bouclage réussisse, le groupe qui contient les comptes de travail, SQLRUserGroup, doit disposer des autorisations « Autoriser l’ouverture d’une session locale ». Par défaut, ce droit est attribué à tous les nouveaux utilisateurs locaux, mais dans certaines organisations des stratégies de groupe plus strictes peuvent être appliquées.

![Authentification implicite pour R](media/implied-auth-rsql.png)

## <a name="security-of-worker-accounts"></a>Sécurité des comptes de travail

Le mappage d’un utilisateur Windows externe ou d’une connexion SQL valide à un compte de travail est valide uniquement pendant la durée de vie de la durée de vie de la requête SQL qui exécute le script R.

Les requêtes en parallèle du même compte de connexion sont mappées au même compte de travail utilisateur.

Les répertoires utilisés pour les processus sont gérés par [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] à l’aide de RLauncher, et les répertoires ont un accès limité. Si le compte de travail ne peut accéder à aucun des fichiers contenus dans les dossiers situés au-dessus du sien, il peut en revanche lire, écrire ou supprimer les enfants situés en dessous du dossier de travail de session qui a été créé pour la requête SQL avec le script R.

Pour plus d’informations sur la façon de modifier le nombre de comptes de travail, les noms de compte ou les mots de passe de compte, consultez [modifier le pool de comptes d’utilisateur pour l’apprentissage de SQL Server](../../advanced-analytics/r/modify-the-user-account-pool-for-sql-server-r-services.md).

## <a name="security-isolation-for-multiple-external-scripts"></a>Isolation de sécurité pour plusieurs scripts externes

Le mécanisme d’isolation repose sur des comptes d’utilisateurs physiques. À mesure que des processus satellites sont lancés pour un runtime de langage spécifique, chaque tâche satellite utilise le compte de travail spécifié par [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]. Si une tâche nécessite plusieurs satellites, par exemple, dans le cas de requêtes en parallèle, un même compte de travail est utilisé pour toutes les tâches associées.

Un compte de travail ne peut ni afficher ni manipuler les fichiers utilisés par d’autres comptes de travail.
 
Si vous êtes administrateur de l’ordinateur, vous pouvez afficher les répertoires créés pour chaque processus. Chaque répertoire est identifié par son GUID de session.

## <a name="see-also"></a>Voir aussi

[Présentation de l’architecture pour l’apprentissage de SQL Server](../../advanced-analytics/r/architecture-overview-sql-server-r.md)
