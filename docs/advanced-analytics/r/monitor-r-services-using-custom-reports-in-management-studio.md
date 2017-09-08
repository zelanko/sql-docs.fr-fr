---
title: "Analyser R Services à l’aide de rapports personnalisés dans Management Studio | Microsoft Docs"
ms.custom: 
ms.date: 02/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5933c72c-ba63-4966-b882-75719ef8428e
caps.latest.revision: 13
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 14f6d6d7373afd452f06acae43f7023de136bc71
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="monitor-r-services-using-custom-reports-in-management-studio"></a>Analyser R Services à l’aide de rapports personnalisés dans Management Studio
Pour faciliter la gestion de SQL Server R Services, l’équipe produit a fourni de nombreux exemples de rapports personnalisés que vous pouvez ajouter à SQL Server Management Studio pour afficher les détails relatifs à R Services, par exemple :

- une liste des sessions R actives ;
- la configuration R de l’instance actuelle ;
- des statistiques d’exécution pour le runtime R ;
- une liste des événements étendus pour R Services ;
- une liste des packages R installés sur l’instance actuelle.

Cette rubrique explique comment installer et utiliser les rapports. Pour plus d’informations sur les rapports personnalisés dans Management Studio, consultez [Rapports personnalisés dans Management Studio](~/ssms/object/custom-reports-in-management-studio.md).

## <a name="how-to-install-the-reports"></a>Comment installer les rapports

Les rapports sont conçus à l’aide de SQL Server Reporting Services, mais il peuvent être utilisés directement à partir de SQL Server Management Studio, même si Reporting Services n’est pas installé sur votre instance. 

Pour utiliser ces rapports :

* Téléchargez les fichiers RDL à partir du dépôt GitHub d’exemples des produits SQL Server.
* Ajoutez les fichiers au dossier des rapports personnalisés utilisé par SQL Server Management Studio.
* Ouvrez les rapports dans SQL Server Management Studio.


### <a name="step-1-download-the-reports"></a>Étape 1. Télécharger les rapports

1. Ouvrez le dépôt GitHub qui contient les [exemples du produit SQL Server](https://github.com/Microsoft/sql-server-samples) et téléchargez les exemples de rapports à partir de cette page : 

   + [Rapports personnalisés SSMS](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/r-services/ssms-custom-reports)
      
2. Pour télécharger les exemples, vous pouvez également vous connecter à GitHub et effectuer un branchement local des exemples. 

### <a name="step-2-copy-the-reports-to-management-studio"></a>Étape 2. Copier les rapports dans Management Studio

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

Le dépôt GitHub d’exemples des produits comprend les rapports suivants pour SQL Server R Services :

+ **R Services - Sessions actives**

  Utilisez ce rapport pour afficher les utilisateurs actuellement connectés à l’instance SQL et exécutant des tâches R. 
  
+ **R Services - Configuration**

  Utilisez ce rapport pour afficher les propriétés du runtime R et la configuration de R Services. Le rapport indique si un redémarrage est nécessaire et recherche les protocoles réseau requis. 
  
  Une authentification implicite est obligatoire pour l’exécution de R dans un contexte de calcul SQL. Pour contrôler cela, le rapport vérifie si une connexion de base de données existe pour le groupe SQLRUserGroup.

  > [!NOTE]
  > Pour plus d’informations sur ces champs, consultez [Package metadata](http://r-pkgs.had.co.nz/description.html), par Hadley Wickam. Par exemple, le champ *Nickname* (Pseudonyme) pour le runtime R a été introduit pour comprendre la différence entre les versions. 

 + **R Services - Configurer l’instance** 

   Ce rapport est destiné à vous aider à configurer R Services après l’installation. Vous pouvez l’exécuter à partir du rapport précédent si R Services n’est pas configuré correctement.
 
+ **R Services - Statistiques d’exécution**

  Utilisez ce rapport pour afficher les statistiques d’exécution de R Services. Par exemple, vous pouvez obtenir le nombre total de scripts R qui ont été exécutés, le nombre d’exécutions en parallèle et les fonctions RevoScaleR le plus fréquemment utilisées.
  Actuellement, le rapport analyse uniquement les statistiques pour les fonctions de package RevoScaleR.
  Cliquez sur **View SQL Script** (Afficher le script SQL) pour obtenir le code T-SQL pour ce rapport. 

+ **R Services - Événements étendus**

  Utilisez ce rapport pour afficher une liste des événements étendus qui sont disponibles pour l’analyse de l’exécution du script R. 
  Cliquez sur **View SQL Script** (Afficher le script SQL) pour obtenir le code T-SQL pour ce rapport.

+ **R Services - Packages**

  Utilisez ce rapport pour afficher une liste des packages R installés sur l’instance SQL Server. Actuellement, le rapport comprend les propriétés de package suivantes : 
  + Package (nom)
  + Version 
  + Dépend
  + Licence
  + Built (Généré)
  + Lib Path (Chemin de bibliothèque)

+ **R Services - Utilisation des ressources**

  Utilisez ce rapport pour afficher la consommation des ressources processeur, mémoire et E/S par l’exécution de scripts SQL Server R. Vous pouvez également afficher le paramètre de mémoire de pools de ressources externes. 


## <a name="see-also"></a>Voir aussi

[Analyse de R Services](../../advanced-analytics/r-services/monitoring-r-services.md)

[Événements étendus pour R Services](../../advanced-analytics/r-services/extended-events-for-sql-server-r-services.md)


