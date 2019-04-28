---
title: Utilisation de la base de connaissances par défaut DQS | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: b36af13b-9fcc-4168-bb92-214d600b1c93
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 40a69447a0aff678cfd53a75603200b467a542c7
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62791731"
---
# <a name="using-the-dqs-default-knowledge-base"></a>Utilisation de la base de connaissances par défaut DQS
  Cette rubrique décrit la base de connaissances par défaut, **DQS Data**, qui est installée avec [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS). Il s'agit d'une base de connaissances par défaut prégénérée qui contient les domaines suivants :  
  
-   **Pays/région** : contient le nom long conventionnel (nom officiel tel que désigné par le pays/la région) et le nom court (nom commun utilisé dans les listes, sur les cartes, etc.), une abréviation à deux lettres, une abréviation à trois lettres et le code à trois chiffres pour chaque lieu.  La valeur principale est le nom long du pays.  
  
-   **Pays/région (commençant par trois lettres)**  : contient le nom long conventionnel (nom officiel tel que désigné par le pays/la région) et le nom court (nom commun utilisé dans les listes, sur les cartes, etc.), une abréviation à deux lettres, une abréviation à trois lettres et le code à trois chiffres pour chaque lieu.  Les valeurs principales sont l'abréviation de trois lettres pour Compté.  
  
-   **Pays/région (commençant par deux lettres)**  : contient le nom long conventionnel (nom officiel tel que désigné par le pays/la région) et le nom court (nom commun utilisé dans les listes, sur les cartes, etc.), une abréviation à deux lettres, une abréviation à trois lettres et le code à trois chiffres pour chaque lieu.  La valeur principale est l'abréviation de deux lettres pour Pays.  
  
-   **États-Unis - Comtés** : contient la liste des comtés des États-Unis.  
  
-   **États-Unis - Nom** : contient la liste des noms (de famille) présentant au moins 100 occurrences dans le recensement de 2000.  
  
-   **États-Unis - Emplacements** : contient la liste des emplacements des 50 États, du District de Columbia et de Porto Rico, tirée du recensement de 2010.  
  
-   **États-Unis - État** : contient le nom long conventionnel (officiel) et l’abréviation à deux lettres de chaque État des États-Unis. La valeur principale est le nom conventionnel de l'État.  
  
-   **États-Unis - État (en-tête à deux lettres)**  : contient le nom long conventionnel (officiel) et l’abréviation à deux lettres de chaque État des États-Unis. La valeur principale est l'abréviation de deux lettres pour le nom de l'État.  
  
## <a name="using-the-default-knowledge-base"></a>Utilisation de la base de connaissances par défaut  
 Vous pouvez utiliser la base de connaissances par défaut, Données DQS, comme suit :  
  
-   Démarrez et exécutez rapidement un projet de nettoyage de qualité des données à l'aide de la base de connaissances par défaut sans devoir créer d'abord une nouvelle base de connaissances dans DQS.  
  
-   Exécutez les activités de gestion du domaine, de découverte des connaissances ou de stratégie de correspondance sur la base de connaissances par défaut. Pour cela, cliquez sur **Ouvrir la base de connaissances** dans [Data Quality Client Home Screen](../../2014/data-quality-services/data-quality-client-home-screen.md), sélectionnez la base de connaissances **Données de DQS** dans l'écran **Ouvrir la base de connaissances** , puis sélectionnez l'activité requise dans la zone **Sélectionner une activité** . Cliquez sur **Suivant** pour continuer.  
  
-   Créez une nouvelle base de connaissances à l'aide de la base de connaissances par défaut. Pour créer une base de connaissances à partir d'une base de connaissances existante, consultez [Create a Knowledge Base](../../2014/data-quality-services/create-a-knowledge-base.md).  
  
-   Utilisez-la dans le [composant de nettoyage DQS de Integration Services](https://go.microsoft.com/fwlink/?LinkId=238830) et le [complément Master Data Services pour Excel](../master-data-services/microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Bases de connaissances et domaines DQS](../../2014/data-quality-services/dqs-knowledge-bases-and-domains.md)  
  
  
