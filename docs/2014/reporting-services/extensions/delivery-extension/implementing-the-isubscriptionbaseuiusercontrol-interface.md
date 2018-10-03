---
title: Implémentation de l’Interface ISubscriptionBaseUIUserControl pour une Extension de remise | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- user controls [Reporting Services]
- ISubscriptionBaseUIUserControl interface
- delivery extensions [Reporting Services], user controls
ms.assetid: a1e9122c-aa0b-45de-b536-4f1202875ab1
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 7885f486ef19b0fa5424857bc03146f5d0b1c8bd
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48220769"
---
# <a name="implementing-the-isubscriptionbaseuiusercontrol-interface-for-a-delivery-extension"></a>Implémentation de l'interface ISubscriptionBaseUIUserControl pour une extension de remise
  Les extensions de remise [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] peuvent contenir une implémentation d'une interface utilisateur d'abonnement pour rassembler des informations spécifiques à l'extension dans le Gestionnaire de rapports. L'interface utilisateur est appelée lorsqu'un utilisateur crée un abonnement ou en modifie un. Lorsqu'un nouvel abonnement est créé, l'interface utilisateur affiche des valeurs par défaut appropriées et active des utilisateurs pour interagir avec le fournisseur de remise. Lorsqu'un abonnement est modifié, l'interface utilisateur est pré-remplie avec les informations dans l'abonnement actuel.  
  
 Les extensions de remise fournissent l'interface utilisateur d'abonnement sous la forme d'un contrôle utilisateur ASP.NET. Le serveur de rapports incorpore le contrôle utilisateur défini par l'extension de remise lors de l'affichage de l'interface utilisateur d'abonnements. L'interface de base qui fournit des méthodes abstraites qui activent ces fonctionnalités est l'interface <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl>. Cette interface garantit que les opérations communes, telles que la validation des valeurs d'entrée, sont effectuées correctement. En outre, le contrôle utilisateur de base fournit un jeu de propriétés par défaut utilisées par le serveur de rapports pour veiller à la cohérence dans les abonnements. Ces propriétés sont requises par les extensions de remise intégrées au Gestionnaire de rapports.  
  
 Vous pouvez implémenter l'interface <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> dans un fournisseur de remise pour générer une interface utilisateur d'abonnement pour le Gestionnaire de rapports. L'interface <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> fournit l'infrastructure pour permettre aux utilisateurs d'entrer des valeurs pour les paramètres d'abonnement, pour traiter les paramètres dont a besoin l'extension de remise, et pour valider les paramètres.  
  
> [!NOTE]  
>  Vous n'êtes pas obligé d'implémenter l'interface <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> dans votre extension de remise. Les abonnements qui utilisent votre extension de remise peuvent toujours être créés à l'aide des méthodes de l'API SOAP <xref:ReportService2010.ReportingService2010.CreateSubscription%2A> et <xref:ReportService2010.ReportingService2010.CreateDataDrivenSubscription%2A>. Pour plus d’informations sur les fonctionnalités de l’API SOAP pour la gestion des abonnements et des remises, consultez [Méthodes d’abonnement et de remise](../../report-server-web-service/methods/subscription-and-delivery-methods.md).  
  
 L'interface <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> étend <xref:Microsoft.ReportingServices.Interfaces.IExtension>. Votre contrôle utilisateur qui implémente <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> doit également hériter de **System.Web.UI.WebControls.WebControl**. Pour plus d’informations sur la classe **WebControl**, consultez votre Guide du développeur [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
 Pour un exemple d’utilisation de l’interface <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl>, consultez [SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889) (Exemples Reporting Services pour le produit SQL Server).  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation d’une extension de remise](implementing-a-delivery-extension.md)   
 [Bibliothèque d'extensions Reporting Services](../reporting-services-extension-library.md)  
  
  
