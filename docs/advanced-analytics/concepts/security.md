---
title: Vue d’ensemble de la sécurité pour les extensions R et Python
description: Vue d’ensemble de la sécurité de l’infrastructure d’extensibilité dans SQL Server Machine Learning Services. Sécurité pour les comptes de connexion et d’utilisateur, SQL Server Launchpad service, les comptes de travail, l’exécution de plusieurs scripts et les autorisations de fichiers.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/17/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 39a9d05761b60878f1d7856378ba4cb28e54e2f9
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68470481"
---
# <a name="security-overview-for-the-extensibility-framework-in-sql-server-machine-learning-services"></a>Vue d’ensemble de la sécurité de l’infrastructure d’extensibilité dans SQL Server Machine Learning Services

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cet article décrit l’architecture de sécurité globale utilisée pour intégrer le moteur de base de données SQL Server et les composants associés à l’infrastructure d’extensibilité. Il examine les éléments sécurisables, les services, l’identité du processus et les autorisations. Pour plus d’informations sur les principaux concepts et composants de l’extensibilité dans SQL Server, consultez [architecture d’extensibilité dans SQL Server machine learning services](extensibility-framework.md)].

## <a name="securables-for-external-script"></a>Éléments sécurisables pour script externe

Un script externe écrit en R ou python est soumis en tant que paramètre d’entrée à une [procédure stockée système](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) créée à cet effet, ou est encapsulé dans une procédure stockée que vous définissez. Vous pouvez également avoir des modèles préformés et stockés dans un format binaire dans une table de base de données, pouvant être appelé dans une fonction de [prédiction](../../t-sql/queries/predict-transact-sql.md) T-SQL.

Étant donné que le script est fourni par le biais d’objets de schéma de base de données existants,  de procédures stockées et de tables, il n’existe pas de nouveaux éléments [sécurisables](../../relational-databases/security/securables.md) pour SQL Server machine learning services.

Quelle que soit la façon dont vous utilisez le script ou, ce qu’ils consistent, les objets de base de données sont créés et probablement enregistrés, mais aucun nouveau type d’objet n’est introduit pour le stockage du script. Par conséquent, la possibilité de consommer, de créer et d’enregistrer des objets de base de données dépend largement des autorisations de base de données déjà définies pour vos utilisateurs.

<a name="permissions"></a>

## <a name="permissions"></a>Autorisations

Le modèle de sécurité des données de SQL Server des connexions et des rôles de base de données s’étend aux scripts R et Python. Une connexion SQL Server ou un compte d’utilisateur Windows est requis pour exécuter des scripts externes qui utilisent des données SQL Server ou qui s’exécutent avec SQL Server comme contexte de calcul. Les utilisateurs de base de données disposant des autorisations nécessaires pour exécuter une requête ad hoc peuvent accéder aux mêmes données à partir d’un script R ou python.

La connexion ou le compte d’utilisateur identifie le *principal de sécurité*, qui peut nécessiter plusieurs niveaux d’accès, en fonction des exigences du script externe:

+ Autorisation d’accéder à la base de données dans laquelle les scripts externes sont activés.
+ Autorisations de lire des données à partir d’objets sécurisés, tels que des tables.
+ La possibilité d’écrire de nouvelles données dans une table, comme un modèle, ou des résultats de notation.
+ La possibilité de créer des objets, tels que des tables, des procédures stockées qui utilisent le script externe, ou des fonctions personnalisées qui utilisent le travail R ou python.
+ Droit d’installer de nouveaux packages sur l’ordinateur SQL Server ou d’utiliser des packages fournis à un groupe d’utilisateurs.

Chaque personne qui exécute un script externe à l’aide d’SQL Server en tant que contexte d’exécution doit être mappée à un utilisateur dans la base de données. Plutôt que de définir individuellement des autorisations utilisateur de base de données, vous pouvez créer des rôles pour gérer des jeux d’autorisations et affecter des utilisateurs à ces rôles, plutôt que de définir individuellement des autorisations utilisateur.

Pour plus d’informations, consultez [accorder aux utilisateurs l’autorisation d’SQL Server machine learning services](../../advanced-analytics/security/user-permission.md).

## <a name="permissions-when-using-an-external-client-tool"></a>Autorisations lors de l’utilisation d’un outil client externe

Les utilisateurs qui utilisent R ou python dans un outil client externe doivent disposer d’une connexion ou d’un compte mappé à un utilisateur de la base de données s’ils ont besoin d’exécuter un script externe dans la base de données ou d’accéder à des objets et des données de base de données. Les mêmes autorisations sont requises si le script externe est envoyé à partir d’un client de science des données distant ou s’il est exécuté à l’aide d’une procédure stockée T-SQL.

