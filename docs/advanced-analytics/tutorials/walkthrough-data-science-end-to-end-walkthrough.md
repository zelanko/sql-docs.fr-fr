---
title: Didacticiel pour les scientifiques des données à l’aide du langage R
description: Didacticiel illustrant comment créer une solution R de bout en bout pour l’analyse dans la base de données.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/11/2019
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: ad7f5a500f740e4a302f814ec9523dfb33ecc68b
ms.sourcegitcommit: 710d60e7974e2c4c52aebe36fceb6e2bbd52727c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/11/2019
ms.locfileid: "72278274"
---
# <a name="tutorial-sql-development-for-r-data-scientists"></a>Tutoriel : Développement SQL pour les scientifiques de données R
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Dans ce didacticiel pour les scientifiques des données, Découvrez comment créer une solution de bout en bout pour la modélisation prédictive basée sur la prise en charge des fonctionnalités R dans SQL Server 2016 ou SQL Server 2017. Ce didacticiel utilise une base de données [NYCTaxi_sample](demo-data-nyctaxi-in-sql.md) sur SQL Server. 

Vous utilisez une combinaison de code R, de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et de fonctions SQL personnalisées pour créer un modèle de classification qui indique la probabilité que le pilote puisse obtenir un pourboire sur un voyage de taxi particulier. Vous déployez également votre modèle R sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et utilisez les données du serveur pour générer des scores basés sur le modèle.

Cet exemple peut être étendu à tous les types de problèmes réels, tels que la prédiction des réponses des clients aux campagnes de vente ou la prédiction des dépenses ou la participation aux événements. Étant donné que le modèle peut être appelé à partir d’une procédure stockée, vous pouvez facilement l’incorporer dans une application.

Étant donné que la procédure pas à pas est conçue pour introduire des développeurs R pour [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], R est utilisé dans la mesure du possible. Toutefois, cela ne signifie pas que R est nécessairement l’outil le mieux adapté à chaque tâche. Dans de nombreux cas, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut offrir de meilleures performances, en particulier pour des tâches telles que l’agrégation de données et l’ingénierie de caractéristiques.  Ces tâches peuvent notamment profiter de nouvelles fonctionnalités dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], telles que les index columnstore optimisés en mémoire. Nous essayons de souligner les optimisations possibles en cours de route.

## <a name="prerequisites"></a>Prérequis

