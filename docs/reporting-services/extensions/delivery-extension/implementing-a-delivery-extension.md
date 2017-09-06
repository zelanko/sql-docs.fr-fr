---
title: "Implémentation d’une Extension de remise | Documents Microsoft"
ms.custom: 
ms.date: 03/16/2017
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
- delivery [Reporting Services]
- custom delivery extensions [Reporting Services]
- extensions [Reporting Services], delivery
- delivery extensions [Reporting Services]
ms.assetid: 600cd229-efcd-480e-8c95-3c3c39ff4e7a
caps.latest.revision: 32
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 5db9bf52437c018bc1dcb40e7fa8a8ce2824fa12
ms.contentlocale: fr-fr
ms.lasthandoff: 08/12/2017

---
# <a name="implementing-a-delivery-extension"></a>Implémentation d'une extension de remise
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] permet aux utilisateurs de créer et publier des rapports qui, une fois créés et publiés, peuvent être remis à différents emplacements. De plus, [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] inclut plusieurs extensions de remise et une API de remise qui permettent aux développeurs de créer des extensions de remise supplémentaires pour étendre les fonctionnalités de remise proposées dans [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
 Pour un exemple d’implémentation d’une extension de remise, consultez [SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Vue d’ensemble des Extensions de remise](../../../reporting-services/extensions/delivery-extension/delivery-extensions-overview.md)  
 Explique comment écrire une extension de remise personnalisée pour [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
 [Préparation à l’implémentation d’une Extension de remise](../../../reporting-services/extensions/delivery-extension/preparing-to-implement-a-delivery-extension.md)  
 Décrit les interfaces et les classes disponibles lors de l'implémentation d'une extension de remise [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], ainsi que les problèmes à prendre en considération avant l'implémentation.  
  
 [Création d’une bibliothèque d’Extension de remise](../../../reporting-services/extensions/delivery-extension/creating-a-delivery-extension-library.md)  
 Décrit comment assigner un espace de noms à votre extension de remise [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] et comment compiler votre extension de remise dans une DLL de bibliothèque.  
  
 [Implémentation de l’Interface IDeliveryExtension pour une Extension de remise](../../../reporting-services/extensions/delivery-extension/implementing-the-ideliveryextension-interface-for-a-delivery-extension.md)  
 Décrit les attributs d'une extension de remise et comment implémenter votre propre classe d'extension de remise.  
  
 [À l’aide d’une classe de Notification pour une Extension de remise](../../../reporting-services/extensions/delivery-extension/using-a-notification-class-for-a-delivery-extension.md)  
 Décrit les attributs d’un **Notification** classe et comment l’utiliser dans votre implémentation d’extension de remise.  
  
 [À l’aide de la classe de paramètre pour une Extension de remise](../../../reporting-services/extensions/delivery-extension/using-the-setting-class-for-a-delivery-extension.md)  
 Décrit les attributs d’un **paramètre** classe et comment l’utiliser dans votre implémentation d’extension de remise.  
  
 [À l’aide de l’Interface IDeliveryReportServerInformation pour une Extension de remise](../../../reporting-services/extensions/delivery-extension/using-the-ideliveryreportserverinformation-interface-for-a-delivery-extension.md)  
 Décrit les attributs d’un **IDeliveryReportServerInformation** interface et comment l’utiliser dans votre implémentation d’extension de remise.  
  
 [À l’aide de la classe de rapport pour une Extension de remise](../../../reporting-services/extensions/delivery-extension/using-the-report-class-for-a-delivery-extension.md)  
 Décrit les attributs d’un **rapport** classe et comment l’utiliser dans votre implémentation d’extension de remise.  
  
 [À l’aide de la classe RenderedOutputFile pour une Extension de remise](../../../reporting-services/extensions/delivery-extension/using-the-renderedoutputfile-class-for-a-delivery-extension.md)  
 Décrit les attributs d’un **RenderedOutputFile** classe et comment l’utiliser dans votre implémentation d’extension de remise.  
  
 [Implémentation de l’Interface ISubscriptionBaseUIUserControl pour une Extension de remise](../../../reporting-services/extensions/delivery-extension/implementing-the-isubscriptionbaseuiusercontrol-interface.md)  
 Décrit les attributs d'un contrôle utilisateur d'extension de remise et comment implémenter votre propre interface utilisateur pour un abonnement.  
  
 [Déploiement d’une Extension de remise](../../../reporting-services/extensions/delivery-extension/deploying-a-delivery-extension.md)  
 Décrit comment déployer votre extension de remise.  
  
 [Débogage du Code d’Extension de remise](../../../reporting-services/extensions/delivery-extension/debugging-delivery-extension-code.md)  
 Décrit comment déboguer le code dans votre extension de remise.  
  
 [Suppression d’une Extension de remise](../../../reporting-services/extensions/delivery-extension/removing-a-delivery-extension.md)  
 Décrit comment supprimer une extension de remise d'un serveur de rapports.  
  
## <a name="see-also"></a>Voir aussi  
 [Extensions Reporting Services](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Bibliothèque d’Extension de Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
