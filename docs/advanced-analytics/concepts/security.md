---
title: Sécurité pour l’apprentissage de SQL Server | Microsoft Docs
description: Vue d’ensemble de la sécurité pour l’infrastructure d’extensibilité dans SQL Server Machine Learning Services. Sécurité pour les comptes d’utilisateur et de connexion, le service SQL Server Launchpad, comptes de travail, exécution de plusieurs scripts et les autorisations de fichiers.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/10/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: bee8e2162c56ac1b26273873943d848c2167dbda
ms.sourcegitcommit: 485e4e05d88813d2a8bb8e7296dbd721d125f940
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/11/2018
ms.locfileid: "49100400"
---
# <a name="security-overview-for-the-extensibility-framework-in-sql-server-machine-learning-services"></a>Vue d’ensemble de la sécurité pour l’infrastructure d’extensibilité dans SQL Server Machine Learning Services

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article décrit l’architecture de sécurité globale qui permet de connecter le moteur de base de données SQL Server et les composants associés à l’infrastructure d’extensibilité. Il décrit les interactions et les composants. 

<a name="launchpad"></a>

## <a name="sql-server-launchpad-service"></a>Service SQL Server Launchpad

Pour instancier des processus externes, le moteur de base de données fournit le service Launchpad de SQL Server pour créer une session R ou Python. Distinct [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] service est créé pour l’instance du moteur de base de données à laquelle vous avez ajouté SQL Server machine learning (R ou Python) service d’intégration, un par instance.

Par défaut, [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] est configuré pour s’exécuter sous **NT Service\MSSQLLaunchpad**, qui est doté de toutes les autorisations nécessaires pour exécuter des scripts externes. Suppression des autorisations de ce compte peut entraîner [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] le basculement pour démarrer ou pour accéder à l’instance de SQL Server exécutant des scripts externes. Le service LaunchPad est généralement utilisé en tant que-est, mais pour plus d’informations sur les options configurables, consultez [configuration du service SQL Server Launchpad](../security/sql-server-launchpad-service-account.md).

<a name="sqlrusergroup"></a>

## <a name="sqlrusergroup-and-worker-accounts"></a>Comptes SQLRUserGroup et de travail

Les scripts externes exécutés dans des processus externes, sous l’identité de comptes de travail local de moindre privilège, soumis à la liste de contrôle d’accès (ACL) du parent **SQLRUserGroup** (groupes d’utilisateurs restreints SQL). 

**SQLRUserGroup** est créé par le programme d’installation de SQL Server et contient le pool de comptes d’utilisateur Windows locales. Lorsqu’un processus externe est nécessaire, Launchpad prend un compte de travail disponibles et l’utilise pour exécuter un processus. Plus précisément, Launchpad Active un compte de travail disponibles est mappé à l’identité de l’utilisateur appelant et exécute le script sous le compte de travail. 

+ **SQLRUserGroup** est lié à une instance spécifique. Un pool distinct de comptes de travail est nécessaire pour chaque instance sur lequel machine learning a été activée. Les comptes ne peuvent pas être partagés par plusieurs instances.

+ La taille du pool de comptes d’utilisateur est statique et la valeur par défaut est de 20, qui prend en charge 20 sessions simultanées. Le nombre de sessions de runtime externes qui peuvent s’exécuter simultanément est limité par la taille de ce pool de comptes d’utilisateur. 

+ Noms de compte de travail dans le pool sont au format SQLInstanceName*nn*. Par exemple, sur une instance par défaut, **SQLRUserGroup** contient des comptes nommés MSSQLSERVER01, MSSQLSERVER02 et ainsi de suite sur jusqu'à MSSQLSERVER20.

Tâches en parallèle ne consomment pas de comptes supplémentaires. Par exemple, si un utilisateur exécute une tâche de calcul de score qui utilise le traitement parallèle, le même compte de travail est réutilisé pour tous les threads. Si vous avez l’intention de faire un usage intensif de l’apprentissage, vous pouvez augmenter le nombre de comptes utilisés pour exécuter des scripts externes. Pour plus d’informations, consultez [modifier le pool de comptes d’utilisateur pour l’apprentissage](../../advanced-analytics/administration/modify-user-account-pool.md).

### <a name="permissions-granted-to-sqlrusergroup"></a>Autorisations accordées à SQLRUserGroup

Par défaut, les membres de **SQLRUserGroup** ont autorisations read et execute sur les fichiers dans SQL Server **Binn**, **R_SERVICES**, et **PYTHON_SERVICES** annuaires, avec accès aux fichiers exécutables, des bibliothèques et des jeux de données intégrées dans les distributions de R et Python installées avec SQL Server. 

Pour protéger les ressources sensibles sur SQL Server, vous pouvez éventuellement définir une liste de contrôle d’accès (ACL) qui refuse l’accès à **SQLRUserGroup**. À l’inverse, vous pouvez également accorder des autorisations relatives aux ressources de données locales qui existent sur l’ordinateur hôte, en dehors de SQL Server lui-même. 

