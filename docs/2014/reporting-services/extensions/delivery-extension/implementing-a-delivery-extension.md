---
title: Implémentation d’une extension de remise | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- delivery [Reporting Services]
- custom delivery extensions [Reporting Services]
- extensions [Reporting Services], delivery
- delivery extensions [Reporting Services]
ms.assetid: 600cd229-efcd-480e-8c95-3c3c39ff4e7a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cae33496e4dddcaf2d14ba2d87f0d4013795e58f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63165130"
---
# <a name="implementing-a-delivery-extension"></a>Implémentation d'une extension de remise
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] permet aux utilisateurs de créer et de publier des rapports qui, une fois créés et publiés, peuvent être remis à différents emplacements. De plus, [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] inclut plusieurs extensions de remise et une API de remise qui permettent aux développeurs de créer des extensions de remise supplémentaires pour étendre les fonctionnalités de remise proposées dans [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
 Pour un exemple d’implémentation d’extension de remise, consultez [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889) (Exemples Reporting Services pour le produit SQL Server).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Présentation des extensions de remise] Delivery-extensions-overview.md)  
 Explique comment écrire une extension de remise personnalisée pour [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
 [Préparation à l'implémentation d'une extension de remise](preparing-to-implement-a-delivery-extension.md)  
 Décrit les interfaces et les classes disponibles lors de l'implémentation d'une extension de remise [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], ainsi que les problèmes à prendre en considération avant l'implémentation.  
  
 [Création d'une bibliothèque d'extensions de remise](creating-a-delivery-extension-library.md)  
 Décrit comment assigner un espace de noms à votre extension de remise [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] et comment compiler votre extension de remise dans une DLL de bibliothèque.  
  
 [Implémentation de l'interface IDeliveryExtension pour une extension de remise](implementing-the-ideliveryextension-interface-for-a-delivery-extension.md)  
 Décrit les attributs d'une extension de remise et comment implémenter votre propre classe d'extension de remise.  
  
 [Utilisation d'une classe Notification pour une extension de remise](using-a-notification-class-for-a-delivery-extension.md)  
 Décrit les attributs d’une classe **Notification** et comment l’utiliser dans l’implémentation de votre extension de remise.  
  
 [Utilisation de la classe Setting pour une extension de remise](using-the-setting-class-for-a-delivery-extension.md)  
 Décrit les attributs d’une classe **Setting** et comment l’utiliser dans l’implémentation de votre extension de remise.  
  
 [Utilisation de l'interface IDeliveryReportServerInformation pour une extension de remise](using-the-ideliveryreportserverinformation-interface-for-a-delivery-extension.md)  
 Décrit les attributs d’une interface **IDeliveryReportServerInformation** et comment l’utiliser dans l’implémentation de votre extension de remise.  
  
 [Utilisation de la classe Report pour une extension de remise](using-the-report-class-for-a-delivery-extension.md)  
 Décrit les attributs d’une classe **Report** et comment l’utiliser dans l’implémentation de votre extension de remise.  
  
 [Utilisation de la classe RenderedOutputFile pour une extension de remise](using-the-renderedoutputfile-class-for-a-delivery-extension.md)  
 Décrit les attributs d’une classe **RenderedOutputFile** et comment l’utiliser dans l’implémentation de votre extension de remise.  
  
 [Implémentation de l'interface ISubscriptionBaseUIUserControl pour une extension de remise](implementing-the-isubscriptionbaseuiusercontrol-interface.md)  
 Décrit les attributs d'un contrôle utilisateur d'extension de remise et comment implémenter votre propre interface utilisateur pour un abonnement.  
  
 [Déploiement d'une extension de remise](deploying-a-delivery-extension.md)  
 Décrit comment déployer votre extension de remise.  
  
 [Débogage du code d'extension de remise](debugging-delivery-extension-code.md)  
 Décrit comment déboguer le code dans votre extension de remise.  
  
 [Suppression d'une extension de remise](removing-a-delivery-extension.md)  
 Décrit comment supprimer une extension de remise d'un serveur de rapports.  
  
## <a name="see-also"></a>Voir aussi  
 [Extensions Reporting Services](../reporting-services-extensions.md)   
 [Bibliothèque d'extensions Reporting Services](../reporting-services-extension-library.md)  
  
  
