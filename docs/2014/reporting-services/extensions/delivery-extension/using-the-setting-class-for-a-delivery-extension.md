---
title: Utilisation de la classe Setting pour une extension de remise | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- delivery extensions [Reporting Services], settings
- Setting class
ms.assetid: 50746639-da7c-46a5-ac7b-e87dd6b91880
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 58f8e9f581781c3a7503c55744c0ec0abf3973dd
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53360671"
---
# <a name="using-the-setting-class-for-a-delivery-extension"></a>Utilisation de la classe Setting pour une extension de remise
  La classe <xref:Microsoft.ReportingServices.Interfaces.Setting> se trouve dans l'espace de noms <xref:Microsoft.ReportingServices.Interfaces> et représente les informations relatives aux paramètres d'une extension de remise. La classe <xref:Microsoft.ReportingServices.Interfaces.Setting> fournit l'infrastructure de stockage des informations sur les paramètres nécessaires au bon fonctionnement d'une extension de remise. Par exemple, dans l'extension de remise par messagerie du serveur de rapports, un utilisateur est tenu de fournir des paramètres spécifiques à la remise par messagerie, tels que l'adresse du destinataire, l'adresse de l'expéditeur ou la ligne d'objet du message électronique. Vos fournisseurs de remise personnalisés demanderont sans aucun doute à l'utilisateur de fournir des paramètres spécifiques afin que l'extension de remise puisse remettre des notifications et des rapports.  
  
 La classe <xref:Microsoft.ReportingServices.Interfaces.Setting> est utilisée lors de l'implémentation de la propriété <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ExtensionSettings%2A> de l'interface <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension>. La classe <xref:Microsoft.ReportingServices.Interfaces.Setting> est également utilisée pour traiter les données de paramètre d'extension fournies par un utilisateur lorsqu'un abonnement ou la notification est créé(e).  
  
 Pour un exemple d’utilisation de la classe <xref:Microsoft.ReportingServices.Interfaces.Setting>, consultez [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889) (Exemples Reporting Services pour le produit SQL Server).  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation d’une extension de remise](implementing-a-delivery-extension.md)   
 [Bibliothèque d'extensions Reporting Services](../reporting-services-extension-library.md)  
  
  
