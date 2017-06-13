---
title: "Intégration de Reporting Services dans des Applications | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
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
helpviewer_keywords:
- integrating reports [Reporting Services]
- custom applications [SSRS]
- Reporting Services, application integration
- application integration [Reporting Services]
- reports [Reporting Services], integrating
ms.assetid: 49eb539c-d89b-4291-839a-0ec1a65cd270
caps.latest.revision: 57
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 8a1cabc088c7c0ec6c69c8290549e035a4cec7bb
ms.contentlocale: fr-fr
ms.lasthandoff: 06/13/2017

---
# <a name="integrating-reporting-services-into-applications"></a>Intégration de Reporting Services dans les applications
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] est une plate-forme de création de rapports ouverte et extensible conçue pour fournir aux développeurs un jeu complet d'API  pour développer des solutions.  
  
 Il existe trois options pour l’intégration [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dans des applications personnalisées : service Web Report Server, également appelé le [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] API SOAP, les contrôles ReportViewer pour [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)]et l’accès URL. Chaque option représente une approche différente de l'intégration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dans vos applications.  
  
## <a name="report-server-web-service"></a>service Web Report Server  
 Le service Web Report Server constitue la principale interface de développement avec [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Que vous développiez du code pour gérer votre catalogue de rapports ou pour effectuer le rendu de rapports dans un format pris en charge, le service Web propose toutes les méthodes nécessaires pour intégrer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dans vos applications. Un exemple d’une telle application est le Gestionnaire de rapports, qui est inclus avec [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]; il utilise le service Web pour gérer la base de données du serveur de rapports.  
  
## <a name="reportviewer-controls-for-visual-studio"></a>Contrôles ReportViewer pour Visual Studio  
 Les contrôles ReportViewer inclus dans [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] sont utilisés pour intégrer la consultation de rapports dans vos applications. Il existe deux contrôles : un pour les applications Windows Forms et un autre pour les applications Web Forms. Chaque contrôle propose une fonctionnalité de consultation des rapports qui ont été déployés sur un serveur de rapports et permet d'effectuer le rendu de rapports dans un environnement où un aucun serveur de rapports n'est installé.  
  
## <a name="url-access"></a>Accès URL  
 L'accès URL est une autre option d'intégration de la consultation de rapports dans vos applications si les contrôles ReportViewer ne sont pas proposés en option. Par ailleurs, l'accès URL est utile pour envoyer aux utilisateurs des liens vers des rapports par courrier électronique.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Intégration de Reporting Services à l’aide de SOAP](../../reporting-services/application-integration/integrating-reporting-services-using-soap.md)  
 Décrit comment intégrer la navigation et la gestion des rapports [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dans vos applications de gestion existantes à l'aide du service Web Report Server.  
  
 [Intégration de Reporting Services à l’aide de contrôles ReportViewer](../../reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls.md)  
 Décrit comment intégrer la consultation de rapports dans vos applications existantes à l'aide de contrôles ReportViewer.  
  
 [Intégration de Reporting Services à l’aide de l’accès URL](../../reporting-services/application-integration/integrating-reporting-services-using-url-access.md)  
 Décrit comment intégrer la navigation entre les rapports [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dans vos applications de gestion existantes à l'aide de l'accès URL.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestionnaire de rapports &#40;SSRS en mode natif&#41;](http://msdn.microsoft.com/library/80949f9d-58f5-48e3-9342-9e9bf4e57896)   
 [Choix entre l’accès URL et SOAP](../../reporting-services/application-integration/choosing-between-url-access-and-soap.md)   
 [Informations techniques de référence &#40;SSRS&#41;](../../reporting-services/technical-reference-ssrs.md)   
 [Service Web Report Server](../../reporting-services/report-server-web-service/report-server-web-service.md)  
  
  
