---
title: Différences dans SQL Server 2019
description: Découvrez les nouveautés de R et Python SQL Server les extensions Machine Learning dans la version préliminaire SQL Server 2019.
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/22/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 218ae9bd0685370f38942592fd32da75272fbcac
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68470311"
---
# <a name="differences-in-sql-server-machine-learning-services-installation-in-sql-server-2019"></a>Différences dans SQL Server installation Machine Learning Services dans SQL Server 2019  
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Sur Windows, le programme d’installation de SQL Server 2019 modifie le mécanisme d’isolation pour les processus externes. Cette modification remplace les comptes de travail locaux par [AppContainers](https://docs.microsoft.com/windows/desktop/secauthz/appcontainer-isolation), une technologie d’isolation pour les applications clientes s’exécutant sur Windows. 

Il n’existe aucun élément d’action spécifique pour l’administrateur en raison de la modification. Sur un serveur nouveau ou mis à niveau, tous les scripts externes et le code exécuté à partir de [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) suivent automatiquement le nouveau modèle d’isolation. 

Résumé, les principales différences dans cette version sont les suivantes:

+ Les comptes d’utilisateurs locaux sous le **groupe d’utilisateurs restreints SQL (SQLRUserGroup)** ne sont plus créés ou utilisés pour exécuter des processus externes. AppContainers les remplacent.
+ L’appartenance à **SQLRUserGroup** a changé. Au lieu de plusieurs comptes d’utilisateur locaux, l’appartenance se compose uniquement du compte de service SQL Server Launchpad. Les processus R et Python s’exécutent désormais sous l’identité du service Launchpad, isolée par le biais de AppContainers.

Bien que le modèle d’isolation ait changé, l’Assistant Installation et les paramètres de ligne de commande restent les mêmes dans SQL Server 2019. Pour obtenir de l’aide sur l’installation, consultez [installer SQL Server machine learning services](sql-machine-learning-services-windows-install.md).

## <a name="about-appcontainer-isolation"></a>À propos de l’isolation AppContainer

Dans les versions précédentes, **SQLRUserGroup** contenait un pool de comptes d’utilisateur Windows locaux (MSSQLSERVER00-MSSQLSERVER20) utilisé pour isoler et exécuter des processus externes. Lorsqu’un processus externe était nécessaire, SQL Server Launchpad service prendrait un compte disponible et l’utilisera pour exécuter un processus. 

Dans SQL Server 2019, le programme d’installation ne crée plus de comptes Worker locaux. Au lieu de cela, l’isolation est obtenue via [AppContainers](https://docs.microsoft.com/windows/desktop/secauthz/appcontainer-isolation). Au moment de l’exécution, lorsqu’un script ou un code incorporé est détecté dans une procédure stockée ou une requête, SQL Server appelle Launchpad avec une demande de lanceur spécifique à l’extension. Launchpad appelle l’environnement d’exécution approprié dans un processus sous son identité et instancie un AppContainer pour le contenir. Cette modification est avantageuse, car la gestion des comptes et des mots de passe locaux n’est plus nécessaire. En outre, sur les installations où les comptes d’utilisateurs locaux sont interdits, l’élimination de la dépendance de compte d’utilisateur local signifie que vous pouvez désormais utiliser cette fonctionnalité.

Comme implémenté par SQL Server, AppContainers est un mécanisme interne. Bien que vous ne puissiez pas voir les preuves physiques de AppContainers dans Process Monitor, vous pouvez les trouver dans les règles de pare-feu sortantes créées par le programme d’installation pour empêcher les processus d’effectuer des appels réseau.

## <a name="firewall-rules-created-by-setup"></a>Règles de pare-feu créées par le programme d’installation

Par défaut, SQL Server désactive les connexions sortantes en créant des règles de pare-feu. Dans le passé, ces règles étaient basées sur des comptes d’utilisateur locaux, où le programme d’installation créait une règle sortante pour les **SQLRUserGroup** qui ont refusé l’accès réseau à ses membres (chaque compte Worker était listé comme un principe local soumis au rule_. 

Dans le cadre de la migration vers AppContainers, il existe de nouvelles règles de pare-feu basées sur les SID AppContainer: une pour chacune des 20 AppContainers créées par SQL Server installation. Les conventions d’affectation de noms pour le nom de règle de pare-feu sont **accès réseau de blocage pour AppContainer-00 dans SQL Server instance MSSQLSERVER**, où 00 est le numéro de l’appcontainer (00-20 par défaut) et MSSQLSERVER est le nom de l’instance de SQL Server. 

> [!Note]
> Si des appels réseau sont requis, vous pouvez désactiver les règles de trafic sortant dans le pare-feu Windows.

## <a name="program-file-permissions"></a>Autorisations des fichiers programme

Comme avec les versions précédentes, **SQLRUserGroup** continue de fournir des autorisations de lecture et d’exécution sur les exécutables des répertoires Binn, **R_SERVICES**et **PYTHON_SERVICES** de SQL Server **Binn**. Dans cette version, le seul membre de **SQLRUserGroup** est le compte de service SQL Server launchpad.  Lorsque le service Launchpad démarre un environnement d’exécution R ou python, le processus s’exécute en tant que service LaunchPad.

## <a name="implied-authentication"></a>Authentification implicite

Comme précédemment, une configuration supplémentaire est toujours nécessaire pour *l’authentification implicite* dans les cas où le script ou le code doit se reconnecter à SQL Server à l’aide de l’authentification approuvée pour récupérer des données ou des ressources. La configuration supplémentaire implique la création d’une connexion de base de données pour **SQLRUserGroup**, dont le seul membre est maintenant le seul compte de service SQL Server Launchpad au lieu de plusieurs comptes de travail. Pour plus d’informations sur cette tâche, consultez [Ajouter SQLRUserGroup en tant qu’utilisateur de base de données](../security/create-a-login-for-sqlrusergroup.md).


## <a name="symbolic-link-created-by-setup"></a>Lien symbolique créé par le programme d’installation

Un lien symbolique est créé vers le **R_SERVICES** et le **PYTHON_SERVICES** par défaut actuels dans le cadre de l’installation de SQL Server. Si vous ne souhaitez pas créer ce lien, une autre solution consiste à accorder l’autorisation de lecture «tous les packages d’application» à la hiérarchie menant au dossier.


## <a name="see-also"></a>Voir aussi

+ [Installer SQL Server Machine Learning Services sur Windows](sql-machine-learning-services-windows-install.md)

+ [Installer SQL Server 2019 Machine Learning Services sur Linux](../../linux/sql-server-linux-setup-machine-learning.md)
