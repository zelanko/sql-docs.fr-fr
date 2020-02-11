---
title: Vue d’ensemble de la sécurité pour l’extensibilité
description: Vue d’ensemble de la sécurité de l’infrastructure d’extensibilité dans SQL Server Machine Learning Services. Sécurité pour les comptes de connexion et d’utilisateur, le service SQL Server Launchpad, les comptes de travail, l’exécution de plusieurs scripts et les autorisations de fichiers.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/17/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: f2e2d696a09e5b5bb321da583efd76f580759ce6
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "73727663"
---
# <a name="security-overview-for-the-extensibility-framework-in-sql-server-machine-learning-services"></a>Vue d’ensemble de la sécurité de l’infrastructure d’extensibilité dans SQL Server Machine Learning Services

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cet article décrit l’architecture de sécurité globale utilisée pour intégrer le moteur de base de données SQL Server et les composants associés à l’infrastructure d’extensibilité. Il examine les éléments sécurisables, les services, l’identité du processus et les autorisations. Pour plus d’informations sur les principaux concepts et composants de l’extensibilité dans SQL Server, consultez [Architecture d’extensibilité dans SQL Server Machine Learning Services](extensibility-framework.md)].

## <a name="securables-for-external-script"></a>Éléments sécurisables pour script externe

Un script externe écrit en R ou Python est soumis en tant que paramètre d’entrée à une [procédure stockée système](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) créée à cet effet, ou est encapsulé dans une procédure stockée que vous définissez. Vous pouvez également avoir des modèles préformés et stockés dans un format binaire dans une table de base de données, pouvant être appelée dans une fonction T-SQL [PREDICT](../../t-sql/queries/predict-transact-sql.md).

Étant donné que le script est fourni via des objets de schéma de la base de données, des procédures stockées et des tables existants, il n’existe aucun nouvel [élément sécurisable](../../relational-databases/security/securables.md) pour SQL Server Machine Learning Services.

Quelle que soit la façon dont vous utilisez le script ou, ce en quoi ils consistent, des objets de base de données seront créés et probablement enregistrés, mais aucun nouveau type d’objet ne sera introduit pour le stockage du script. Par conséquent, la possibilité de consommer, de créer et d’enregistrer des objets de base de données dépend largement des autorisations de base de données déjà définies pour vos utilisateurs.

<a name="permissions"></a>

## <a name="permissions"></a>Autorisations

Le modèle de sécurité des données de SQL Server pour les rôles et connexions de base de données s’étend aux scripts R et Python. Un compte de connexion SQL Server ou un compte d’utilisateur Windows est requis pour exécuter des scripts externes qui utilisent des données SQL Server ou qui s’exécutent avec SQL Server comme contexte de calcul. Les utilisateurs de base de données disposant des autorisations nécessaires pour exécuter une requête ad hoc peuvent accéder aux mêmes données à partir d’un script R ou Python.

Le compte de connexion ou d’utilisateur identifie le *principal de sécurité*, qui peut avoir besoin de plusieurs niveaux d’accès, selon les exigences de script externe :

+ Autorisation d’accéder à la base de données dans laquelle les scripts externes sont activés.
+ Autorisations de lire des données à partir d’objets sécurisés, tels que des tables.
+ Possibilité d’écrire de nouvelles données dans une table, comme un modèle, ou des résultats de scoring.
+ Possibilité de créer des objets, tels que des tables, des procédures stockées qui utilisent le script externe, ou des fonctions personnalisées qui utilisent le travail R ou Python.
+ Droit d’installer de nouveaux packages sur l’ordinateur SQL Server ou d’utiliser des packages fournis à un groupe d’utilisateurs.

Chaque personne qui exécute un script externe à l’aide de SQL Server en tant que contexte d’exécution doit être mappé à un utilisateur dans la base de données. Plutôt que de définir individuellement des autorisations utilisateur de base de données, vous pouvez créer des rôles pour gérer des jeux d’autorisations et affecter des utilisateurs à ces rôles.