Par exemple, supposons que vous avez créé un script externe qui s’exécute sur votre ordinateur local et que vous souhaitez exécuter ce script sur SQL Server. Vous devez veiller à ce que les conditions suivantes soient réunies :

+ La base de données autorise les connexions à distance.
+ La connexion SQL ou le compte Windows que vous avez utilisé pour l’accès à la base de données a été ajouté au SQL Server au niveau de l’instance.
+ La connexion SQL ou l’utilisateur Windows doit avoir l’autorisation d’exécuter des scripts externes. En règle générale, cette autorisation ne peut être ajoutée que par un administrateur de base de données.
+ La connexion SQL ou l’utilisateur Windows doit être ajouté en tant qu’utilisateur, avec les autorisations appropriées, dans chaque base de données où le script externe effectue l’une des opérations suivantes:
  + Récupération des données.
  + Écriture ou mise à jour des données.
  + Création d’objets, tels que des tables ou des procédures stockées.

Une fois que la connexion ou le compte d’utilisateur Windows a été configuré et que vous avez donné les autorisations nécessaires, vous pouvez exécuter un script externe sur SQL Server à l’aide d’un objet de source de données dans R ou de la bibliothèque **revoscalepy** dans Python, ou en appelant une procédure stockée qui contient le script externe.

Chaque fois qu’un script externe est lancé à partir de SQL Server, la sécurité du moteur de base de données obtient le contexte de sécurité de l’utilisateur qui a démarré le travail et gère les mappages de l’utilisateur ou de la connexion aux objets sécurisables.

Par conséquent, tous les scripts externes initiés à partir d’un client distant doivent spécifier la connexion ou les informations utilisateur dans le cadre de la chaîne de connexion.

<a name="launchpad"></a>

## <a name="services-used-in-external-processing-launchpad"></a>Services utilisés dans le traitement externe (Launchpad)

