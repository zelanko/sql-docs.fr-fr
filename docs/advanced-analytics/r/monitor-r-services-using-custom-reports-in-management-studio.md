---
title: Surveiller R services à l’aide de rapports personnalisés dans Management Studio
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: d8768532e3891183d82cbb2273ded8dcc378b1fc
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68345295"
---
# <a name="monitor-machine-learning-services-using-custom-reports-in-management-studio"></a>Surveiller Machine Learning Services à l’aide de rapports personnalisés dans Management Studio
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Pour faciliter la gestion de l’instance utilisée pour Machine Learning, l’équipe de produit a fourni un certain nombre d’exemples de rapports personnalisés que vous pouvez ajouter à SQL Server Management Studio. Dans ces rapports, vous pouvez afficher des détails tels que:

- Sessions R ou python actives
- Paramètres de configuration de l’instance
- Statistiques d’exécution pour les travaux de Machine Learning
- Événements étendus pour R services
- Packages R ou python installés sur l’instance actuelle

Cet article explique comment installer et utiliser les rapports personnalisés fournis spécifiquement pour l’ordinateur leaerning. 

Pour obtenir une présentation générale des rapports dans Management Studio, consultez [rapports personnalisés dans Management Studio](../../ssms/object/custom-reports-in-management-studio.md).

## <a name="how-to-install-the-reports"></a>Comment installer les rapports

Les rapports sont conçus à l’aide de SQL Server Reporting Services, mais il peuvent être utilisés directement à partir de SQL Server Management Studio, même si Reporting Services n’est pas installé sur votre instance. 

Pour utiliser ces rapports :

* Téléchargez les fichiers RDL à partir du dépôt GitHub d’exemples des produits SQL Server.
* Ajoutez les fichiers au dossier des rapports personnalisés utilisé par SQL Server Management Studio.
* Ouvrez les rapports dans SQL Server Management Studio.


### <a name="step-1-download-the-reports"></a>Étape 1. Télécharger les rapports

1. Ouvrez le référentiel GitHub qui contient des [exemples de produits SQL Server](https://github.com/Microsoft/sql-server-samples), puis téléchargez les exemples de rapports. 

    + [Rapports personnalisés de SSMS](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/machine-learning-services/ssms-custom-reports)

    > [!NOTE]
    > Les rapports peuvent être utilisés avec SQL Server 2017 services d’apprentissage machiine ou SQL Server 2016 R services.

2. Pour télécharger les exemples, vous pouvez également vous connecter à GitHub et effectuer un branchement local des exemples. 

### <a name="step-2-copy-the-reports-to-management-studio"></a>Étape 2. Copier les rapports dans Management Studio

3. Recherchez le dossier des rapports personnalisés utilisé par SQL Server Management Studio. Par défaut, les rapports personnalisés sont stockés dans ce dossier :
    
   `C:\Users\user_name\Documents\SQL Server Management Studio\Custom Reports`

   Toutefois, vous pouvez spécifier un autre dossier, ou créer des sous-dossiers.

4. Copiez les fichiers *.RDL dans le dossier des rapports personnalisés.


### <a name="step-3-run-the-reports"></a>Étape 3. Exécuter les rapports

5. Dans Management Studio, cliquez avec le bouton droit sur le nœud **Bases de données** de l’instance où vous souhaitez exécuter les rapports.
6. Cliquez sur **Rapports**, puis sur **Rapports personnalisés**.
7. Dans la boîte de dialogue **Ouvrir un fichier** , recherchez le dossier des rapports personnalisés.
8. Sélectionnez l’un des fichiers RDL que vous avez téléchargés, puis cliquez sur **Ouvrir**.

> [!IMPORTANT]
> Sur certains ordinateurs, tels que ceux avec des périphériques d’affichage en haute résolution ou avec une résolution supérieure à 1080p, ou dans certaines sessions Bureau à distance, ces rapports ne sont pas utilisables. Il existe un bogue dans le contrôle Visionneuse de rapports dans SSMS qui bloque le rapport.

## <a name="report-list"></a>Liste des rapports

Le référentiel d’exemples de produits dans GitHub comprend actuellement les rapports suivants:

+ **R Services - Sessions actives**

  Utilisez ce rapport pour afficher les utilisateurs qui sont actuellement connectés à l’instance SQL Server et qui exécutent des travaux Machine Learning. 
  
+ **R Services - Configuration**

  Utilisez ce rapport pour afficher la configuration de l’exécution de script externe et des services associés. Le rapport indique si un redémarrage est nécessaire et recherche les protocoles réseau requis. 
  
  L’authentification implicite est requise pour Machine Learning les tâches qui s’exécutent dans SQL Server comme un contexte de calcul. Pour vérifier que l’authentification implicite est configurée, le rapport vérifie si une connexion de base de données existe pour le groupe SQLRUserGroup.

 + **R Services - Configurer l’instance** 

   Ce rapport est destiné à vous aider à configurer Machine Learning. Vous pouvez également exécuter ce rapport pour corriger les erreurs de configuration trouvées dans le rapport précédent.
 
+ **R Services - Statistiques d’exécution**

  Utilisez ce rapport pour afficher les statistiques d’exécution des travaux de Machine Learning. Par exemple, vous pouvez obtenir le nombre total de scripts R qui ont été exécutés, le nombre d’exécutions en parallèle et les fonctions RevoScaleR le plus fréquemment utilisées. Cliquez sur **afficher le script SQL** pour obtenir le code T-SQL complet derrière ce rapport.

  Actuellement, le rapport analyse uniquement les statistiques pour les fonctions de package RevoScaleR.

+ **R Services - Événements étendus**

  Utilisez ce rapport pour afficher la liste des événements étendus disponibles pour l’analyse des tâches liées aux runtimes de script externes. Cliquez sur **afficher le script SQL** pour obtenir le code T-SQL complet derrière ce rapport.

+ **R Services - Packages**

  Utilisez ce rapport pour afficher la liste des packages R ou python installés sur l’instance SQL Server.

+ **R Services - Utilisation des ressources**

  Utilisez ce rapport pour afficher la consommation du processeur, de la mémoire et des ressources d’e/s par exécution de script externe. Vous pouvez également afficher le paramètre de mémoire de pools de ressources externes.

## <a name="see-also"></a>Voir aussi

[Surveillance des services](managing-and-monitoring-r-solutions.md)

[Événements étendus pour R Services](extended-events-for-sql-server-r-services.md)
