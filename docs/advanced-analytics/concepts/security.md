---
title: Vue d’ensemble de la sécurité pour les extensions R et Python - SQL Server Machine Learning
description: Vue d’ensemble de la sécurité pour l’infrastructure d’extensibilité dans SQL Server Machine Learning Services. Sécurité pour les comptes d’utilisateur et de connexion, le service SQL Server Launchpad, comptes de travail, exécution de plusieurs scripts et les autorisations de fichiers.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/17/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: f9f5552a106d0549aaf3b5e9ae291ebe3b534543
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67963033"
---
# <a name="security-overview-for-the-extensibility-framework-in-sql-server-machine-learning-services"></a>Vue d’ensemble de la sécurité pour l’infrastructure d’extensibilité dans SQL Server Machine Learning Services

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article décrit l’architecture de sécurité globale qui est utilisé pour intégrer le moteur de base de données SQL Server et les composants associés avec l’infrastructure d’extensibilité. Il examine les éléments sécurisables, services, l’identité du processus et les autorisations. Pour plus d’informations sur les concepts clés et les composants d’extensibilité dans SQL Server, consultez [architecture d’extensibilité dans SQL Server Machine Learning Services](extensibility-framework.md)].

## <a name="securables-for-external-script"></a>Éléments sécurisables de script externe

Un script externe écrit en R ou Python est soumis en tant que paramètre d’entrée d’un [procédure stockée système](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) créé à cet effet, ou est encapsulé dans une procédure stockée que vous définissez. Ou bien, vous pouvez avoir des modèles préformés et stockées dans un format binaire dans une table de base de données, pouvant être appelé dans T-SQL [PREDICT](../../t-sql/queries/predict-transact-sql.md) (fonction).

Comme le script est fourni par le biais des objets de schéma de base de données existants, les tables et procédures stockées, il n’existe aucune nouvelle [éléments sécurisables](../../relational-databases/security/securables.md) pour SQL Server Machine Learning Services.

Quel que soit votre utilisation de script, ou qu’ils se composent de, les objets de base de données seront créés et enregistrés probablement, mais aucun nouveau type d’objet n’est introduite pour stocker le script. Par conséquent, la capacité de consommer, créer et enregistrer la base de données objets dépend en grande partie des autorisations de base de données déjà définies pour vos utilisateurs.

<a name="permissions"></a>

## <a name="permissions"></a>Autorisations

Modèle de sécurité des données de SQL Server des connexions de base de données et des rôles étendre au script R et Python. Une connexion SQL Server ou compte d’utilisateur Windows est requis pour exécuter des scripts externes qui utilisent des données SQL Server ou qui s’exécutent avec SQL Server comme contexte de calcul. Base de données accessibles aux utilisateurs ayant des autorisations pour exécuter une requête ad hoc les mêmes données à partir du script R ou Python.

Le compte d’utilisateur ou de connexion identifie le *principal de sécurité*, qui peut ont besoin de plusieurs niveaux d’accès, selon les besoins de script externe :

+ Autorisation d’accéder à la base de données où les scripts externes sont activés.
+ Autorisations pour lire les données d’objets sécurisés tels que des tables.
+ La capacité d’écrire de nouvelles données à une table, comme un modèle ou de score des résultats.
+ La possibilité de créer de nouveaux objets, tels que des tables, des procédures stockées qui utilisent le script externe, ou les fonctions personnalisées qui utilisent R ou un travail Python.
+ Le droit d’installer de nouveaux packages sur l’ordinateur SQL Server, ou utiliser des packages fournis à un groupe d’utilisateurs.

Chaque personne qui exécute un script externe à l’aide de SQL Server en tant que le contexte d’exécution doit être mappé à un utilisateur dans la base de données. Au lieu d’individuellement de base de données des autorisations utilisateur, vous pouvez créer des rôles pour gérer des ensembles d’autorisations et affecter des utilisateurs à ces rôles, au lieu de définir individuellement les autorisations utilisateur.

Pour plus d’informations, consultez [autoriser les utilisateurs à SQL Server Machine Learning Services](../../advanced-analytics/security/user-permission.md).

## <a name="permissions-when-using-an-external-client-tool"></a>Autorisations lorsque vous utilisez un outil client externe

Utilisateurs qui sont à l’aide de R ou Python dans un outil client externes doivent avoir leur connexion ou le compte mappé à un utilisateur dans la base de données s’ils doivent exécuter un script externe en base de données, ou les objets de base de données access et les données. Les mêmes autorisations sont requises si le script externe est envoyé à partir d’un client de science des données distant ou exécutés à l’aide d’une procédure stockée T-SQL.

Par exemple, supposons que vous avez créé un script externe qui s’exécute sur votre ordinateur local, et que vous souhaitez exécuter ce script sur SQL Server. Vous devez veiller à ce que les conditions suivantes soient réunies :

