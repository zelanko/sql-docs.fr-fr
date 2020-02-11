---
title: Utilisation de la base de connaissances par défaut DQS
ms.custom: ''
ms.date: 07/31/2012
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: b36af13b-9fcc-4168-bb92-214d600b1c93
author: swinarko
ms.author: sawinark
ms.openlocfilehash: 2696a911edeefecc1dc34efeb77351acbaafc0d8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "75257746"
---
# <a name="using-the-dqs-default-knowledge-base"></a>Utilisation de la base de connaissances par défaut DQS

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Cette rubrique décrit la base de connaissances par défaut, **DQS Data**, qui est installée avec [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS). Il s'agit d'une base de connaissances par défaut prégénérée qui contient les domaines suivants :  
  
-   **Pays/région**: contient le nom long conventionnel (nom officiel tel que désigné par le pays/région) et les noms courts (nom commun utilisé dans les listes, sur les cartes, etc.), l’abréviation à deux lettres, l’abréviation à trois lettres et le code à trois chiffres pour chaque emplacement.  La valeur principale est le nom long du pays.  
  
-   **Pays/région (de début à trois lettres)**: contient le nom long conventionnel (nom officiel tel que désigné par le pays/région) et le nom court (nom commun utilisé dans les listes, sur les cartes, etc.), l’abréviation à deux lettres, l’abréviation à trois lettres et le code à trois chiffres pour chaque emplacement.  Les valeurs principales sont l'abréviation de trois lettres pour Compté.  
  
-   **Pays/région (début à deux lettres)**: contient le nom long conventionnel (nom officiel tel que désigné par le pays/région) et le nom court (nom commun utilisé dans les listes, sur les cartes, etc.), l’abréviation à deux lettres, l’abréviation à trois lettres et le code à trois chiffres pour chaque emplacement.  La valeur principale est l'abréviation de deux lettres pour Pays.  
  
-   **US-countings**: contient la liste des comtés américains.  
  
-   **US-Last Name**: contient une liste de noms (noms) qui se produisent 100 ou plusieurs fois dans le recensement 2000.  
  
-   **US-places**: contient la liste des emplacements des États 50, du district de Columbia et de Porto Rico extraits du recensement 2010.  
  
-   États- **Unis-État**: contient le nom long conventionnel (officiel) et l’abréviation à deux lettres de chaque État en France. La valeur principale est le nom conventionnel de l'État.  
  
-   États- **Unis-État (en-tête à 2 lettres)**: contient le nom long conventionnel (officiel) et l’abréviation à deux lettres de chaque État en France. La valeur principale est l'abréviation de deux lettres pour le nom de l'État.  
  
## <a name="using-the-default-knowledge-base"></a>Utilisation de la base de connaissances par défaut  
 Vous pouvez utiliser la base de connaissances par défaut, Données DQS, comme suit :  
  
-   Démarrez et exécutez rapidement un projet de nettoyage de qualité des données à l'aide de la base de connaissances par défaut sans devoir créer d'abord une nouvelle base de connaissances dans DQS.  
  
-   Exécutez les activités de gestion du domaine, de découverte des connaissances ou de stratégie de correspondance sur la base de connaissances par défaut. Pour cela, cliquez sur **Ouvrir la base de connaissances** dans [Data Quality Client Home Screen](../data-quality-services/data-quality-client-home-screen.md), sélectionnez la base de connaissances **Données de DQS** dans l'écran **Ouvrir la base de connaissances** , puis sélectionnez l'activité requise dans la zone **Sélectionner une activité** . Cliquez sur **Suivant** pour continuer.  
  
-   Créez une nouvelle base de connaissances à l'aide de la base de connaissances par défaut. Pour créer une base de connaissances à partir d'une base de connaissances existante, consultez [Create a Knowledge Base](../data-quality-services/create-a-knowledge-base.md).  
  
-   Utilisez-la dans le [composant de nettoyage DQS de Integration Services](https://go.microsoft.com/fwlink/?LinkId=238830) et le [complément Master Data Services pour Excel](../master-data-services/microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Bases de connaissances et domaines DQS](../data-quality-services/dqs-knowledge-bases-and-domains.md)  
  
  
