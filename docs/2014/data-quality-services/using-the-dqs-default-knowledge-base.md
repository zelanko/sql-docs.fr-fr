---
title: Utilisation de la base de connaissances par défaut DQS | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: b36af13b-9fcc-4168-bb92-214d600b1c93
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ae4688108f7e0d2bf045581b7afe50235c7ff012
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53368263"
---
# <a name="using-the-dqs-default-knowledge-base"></a>Utilisation de la base de connaissances par défaut DQS
  Cette rubrique décrit la base de connaissances par défaut, **DQS Data**, qui est installée avec [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS). Il s'agit d'une base de connaissances par défaut prégénérée qui contient les domaines suivants :  
  
-   **Pays/région**: Contient le nom long conventionnel (nom officiel tel que désigné par le pays/région) et nom court (nom commun utilisé dans les listes, sur les cartes, etc.), abréviation à deux lettres, abréviation à trois lettres et code de trois chiffres pour chaque emplacement.  La valeur principale est le nom long du pays.  
  
-   **Pays/région (valeur principale de trois lettres)**: Contient le nom long conventionnel (nom officiel tel que désigné par le pays/région) et nom court (nom commun utilisé dans les listes, sur des cartes et ainsi de suite), abréviation à deux lettres, abréviation à trois lettres et code de trois chiffres pour chaque emplacement.  Les valeurs principales sont l'abréviation de trois lettres pour Compté.  
  
-   **Pays/région (valeur principale de deux lettres)**: Contient le nom long conventionnel (nom officiel tel que désigné par le pays/région) et nom court (nom commun utilisé dans les listes, sur les cartes, etc.), abréviation à deux lettres, abréviation à trois lettres et code de trois chiffres pour chaque emplacement.  La valeur principale est l'abréviation de deux lettres pour Pays.  
  
-   **États-Unis - comtés**: Contient une liste des comtés américains.  
  
-   **États-Unis - nom de la dernière**: Contient une liste des noms de famille () survenant 100 fois ou plus dans le recensement 2000.  
  
-   **États-Unis - emplacements**: Contient une liste des emplacements des 50 états, le District de Columbia et Porto Rico, extrait du recensement 2010.  
  
-   **États-Unis - état**: Contient le nom long conventionnel (officiel) nom et l’abréviation à deux lettres pour chaque état des États-Unis. La valeur principale est le nom conventionnel de l'État.  
  
-   **États-Unis - état (2-en-tête)**: Contient le nom long conventionnel (officiel) nom et l’abréviation à deux lettres pour chaque état des États-Unis. La valeur principale est l'abréviation de deux lettres pour le nom de l'État.  
  
## <a name="using-the-default-knowledge-base"></a>Utilisation de la base de connaissances par défaut  
 Vous pouvez utiliser la base de connaissances par défaut, Données DQS, comme suit :  
  
-   Démarrez et exécutez rapidement un projet de nettoyage de qualité des données à l'aide de la base de connaissances par défaut sans devoir créer d'abord une nouvelle base de connaissances dans DQS.  
  
-   Exécutez les activités de gestion du domaine, de découverte des connaissances ou de stratégie de correspondance sur la base de connaissances par défaut. Pour cela, cliquez sur **Ouvrir la base de connaissances** dans [Data Quality Client Home Screen](../../2014/data-quality-services/data-quality-client-home-screen.md), sélectionnez la base de connaissances **Données de DQS** dans l'écran **Ouvrir la base de connaissances** , puis sélectionnez l'activité requise dans la zone **Sélectionner une activité** . Cliquez sur **Suivant** pour continuer.  
  
-   Créez une nouvelle base de connaissances à l'aide de la base de connaissances par défaut. Pour créer une base de connaissances à partir d'une base de connaissances existante, consultez [Create a Knowledge Base](../../2014/data-quality-services/create-a-knowledge-base.md).  
  
-   Utilisez-la dans le [composant de nettoyage DQS de Integration Services](https://go.microsoft.com/fwlink/?LinkId=238830) et le [complément Master Data Services pour Excel](../master-data-services/microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Bases de connaissances et domaines DQS](../../2014/data-quality-services/dqs-knowledge-bases-and-domains.md)  
  
  