+ La base de données autorise les connexions à distance.
+ La connexion SQL ou un compte Windows que vous avez utilisé pour l’accès de base de données a été ajoutée à SQL Server au niveau de l’instance.
+ Le compte de connexion SQL ou l’utilisateur de Windows doit avoir l’autorisation d’exécuter des scripts externes. En règle générale, cette autorisation ne peut être ajoutée que par un administrateur de base de données.
+ La connexion SQL ou l’utilisateur Windows doit être ajouté en tant qu’utilisateur, avec les autorisations appropriées, dans chaque base de données où le script externe effectue l’une de ces opérations :
  + Récupération de données.
  + Écriture ou la mise à jour des données.
  + Création d’objets, tels que des tables ou des procédures stockées.

Une fois la connexion ou un compte d’utilisateur Windows a été mis en service et les autorisations nécessaires, vous pouvez exécuter un script externe sur SQL Server à l’aide d’un objet de source de données dans R ou **revoscalepy** bibliothèque dans Python, ou en appelant un stockée procédure qui contient le script externe.

Chaque fois qu’un script externe est lancé à partir de SQL Server, la sécurité du moteur de base de données obtient le contexte de sécurité de l’utilisateur qui a démarré la tâche et gère les mappages de l’utilisateur ou d’une connexion à des objets sécurisables.

Par conséquent, tous les scripts externes qui sont lancées à partir d’un client distant doivent spécifier les informations de connexion ou un utilisateur dans le cadre de la chaîne de connexion.

<a name="launchpad"></a>

## <a name="services-used-in-external-processing-launchpad"></a>Services utilisés dans le traitement externe (Launchpad)