Pour plus d’informations, consultez [Accorder des autorisations utilisateur pour SQL Server Machine Learning Services](../../advanced-analytics/security/user-permission.md).

## <a name="permissions-when-using-an-external-client-tool"></a>Autorisations lors de l’utilisation d’un outil client externe

Les utilisateurs qui utilisent R ou Python dans un outil client externe doivent disposer d’une connexion ou d’un compte mappé à un utilisateur de la base de données s’ils ont besoin d’exécuter un script externe dans la base de données ou d’accéder à des objets et des données de base de données. Les mêmes autorisations sont requises si le script externe est envoyé à partir d’un client de science des données distant ou s’il est exécuté à l’aide d’une procédure stockée T-SQL.

Par exemple, supposons que vous avez créé un script externe qui s’exécute sur votre ordinateur local et que vous souhaitez exécuter ce script sur SQL Server. Vous devez veiller à ce que les conditions suivantes soient réunies :

+ La base de données autorise les connexions à distance.
+ Le compte de connexion SQL ou le compte d’utilisateur Windows que vous avez utilisé pour l’accès à la base de données a été ajouté au niveau de l’instance de SQL Server.
+ Le compte de connexion SQL ou le compte d’utilisateur Windows doit être autorisé à exécuter des scripts externes. En règle générale, cette autorisation ne peut être ajoutée que par un administrateur de base de données.
+ Le compte de connexion SQL ou le compte d’utilisateur Windows doit être ajouté en tant qu’utilisateur, avec les autorisations appropriées, dans chaque base de données où le script externe effectue l’une de ces opérations :
  + Récupération de données.
  + Écriture ou mise à jour de données.
  + Création d’objets, tels que des tables ou des procédures stockées.

Une fois que le compte de connexion ou le compte d’utilisateur Windows a été configuré et qu’il a obtenu les autorisations nécessaires, vous pouvez exécuter un script externe sur SQL Server à l’aide d’un objet de source de données dans R ou la bibliothèque **revoscalepy** dans Python, ou en appelant une procédure stockée qui contient le script externe.

Chaque fois qu’un script externe est lancé à partir de SQL Server, la sécurité du moteur de base de données obtient le contexte de sécurité de l’utilisateur qui a démarré le travail et gère les mappages du compte d’utilisateur ou du compte de connexion à des objets sécurisables.

Par conséquent, tous les scripts externes qui sont lancés à partir d’un client distant doivent spécifier les informations de connexion ou de l’utilisateur dans la chaîne de connexion.

<a name="launchpad"></a>

## <a name="services-used-in-external-processing-launchpad"></a>Services utilisés dans le traitement externe (Launchpad)

