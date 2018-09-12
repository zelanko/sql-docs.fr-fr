---
title: Vue d’ensemble de la sécurité pour Python dans SQL Server Machine Learning | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: a33701283635327fcaac4a9629cb02044b30dda8
ms.sourcegitcommit: 2666ca7660705271ec5b59cc5e35f6b35eca0a96
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43890055"
---
# <a name="security-overview-for-python-in-sql-server-machine-learning"></a>Vue d’ensemble de la sécurité pour Python dans SQL Server Machine Learning
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cette rubrique décrit l’architecture de sécurité qui permet de connecter le [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] moteur et les composants de Python de base de données. Exemples du processus de sécurité sont fournis pour deux scénarios courants : exécution de Python dans SQL Server à l’aide d’une procédure stockée et l’exécution de Python avec SQL Server comme contexte de calcul à distance.

## <a name="security-overview"></a>Vue d’ensemble de la sécurité

A [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] connexion ou compte d’utilisateur Windows est requis pour exécuter le script Python dans SQL Server. Ces *principaux de sécurité* sont gérés à l’instance et le niveau de la base de données et identifier les utilisateurs habilités à se connecter à la base de données, lire et écrire des données ou créer des objets de base de données tels que des tables ou des procédures stockées. En outre, les utilisateurs qui exécutent le script Python doivent avoir l’autorisation d’exécuter un script externe au niveau de la base de données.

Si l’utilisateur doit s’exécuter Python code de base de données, ou les objets de base de données access et les données, même les utilisateurs qui sont à l’aide de Python dans un outil externe doivent être mappés à un compte dans la base de données ou de connexion. Les mêmes autorisations sont nécessaires si le script Python est envoyé à partir d’un client de science des données distantes ou démarré à l’aide d’une procédure stockée T-SQL.

Par exemple, supposons que vous avez créé un script Python qui s’exécute sur votre ordinateur portable, et que vous souhaitez exécuter ce code sur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Vous devez veiller à ce que les conditions suivantes soient réunies :

+ La base de données autorise les connexions à distance.
+ La connexion SQL ou un compte Windows que vous avez utilisé pour l’accès de base de données a été ajouté à la [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] au niveau de l’instance.
+ Le compte de connexion SQL ou l’utilisateur Windows doit être autorisé à exécuter des scripts externes. En règle générale, cette autorisation ne peut être ajoutée que par un administrateur de base de données.
+ La connexion SQL ou l’utilisateur Windows doit être ajouté en tant qu’utilisateur, avec les autorisations appropriées, dans chaque base de données où le script Python effectue l’une de ces opérations :
    + Extraction de données
    + Écriture ou mise à jour de données
    + Création d’objets, tels que des tables ou des procédures stockées

Une fois la connexion ou un compte d’utilisateur Windows a été mis en service et les autorisations nécessaires, vous pouvez exécuter le code Python sur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] en utilisant les objets de source de données fournis par le **revoscalepy** bibliothèque, ou en appelant un stockée procédure qui contient le script Python.

Chaque fois qu’un script Python est lancé à partir de [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], la sécurité du moteur de base de données obtient le contexte de sécurité de l’utilisateur qui a démarré la tâche et gère les mappages de l’utilisateur ou d’une connexion à des objets sécurisables.

Par conséquent, tous les scripts Python qui sont lancées à partir d’un client distant doivent spécifier les informations de connexion ou un utilisateur dans le cadre de la chaîne de connexion.

## <a name="interaction-of-includessnoversionmdincludesssnoversion-mdmd-security-and-launchpad-security"></a>Interaction de [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] sécurité et la sécurité de Launchpad

Quand un script Python est exécuté dans le contexte de la [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ordinateur, le [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] service obtient un compte de travail disponible (un compte d’utilisateur local) à partir d’un pool de comptes de travail établie pour les processus externes et utilise ce compte de travail à effectuer les tâches associées.

Par exemple, supposons que vous lancez un script Python sous vos informations d’identification de domaine Windows. Obtient de vos informations d’identification de SQL Server et mappe la tâche à un compte de travail Launchpad disponible, tel que *SQLRUser01*.

> [!NOTE]
> Le nom du groupe de comptes de travail est le même, que vous utilisiez R ou Python. Toutefois, un groupe distinct est créé pour chaque instance où vous activez n’importe quel langage externe.

Après avoir effectué le mappage à un compte de travail, [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] crée un jeton utilisateur qui sert à lancer les processus. 

Quand toutes les opérations [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] sont terminées, le compte de travail utilisateur est marqué comme étant libre et réintègre le pool.

Pour plus d’informations sur le service, consultez [Extensibility framework](../concepts/extensibility-framework.md).

### <a name="implied-authentication"></a>Authentification implicite

**L’authentification implicite** est le terme utilisé pour le processus sous lequel SQL Server obtient l’utilisateur des informations d’identification, puis exécute toutes les tâches de script externe au profit des utilisateurs, en supposant que l’utilisateur dispose des autorisations appropriées dans la base de données. L’authentification implicite est particulièrement importante si le script Python a besoin effectuer un appel ODBC en dehors de la base de données SQL Server. Par exemple, le code peut récupérer une liste plus courte des facteurs à partir d’une feuille de calcul ou une autre source.

Pour ces appels de bouclage réussisse, le groupe qui contient les comptes de travail, SQLRUserGroup, doit disposer des autorisations « Autoriser l’ouverture d’une session locale ». Par défaut, ce droit est attribué à tous les nouveaux utilisateurs locaux, mais dans certaines organisations des stratégies de groupe plus strictes peuvent être appliquées.

![Authentification implicite pour R](media/implied-auth-python2.png)

## <a name="security-of-worker-accounts"></a>Sécurité des comptes de travail

Le mappage d’un utilisateur Windows externe ou d’une connexion SQL valide à un compte de travail est valide uniquement pour la durée de vie de l’instruction SQL de procédure stockée qui exécute le script Python.

Les requêtes en parallèle du même compte de connexion sont mappées au même compte de travail utilisateur.

Les répertoires utilisés pour les processus sont gérés par le [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)], et les répertoires ont un accès limité. Pour Python, PythonLauncher exécute cette tâche. Chaque compte de travail individuels est limité à son propre dossier et ne peut pas accéder aux fichiers dans les dossiers situés au-dessus du niveau de son propre. Toutefois, le compte de travail peut lire, écrire ou supprimer des enfants sous le dossier de travail de session qui a été créé.

Pour plus d’informations sur la façon de modifier le nombre de comptes de travail, les noms de compte ou les mots de passe de compte, consultez [modifier le pool de comptes d’utilisateur pour l’apprentissage de SQL Server](../../advanced-analytics/r/modify-the-user-account-pool-for-sql-server-r-services.md).


## <a name="security-isolation-for-multiple-external-scripts"></a>Isolation de sécurité pour plusieurs scripts externes

Le mécanisme d’isolation repose sur les comptes d’utilisateurs physiques. À mesure que des processus satellites sont lancés pour un runtime de langage spécifique, chaque tâche satellite utilise le compte de travail spécifié par [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]. Si une tâche nécessite plusieurs satellites, par exemple, dans le cas de requêtes en parallèle, un même compte de travail est utilisé pour toutes les tâches associées.

Un compte de travail ne peut ni afficher ni manipuler les fichiers utilisés par d’autres comptes de travail.

Si vous êtes administrateur de l’ordinateur, vous pouvez afficher les répertoires créés pour chaque processus. Chaque répertoire est identifié par son GUID de session.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de l’architecture](../../advanced-analytics/python/architecture-overview-sql-server-python.md)
