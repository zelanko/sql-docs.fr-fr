---
title: Didacticiel pour scientifiques des données à l’aide du langage R - SQL Server Machine Learning
description: Didacticiel montrant comment créer une solution R de bout en bout pour la base de données analytique.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/26/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 45d587b4d62c33e944b15c6b951fa1323620c50e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67961701"
---
# <a name="tutorial-sql-development-for-r-data-scientists"></a>Tutoriel : Développement de SQL pour les scientifiques de données R
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dans ce didacticiel pour scientifiques des données, découvrez comment créer des solutions de bout en bout pour la modélisation prédictive basée sur la prise en charge des fonctionnalités de R dans SQL Server 2016 ou SQL Server 2017. Ce didacticiel utilise un [NYCTaxi_sample](demo-data-nyctaxi-in-sql.md) base de données sur SQL Server. 

Vous utilisez une combinaison de code R, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] données et fonctions SQL personnalisées pour générer un modèle de classification qui indique la probabilité que le pilote peut obtienne un pourboire lors d’un trajet en taxi particulier. Vous également déployer votre modèle R sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et utiliser les données de serveur pour générer des scores basés sur le modèle.

Cet exemple peut être étendu à tous les types de problèmes réels, tels que la prédiction des réponses des clients aux campagnes de vente ou la prédiction des dépenses ou la participation aux événements. Étant donné que le modèle peut être appelé à partir d’une procédure stockée, vous pouvez facilement l’incorporer dans une application.

Étant donné que la procédure pas à pas étant conçue pour présenter aux développeurs R [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], R est utilisé dans la mesure du possible. Toutefois, cela ne signifie pas que R est nécessairement le meilleur outil pour chaque tâche. Dans de nombreux cas, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut offrir de meilleures performances, en particulier pour des tâches telles que l’agrégation de données et l’ingénierie de caractéristiques.  Ces tâches peuvent notamment profiter de nouvelles fonctionnalités dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], telles que les index columnstore optimisés en mémoire. Nous essayons de souligner les optimisations possibles tout au long du processus.

## <a name="prerequisites"></a>Prérequis

+ [SQL Server 2017 Machine Learning Services avec intégration de R](../install/sql-machine-learning-services-windows-install.md#verify-installation) ou [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md)

+ [Autorisations de base de données](../security/user-permission.md) et une connexion d’utilisateur de base de données SQL Server

+ [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)

+ [Base de données de démonstration NYC Taxi](demo-data-nyctaxi-in-sql.md)

+ Un IDE R tel que RStudio ou l’outil RGUI intégré inclus avec R

Nous vous recommandons d’effectuer cette procédure pas à pas sur une station de travail cliente. Vous devez être en mesure de vous connecter, sur le même réseau, à un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ordinateur avec SQL Server et le langage R est activé. Pour obtenir des instructions sur la configuration de la station de travail, consultez [configurer un client de science des données pour le développement R](../r/set-up-a-data-science-client.md).

Vous pouvez également exécuter la procédure pas à pas sur un ordinateur qui possède ces deux [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et un environnement de développement R, mais nous ne recommandons pas cette configuration pour un environnement de production. Si vous avez besoin de placer le client et le serveur sur le même ordinateur, veillez à installer un deuxième ensemble de bibliothèques Microsoft R pour l’envoi de script R à partir d’un client « distant ». N’utilisez pas les bibliothèques R qui sont installés dans les fichiers de programme de l’instance de SQL Server. Plus précisément, si vous utilisez un seul ordinateur, vous avez besoin de la bibliothèque RevoScaleR dans ces deux emplacements pour prendre en charge les opérations de client et serveur.

+ C:\Program Files\Microsoft\R Client\R_SERVER\library\RevoScaleR 
+ C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library\RevoScaleR

<a name="add-packages"></a>

## <a name="additional-r-packages"></a>Packages R supplémentaires

Cette procédure pas à pas nécessite plusieurs bibliothèques R qui ne sont pas installés par défaut dans le cadre de [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]. Vous devez installer les packages sur le client lorsque vous développez la solution et sur le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ordinateur où vous déployez la solution.

### <a name="on-a-client-workstation"></a>Sur une station de travail cliente

Dans votre environnement R, copiez les lignes suivantes et exécutez le code dans une fenêtre de Console (Rgui ou un IDE). Certains packages installent également les packages requis. En tout, environ 32 packages sont installés. Vous devez disposer d’une connexion internet pour effectuer cette étape.
    
  ```R
  # Install required R libraries, if they are not already installed.
  if (!('ggmap' %in% rownames(installed.packages()))){install.packages('ggmap')}
  if (!('mapproj' %in% rownames(installed.packages()))){install.packages('mapproj')}
  if (!('ROCR' %in% rownames(installed.packages()))){install.packages('ROCR')}
  if (!('RODBC' %in% rownames(installed.packages()))){install.packages('RODBC')}
  ```

### <a name="on-the-server"></a>Sur le serveur

Vous avez plusieurs options pour l’installation des packages sur SQL Server. Par exemple, SQL Server fournit [gestion des packages R](../r/install-additional-r-packages-on-sql-server.md) fonctionnalité qui permet aux administrateurs de base de données de créer un référentiel de packages et affecter utilisateur les droits pour installer leurs propres packages. Toutefois, si vous êtes un administrateur sur l’ordinateur, vous pouvez installer de nouveaux packages à l’aide de R, tant que vous installez à la bibliothèque appropriée.

> [!NOTE]
> Sur le serveur, **ne le faites pas** installer dans une bibliothèque utilisateur même si vous y êtes invité. Si vous installez dans une bibliothèque utilisateur, l’instance de SQL Server ne peut pas trouver ou exécutez le package. Pour plus d’informations, consultez [l’installation de nouveaux Packages R sur SQL Server](../r/install-additional-r-packages-on-sql-server.md).

1. Sur l’ordinateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ouvrez RGui.exe **en tant qu’administrateur**.  Si vous avez installé SQL Server R Services à l’aide des valeurs par défaut, vous trouverez Rgui.exe dans C:\Program Files\Microsoft SQL Server\MSSQL13. MSSQLSERVER\R_SERVICES\bin\x64).

2. À l’invite R, exécutez les commandes R suivantes :
  
  ```R
  install.packages("ggmap", lib=grep("Program Files", .libPaths(), value=TRUE)[1])
  install.packages("mapproj", lib=grep("Program Files", .libPaths(), value=TRUE)[1])
  install.packages("ROCR", lib=grep("Program Files", .libPaths(), value=TRUE)[1])
  install.packages("RODBC", lib=grep("Program Files", .libPaths(), value=TRUE)[1])
  ```
  Cet exemple utilise la fonction grep R pour rechercher le vecteur de chemins d’accès disponibles et trouver le chemin d’accès qui inclut « Program Files ». Pour plus d’informations, consultez [ https://www.rdocumentation.org/packages/base/functions/grep ](https://www.rdocumentation.org/packages/base/functions/grep).

  Si vous pensez que les packages sont déjà installés, vérifiez la liste des packages installés en exécutant `installed.packages()`.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Explorer et synthétiser les données](walkthrough-view-and-summarize-data-using-r.md)