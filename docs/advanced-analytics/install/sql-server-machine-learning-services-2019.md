---
title: Différences dans SQL Server 2019 - Machine Learning Services SQL Server
description: Découvrez les nouveautés de R et Python SQL Server extensions machine learning dans la version préliminaire de SQL Server 2019.
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/22/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 43d427129cae773fc17a0d73f57a26144b7cd09f
ms.sourcegitcommit: a91c3f4fe2587d474cd4d470bda93239ba2693bb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2019
ms.locfileid: "67141418"
---
# <a name="differences-in-sql-server-machine-learning-services-installation-in-sql-server-2019"></a>Différences dans l’installation de SQL Server Machine Learning Services dans SQL Server 2019  
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Sur Windows, le programme d’installation de SQL Server 2019 modifie le mécanisme d’isolation des processus externes. Cette modification remplace les comptes de travail local avec [AppContainers](https://docs.microsoft.com/windows/desktop/secauthz/appcontainer-isolation), une technologie d’isolation pour les applications clientes s’exécutant sur Windows. 

Il n’y a aucun élément d’action spécifique pour l’administrateur à la suite de la modification. Sur un serveur nouveau ou mis à niveau, tous les scripts externes et le code exécuté à partir de [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) suivez le nouveau modèle d’isolation automatiquement. 

Résumé, les principales différences dans cette version sont :

+ Comptes d’utilisateurs locaux sous **groupe d’utilisateurs restreint SQL (SQLRUserGroup)** ne sont plus créés ou utilisés pour exécuter des processus externes. AppContainers les remplacer.
+ **SQLRUserGroup** appartenance a changé. Au lieu de plusieurs comptes d’utilisateurs locaux, consistent en des simplement le compte de service SQL Server Launchpad. Les processus R et Python s’exécutent désormais sous l’identité du service Launchpad isolée via AppContainers.

Bien que le modèle d’isolation a changé, les paramètres d’Assistant et de ligne de commande Installation restent les mêmes dans SQL Server 2019. Pour faciliter l’installation, consultez [installer SQL Server Machine Learning Services](sql-machine-learning-services-windows-install.md).

## <a name="about-appcontainer-isolation"></a>Sur l’isolement de AppContainer

Dans les versions précédentes, **SQLRUserGroup** contenait un pool locales Windows des comptes d’utilisateur (MSSQLSERVER00 MSSQLSERVER20) utilisés pour isoler et en cours d’exécution des processus externes. Lorsqu’un processus externe était nécessaire, service SQL Server Launchpad serait tenir un compte disponible et l’utiliser pour exécuter un processus. 

Dans SQL Server 2019, le programme d’installation ne crée plus comptes de travail local. Au lieu de cela, l’isolation est obtenue via [AppContainers](https://docs.microsoft.com/windows/desktop/secauthz/appcontainer-isolation). Au moment de l’exécution, quand les code ou script incorporé est détectée dans une procédure stockée ou une requête, SQL Server appelle Launchpad avec une demande pour un lanceur spécifiques à l’extension. LaunchPad appelle l’environnement d’exécution appropriée dans un processus sous son identité et instancie un AppContainer pour le contenir. Cette modification est utile, car la gestion de compte et mot de passe local n’est plus nécessaire. En outre, sur les installations où les comptes d’utilisateurs locaux sont interdites, élimination de la dépendance de compte d’utilisateur local signifie que vous pouvez maintenant utiliser cette fonctionnalité.

Implémenté par SQL Server, AppContainers sont un mécanisme interne. Pendant que vous les verrez des preuves physiques de AppContainers dans le moniteur de processus, vous pouvez les trouver dans les règles de pare-feu sortantes créées par le programme d’installation pour empêcher les processus d’effectuer des appels réseau.

## <a name="firewall-rules-created-by-setup"></a>Règles de pare-feu créées par le programme d’installation

Par défaut, SQL Server désactive les connexions sortantes en créant des règles de pare-feu. Dans le passé, ces règles étaient basés sur les comptes d’utilisateurs locaux, où le programme d’installation créé une règle sortante pour **SQLRUserGroup** qui refuse l’accès de réseau à ses membres (chaque compte de travail a été répertoriée comme un principe local soumis à la rule_. 

Dans le cadre du passage à AppContainers, il existe de nouvelles règles de pare-feu en fonction des AppContainer SIDs : un pour chacune des 20 AppContainers créé par le programme d’installation de SQL Server. Conventions d’affectation de noms pour le nom de règle de pare-feu sont **bloquer l’accès réseau pour AppContainer-00 dans l’instance SQL Server MSSQLSERVER**où 00 est le nombre de l’AppContainer (00-20 par défaut) et MSSQLSERVER est le nom de l’instruction SQL Instance de serveur. 

> [!Note]
> Si les appels réseau sont nécessaires, vous pouvez désactiver les règles de trafic sortant dans le pare-feu Windows.

## <a name="program-file-permissions"></a>Autorisations de fichiers de programme

Comme avec les versions précédentes, le **SQLRUserGroup** continue à fournir en lecture et d’autorisations d’exécution des exécutables dans SQL Server **Binn**, **R_SERVICES**et  **PYTHON_SERVICES** répertoires. Dans cette version, le seul membre de **SQLRUserGroup** est le compte de service SQL Server Launchpad.  Lorsque le service Launchpad démarre un environnement d’exécution R ou Python, le processus s’exécute en tant que service LaunchPad.

## <a name="implied-authentication"></a>Authentification implicite

Comme auparavant, une configuration supplémentaire est toujours requise pour *l’authentification implicite* au cas où le script ou code possède pour se connecter à SQL Server à l’aide de l’authentification approuvée pour récupérer des données ou ressources. La configuration supplémentaire implique la création d’une connexion de base de données pour **SQLRUserGroup**, dont seul le membre est désormais le compte de service SQL Server Launchpad unique au lieu de plusieurs comptes de travail. Pour plus d’informations sur cette tâche, consultez [SQLRUserGroup d’ajouter en tant qu’un utilisateur de base de données](../security/create-a-login-for-sqlrusergroup.md).


## <a name="symbolic-link-created-by-setup"></a>Lien symbolique créé par le programme d’installation

Un lien symbolique est créé à la valeur par défaut actuelle **R_SERVICES** et **PYTHON_SERVICES** dans le cadre du programme d’installation de SQL Server. Si vous ne souhaitez pas créer ce lien, une alternative consiste à accorder l’autorisation de lecture « tous les packages d’application » à la hiérarchie mènent vers le dossier.


## <a name="see-also"></a>Voir aussi

+ [Installer SQL Server Machine Learning Services sur Windows](sql-machine-learning-services-windows-install.md)

+ [Installer SQL Server 2019 Machine Learning Services sur Linux](../../linux/sql-server-linux-setup-machine-learning.md)
