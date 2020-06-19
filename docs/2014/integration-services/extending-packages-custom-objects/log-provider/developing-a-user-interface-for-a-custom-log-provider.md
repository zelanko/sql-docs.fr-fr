---
title: Développement d’une interface utilisateur pour un module fournisseur d’informations personnalisé | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- custom user interface [Integration Services], custom log providers
- custom log providers [Integration Services], developing custom user interface
ms.assetid: 6fd2d269-d87a-4134-82a1-40a09b3b5453
author: janinezhang
ms.author: janinez
ms.openlocfilehash: b3722fdc263173b543095b56cee62d273edd7bdc
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84968711"
---
# <a name="developing-a-user-interface-for-a-custom-log-provider"></a>Développement d'une interface utilisateur pour un module fournisseur d'informations personnalisé
  De nombreux modules fournisseurs d’informations [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] ont une interface utilisateur personnalisée qui implémente <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsLogProviderUI> et remplace la zone de texte **Configuration** dans la boîte de dialogue **Configurer les journaux SSIS** par la liste déroulante filtrée des gestionnaires de connexions disponibles. Toutefois, les interfaces utilisateur personnalisées des modules fournisseurs d'informations personnalisés ne sont pas implémentées dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].  
  
![Icône de Integration Services (petite)](../../media/dts-16.gif "Icône Integration Services (petite)")  **restez à jour avec Integration Services**<br /> Pour obtenir les derniers téléchargements, articles, exemples et vidéos de Microsoft, ainsi que des solutions sélectionnées par la communauté, visitez la page [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visiter la page Integration Services sur MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’un module fournisseur d’informations personnalisé](creating-a-custom-log-provider.md)   
 [Codage d'un module fournisseur d'informations personnalisé](coding-a-custom-log-provider.md)  
  
  
