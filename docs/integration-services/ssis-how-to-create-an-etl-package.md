---
title: "SSIS comment créer un Package ETL | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- SSIS, tutorials
- packages [Integration Services], tutorials
- Integration Services, tutorials
- SQL Server Integration Services, tutorials
- logs [Integration Services], tutorials
- walkthroughs [Integration Services]
ms.assetid: d6d5bb1f-4cb1-4605-9cd6-f60b858382c4
caps.latest.revision: 38
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: d4dc2ff665ff191fb75dd99103a222542262d4c4
ms.openlocfilehash: 2005755d073f7bb4950268e0fba827860491d1c4
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="ssis-how-to-create-an-etl-package"></a>SSIS : comment créer un package ETL

 > Pour obtenir un contenu pour les versions précédentes de SQL Server, consultez [didacticiel SSIS : création d’un Package ETL Simple](https://msdn.microsoft.com/en-US/library/ms169917(SQL.120).aspx).

[!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] (SSIS) est une plateforme conçue pour créer des solutions d’intégration de données très performantes, notamment des packages d’extraction, de transformation et de chargement (ETL) pour l’entreposage des données. SSIS propose des outils graphiques et des assistants permettant de créer et de déboguer des packages ; des tâches permettant de réaliser des fonctions de flux de travail comme les opérations FTP, l'exécution d'instructions SQL et l'envoi de messages électroniques ; des sources de données et des destinations permettant d'extraire et de charger des données ; des transformations permettant de nettoyer, d'agréger, de fusionner et de copier des données ; un service de gestion, le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , permettant d'administrer l'exécution et le stockage des packages, et des API (Application Programming Interface) permettant de programmer le modèle objet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
Au cours de ce didacticiel, vous allez apprendre à utiliser le Concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] pour créer un package [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] simple. Ce package extrait les données d'un fichier plat, les reformate et les insère dans une table de faits. Au cours des leçons suivantes, ce package est développé pour illustrer le bouclage, les options de configuration de package, l'écriture dans un journal et le flux d'erreurs.  
  
Lorsque vous procédez à l'installation des données exemples qu'exploite le didacticiel, vous installez également les versions finales des packages créés au cours de chaque leçon du didacticiel. En utilisant les packages finaux, vous pouvez à votre guise passer outre une leçon et débuter à partir d'une leçon ultérieure du didacticiel. S'il s'agit de la première fois que vous travaillez avec des packages ou le nouvel environnement de développement, nous vous recommandons de commencer par la leçon 1.  
  
## <a name="what-you-will-learn"></a>Contenu du didacticiel  
Le meilleur moyen de se familiariser avec les nouveaux outils et les nouvelles commandes et fonctionnalités de [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] est de les utiliser. Ce didacticiel va vous guider à travers le Concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] pour créer un package ETL simple qui offre le bouclage, les options de configuration, la logique de flux d'erreurs et la fonction d'écriture dans un journal.  
  
## <a name="requirements"></a>Spécifications  
Ce didacticiel s'adresse aux utilisateurs qui ont une connaissance des notions fondamentales liées à l'utilisation des bases de données mais une maîtrise limitée des nouvelles fonctionnalités disponibles dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
Pour utiliser ce didacticiel, les composants suivants doivent être installés sur votre système :  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]avec la **AdventureWorksDW2012** base de données. Pour des raisons de sécurité, les exemples de bases de données ne sont pas installés par défaut. Pour télécharger la base de données **AdventureWorksDW2012** , accédez à [Adventure Works pour SQL Server 2012](http://go.microsoft.com/fwlink/?LinkId=275026).  
  
    > [!IMPORTANT]  
    > Quand vous attachez la base de données (fichier\*.mdf), [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] recherche par défaut un fichier .ldf. Vous devez supprimer manuellement le fichier .ldf avant de cliquer sur OK dans la boîte de dialogue **Attacher des bases de données** .  
    >   
    > Pour plus d'informations sur l'attachement de bases de données, consultez [Attach a Database](../relational-databases/databases/attach-a-database.md).  
  
-   Exemples de données. Ces données exemple sont incluses dans les packages de leçons [!INCLUDE[ssIS](../includes/ssis-md.md)] . Pour télécharger ces exemples de données et les packages de leçons, procédez comme suit.  
  
    1.  Accédez à [Exemples de produits Integration Services](http://go.microsoft.com/fwlink/?LinkId=275027)  
  
    2.  Cliquez sur l'onglet **DOWNLOADS** (Téléchargements).  
  
    3.  Cliquez sur le fichier SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip.  
  
## <a name="lessons-in-this-tutorial"></a>Leçons du didacticiel  
[Leçon 1 : Créer un projet et un package de base avec SSIS](../integration-services/lesson-1-create-a-project-and-basic-package-with-ssis.md)  
Au cours de cette leçon, vous allez créer un package ETL simple qui extrait des données d'un seul fichier plat, transforme ces données en utilisant des transformations de recherche et enfin, charge le résultat dans une destination de table de faits.  
  
[Leçon 2 : Ajout d’un bouclage avec SSIS](../integration-services/lesson-2-adding-looping-with-ssis.md)  
Au cours de cette leçon, vous allez développer le package créé au cours de la leçon 1 pour pouvoir utiliser les nouvelles fonctionnalités de bouclage et extraire des données de plusieurs fichiers plats en un seul processus de flux de données.  
  
[Leçon 3 : Ajouter la journalisation avec SSIS](../integration-services/lesson-3-add-logging-with-ssis.md)  
Au cours de cette leçon, vous allez développer le package que vous avez créé au cours de la leçon 2 pour tirer parti des nouvelles fonctions d'écriture dans un journal.  
  
[Leçon 4 : Ajouter une redirection de flux d’erreurs avec SSIS](../integration-services/lesson-4-add-error-flow-redirection-with-ssis.md)  
Dans cette leçon, vous allez développer le package que vous avez créé au cours de la leçon 3 pour tirer parti des nouvelles configurations de sortie d'erreur.  
  
[Leçon 5 : Ajouter des configurations de package SSIS pour le modèle de déploiement de package](../integration-services/lesson-5-add-ssis-package-configurations-for-the-package-deployment-model.md)  
Au cours de cette leçon, vous allez développer le package que vous avez créé au cours de la leçon 4 pour tirer parti des nouvelles options de configuration de package.  
  
[Leçon 6 : Utilisation des paramètres avec le modèle de déploiement de projet dans SSIS](../integration-services/lesson-6-using-parameters-with-the-project-deployment-model-in-ssis.md)  
Au cours de cette leçon, vous allez développer le package que vous avez créé au cours de la leçon 5 pour tirer parti des nouveaux paramètres dans le modèle de déploiement de projet.  
  
  
  