L’infrastructure d’extensibilité ajoute un nouveau service de NT à la [liste des services](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md#Service_Details) dans une installation de SQL Server : [**SQL Server Launchpad (MSSSQLSERVER)** ](extensibility-framework.md#launchpad).

Le moteur de base de données utilise le service SQL Server Launchpad pour instancier une session R ou Python comme un processus séparé. Le processus s’exécute sous un compte à faibles privilèges ; distinctes de SQL Server, Launchpad lui-même et l’identité d’utilisateur sous lequel la requête d’hôte ou de la procédure stockée a été exécutée. Script en cours d’exécution dans un processus distinct, sous compte à faibles privilèges, est la base du modèle de sécurité et d’isolation de R et Python dans SQL Server.

Outre lançant des processus externes, Launchpad est également chargé de suivre l’identité de l’utilisateur appelant et cette identité de mappage pour le compte de travail de faibles privilèges utilisé pour démarrer le processus. Dans certains scénarios où code ou script rappelle à SQL Server pour les opérations et les données, Launchpad est souvent capable de gérer le transfert d’identité en toute transparence. Script contenant des instructions SELECT ou l’appel de fonctions et autres objets de programmation réussit généralement si l’utilisateur appelant dispose des autorisations suffisantes.

> [!NOTE]
> Par défaut, [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] est configuré pour s’exécuter sous **NT Service\MSSQLLaunchpad**, qui est doté de toutes les autorisations nécessaires pour exécuter des scripts externes. Pour plus d’informations sur les options configurables, consultez [configuration du service SQL Server Launchpad](../security/sql-server-launchpad-service-account.md).

<a name="sqlrusergroup"></a>

## <a name="identities-used-in-processing-sqlrusergroup"></a>Identités utilisées lors du traitement (SQLRUserGroup)

**SQLRUserGroup** (groupes d’utilisateurs restreints SQL) est créé par le programme d’installation de SQL Server et contient un pool de comptes utilisateur Windows locales à faibles privilèges. Lorsqu’un processus externe est nécessaire, Launchpad prend un compte de travail disponibles et l’utilise pour exécuter un processus. Plus précisément, Launchpad Active un compte de travail disponibles est mappé à l’identité de l’utilisateur appelant et exécute le script sous le compte de travail.

+ **SQLRUserGroup** est lié à une instance spécifique. Un pool distinct de comptes de travail est nécessaire pour chaque instance sur lequel machine learning a été activée. Les comptes ne peuvent pas être partagés par plusieurs instances.

+ La taille du pool de comptes d’utilisateur est statique et la valeur par défaut est de 20, qui prend en charge 20 sessions simultanées. Le nombre de sessions de runtime externes qui peuvent s’exécuter simultanément est limité par la taille de ce pool de comptes d’utilisateur. 

+ Noms de compte de travail dans le pool sont au format SQLInstanceName*nn*. Par exemple, sur une instance par défaut, **SQLRUserGroup** contient des comptes nommés MSSQLSERVER01, MSSQLSERVER02 et ainsi de suite sur jusqu'à MSSQLSERVER20.

Tâches en parallèle ne consomment pas de comptes supplémentaires. Par exemple, si un utilisateur exécute une tâche de calcul de score qui utilise le traitement parallèle, le même compte de travail est réutilisé pour tous les threads. Si vous avez l’intention de faire un usage intensif de l’apprentissage, vous pouvez augmenter le nombre de comptes utilisés pour exécuter des scripts externes. Pour plus d’informations, consultez [modifier le pool de comptes d’utilisateur pour l’apprentissage](../../advanced-analytics/administration/modify-user-account-pool.md).

::: moniker range=">=sql-server-ver15||=sqlallproducts-allversions"
### <a name="appcontainer-isolation-in-sql-server-2019"></a>Isolement de AppContainer dans SQL Server 2019

Dans SQL Server 2019, le programme d’installation ne crée plus de comptes de travail pour **SQLRUserGroup**. Au lieu de cela, l’isolation est obtenue via [AppContainers](https://docs.microsoft.com/windows/desktop/secauthz/appcontainer-isolation). Au moment de l’exécution, quand un script externe est détecté dans une procédure stockée ou une requête, SQL Server appelle Launchpad avec une demande pour un lanceur spécifiques à l’extension. LaunchPad appelle l’environnement d’exécution appropriée dans un processus sous son identité et instancie un AppContainer pour le contenir. Cette modification est utile, car la gestion de compte et mot de passe local n’est plus nécessaire. En outre, sur les installations où les comptes d’utilisateurs locaux sont interdites, élimination de la dépendance de compte d’utilisateur local signifie que vous pouvez maintenant utiliser cette fonctionnalité.

Implémenté par SQL Server, AppContainers sont un mécanisme interne. Pendant que vous les verrez des preuves physiques de AppContainers dans le moniteur de processus, vous pouvez les trouver dans les règles de pare-feu sortantes créées par le programme d’installation pour empêcher les processus d’effectuer des appels réseau. Pour plus d’informations, consultez [configuration du pare-feu pour SQL Server Machine Learning Services](../../advanced-analytics/security/firewall-configuration.md).

> [!Note]
> Dans SQL Server 2019, **SQLRUserGroup** a uniquement un membre qui est maintenant le compte de service SQL Server Launchpad unique au lieu de plusieurs comptes de travail.
::: moniker-end

### <a name="permissions-granted-to-sqlrusergroup"></a>Autorisations accordées à SQLRUserGroup

Par défaut, les membres de **SQLRUserGroup** ont autorisations read et execute sur les fichiers dans SQL Server **Binn**, **R_SERVICES**, et **PYTHON_SERVICES** annuaires, avec accès aux fichiers exécutables, des bibliothèques et des jeux de données intégrées dans les distributions de R et Python installées avec SQL Server. 

Pour protéger les ressources sensibles sur SQL Server, vous pouvez éventuellement définir une liste de contrôle d’accès (ACL) qui refuse l’accès à **SQLRUserGroup**. À l’inverse, vous pouvez également accorder des autorisations relatives aux ressources de données locales qui existent sur l’ordinateur hôte, en dehors de SQL Server lui-même. 

Par conception, **SQLRUserGroup** n’a pas d’une connexion de base de données ou des autorisations pour toutes les données. Dans certaines circonstances, vous souhaiterez créer une connexion pour autoriser les connexions de retour de boucle, en particulier lorsqu’une identité Windows approuvé est l’utilisateur appelant. Cette fonctionnalité s’appelle [ *l’authentification implicite*](#implied-authentication). Pour plus d’informations, consultez [SQLRUserGroup d’ajouter en tant qu’un utilisateur de base de données](../../advanced-analytics/security/create-a-login-for-sqlrusergroup.md).

## <a name="identity-mapping"></a>Mappage d’identité

Lorsqu’une session est démarrée, Launchpad mappe l’identité de l’utilisateur appelant à un compte de travail. Le mappage d’un utilisateur Windows externe ou d’une connexion SQL valide à un compte de travail est valide uniquement pour la durée de vie de l’instruction SQL de procédure stockée qui exécute le script externe. Les requêtes en parallèle du même compte de connexion sont mappées au même compte de travail utilisateur.

Pendant l’exécution, Launchpad crée des dossiers temporaires pour stocker les données de session, en supprimant lorsque la session se termine. Les répertoires ont un accès limité. Pour R, RLauncher effectue cette tâche. Pour Python, PythonLauncher exécute cette tâche. Chaque compte de travail individuels est limité à son propre dossier et ne peut pas accéder aux fichiers dans les dossiers situés au-dessus du niveau de son propre. Toutefois, le compte de travail peut lire, écrire ou supprimer des enfants sous le dossier de travail de session qui a été créé. Si vous êtes administrateur de l’ordinateur, vous pouvez afficher les répertoires créés pour chaque processus. Chaque répertoire est identifié par son GUID de session.

<a name="implied-authentication"></a>

## <a name="implied-authentication-loop-back-requests"></a>Authentification implicite (demandes de retour de boucle)

*L’authentification implicite* décrit le comportement de demande de connexion sous lequel les processus externes en cours d’exécution comme comptes de travail de faibles privilèges sont présentés comme une identité utilisateur approuvée à SQL Server sur une boucle des demandes de publication de données ou d’opérations. Comme un concept, l’authentification implicite est propre à l’authentification Windows, dans les chaînes de connexion SQL Server en spécifiant une connexion approuvée, sur les demandes provenant d’un processus externe comme script R ou Python. Il est parfois également appelé un *demi-tour*.

Connexions approuvées sont envisageables à partir d’un script R et Python, mais uniquement avec une configuration supplémentaire. Dans l’architecture d’extensibilité, les processus de R et Python s’exécutent sous des comptes de travail, héritant des autorisations du parent **SQLRUserGroup**. Lorsqu’une chaîne de connexion spécifie `Trusted_Connection=True`, l’identité du compte de travail est présentée sur la demande de connexion est inconnue par défaut pour SQL Server.

Pour établir des connexions fiables réussie, vous devez créer une connexion de base de données pour le **SQLRUserGroup**. Après cela, une connexion à partir de n’importe quel membre est approuvée **SQLRUserGroup** a des droits de connexion à SQL Server. Pour obtenir des instructions détaillées, consultez [ajouter SQLRUserGroup à une connexion de base de données](../../advanced-analytics/security/create-a-login-for-sqlrusergroup.md).

Connexions approuvées ne sont pas la formulation plus largement utilisée d’une demande de connexion. Lorsque le script R ou Python spécifie une connexion, il peut être plus courant d’utiliser une connexion SQL, ou un nom d’utilisateur spécifié et le mot de passe si la connexion à une source de données ODBC.

### <a name="how-implied-authentication-works-for-r-and-python-sessions"></a>Fonctionnement de l’authentification comment implicite pour les sessions R et Python

Le diagramme suivant illustre l’interaction des composants SQL Server avec le runtime R et comment il le fait l’authentification implicite pour R.

![Authentification implicite pour R](../security/media/implied-auth-rsql.png)

Le diagramme suivant illustre l’interaction des composants SQL Server avec le runtime Python et le fonctionnement de l’authentification implicite pour Python.

![Authentification implicite pour Python](../security/media/implied-auth-python2.png)

## <a name="no-support-for-transparent-data-encryption-at-rest"></a>Aucune prise en charge pour le chiffrement Transparent des données au repos

[Transparent Data Encryption (TDE)](../../relational-databases/security/encryption/transparent-data-encryption.md) n’est pas pris en charge pour les données envoyées ou reçues à partir de l’exécution du script externe. La raison est que le processus externe (R ou Python) s’exécute en dehors du processus SQL Server. Par conséquent, les données utilisées par le runtime externe ne sont pas protégées par les fonctionnalités de chiffrement du moteur de base de données. Ce comportement n’est pas différent de celui de tout autre client en cours d’exécution sur l’ordinateur SQL Server qui lit des données à partir de la base de données et effectue une copie.

Par conséquent, le chiffrement transparent des données **n’est pas** appliqués à toutes les données que vous utilisez dans des scripts R ou Python, ou à toutes les données enregistrées sur disque, ou aucun résultat intermédiaire persistant. Toutefois, autres types de chiffrement, tels que le chiffrement de BitLocker de Windows ou par des tiers appliquée au niveau du fichier ou dossier, toujours s’appliquent.

Dans le cas de [Always Encrypted](../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md), les runtimes externes n’ont pas accès aux clés de chiffrement. Par conséquent, les données ne peut pas être envoyées aux scripts.

## <a name="next-steps"></a>Étapes suivantes

Dans cet article, vous avez appris les composants et le modèle d’interaction de l’architecture de sécurité intégrée à la [infrastructure d’extensibilité](../../advanced-analytics/concepts/extensibility-framework.md). Points clés abordés dans cet article incluent l’objectif de comptes Launchpad et de travail, SQLRUserGroup, isolation des processus de R et Python, et comment les identités des utilisateurs sont mappées aux comptes de travail. 

Comme prochaine étape, passez en revue les instructions pour [l’octroi d’autorisations](../../advanced-analytics/security/user-permission.md). Pour les serveurs qui utilisent l’authentification Windows, vous devez également examiner [ajouter SQLRUserGroup à une connexion de base de données](../../advanced-analytics/security/create-a-login-for-sqlrusergroup.md) pour savoir quand une configuration supplémentaire est requise.