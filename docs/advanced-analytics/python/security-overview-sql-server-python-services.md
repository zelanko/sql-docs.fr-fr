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
ms.openlocfilehash: 6ddfc3ccb67d017dc618cfbb7e7680c0164f3a21
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="security-overview"></a>Vue d’ensemble de la sécurité

Cette rubrique décrit l’architecture de sécurité qui permet de connecter le [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] les composants de Python et de moteur de base de données. Exemples du processus de sécurité sont fournis pour deux scénarios courants : Python en cours d’exécution dans SQL Server à l’aide d’une procédure stockée et l’exécution de Python avec SQL Server en tant que le contexte de calcul à distance.

## <a name="security-overview"></a>Vue d’ensemble de la sécurité

A [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] connexion ou compte d’utilisateur Windows est requise pour exécuter le script Python dans SQL Server. Le compte d’utilisateur ou de connexion identifie le *principal de sécurité*, qui doit détenir des autorisation d’accéder à la base de données où les données sont récupérées à partir de. Selon que le script Python crée de nouveaux objets ou écrit des nouvelles données, l’utilisateur peut avoir besoin d’autorisations pour créer des tables, écrire des données ou créer des fonctions personnalisées ou des procédures stockées.

Par conséquent, il s’agit d’une condition préalable stricte que chaque personne qui exécute le code Python dans [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] doit être mappée à une connexion ou un compte dans la base de données. Cette restriction s’applique indépendamment de si le script est envoyé à partir d’un client de science des données à distance ou de démarrage à l’aide d’une procédure stockée T-SQL.

Par exemple, supposons que vous avez créé un script Python qui s’exécute sur votre ordinateur portable et que vous souhaitez exécuter ce code [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Vous devez veiller à ce que les conditions suivantes soient réunies :

+ La base de données autorise les connexions à distance.
+ La connexion SQL ou le compte Windows que vous avez utilisé pour l’accès de la base de données a été ajouté à la [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] au niveau de l’instance.
+ Le compte de connexion SQL ou l’utilisateur Windows doit être autorisé à exécuter des scripts externes. En règle générale, cette autorisation ne peut être ajoutée que par un administrateur de base de données.
+ Le compte de connexion SQL ou l’utilisateur de la fenêtre doit être ajouté en tant qu’utilisateur, avec les autorisations appropriées, dans chaque base de données où le script Python effectue une des opérations suivantes :
    + Extraction de données
    + Écriture ou mise à jour de données
    + Création d’objets, tels que des tables ou des procédures stockées

Après la connexion ou le compte d’utilisateur Windows a été configuré et possède les autorisations nécessaires, vous pouvez exécuter le code Python [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] à l’aide d’objets de source de données fournis par le **revoscalepy** bibliothèque, ou en appelant une procédure stockée qui contient le script Python.

Chaque fois qu’un script Python est lancé à partir de [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], la sécurité du moteur de base de données obtient le contexte de sécurité de l’utilisateur qui a démarré la tâche et gère les mappages de l’utilisateur ou d’une connexion à des objets sécurisables.

Par conséquent, tous les scripts Python lancées à partir d’un client distant doivent spécifier les informations de connexion ou un utilisateur dans le cadre de la chaîne de connexion.


## <a name="interaction-of-includessnoversionmdincludesssnoversion-mdmd-security-and-launchpad-security"></a>Interaction de la sécurité de [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] et de la sécurité de LaunchPad

Lorsqu’un script Python est exécuté dans le contexte de la [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ordinateur, le [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] service obtient un compte de travail disponible (un compte d’utilisateur local) à partir d’un pool de comptes de travail établies pour les processus externes et utilise ce compte de processus de travail à effectuer les tâches associées.

Par exemple, supposons que vous lancez un script Python sous vos informations d’identification de domaine Windows. SQL Server obtenir vos informations d’identification et le mapper à un compte de processus de travail Launchpad disponible, telles que *SQLRUser01*.

> [!NOTE]
> Le nom du groupe de comptes de travail est la même, si vous utilisez R ou Python. Toutefois, un groupe distinct est créé pour chaque instance où vous permettent de n’importe quel langage externe.

Après avoir effectué le mappage à un compte de travail, [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] crée un jeton utilisateur qui sert à lancer les processus. 

Quand toutes les opérations [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] sont terminées, le compte de travail utilisateur est marqué comme étant libre et réintègre le pool.

Pour plus d’informations sur [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)], consultez [nouveaux composants de SQL Server prise en charge de l’intégration Python](../../advanced-analytics/python/new-components-in-sql-server-to-support-python-integration.md).

> [!NOTE]
> Pour le Launchpad gérer les comptes de travail et exécuter des travaux de Python, le groupe qui contient les comptes de travail, *SQLRUserGroup*, doit disposer des autorisations « Autoriser la connexion localement » ; sinon, le runtime Python ne peut-être pas démarrer. Par défaut, ce droit est attribué à tous les nouveaux utilisateurs locaux, mais dans certaines organisations, les stratégies de groupe plus strictes peuvent être appliqués, qui empêche les comptes de travail à partir de la connexion à SQL Server à des travaux de Python.

## <a name="security-of-worker-accounts"></a>Sécurité des comptes de travail

Le mappage d’un utilisateur Windows externe ou d’une connexion SQL valide à un compte de processus de travail est valide uniquement pour la durée de vie de l’instruction SQL d’une procédure stockée qui s’exécute le script Python.

Les requêtes en parallèle du même compte de connexion sont mappées au même compte de travail utilisateur.

Les répertoires utilisés pour les processus sont gérés par le [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)], et les répertoires sont à accès restreint. Pour Python, PythonLauncher effectue cette tâche. Chaque compte de travail individuel est limité à son propre dossier et ne peut pas accéder aux fichiers des dossiers au-dessus de son propre niveau. Toutefois, le compte de travail peut lire, écrire ou supprimer des enfants sous le dossier de travail de session qui a été créé.

Pour plus d’informations sur la modification du nombre de comptes de travail, du nom des comptes ou de leur mot de passe, consultez [Modifier le pool de comptes d’utilisateurs pour SQL Server R Services](../../advanced-analytics/r/modify-the-user-account-pool-for-sql-server-r-services.md).


## <a name="security-isolation-for-multiple-external-scripts"></a>Isolation de sécurité pour plusieurs scripts externes

Le mécanisme d’isolation repose sur des comptes d’utilisateurs physiques. À mesure que des processus satellites sont lancés pour un runtime de langage spécifique, chaque tâche satellite utilise le compte de travail spécifié par [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]. Si une tâche nécessite plusieurs satellites, par exemple, dans le cas de requêtes en parallèle, un même compte de travail est utilisé pour toutes les tâches associées.

Un compte de travail ne peut ni afficher ni manipuler les fichiers utilisés par d’autres comptes de travail.

Si vous êtes administrateur de l’ordinateur, vous pouvez afficher les répertoires créés pour chaque processus. Chaque répertoire est identifié par son GUID de session.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de l’architecture](../../advanced-analytics/python/architecture-overview-sql-server-python.md)