L’infrastructure d’extensibilité ajoute un nouveau service NT à la [liste des services](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md#Service_Details) dans une installation SQL Server: [**SQL Server Launchpad (MSSSQLSERVER)** ](extensibility-framework.md#launchpad).

Le moteur de base de données utilise le service SQL Server Launchpad pour instancier une session R ou python en tant que processus distinct. Le processus s’exécute sous un compte à faibles privilèges; distinct de SQL Server, Launchpad lui-même et l’identité de l’utilisateur sous laquelle la requête de la procédure stockée ou de l’hôte a été exécutée. L’exécution de script dans un processus distinct, sous un compte à faibles privilèges, est la base du modèle de sécurité et d’isolation pour R et Python dans SQL Server.

En plus de lancer des processus externes, Launchpad est également chargé de suivre l’identité de l’utilisateur appelant et de mapper cette identité au compte de travail à faibles privilèges utilisé pour démarrer le processus. Dans certains scénarios, où le script ou le code rappelle à SQL Server pour les données et les opérations, Launchpad est généralement en mesure de gérer le transfert d’identité en toute transparence. Le script contenant des instructions SELECT ou des fonctions appelées et d’autres objets de programmation fonctionne généralement si l’utilisateur appelant dispose des autorisations suffisantes.

> [!NOTE]
> Par défaut, [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] est configuré pour s’exécuter sous **NT Service\MSSQLLaunchpad**, qui est approvisionné avec toutes les autorisations nécessaires pour exécuter des scripts externes. Pour plus d’informations sur les options configurables, consultez [SQL Server Launchpad configuration du service](../security/sql-server-launchpad-service-account.md).

<a name="sqlrusergroup"></a>

## <a name="identities-used-in-processing-sqlrusergroup"></a>Identités utilisées en traitement (SQLRUserGroup)

**SQLRUserGroup** (Groupe d’utilisateurs SQL restreint) est créé par le programme d’installation de SQL Server et contient un pool de comptes d’utilisateur Windows locaux à faibles privilèges. Lorsqu’un processus externe est nécessaire, Launchpad prend un compte de travail disponible et l’utilise pour exécuter un processus. Plus précisément, Launchpad active un compte de travail disponible, le mappe à l’identité de l’utilisateur appelant et exécute le script sous le compte de travail.

+ **SQLRUserGroup** est lié à une instance spécifique. Un pool distinct de comptes de travail est nécessaire pour chaque instance sur laquelle Machine Learning a été activé. Les comptes ne peuvent pas être partagés par plusieurs instances.

+ La taille du pool de comptes d’utilisateur est statique et la valeur par défaut est 20, qui prend en charge 20 sessions simultanées. Le nombre de sessions d’exécution externes qui peuvent être lancées simultanément est limité par la taille de ce pool de comptes d’utilisateur. 

+ Les noms de compte de travail dans le pool sont au format SQLInstanceName*nn*. Par exemple, sur une instance par défaut, **SQLRUserGroup** contient des comptes nommés MSSQLSERVER01, MSSQLSERVER02, etc., jusqu’à MSSQLSERVER20.

Les tâches en parallèle ne consomment pas de comptes supplémentaires. Par exemple, si un utilisateur exécute une tâche de notation qui utilise le traitement parallèle, le même compte de travail est réutilisé pour tous les threads. Si vous envisagez d’utiliser intensivement des Machine Learning, vous pouvez augmenter le nombre de comptes utilisés pour exécuter des scripts externes. Pour plus d’informations, consultez [modifier le pool de comptes d’utilisateurs pour machine learning](../../advanced-analytics/administration/modify-user-account-pool.md).

::: moniker range=">=sql-server-ver15||=sqlallproducts-allversions"
### <a name="appcontainer-isolation-in-sql-server-2019"></a>Isolation d’AppContainer dans SQL Server 2019

Dans SQL Server 2019, le programme d’installation ne crée plus de comptes de travail pour **SQLRUserGroup**. Au lieu de cela, l’isolation est obtenue via [AppContainers](https://docs.microsoft.com/windows/desktop/secauthz/appcontainer-isolation). Au moment de l’exécution, lorsqu’un script externe est détecté dans une procédure stockée ou une requête, SQL Server appelle Launchpad avec une demande de lanceur spécifique à l’extension. Launchpad appelle l’environnement d’exécution approprié dans un processus sous son identité et instancie un AppContainer pour le contenir. Cette modification est avantageuse, car la gestion des comptes et des mots de passe locaux n’est plus nécessaire. En outre, sur les installations où les comptes d’utilisateurs locaux sont interdits, l’élimination de la dépendance de compte d’utilisateur local signifie que vous pouvez désormais utiliser cette fonctionnalité.

Comme implémenté par SQL Server, AppContainers est un mécanisme interne. Bien que vous ne puissiez pas voir les preuves physiques de AppContainers dans Process Monitor, vous pouvez les trouver dans les règles de pare-feu sortantes créées par le programme d’installation pour empêcher les processus d’effectuer des appels réseau. Pour plus d’informations, consultez [configuration du pare-feu pour SQL Server machine learning services](../../advanced-analytics/security/firewall-configuration.md).

> [!Note]
> Dans SQL Server 2019, **SQLRUserGroup** ne possède qu’un seul membre qui est maintenant le seul compte de service SQL Server Launchpad au lieu de plusieurs comptes Worker.
::: moniker-end

### <a name="permissions-granted-to-sqlrusergroup"></a>Autorisations accordées à SQLRUserGroup

Par défaut, les membres de **SQLRUserGroup** disposent d’autorisations de lecture et d’exécution sur SQL Server les fichiers des répertoires **Binn**, **R_SERVICES**et **PYTHON_SERVICES** , avec accès aux fichiers exécutables, aux bibliothèques et aux jeux de données intégrés dans R et les distributions python installés avec SQL Server. 

Pour protéger les ressources sensibles sur SQL Server, vous pouvez éventuellement définir une liste de contrôle d’accès (ACL) qui refuse l’accès à **SQLRUserGroup**. À l’inverse, vous pouvez également accorder des autorisations aux ressources de données locales qui existent sur l’ordinateur hôte, en plus de SQL Server lui-même. 

Par défaut, **SQLRUserGroup** n’a pas de connexion à la base de données ni d’autorisations sur les données. Dans certaines circonstances, vous souhaiterez peut-être créer une connexion pour autoriser les connexions de boucle, en particulier lorsqu’une identité Windows approuvée est l’utilisateur appelant. Cette fonctionnalité est appelée [*authentification implicite*](#implied-authentication). Pour plus d’informations, consultez [Ajouter SQLRUserGroup en tant qu’utilisateur de base de données](../../advanced-analytics/security/create-a-login-for-sqlrusergroup.md).

## <a name="identity-mapping"></a>Mappage d’identité

Lorsqu’une session est démarrée, Launchpad mappe l’identité de l’utilisateur appelant à un compte de travail. Le mappage d’un utilisateur Windows externe ou d’une connexion SQL valide à un compte de travail est valide uniquement pendant la durée de vie de la procédure stockée SQL qui exécute le script externe. Les requêtes en parallèle du même compte de connexion sont mappées au même compte de travail utilisateur.

Au cours de l’exécution, Launchpad crée des dossiers temporaires pour stocker les données de session, en les supprimant lorsque la session se termine. Les répertoires sont restreints à l’accès. Pour R, RLauncher effectue cette tâche. Pour Python, PythonLauncher effectue cette tâche. Chaque compte de travail individuel est limité à son propre dossier et ne peut pas accéder aux fichiers dans les dossiers situés au-dessus de son propre niveau. Toutefois, le compte de travail peut lire, écrire ou supprimer des enfants dans le dossier de travail de session qui a été créé. Si vous êtes administrateur de l’ordinateur, vous pouvez afficher les répertoires créés pour chaque processus. Chaque répertoire est identifié par son GUID de session.

<a name="implied-authentication"></a>

## <a name="implied-authentication-loop-back-requests"></a>Authentification implicite (demandes de bouclage)

*L’authentification implicite* décrit le comportement de la demande de connexion sous lequel les processus externes s’exécutant en tant que comptes de travail à faibles privilèges sont présentés en tant qu’identité d’utilisateur approuvé pour SQL Server sur les demandes de données ou d’opérations en boucle. En guise de concept, l’authentification implicite est propre à l’authentification Windows, dans SQL Server chaînes de connexion spécifiant une connexion approuvée, sur les demandes provenant de processus externes comme R ou python script. Il est parfois également désigné sous le terme de *boucle*.

Les connexions approuvées sont réalisables à partir de scripts R et Python, mais uniquement avec une configuration supplémentaire. Dans l’architecture d’extensibilité, les processus R et Python s’exécutent sous des comptes de travail, en héritant des autorisations du **SQLRUserGroup**parent. Lorsqu’une chaîne de connexion `Trusted_Connection=True`spécifie, l’identité du compte de travail est présentée sur la demande de connexion, qui est inconnue par défaut pour SQL Server.

Pour garantir la réussite des connexions approuvées, vous devez créer une connexion de base de données pour le **SQLRUserGroup**. Après cela, toute connexion approuvée à partir de n’importe quel membre de **SQLRUserGroup** dispose de droits de connexion pour SQL Server. Pour obtenir des instructions pas à pas, consultez [Ajouter SQLRUserGroup à une connexion de base de données](../../advanced-analytics/security/create-a-login-for-sqlrusergroup.md).

Les connexions approuvées ne sont pas la formulation la plus couramment utilisée d’une demande de connexion. Lorsque le script R ou python spécifie une connexion, il peut être plus courant d’utiliser une connexion SQL, ou un nom d’utilisateur et un mot de passe entièrement spécifiés si la connexion est à une source de données ODBC.

### <a name="how-implied-authentication-works-for-r-and-python-sessions"></a>Fonctionnement de l’authentification implicite pour les sessions R et Python

Le diagramme suivant illustre l’interaction entre les composants SQL Server et le runtime R, ainsi que l’authentification implicite pour R.

![Authentification implicite pour R](../security/media/implied-auth-rsql.png)

Le diagramme suivant montre l’interaction des composants SQL Server avec le runtime Python et comment il effectue l’authentification implicite pour Python.

![Authentification implicite pour Python](../security/media/implied-auth-python2.png)

## <a name="no-support-for-transparent-data-encryption-at-rest"></a>Aucune prise en charge de Transparent Data Encryption au repos

[Transparent Data Encryption (TDE)](../../relational-databases/security/encryption/transparent-data-encryption.md) n’est pas pris en charge pour les données envoyées ou reçues à partir du runtime de script externe. Cela est dû au fait que le processus externe (R ou python) s’exécute en dehors du processus de SQL Server. Par conséquent, les données utilisées par le runtime externe ne sont pas protégées par les fonctionnalités de chiffrement du moteur de base de données. Ce comportement n’est pas différent de celui de tout autre client s’exécutant sur l’ordinateur SQL Server qui lit les données de la base de données et effectue une copie.

Par conséquent, TDE **n’est pas** appliqué aux données que vous utilisez dans les scripts R ou python, ou à toutes les données enregistrées sur le disque, ou à tout résultat intermédiaire persistant. Toutefois, d’autres types de chiffrement, tels que le chiffrement BitLocker Windows ou le chiffrement tiers appliqué au niveau du fichier ou du dossier, s’appliquent toujours.

Dans le cas de [Always Encrypted](../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md), les runtimes externes n’ont pas accès aux clés de chiffrement. Par conséquent, les données ne peuvent pas être envoyées aux scripts.

## <a name="next-steps"></a>Étapes suivantes

Dans cet article, vous avez appris les composants et le modèle d’interaction de l’architecture de sécurité intégrée à l' [infrastructure d’extensibilité](../../advanced-analytics/concepts/extensibility-framework.md). Les points clés abordés dans cet article incluent l’objectif des comptes Launchpad, SQLRUserGroup et Worker, l’isolation des processus R et Python et la façon dont les identités des utilisateurs sont mappées aux comptes Worker. 

À l’étape suivante, passez en revue les instructions pour [accorder des autorisations](../../advanced-analytics/security/user-permission.md). Pour les serveurs qui utilisent l’authentification Windows, vous devez également passer [en revue ajouter SQLRUserGroup à une connexion de base de données](../../advanced-analytics/security/create-a-login-for-sqlrusergroup.md) pour savoir quand une configuration supplémentaire est requise.