+ [SQL Server machine learning services avec l’intégration r](../install/sql-machine-learning-services-windows-install.md#verify-installation) ou [SQL Server 2016 r services](../install/sql-r-services-windows-install.md)

+ [Autorisations de base de](../security/user-permission.md) données et connexion utilisateur de base de données SQL Server

+ [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)

+ [Base de données de démonstration du taxi de New York](demo-data-nyctaxi-in-sql.md)

+ Un IDE R tel que RStudio ou l’outil RGUI intégré fourni avec R

Nous vous recommandons d’effectuer cette procédure pas à pas sur une station de travail cliente. Vous devez être en mesure de vous connecter, sur le même réseau, à un ordinateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avec SQL Server et le langage R activé. Pour obtenir des instructions sur la configuration de la station de travail, consultez [configurer un client de science des données pour le développement R](../r/set-up-a-data-science-client.md).

Vous pouvez également exécuter la procédure pas à pas sur un ordinateur qui a à la fois [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et un environnement de développement R, mais nous ne recommandons pas cette configuration pour un environnement de production. Si vous devez placer le client et le serveur sur le même ordinateur, veillez à installer un deuxième ensemble de bibliothèques Microsoft R pour envoyer un script R à partir d’un client « distant ». N’utilisez pas les bibliothèques R qui sont installées dans les fichiers programme de l’instance SQL Server. Plus précisément, si vous utilisez un ordinateur, vous avez besoin de la bibliothèque RevoScaleR dans ces deux emplacements pour prendre en charge les opérations du client et du serveur.

+ C:\Program Files\Microsoft\R Client\R_SERVER\library\RevoScaleR 
+ C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library\RevoScaleR

> [!NOTE]
> Si vous utilisez [machine learning Server](https://docs.microsoft.com/machine-learning-server/) ou le [Data science Virtual Machine](https://docs.microsoft.com/azure/machine-learning/data-science-virtual-machine/), au lieu de R client, le chemin d’accès à RevoScaleR est C:\Program Files\Microsoft\ML Server\R_SERVER\library\RevoScaleR

<a name="add-packages"></a>

## <a name="additional-r-packages"></a>Packages R supplémentaires

Cette procédure pas à pas requiert plusieurs bibliothèques R qui ne sont pas installées par défaut dans le cadre de [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]. Vous devez installer les packages sur le client sur lequel vous développez la solution et sur l’ordinateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur lequel vous déployez la solution.

### <a name="on-a-client-workstation"></a>Sur une station de travail cliente

Dans votre environnement R, copiez les lignes suivantes et exécutez le code dans une fenêtre de console (RGUI ou IDE). Certains packages installent également les packages requis. En tout, environ 32 packages sont installés. Vous devez disposer d’une connexion Internet pour effectuer cette étape.
    
  ```R
  # Install required R libraries, if they are not already installed.
  if (!('ggmap' %in% rownames(installed.packages()))){install.packages('ggmap')}
  if (!('mapproj' %in% rownames(installed.packages()))){install.packages('mapproj')}
  if (!('ROCR' %in% rownames(installed.packages()))){install.packages('ROCR')}
  if (!('RODBC' %in% rownames(installed.packages()))){install.packages('RODBC')}
  ```

### <a name="on-the-server"></a>Sur le serveur

Plusieurs options s’offrent à vous pour installer des packages sur SQL Server. Par exemple, SQL Server fournit une fonctionnalité de [gestion des packages R](../r/install-additional-r-packages-on-sql-server.md) qui permet aux administrateurs de base de données de créer un référentiel de packages et d’affecter aux utilisateurs les droits nécessaires pour installer leurs propres packages. Toutefois, si vous êtes administrateur de l’ordinateur, vous pouvez installer de nouveaux packages à l’aide de R, à condition que vous installiez dans la bibliothèque appropriée.

> [!NOTE]
> Sur le serveur, **ne procédez pas** à l’installation dans une bibliothèque utilisateur, même si vous y êtes invité. Si vous installez dans une bibliothèque utilisateur, l’instance de SQL Server ne peut pas trouver ou exécuter les packages. Pour plus d’informations, consultez [installation de nouveaux packages R sur SQL Server](../r/install-additional-r-packages-on-sql-server.md).

1. Sur l’ordinateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ouvrez RGui.exe **en tant qu’administrateur**.  Si vous avez installé SQL Server R Services à l’aide des paramètres par défaut, RGUI. exe se trouve dans C:\Program Files\Microsoft SQL Server\MSSQL13. MSSQLSERVER\R_SERVICES\bin\x64).

2. À l’invite R, exécutez les commandes R suivantes :
  
  ```R
  install.packages("ggmap", lib=grep("Program Files", .libPaths(), value=TRUE)[1])
  install.packages("mapproj", lib=grep("Program Files", .libPaths(), value=TRUE)[1])
  install.packages("ROCR", lib=grep("Program Files", .libPaths(), value=TRUE)[1])
  install.packages("RODBC", lib=grep("Program Files", .libPaths(), value=TRUE)[1])
  ```
  Cet exemple utilise la fonction grep R pour rechercher le vecteur de chemins disponibles et rechercher le chemin d’accès qui contient « Program Files ». Pour plus d’informations, consultez [https://www.rdocumentation.org/packages/base/functions/grep](https://www.rdocumentation.org/packages/base/functions/grep).

  Si vous pensez que les packages sont déjà installés, vérifiez la liste des packages installés en exécutant `installed.packages()`.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Explorer et résumer les données](walkthrough-view-and-summarize-data-using-r.md)
