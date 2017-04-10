---
title: "Utilisation de la base de connaissances par d&#233;faut DQS | Microsoft Docs"
ms.custom: ""
ms.date: "07/31/2012"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b36af13b-9fcc-4168-bb92-214d600b1c93
caps.latest.revision: 13
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 13
---
# Utilisation de la base de connaissances par d&#233;faut DQS
  Cette rubrique décrit la base de connaissances par défaut **données DQS**, qui est installé avec [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS). Il s'agit d'une base de connaissances par défaut prégénérée qui contient les domaines suivants :  
  
-   **Pays/région**: contient le nom long conventionnel (nom officiel tel que désigné par le pays/région) et nom court (nom commun utilisé dans les listes, sur des cartes, etc.), abréviation à deux lettres, abréviation à trois lettres et code à trois chiffres pour chaque emplacement.  La valeur principale est le nom long du pays.  
  
-   **Pays/région (valeur principale de trois lettres)**: contient le nom long conventionnel (nom officiel tel que désigné par le pays/région) et nom court (nom commun utilisé dans les listes, cartes, etc.), abréviation à deux lettres, abréviation à trois lettres et code à trois chiffres pour chaque emplacement.  Les valeurs principales sont l'abréviation de trois lettres pour Compté.  
  
-   **Pays/région (valeur principale de deux lettres)**: contient le nom long conventionnel (nom officiel tel que désigné par le pays/région) et nom court (nom commun utilisé dans les listes, sur des cartes, etc.), abréviation à deux lettres, abréviation à trois lettres et code à trois chiffres pour chaque emplacement.  La valeur principale est l'abréviation de deux lettres pour Pays.  
  
-   **États-Unis - comtés**: contient une liste des comtés américains.  
  
-   **États-Unis - nom**: contient une liste de noms (noms de famille) survenant 100 fois ou plus dans le recensement 2000.  
  
-   **États-Unis - emplacements**: contient une liste des emplacements des 50 états, le District de Columbia et Porto Rico, extrait du recensement 2010.  
  
-   **États-Unis - état**: contient le nom long conventionnel (officiel) nom et l’abréviation à deux lettres pour chaque état des États-Unis. La valeur principale est le nom conventionnel de l'État.  
  
-   **États-Unis-état (n° 2 lettres)**: contient le nom long conventionnel (officiel) nom et l’abréviation à deux lettres pour chaque état des États-Unis. La valeur principale est l'abréviation de deux lettres pour le nom de l'État.  
  
## Utilisation de la base de connaissances par défaut  
 Vous pouvez utiliser la base de connaissances par défaut, Données DQS, comme suit :  
  
-   Démarrez et exécutez rapidement un projet de nettoyage de qualité des données à l'aide de la base de connaissances par défaut sans devoir créer d'abord une nouvelle base de connaissances dans DQS.  
  
-   Exécutez les activités de gestion du domaine, de découverte des connaissances ou de stratégie de correspondance sur la base de connaissances par défaut. Pour cela, cliquez sur **Ouvrir la base de connaissances** dans [Data Quality Client Home Screen](../data-quality-services/data-quality-client-home-screen.md), sélectionnez la base de connaissances **Données de DQS** dans l'écran **Ouvrir la base de connaissances** , puis sélectionnez l'activité requise dans la zone **Sélectionner une activité** . Cliquez sur **Suivant** pour continuer.  
  
-   Créez une nouvelle base de connaissances à l'aide de la base de connaissances par défaut. Pour créer une base de connaissances à partir d'une base de connaissances existante, consultez [Create a Knowledge Base](../data-quality-services/create-a-knowledge-base.md).  
  
-   Utilisez-la dans le [composant de nettoyage DQS dans Integration Services](http://go.microsoft.com/fwlink/?LinkId=238830) et [complément Master Data Services pour Excel](../master-data-services/microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md).  
  
## Voir aussi  
 [Bases de connaissances et domaines DQS](../data-quality-services/dqs-knowledge-bases-and-domains.md)  
  
  