L’infrastructure d’extensibilité ajoute un nouveau service NT à la [liste des services](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md#Service_Details) dans une installation SQL Server : [**SQL Server Launchpad (MSSSQLSERVER)** ](extensibility-framework.md#launchpad).

Le moteur de base de données utilise le service SQL Server Launchpad pour instancier une session R ou Python en tant que processus distinct. Le processus s’exécute sous un compte à faibles privilèges ; distinct de SQL Server Launchpad lui-même et de l’identité de l’utilisateur sous laquelle la procédure stockée ou la requête de l’hôte a été exécutée. L’exécution de scripts dans un processus distinct, sous un compte à faibles privilèges, est la base du modèle de sécurité et d’isolation pour R et Python dans SQL Server.

En plus de lancer des processus externes, Launchpad est également chargé de suivre l’identité de l’utilisateur appelant et de mapper cette identité au compte professionnel à faibles privilèges utilisé pour démarrer le processus. Dans certains scénarios, où le script ou le code rappelle SQL Server pour des données et des opérations, Launchpad est généralement en mesure de gérer le transfert d’identité en toute transparence. Le script contenant des instructions SELECT ou appelant des fonctions et d’autres objets de programme fonctionnera généralement si l’utilisateur à l’origine de l’appel dispose des autorisations nécessaires.

> [!NOTE]
> Par défaut, [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] est configuré pour s’exécuter sous**NT Service\MSSQLLaunchpad**, qui dispose de toutes les autorisations nécessaires pour exécuter des scripts externes. Pour plus d’informations sur les options configurables, consultez [Configuration du service SQL Server Launchpad](../security/sql-server-launchpad-service-account.md).

<a name="sqlrusergroup"></a>

## <a name="identities-used-in-processing-sqlrusergroup"></a>Identités utilisées pour le traitement (SQLRUserGroup)

**SQLRUserGroup** (groupe d’utilisateurs restreints SQL) est créé par le programme d’installation de SQL Server et contient un pool de comptes d’utilisateur Windows locaux à faibles privilèges. Lorsqu’un processus externe est nécessaire, Launchpad prend un compte professionnel disponible et l’utilise pour exécuter un processus. Plus précisément, Launchpad active un compte professionnel disponible, le mappe à l’identité de l’utilisateur à l’origine de l’appel et exécute le script sous le compte professionnel.

+ **SQLRUserGroup** est lié à une instance particulière. Un pool distinct de comptes professionnels est nécessaire pour chaque instance sur laquelle l’apprentissage automatique a été activé. Les comptes ne peuvent pas être partagés par plusieurs instances.

+ La taille du pool de comptes d’utilisateur est statique et sa valeur par défaut est 20 et prend en charge 20 sessions simultanées. Le nombre de sessions du runtime externe qui peuvent s’exécuter simultanément est limité par la taille du pool de ce compte d’utilisateur. 

+ Les noms de comptes professionnels dans le pool sont au format SQLInstanceName*nn*. Par exemple, sur une instance par défaut, **SQLRUserGroup** contient des comptes nommés MSSQLSERVER01, MSSQLSERVER02, et ainsi de suite, jusqu’à MSSQLSERVER20.

Les tâches en parallèle ne consomment pas de comptes supplémentaires. Par exemple, si un utilisateur exécute une tâche de scoring qui utilise le traitement parallèle, le même compte professionnel est réutilisé pour tous les threads. Si vous envisagez d’utiliser intensivement l’apprentissage automatique, vous pouvez augmenter le nombre de comptes utilisés pour exécuter des scripts externes. Pour plus d’informations, consultez [Mettre à l’échelle l’exécution simultanée de scripts externes dans SQL Server Machine Learning Services](../../advanced-analytics/administration/modify-user-account-pool.md).

::: moniker range=">=sql-server-ver15||=sqlallproducts-allversions"
### <a name="appcontainer-isolation-in-sql-server-2019"></a>Isolation AppContainer dans SQL Server 2019

Dans SQL Server 2019, le programme d’installation ne crée plus de comptes professionnels pour **SQLRUserGroup**. Au lieu de cela, l’isolation est obtenue via [AppContainers](https://docs.microsoft.com/windows/desktop/secauthz/appcontainer-isolation). Au moment de l’exécution, lorsqu’un script externe est détecté dans une procédure stockée ou une requête, SQL Server appelle Launchpad avec une demande de lanceur spécifique à l’extension. Launchpad appelle l’environnement de runtime approprié dans un processus sous son identité et instancie un élément AppContainer pour l’héberger. Cette modification est utile, car la gestion des comptes et des mots de passe locaux n’est plus nécessaire. En outre, sur les installations où les comptes d’utilisateurs locaux sont interdits, la suppression de la dépendance de compte d’utilisateur local signifie que vous pouvez désormais utiliser cette fonctionnalité.

Tels qu’implémentés par SQL Server, les éléments AppContainers constituent un mécanisme interne. Bien que vous ne puissiez pas voir physiquement les éléments AppContainers dans Process Monitor, vous pouvez les retrouver dans les règles de pare-feu sortantes créées par le programme d’installation pour empêcher les processus d’effectuer des appels réseau. Pour plus d’informations, consultez [Configurer le pare-feu pour SQL Server Machine Learning Services](../../advanced-analytics/security/firewall-configuration.md).

> [!Note]
> Dans SQL Server 2019, **SQLRUserGroup** ne possède qu’un seul membre qui est maintenant le seul compte de service SQL Server Launchpad (au lieu de plusieurs comptes de travail).
::: moniker-end

### <a name="permissions-granted-to-sqlrusergroup"></a>Autorisations accordées à SQLRUserGroup

Par défaut, les membres de **SQLRUserGroup** disposent d’autorisations de lecture et d’exécution sur des fichiers dans les répertoires **Binn**, **R_SERVICES**et **PYTHON_SERVICES** de SQL Server, avec un accès aux fichiers exécutables, aux bibliothèques et aux jeux de données intégrés des distributions R et Python installées avec SQL Server. 

Pour protéger les ressources sensibles sur SQL Server, vous pouvez éventuellement définir une liste de contrôle d’accès (ACL) qui refuse l’accès à **SQLRUserGroup**. À l’inverse, vous pouvez également accorder des autorisations aux ressources de données locales qui existent sur l’ordinateur hôte, en plus de SQL Server lui-même. 

Par défaut, **SQLRUserGroup** ne dispose pas d’une connexion à la base de données ou d’autorisations sur les données. Dans certaines circonstances, vous souhaiterez peut-être créer un compte de connexion pour autoriser les connexions de bouclage, en particulier lorsqu’une identité Windows approuvée est l’utilisateur à l’origine de l’appel. Cette capacité est ce que l’on appelle [*l’authentification implicite*](#implied-authentication). Pour plus d’informations, consultez [Créer un nom de connexion pour SQLRUserGroup](../../advanced-analytics/security/create-a-login-for-sqlrusergroup.md).

## <a name="identity-mapping"></a>Mappage d’identité

Lorsqu’une session est démarrée, Launchpad mappe l’identité de l’utilisateur à l’origine de l’appel à un compte professionnel. Le mappage d’un utilisateur Windows externe ou d’un compte de connexion SQL valide à un compte professionnel n’est valable que pendant la durée de vie de la procédure stockée SQL qui exécute le script externe. Les requêtes en parallèle du même compte de connexion sont mappées au même compte de travail utilisateur.

Au cours de l’exécution, Launchpad crée des dossiers temporaires pour stocker les données de session, en les supprimant lorsque la session se termine. L’accès aux répertoires est restreint. Pour R, RLauncher effectue cette tâche. Pour Python, PythonLauncher effectue cette tâche. Chaque compte professionnel est limité à son propre dossier et ne peut pas accéder aux fichiers des dossiers de niveau supérieur. Toutefois, le compte professionnel peut lire, écrire ou supprimer des enfants dans le dossier de travail de session qui a été créé. Si vous êtes administrateur de l’ordinateur, vous pouvez afficher les répertoires créés pour chaque processus. Chaque répertoire est identifié par son GUID de session.

<a name="implied-authentication"></a>

## <a name="implied-authentication-loop-back-requests"></a>Authentification implicite (demandes de bouclage)

*L’authentification implicite* décrit le comportement de la requête de connexion avec lequel les processus externes s’exécutant en tant que comptes professionnels à faibles privilèges sont présentés en tant qu’identité d’utilisateur approuvée à SQL Server pour les demandes de bouclage de données ou d’opérations. En tant que concept, l’authentification implicite est unique à l’authentification Windows, dans les chaînes de connexion SQL Server spécifiant une connexion approuvée, sur les demandes issues de processus externes comme un script R ou Python. Elle est parfois également appelée *bouclage*.

Les connexions approuvées sont utilisables à partir de scripts R et Python, mais uniquement avec une configuration supplémentaire. Dans l’architecture d’extensibilité, les processus R et Python s’exécutent sous des comptes professionnels, qui héritent des autorisations du parent **SQLRUserGroup**. Lorsqu’une chaîne de connexion spécifie `Trusted_Connection=True`, l’identité du compte professionnel est présentée à la requête de connexion, qui est, par défaut, inconnue de SQL Server.

Pour garantir la réussite des connexions approuvées, vous devez créer une connexion de base de données pour **SQLRUserGroup**. Après cela, toutes les connexions approuvées des membres de **SQLRUserGroup** disposent de droits de connexion à SQL Server. Pour obtenir des instructions pas à pas, consultez [Créer un nom de connexion pour SQLRUserGroup](../../advanced-analytics/security/create-a-login-for-sqlrusergroup.md).

Les connexions approuvées ne sont pas la formulation la plus couramment utilisée d’une requête de connexion. Lorsque le script R ou Python spécifie une connexion, il peut être plus courant d’utiliser une connexion SQL, ou un nom d’utilisateur et un mot de passe entièrement spécifiés si la connexion est destinée à une source de données ODBC.

### <a name="how-implied-authentication-works-for-r-and-python-sessions"></a>Fonctionnement de l’authentification implicite pour les sessions R et Python

Le schéma suivant illustre l’interaction entre les composants SQL Server et le runtime R, ainsi que le fonctionnement de l’authentification implicite pour R.

![Authentification implicite pour R](../security/media/implied-auth-rsql.png)

Le schéma suivant illustre l’interaction entre les composants SQL Server et le runtime Python, ainsi que le fonctionnement de l’authentification implicite pour Python.

![Authentification implicite pour Python](../security/media/implied-auth-python2.png)

## <a name="no-support-for-transparent-data-encryption-at-rest"></a>Aucune prise en charge de Transparent Data Encryption au repos

[Transparent Data Encryption (TDE)](../../relational-databases/security/encryption/transparent-data-encryption.md) n’est pas pris en charge pour les données reçues ou transmises par le runtime du script externe. Cela est dû au fait que le processus externe (R ou Python) s’exécute en dehors du processus SQL Server. Par conséquent, les données utilisées par le runtime externe ne sont pas protégées par les fonctionnalités de chiffrement du moteur de base de données. Ce comportement n’est pas différent de celui de tout autre client s’exécutant sur l’ordinateur SQL Server qui lit les données de la base de données et effectue une copie.

Par conséquent, TDE **ne s’applique** à aucune donnée utilisée dans les scripts R ou Python, ni à aucune donnée enregistrée sur le disque, ni à aucun résultat intermédiaire persistant. Toutefois, d’autres types de chiffrement, tels que le chiffrement BitLocker Windows ou le chiffrement tiers appliqué au niveau du fichier ou du dossier, s’appliquent toujours.

Dans le cas de [Always Encrypted](../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md), les runtimes externes n’ont pas accès aux clés de chiffrement. Par conséquent, les données ne peuvent pas être envoyées aux scripts.

## <a name="next-steps"></a>Étapes suivantes

Dans cet article, vous avez découvert les composants et le modèle d’interaction de l’architecture de sécurité intégrée à [l’infrastructure d’extensibilité](../../advanced-analytics/concepts/extensibility-framework.md). Les points clés abordés dans cet article incluent le rôle de Launchpad, de SQLRUserGroup et des comptes professionnels, l’isolation des processus R et Python et la façon dont les identités des utilisateurs sont mappées aux comptes professionnels. 

Lors de la prochaine étape, passez en revue les instructions pour [accorder des autorisations](../../advanced-analytics/security/user-permission.md). Pour les serveurs qui utilisent l’authentification Windows, vous devez également consulter [Créer un nom de connexion pour SQLRUserGroup](../../advanced-analytics/security/create-a-login-for-sqlrusergroup.md) pour savoir si une configuration supplémentaire est requise.