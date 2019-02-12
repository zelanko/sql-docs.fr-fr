---
title: Créer un abonnement piloté par les données (didacticiel SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [Reporting Services], tutorials
- walkthroughs [Reporting Services]
- data-driven subscriptions
ms.assetid: 79ab0572-43e9-4dc4-9b5a-cd8b627b8274
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: f4122aa579766d80cfac6600753d4a8f8a672ae9
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56017911"
---
# <a name="create-a-data-driven-subscription-ssrs-tutorial"></a>Créer un abonnement piloté par les données (didacticiel SSRS)
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] fournit des abonnements pilotés par les données qui permettent de personnaliser la distribution d'un rapport basé sur des données d'abonnés dynamiques. Les abonnements pilotés par les données s'utilisent dans les types de scénarios suivants :  
  
-   Distribution de rapports à un large ensemble de destinataires dont les membres peuvent changer d'une distribution à l'autre. Par exemple, distribution d'un rapport mensuel à l'ensemble des clients actuels.  
  
-   Distribution de rapports à un groupe spécifique de destinataires sur la base de critères prédéfinis. Par exemple, envoi d'un rapport sur les résultats des ventes aux dix premiers directeurs commerciaux d'une organisation.  
  
## <a name="what-you-will-learn"></a>Contenu du didacticiel  
 Ce didacticiel explique comment utiliser les abonnements pilotés par les données à l'aide d'un exemple simple qui illustre les concepts de base.  
  
 Ce didacticiel est divisé en trois leçons :  
  
 [Leçon 1 : Création d’une base de données exemple abonné](lesson-1-creating-a-sample-subscriber-database.md)  
 Au cours de cette leçon, vous allez apprendre à créer une base de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] locale qui contient des informations sur les abonnés.  
  
 [Leçon 2 : Modification des propriétés d’une source de données de rapport](lesson-2-modifying-the-report-data-source-properties.md).  
 Dans cette leçon, vous allez apprendre à modifier les propriétés d'une source de données afin que le rapport puisse s'exécuter sans assistance. Les informations d'identification stockées sont nécessaires pour le traitement autonome. Vous allez également modifier le dataset du rapport afin d'inclure un paramètre fourni par les données d'abonné.  
  
 [Leçon 3 : Définition d’un abonnement piloté par les données](lesson-3-defining-a-data-driven-subscription.md)  
 Dans cette leçon, vous allez apprendre à définir un abonnement piloté par les données. Cette leçon vous guide à travers chaque page de l'Assistant Abonnement piloté par les données.  
  
## <a name="requirements"></a>Configuration requise  
 Les abonnements pilotés par les données sont généralement créés par un administrateur de serveur de rapports, qui en assure également la mise à jour. Pour créer des abonnements pilotés par les données, il est nécessaire de savoir créer des requêtes, de connaître les sources de données qui contiennent les données d'abonnés et de disposer d'autorisations élevées sur le serveur de rapports.  
  
 Ce didacticiel utilise le rapport créé dans le didacticiel [créer un rapport de tableau de base &#40;SSRS didacticiel&#41; ](create-a-basic-table-report-ssrs-tutorial.md) et les données à partir de [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]  
  
 Les éléments suivants doivent cependant être installés sur votre système :  
  
-   Une édition de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] qui prend en charge les abonnements pilotés par les données. Pour plus d’informations, consultez [éditions et composants de SQL Server 2014](../sql-server/editions-and-components-of-sql-server-2016.md).  
  
-   Le serveur de rapports doit être exécuté en mode natif. L'interface utilisateur décrite dans ce didacticiel est basée sur un serveur de rapports en mode natif. Les abonnements sont pris en charge sur les serveurs de rapports en mode SharePoint, mais l'interface utilisateur sera différente de ce qui est décrit dans ce didacticiel.  
  
-   Le service Agent SQL Server doit être en cours d'exécution.  
  
-   Rapport contenant des paramètres. Ce didacticiel suppose l’utilisation de l’exemple de rapport `Sales Orders` que vous créez à l’aide du didacticiel [Créer un rapport de tableau de base &#40;didacticiel SSRS&#41;](create-a-basic-table-report-ssrs-tutorial.md).  
  
-   Exemple de base de données [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] contenant des données sur le rapport fourni en exemple.  
  
-   Attribution de rôle incluant la tâche Gérer tous les abonnements dans le rapport fourni en exemple. Cette tâche est obligatoire dans la définition des abonnements pilotés par les données. Si vous êtes l'administrateur de l'ordinateur, l'attribution de rôle par défaut pour les administrateurs locaux fournit les autorisations nécessaires à la création d'abonnements pilotés par les données. Pour plus d’informations, consultez [Octroi d'autorisations sur un serveur de rapports en mode natif](security/granting-permissions-on-a-native-mode-report-server.md).  
  
-   Dossier partagé pour lequel vous bénéficiez de droits d'accès en écriture. Le dossier partagé doit être accessible via une connexion réseau.  
  
 **Durée estimée pour effectuer le tutoriel :** 30 minutes. Trente minutes supplémentaires si vous n'avez pas étudié le didacticiel de création d'un rapport de base.  
  
## <a name="see-also"></a>Voir aussi  
 [Data-Driven Subscriptions](subscriptions/data-driven-subscriptions.md)   
 [Créer un rapport de tableau de base &#40;Didacticiel SSRS&#41;](create-a-basic-table-report-ssrs-tutorial.md)  
  
  
