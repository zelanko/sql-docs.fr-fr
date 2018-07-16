---
title: Préparation pour la mise en œuvre d’une extension de remise | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- interfaces [Reporting Services]
- delivery extensions [Reporting Services], implementing
ms.assetid: aee1608d-374f-4ad3-bc23-fe07fdaa52b7
caps.latest.revision: 33
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: a6a93d48d1962800b4fba7598019561a83dcc5b0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37307389"
---
# <a name="preparing-to-implement-a-delivery-extension"></a>Préparation à l'implémentation d'une extension de remise
  Avant d'implémenter votre extension de remise [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], vous devez définir les interfaces à implémenter. Vous devez en premier décider de la manière dont votre extension de remise sera utilisée, quels paramètres votre extension de remise nécessite, et les fonctionnalités spécifiques à implémenter pour la remise des notifications de rapport.  
  
 Chaque extension de remise [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] doit fournir les fonctionnalités suivantes :  
  
-   Une implémentation d'interface <xref:Microsoft.ReportingServices.Interfaces.IExtension> qui représente l'extension et un nom d'extension localisé.  
  
-   Une implémentation <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> qui crée une extension de remise qui peut être utilisée pour remettre des notifications de rapport aux utilisateurs finaux.  
  
-   La capacité à traiter des données utilisateur spécifiques pour un abonnement.  
  
 Chaque extension de remise peut être améliorée pour inclure les fonctionnalités suivantes :  
  
-   Une implémentation du contrôle utilisateur [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] qui permet aux utilisateurs finaux d'utiliser le Gestionnaire de rapports pour créer des abonnements de rapport qui utilisent l'extension de remise.  
  
 Le tableau suivant décrit les interfaces et les classes disponibles pour les extensions de remise.  
  
|Interface ou classe|Description|  
|------------------------|-----------------|  
|<xref:Microsoft.ReportingServices.Interfaces.IExtension> .|Représente une extension dans [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|  
|<xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> .|Représente une extension de remise dans [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|  
|<xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> .|Contient des informations relatives au serveur de rapports requises par les extensions de remise (par exemple, une liste des extensions de rendu disponibles).|  
|La classe <xref:Microsoft.ReportingServices.Interfaces.Setting>|Représente un paramètre pour une extension.|  
|La classe <xref:Microsoft.ReportingServices.Interfaces.Notification>|Contient des informations d'abonnement que les extensions de remise utilisent pour remettre des rapports.|  
|La classe <xref:Microsoft.ReportingServices.Interfaces.Report>|Représente des informations spécifiques aux rapports et méthodes qui permettent aux extensions de remise de remettre des rapports aux utilisateurs.|  
|La classe <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile>|Représente la sortie d'une extension de rendu. Un objet <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> contient le nom de fichier associé et les informations de type requises par l'extension de remise afin de traiter le flux de données retourné par l'extension de rendu.|  
|<xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> .|Contrôle utilisateur qui représente les moyens d'extraire les informations d'abonnement spécifiques à l'extension de remise auprès de l'utilisateur dans le Gestionnaire de rapports (par exemple, une adresse de messagerie ou le chemin d'accès à un partage de fichiers).|  
  
## <a name="see-also"></a>Voir aussi  
 [Extensions Reporting Services](../reporting-services-extensions.md)   
 [Implémentation d’une extension de remise](implementing-a-delivery-extension.md)   
 [Bibliothèque d'extensions Reporting Services](../reporting-services-extension-library.md)  
  
  
