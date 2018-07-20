---
title: Procédure pas à pas de données de bout en bout science pour R et SQL Server | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 3d4f38fd424c881392d48b0a6a24feb7f7e27ee0
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39086501"
---
# <a name="end-to-end-data-science-walkthrough-for-r-and-sql-server"></a>Procédure pas à pas de données de bout en bout science pour R et SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dans cette procédure pas à pas, vous développez une solution de bout en bout pour la modélisation prédictive basée sur la prise en charge des fonctionnalités de R dans SQL Server 2016 ou SQL Server 2017.

Cette procédure pas à pas est basée sur le jeu de données des taxis de New York, un jeu de données publiques souvent utilisé. Vous utilisez une combinaison de code R, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] données et fonctions SQL personnalisées pour générer un modèle de classification qui indique la probabilité que le pilote peut obtienne un pourboire lors d’un trajet en taxi particulier. Vous également déployer votre modèle R sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et utiliser les données de serveur pour générer des scores basés sur le modèle.

Cet exemple peut être étendu à tous les types de problèmes réels, tels que la prédiction des réponses des clients aux campagnes de vente ou la prédiction des dépenses ou la participation aux événements. Étant donné que le modèle peut être appelé à partir d’une procédure stockée, vous pouvez facilement l’incorporer dans une application.

Étant donné que la procédure pas à pas étant conçue pour présenter aux développeurs R [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], R est utilisé dans la mesure du possible. Toutefois, cela ne signifie pas que R est nécessairement le meilleur outil pour chaque tâche. Dans de nombreux cas, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut offrir de meilleures performances, en particulier pour des tâches telles que l’agrégation de données et l’ingénierie de caractéristiques.  Ces tâches peuvent notamment profiter de nouvelles fonctionnalités dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], telles que les index columnstore optimisés en mémoire. Nous essayons de souligner les optimisations possibles tout au long du processus.

## <a name="target-audience"></a>Public cible

Cette procédure pas à pas est destinée aux développeurs R ou SQL. Elle présente de quelle façon R peut être intégré dans les workflows d’entreprise à l’aide de [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)].  Vous devez connaître avec des opérations de base de données, telles que la création de tables et des bases de données, l’importation de données et l’exécution des requêtes.

+ Tous les scripts SQL et R sont inclus.
+ Vous devrez peut-être modifier les chaînes dans les scripts, à exécuter dans votre environnement. Vous pouvez le faire avec n’importe quel éditeur de code, tel que [Visual Studio Code](https://code.visualstudio.com/Download).

## <a name="prerequisites"></a>Prérequis

Nous vous recommandons d’effectuer cette procédure pas à pas sur un ordinateur portable ou un autre ordinateur qui a les bibliothèques Microsoft R installés. Vous devez être en mesure de vous connecter, sur le même réseau, à un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ordinateur avec SQL Server et le langage R est activé.

Vous pouvez exécuter la procédure pas à pas sur un ordinateur qui possède ces deux [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et un environnement de développement R, mais nous ne recommandons pas cette configuration pour un environnement de production.

Si vous souhaitez exécuter des commandes R à partir d’un ordinateur distant, comme un ordinateur portable ou un autre ordinateur en réseau, vous devez installer les bibliothèques Microsoft R Open. Vous pouvez installer Microsoft R Client ou Microsoft R Server. L’ordinateur distant doit être en mesure de se connecter à la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.

Si vous avez besoin de placer le client et le serveur sur le même ordinateur, veillez à installer un ensemble distinct de bibliothèques Microsoft R à utiliser lors de l’envoi d’un script R à partir d’un client « distant ». N’utilisez pas les bibliothèques R qui sont installés pour une utilisation par l’instance de SQL Server à cet effet.

## <a name="add-r-to-sql-server"></a>Ajouter R vers SQL Server

Vous devez avoir accès à une instance de SQL Server avec la prise en charge de R est installé. Cette procédure pas à pas a été initialement développé pour erver SQL 2016 et testé sur 2017, vous devez donc en mesure d’utiliser une des versions suivantes de SQL Server. (Il existe certaines différences mineures dans les fonctions RevoScaleR entre les versions.)

+ [Installer SQL Server 2017 Machine Learning Services](../install/sql-machine-learning-services-windows-install.md)
+ [Installer SQL Server 2016 R Services](../install/sql-r-services-windows-install.md).

## <a name="install-an-r-development-environment"></a>Installez un environnement de développement R

Pour cette procédure pas à pas, nous vous recommandons d’utiliser un environnement de développement R. Voici quelques suggestions :

- **Outils R pour Visual Studio** (RTVS) est un plug-in qui fournit Intellisense, le débogage et prise en charge de Microsoft R. vous pouvez l’utiliser avec R Server et SQL Server Machine Learning Services. Pour télécharger, consultez [Outils R pour Visual Studio](https://www.visualstudio.com/vs/rtvs/).

- **Microsoft R Client** est un outil de développement léger qui prend en charge le développement dans R à l’aide du package RevoScaleR. Pour l’obtenir, consultez [Get Started with Microsoft R Client (Prise en main de Microsoft R Client)](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client).

- **RStudio** est un des environnements les plus populaires pour le développement R. Pour plus d’informations, consultez [ https://www.rstudio.com/products/RStudio/ ](https://www.rstudio.com/products/RStudio/).

    Vous ne pouvez pas suivre ce didacticiel à l’aide d’une installation générique de RStudio ou un autre environnement ; Vous devez également installer les packages R et les bibliothèques de connectivité pour Microsoft R Open. Pour plus d’informations, consultez [Configurer un client de science des données](../r/set-up-a-data-science-client.md).

- Outils de base R (R.exe, RTerm.exe, RScripts.exe) sont également installés par défaut lorsque vous installez R dans SQL Server ou de R Client. Si vous ne souhaitez pas installer un IDE, vous pouvez utiliser ces outils.

## <a name="get-permissions-on-the-sql-server-instance-and-database"></a>Obtenir les autorisations sur l’instance de SQL Server et de la base de données

Pour vous connecter à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour exécuter des scripts et charger des données, vous devez disposer d’une connexion valide sur le serveur de base de données.  Vous pouvez utiliser un compte de connexion SQL ou l’authentification Windows intégrée. Demandez à l’administrateur de base de données pour configurer les autorisations suivantes pour le compte, dans la base de données dans lequel vous utilisez r :

- Créer une base de données, des tables, des fonctions et des procédures stockées
- Écrire des données dans des tables
- Possibilité d’exécuter le script R (`GRANT EXECUTE ANY EXTERNAL SCRIPT to <user>`)

Pour cette procédure pas à pas, nous avons utilisé la connexion SQL **RTestUser**. Nous recommandons généralement que vous utilisez l’authentification intégrée de Windows, mais à l’aide de la connexion SQL est plus simple des fins de démonstration.

## <a name="next-steps"></a>Étapes suivantes

[Préparer les données à l’aide de PowerShell](walkthrough-prepare-the-data.md)
