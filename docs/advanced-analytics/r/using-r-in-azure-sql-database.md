---
title: "À l’aide de R dans la base de données SQL Azure | Documents Microsoft"
ms.custom: 
ms.date: 09/29/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a90c438-d78b-47be-ac05-479de64378b2
caps.latest.revision: 1
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: e3c781449a8f7a1b236508cd21b8c00ff175774f
ms.openlocfilehash: 619921bbf00801fd5930a1c1b110e69a9fd05a81
ms.contentlocale: fr-fr
ms.lasthandoff: 09/30/2017

---
# <a name="using-r-in-azure-sql-database"></a>À l’aide de R dans la base de données SQL Azure

À compter d’octobre 2017, base de données SQL Azure prend en charge l’exécution de R code de bases de données à l’aide de procédures stockées, semblables à R Services dans SQL Server 2016.

Cet article fournit une vue d’ensemble de la fonctionnalité et décrit les restrictions connues.

> [!NOTE]
> Cette version est une version d’évaluation initiale et est destinée à des tests et l’exploration uniquement. Une version de production sera disponible plus tard dans 2018. La date de la version exacte et de la build doit reposer sur les commentaires des utilisateurs. Par conséquent, nous vous encourageons à essayer la fonctionnalité et faites-le nous savoir quelles sont les fonctionnalités importantes. 
> 
> Pour plus d’informations sur la planification de la mise en production, consultez la [de SQL Server](https://blogs.technet.microsoft.com/dataplatforminsider/) ou [blog Microsoft R Server](https://blogs.msdn.microsoft.com/rserver/).

## <a name="features"></a>Fonctionnalités

La version préliminaire fournit les fonctionnalités suivantes :

+ Appeler le code R à l’aide de procédures stockées pour faciliter le déploiement de solutions d’apprentissage
+ Obtenez des scores à partir du modèle à l’aide de n’importe quelle application qui peut se connecter à votre base de données du cloud
+ Prend en charge native de calcul de score à l’aide de la fonction de prédiction, pour calculer les scores rapide sans utilisation du runtime R

Pour connaître les restrictions spécifiques à la version d’évaluation, consultez [Restrictions et les problèmes connus](#bkmk_restrictions).

### <a name="components"></a>Components

L’architecture globale est similaire à celle de SQL Server Machine R Services.

**Sécurité**

+ Le Launchpad approuvé de SQL Server gère l’exécution de travaux R et contrôle la durée de vie des processus. 

**Packages R**

+ La version préliminaire inclut Microsoft R Open 3.3.3 et Microsoft R Server version 9.2. Le [package RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler) est préinstallé.

+ Certains packages R ont été supprimés ou modifiés afin de réduire l’encombrement dans l’environnement Windows Azure. Par exemple, **mrsdeploy** n’est pas inclus dans la base de données SQL Azure.

**Performances**

+ Prend en charge l’apprentissage et le score à partir de n’importe quel modèle où les données peuvent tenir dans la mémoire.  La quantité de mémoire disponible dépend de l’édition de la base de données. 
+ Parallélisme trivial est pris en charge à l’aide de la @parallel = 1 argument, ainsi que la diffusion en continu pour l’exécution du script R 
+ Dans l’aperçu, limité à un seul script R exécuté simultanément par base de données.

**Traduction**

La feuille de route pour la prochaine version inclut la prise en charge pour les packages supplémentaires et Python.

## <a name="restrictions"></a>Restrictions

Cette section répertorie d’autres limitations qui s’appliquent à la version préliminaire.

### <a name="upgrading-r-components-and-adding-packages-not-supported"></a>La mise à niveau des composants R et ajout de packages non pris en charge.

Base de données SQL Azure est un service géré, et les clients ne devraient pas gérer les mises à niveau vers les composants R. Pour la version préliminaire, utilisez les packages installés disponibles.

Mises à niveau vers R et d’autres composants d’apprentissage seront publiés dès qu’elles sont disponibles.

### <a name="availability"></a>Disponibilité

La capacité d’exécuter R et autres d’apprentissage automatique des scripts dans la base de données SQL Azure est une fonctionnalité d’aperçu dans l’ouest des États-Unis région uniquement. Expansion vers d’autres régions, par exemple Europe de l’ouest, est prévue pour les versions ultérieures.

En cours d’exécution R dans la base de données SQL Azure nécessite suffisamment de stockage et de mémoire. Actuellement les niveaux de performance les niveaux de service de base de données suivants sont pris en charge :

+ Niveau de Service Premium : P1, P2, P4, P6, P11, P15 
+ Niveau de service Reporting Services Premium : PRS1, PRS2, PRS4, PRS6 
+ Pool élastique de Premium : Edtu 125 ou supérieur 
+ Pool de RS élastique Premium : Edtu 125 ou supérieur 

### <a name="resource-management"></a>Gestion des ressources

Cette version ne prend pas en charge la possibilité de personnaliser l’installation de R ou pour surveiller l’utilisation de scripts R.

Par exemple, vous ne pouvez pas activer l’exécution du script R uniquement sur les bases de données spécifiques.

La vue de gestion dynamique sys.dm_db_resource_stats, utilisé pour surveiller l’utilisation du processeur et mémoire de scripts R, n’est pas disponible dans la version préliminaire.

### <a name="other-limitations"></a>Autres limitations

Les fonctionnalités suivantes ne sont pas pris en charge : 

+ Le package MicrosoftML n’est pas disponible.
+ Fonctionnalités de gestion de package comme créer une bibliothèque externe ne sont pas pris en charge.
+ Vous ne pouvez pas utiliser la base de données SQL Azure comme contexte de calcul à distance lors de l’exécution de scripts à partir d’un client de R. Des scripts R doivent être exécutés à l’aide de la procédure stockée sp_execute_external_script. Scripts appelées par la procédure stockée ne peut pas utiliser les autres contextes de calcul.
+ Impossible d’exécuter des appels aux fonctions rx qui nécessitent une exécution parallèle.
+ Connexions de bouclage à partir d’un script R à SQL Server ne sont pas pris en charge. En d’autres termes, vous ne pouvez apporter appels externes à partir de votre script R à une autre source de données ODBC.

## <a name="get-started"></a>Prise en main

Cette annonce à partir de l’équipe de développement SQL Server inclut les exemples courts que vous pouvez exécuter vos propres bases de données SQL Azure à faire des essais avec la création de modèles de R et de générer des prédictions.

+ [Formation et évaluation des modèles dans la base de données SQL Azure](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2017/09/25/announcing-preview-of-machine-learning-services-with-r-support-in-azure-sql-database/)

