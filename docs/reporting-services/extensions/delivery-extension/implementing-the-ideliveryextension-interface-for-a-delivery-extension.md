---
title: "Implémentation de l’Interface IDeliveryExtension pour une Extension de remise | Documents Microsoft"
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
- delivery extensions [Reporting Services], attributes
- delivery extensions [Reporting Services], class creation
- IDeliveryExtension interface
ms.assetid: ab0344db-510b-403f-8dbf-b9831553765d
caps.latest.revision: 37
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: ac54345b14ba3ff84a755e0ce4e8b1c4e9acab13
ms.contentlocale: fr-fr
ms.lasthandoff: 08/12/2017

---
# <a name="implementing-the-ideliveryextension-interface-for-a-delivery-extension"></a>Implémentation de l'interface IDeliveryExtension pour une extension de remise
  Votre classe d'extension de remise sert à remettre des notifications de rapport aux utilisateurs selon le contenu des notifications. La classe d'extension de remise fournit également l'infrastructure pour valider des paramètres utilisateurs passés à l'extension de remise. De plus, votre classe d'extension de remise doit contenir des propriétés spécifiques que les clients peuvent utiliser pour obtenir des informations sur le nom de l'extension, les paramètres pris en charge par l'extension, et les formats de rendu disponibles pour l'extension de remise.  
  
 ![Processus de l’interface IDeliveryExtension](../../../reporting-services/extensions/delivery-extension/media/bk-ext-02.gif "processus d’interface IDeliveryExtension")  
L'interface IDeliveryExtension autorise la validation des données utilisateur et permet aux clients de s'informer des paramètres de remise requis.  
  
 Pour créer une classe d'extension de remise, implémentez <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> et <xref:Microsoft.ReportingServices.Interfaces.IExtension>. Le **IDeliveryExtension** interface permet à votre extension de remise remettre des notifications de rapport à l’aide de la <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.Deliver%2A> (méthode) et de valider les paramètres d’extension entrants à l’aide de la <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ValidateUserData%2A> (méthode). Le **IExtension** interface permet à votre extension de remise pour implémenter un nom d’extension localisé et traiter les informations de configuration spécifiques à l’extension stockées dans le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fichier de configuration. En implémentant **IExtension**, votre extension de remise contient la <xref:Microsoft.ReportingServices.Interfaces.Extension.LocalizedName%2A> propriété. Il est fortement recommandé que [!INCLUDE[ssRS](../../../includes/ssrs-md.md)] prise en charge des extensions de remise la **LocalizedName** propriété, afin que les utilisateurs rencontrent un nom familier pour l’extension dans une interface utilisateur, tels que le Gestionnaire de rapports.  
  
 Votre extension de remise doit également implémenter le **ExtensionSettings** propriété de la **IDeliveryExtension** interface. Le serveur de rapports utilise la valeur retournée par la propriété <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ExtensionSettings%2A> pour évaluer les paramètres qu'une extension de remise requiert. Les clients qui interagissent avec les extensions de remise utilisent la méthode <xref:ReportService2010.ReportingService2010.GetExtensionSettings%2A> du service Web Report Server pour retourner une liste de paramètres pour l'extension de remise.  
  
 Vous pouvez également utiliser votre classe d'extension de remise pour extraire et traiter des données de configuration personnalisées stockées dans le fichier RSReportServer.config. Pour plus d'informations sur le traitement des données de configuration personnalisées, consultez la méthode <xref:Microsoft.ReportingServices.Interfaces.IExtension.SetConfiguration%2A>.  
  
 Pour obtenir un exemple **IDeliveryExtension** implémentation de la classe, consultez [SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation d’une Extension de remise](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Bibliothèque d’Extension de Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