Par conception, **SQLRUserGroup** n’a pas d’une connexion de base de données ou des autorisations pour toutes les données. Dans certaines circonstances, vous souhaiterez créer une connexion pour autoriser les connexions de retour de boucle, en particulier lorsqu’une identité Windows approuvé est l’utilisateur appelant. Cette fonctionnalité s’appelle [ *l’authentification implicite*](#implied-authentication). Pour plus d’informations, consultez [SQLRUserGroup d’ajouter en tant qu’un utilisateur de base de données](../../advanced-analytics/security/add-sqlrusergroup-to-database.md).

::: moniker range=">=sql-server-ver15||=sqlallproducts-allversions"
### <a name="appcontainer-isolation-in-sql-server-2019"></a>Isolement de AppContainer dans SQL Server 2019

Dans SQL Server 2019, le programme d’installation ne crée plus de comptes de travail pour **SQLRUserGroup**. Au lieu de cela, l’isolation est obtenue via [AppContainers](https://docs.microsoft.com/windows/desktop/secauthz/appcontainer-isolation). Au moment de l’exécution, quand les code ou script incorporé est détectée dans une procédure stockée ou une requête, SQL Server appelle Launchpad avec une demande pour un lanceur spécifiques à l’extension. LaunchPad appelle l’environnement d’exécution appropriée dans un processus sous son identité et instancie un AppContainer pour le contenir. Cette modification est utile, car la gestion de compte et mot de passe local n’est plus nécessaire. En outre, sur les installations où les comptes d’utilisateurs locaux sont interdites, élimination de la dépendance de compte d’utilisateur local signifie que vous pouvez maintenant utiliser cette fonctionnalité.

Implémenté par SQL Server, AppContainers sont un mécanisme interne. Pendant que vous les verrez des preuves physiques de AppContainers dans le moniteur de processus, vous pouvez les trouver dans les règles de pare-feu sortantes créées par le programme d’installation pour empêcher les processus d’effectuer des appels réseau.

> [!Note]
> Dans SQL Server 2019, **SQLRUserGroup** a uniquement un membre qui est maintenant le compte de service SQL Server Launchpad unique au lieu de plusieurs comptes de travail.
::: moniker-end

## <a name="user-security"></a>Sécurité de l’utilisateur

Modèle de sécurité des données de SQL Server des connexions de base de données et des rôles étendre au script R et Python. Connexions de base de données peuvent reposer sur les identités Windows ou un utilisateur de base de données SQL Server. 

En tant qu’un utilisateur de base de données, si vous disposez des autorisations pour exécuter une requête particulière, n’importe quel script R ou Python que vous exécutez sur SQL Server a également l’autorisation pour récupérer les mêmes données. La capacité de consommer, créez et enregistrez la base de données objets dépend des autorisations de base de données. Pour plus d’informations, consultez [autoriser les utilisateurs à SQL Server Machine Learning Services](../../advanced-analytics/security/user-permission.md).

### <a name="mapping-user-identities-to-worker-accounts"></a>Mapper les identités d’utilisateur pour les comptes de travail

Lorsqu’une session est démarrée, Launchpad mappe l’identité de l’utilisateur appelant à un compte de travail. Le mappage d’un utilisateur Windows externe ou d’une connexion SQL valide à un compte de travail est valide uniquement pour la durée de vie de l’instruction SQL de procédure stockée qui exécute le script externe. Les requêtes en parallèle du même compte de connexion sont mappées au même compte de travail utilisateur.

Pendant l’exécution, Launchpad crée des dossiers temporaires pour stocker les données de session, en supprimant lorsque la session se termine. Les répertoires ont un accès limité. Pour R, RLauncher effectue cette tâche. Pour Python, PythonLauncher exécute cette tâche. Chaque compte de travail individuels est limité à son propre dossier et ne peut pas accéder aux fichiers dans les dossiers situés au-dessus du niveau de son propre. Toutefois, le compte de travail peut lire, écrire ou supprimer des enfants sous le dossier de travail de session qui a été créé. Si vous êtes administrateur de l’ordinateur, vous pouvez afficher les répertoires créés pour chaque processus. Chaque répertoire est identifié par son GUID de session.

<a name="implied-authentication"></a>

### <a name="implied-authentication"></a>Authentification implicite

*L’authentification implicite* décrit le comportement de demande de connexion sous lequel les processus externes en cours d’exécution comme comptes de travail de faibles privilèges sont présentés comme une identité utilisateur approuvée à SQL Server sur une boucle des demandes de publication de données ou d’opérations. Comme un concept, l’authentification implicite est propre à l’authentification Windows, dans les chaînes de connexion SQL Server en spécifiant une connexion approuvée, sur les demandes provenant d’un processus externe comme script R ou Python. Il est parfois également appelé un *demi-tour*.

Connexions approuvées sont envisageables à partir d’un script R et Python, mais uniquement avec une configuration supplémentaire. Dans l’architecture d’extensibilité, les processus de R et Python s’exécutent sous des comptes de travail, héritant des autorisations du parent **SQLRUserGroup**. Lorsqu’une chaîne de connexion spécifie « Trusted_Connection = True », l’identité du compte de travail est présentée sur la demande de connexion est inconnue par défaut pour SQL Server. 

Pour établir des connexions fiables réussie, vous devez créer une connexion de base de données pour le **SQLRUserGroup**. Après cela, une connexion à partir de n’importe quel membre est approuvée **SQLRUserGroup** a des droits de connexion à SQL Server. Pour obtenir des instructions détaillées, consultez [ajouter SQLRUserGroup à une connexion de base de données](../../advanced-analytics/security/add-sqlrusergroup-to-database.md).

Connexions approuvées ne sont pas la formulation plus largement utilisée d’une demande de connexion. Lorsque le script R ou Python spécifie une connexion, il peut être plus courant d’utiliser une connexion SQL, ou un nom d’utilisateur spécifié et le mot de passe si la connexion à une source de données ODBC.

#### <a name="how-implied-authentication-works-for-r-and-python-sessions"></a>Fonctionnement de l’authentification comment implicite pour les sessions R et Python

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

Comme prochaine étape, passez en revue les instructions pour [l’octroi d’autorisations](../../advanced-analytics/security/user-permission.md). Pour les serveurs qui utilisent l’authentification Windows, vous devez également examiner [ajouter SQLRUserGroup à une connexion de base de données](../../advanced-analytics/security/add-sqlrusergroup-to-database.md) pour savoir quand une configuration supplémentaire est requise.