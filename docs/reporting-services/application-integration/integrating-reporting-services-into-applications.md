---
title: "Intégration de Reporting Services dans des Applications | Documents Microsoft"
ms.custom: 
ms.date: 10/19/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: e20b96e38f798c19a74d5f3a32a25e429dc8ebeb
ms.openlocfilehash: 26e1da5a720aab965d014cada16f85086e0f70a0
ms.contentlocale: fr-fr
ms.lasthandoff: 10/20/2017

---
# <a name="integrating-reporting-services-into-applications"></a>Intégration de Reporting Services dans les applications

[!INCLUDE [ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-not-2017](../../includes/ssrs-appliesto-not-2017.md)] [!INCLUDE [ssrs-appliesto-not-pbirs](../../includes/ssrs-appliesto-not-pbirs.md)])

  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] est une plate-forme de création de rapports ouverte et extensible conçue pour fournir aux développeurs un jeu complet d'API  pour développer des solutions.

> [!NOTE]
> À partir de SQL Server 2017 Reporting Services, accès de l’API REST est disponible pour le développement de solutions. Accès de l’API SOAP a été déconseillée. Pour plus d’informations, consultez [développer avec les API REST pour Reporting Services](../developer/rest-api.md).
  
 Il existe trois options pour l’intégration [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dans des applications personnalisées : service Web Report Server, également appelé le [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] API SOAP, les contrôles ReportViewer pour [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]et l’accès URL. Chaque option représente une approche différente de l'intégration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dans vos applications.
  
## <a name="report-server-web-service"></a>Service web Report Server

 Le service Web Report Server constitue la principale interface de développement avec [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Que vous développiez du code pour gérer votre catalogue de rapports ou pour effectuer le rendu de rapports dans un format pris en charge, le service Web propose toutes les méthodes nécessaires pour intégrer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dans vos applications. Un exemple d’une telle application est le Gestionnaire de rapports, qui est inclus avec [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]; il utilise le service Web pour gérer la base de données du serveur de rapports.  
  
## <a name="reportviewer-controls-for-visual-studio"></a>Contrôles ReportViewer pour Visual Studio

 Les contrôles ReportViewer disponibles pour [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] sont utilisés pour intégrer la consultation de rapports dans vos applications. Il existe deux contrôles : un pour les applications Windows Forms et un autre pour les applications Web Forms. Chaque contrôle propose une fonctionnalité de consultation des rapports qui ont été déployés sur un serveur de rapports et permet d'effectuer le rendu de rapports dans un environnement où un aucun serveur de rapports n'est installé.  
  
## <a name="url-access"></a>accès URL  
 L'accès URL est une autre option d'intégration de la consultation de rapports dans vos applications si les contrôles ReportViewer ne sont pas proposés en option. Par ailleurs, l'accès URL est utile pour envoyer aux utilisateurs des liens vers des rapports par courrier électronique.  
  
## <a name="in-this-section"></a>Contenu de cette section

 [Intégration de Reporting Services à l'aide de SOAP](../../reporting-services/application-integration/integrating-reporting-services-using-soap.md)  
 Décrit comment intégrer la navigation et la gestion des rapports [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dans vos applications de gestion existantes à l'aide du service Web Report Server.  
  
 [Intégration de Reporting Services à l’aide de contrôles ReportViewer](../../reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls.md)  
 Décrit comment intégrer la consultation de rapports dans vos applications existantes à l'aide de contrôles ReportViewer.  
  
 [Intégration de Reporting Services à l'aide de l'accès URL](../../reporting-services/application-integration/integrating-reporting-services-using-url-access.md)  
 Décrit comment intégrer la navigation entre les rapports [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dans vos applications de gestion existantes à l'aide de l'accès URL.  
  
## <a name="next-steps"></a>Étapes suivantes

Pour choisir à l’aide de l’accès URL ou l’API SOAP, consultez [choix entre l’accès URL et SOAP dans Reporting Services](choosing-between-url-access-and-soap.md).

Pour plus d’informations sur le REST API des Services de création de rapports 2017 SQL Server, consultez [développer avec les API REST pour Reporting Services](../developer/rest-api.md).

D’autres questions ? [Essayez de poser une question dans le forum Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)

