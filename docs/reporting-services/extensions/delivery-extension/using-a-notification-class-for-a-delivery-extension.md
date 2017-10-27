---
title: "À l’aide d’une classe de Notification pour une Extension de remise | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
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
- delivery extensions [Reporting Services], notifications
- notifications [Reporting Services]
- retry queues
- Nofication class
ms.assetid: 549c40c4-d33d-46c2-9d6a-7bbb671ac67a
caps.latest.revision: 33
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 064d5556dca130324f69dd49d14f3caa76c8eec8
ms.contentlocale: fr-fr
ms.lasthandoff: 08/12/2017

---
# <a name="using-a-notification-class-for-a-delivery-extension"></a>Utilisation d'une classe Notification pour une extension de remise
  La classe <xref:Microsoft.ReportingServices.Interfaces.Notification> se trouve dans l'espace de noms <xref:Microsoft.ReportingServices.Interfaces> et représente les informations d'abonnement utilisées par les extensions de remise pour la remise de rapports. La classe <xref:Microsoft.ReportingServices.Interfaces.Notification> propose différentes propriétés qui peuvent être utilisées pour effectuer le rendu des rapports à remettre, déterminer l'état de la notification et définir les données utilisateur.  
  
 ![Processus de notification de rapport](../../../reporting-services/extensions/delivery-extension/media/bk-ext-03.gif "signalent les processus de notification")  
La notification est l'objet central de toute remise.  
  
 Lorsqu'un événement associé à un abonnement qui utilise votre extension de remise personnalisée est déclenché, une notification contenant un objet <xref:Microsoft.ReportingServices.Interfaces.Report> est créée. L'objet <xref:Microsoft.ReportingServices.Interfaces.Report> regroupe les fonctionnalités nécessaires pour effectuer le rendu d'un rapport donné dans un format de rendu pris en charge, et contient des propriétés spécifiques au rapport, telles que l'URL d'accès au rapport sur le serveur et le nom du rapport. Pour plus d’informations sur la <xref:Microsoft.ReportingServices.Interfaces.Report> de classe, consultez [à l’aide de la classe de rapport pour une Extension de remise](../../../reporting-services/extensions/delivery-extension/using-the-report-class-for-a-delivery-extension.md).  
  
 L'objet <xref:Microsoft.ReportingServices.Interfaces.Notification> est passé à la méthode <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.Deliver%2A> de votre extension de remise. Votre méthode <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.Deliver%2A> doit contenir du code spécifique pour traiter la notification et remettre le rapport.  
  
 Pour obtenir un exemple montrant comment utiliser les <xref:Microsoft.ReportingServices.Interfaces.Notification> de classe, consultez [SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="retry-functionality"></a>Fonctionnalité relative aux nouvelles tentatives de remise  
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] vous permet de créer une file d'attente de nouvelles tentatives pour les notifications qui ne peuvent pas être remises immédiatement. Une fois que le serveur de rapports a appelé la méthode <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.Deliver%2A> d'une extension de remise, cette extension peut demander que le serveur de rapports effectue une nouvelle tentative de remise à un moment ultérieur. Si cela se produit, le serveur de rapports place la notification dans une file d'attente interne et effectue une nouvelle tentative de remise à l'issue d'un certain délai. Les administrateurs peuvent configurer le nombre maximal de tentatives que le serveur de rapports effectue et la période entre les nouvelles tentatives dans la section d’extension de remise du fichier RSReportServer.config en utilisant le **MaxNumberOfRetries** (élément XML) et le **PeriodBetweenRetries** élément XML. Les notifications sont supprimées de la file d'attente des nouvelles tentatives si la remise réussit ultérieurement ou si le nombre maximal de nouvelles tentatives est atteint. Si la remise échoue après le nombre maximal de nouvelles tentatives, la notification est ignorée.  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation d’une Extension de remise](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Bibliothèque d’Extension de Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  

