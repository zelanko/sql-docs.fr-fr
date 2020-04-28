---
title: Gestionnaire de connexions Analysis Services | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], Analysis Services
- connection managers [Integration Services], Analysis Services
- Analysis Services connection manager
ms.assetid: 9f9cadad-a1d0-4db5-98f5-df5dbbec1be4
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 8f8ca9ce77e151e761e2cbb1f9128a44784af8ca
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68890392"
---
# <a name="analysis-services-connection-manager"></a>Gestionnaire de connexions Analysis Services
  Un gestionnaire de connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] permet à un package de se connecter à un serveur qui exécute une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ou à un projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] qui procure un accès à des données de cube et de dimension. La connexion à un projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] est possible uniquement pendant le développement de packages dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Au moment de l'exécution, les packages se connectent au serveur et à la base de données sur lesquels vous avez déployé le projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
 Les tâches (telles que la tâche DDL d’exécution [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] et la tâche de traitement [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ) et les destinations (telles que la destination Apprentissage du modèle d’exploration de données) utilisent un gestionnaire de connexions [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
 Pour plus d’informations sur les bases de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], consultez [Bases de données de modèle multidimensionnel &#40;SSAS&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/multidimensional-model-databases-ssas).  
  
## <a name="configuration-of-the-analysis-services-connection-manager"></a>Configuration du gestionnaire de connexions Analysis Services  
 Lorsque vous ajoutez un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] gestionnaire de connexions à un package [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , crée un gestionnaire de connexions qui est résolu [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en tant que connexion au moment de l’exécution, définit les propriétés du gestionnaire de connexions et `Connections` ajoute le gestionnaire de connexions à la collection sur le package. La propriété `ConnectionManagerType` du gestionnaire de connexions a pour valeur `MSOLAP100`.  
  
 Vous pouvez configurer le gestionnaire de connexions [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] comme suit :  
  
-   Spécifiez une chaîne de connexion configurée de façon à satisfaire les exigences du fournisseur Microsoft OLE pour Analysis Services.  
  
-   Spécifiez l'instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ou le projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] auquel se connecter.  
  
-   Si vous vous connectez à une instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], spécifiez le mode d'authentification.  
  
-   Indiquez si la connexion créée à partir du gestionnaire de connexions est conservée au moment de l'exécution.  
  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés que vous pouvez définir dans le Concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur une des rubriques suivantes :  
  
-   [Référence de l'interface utilisateur de la boîte de dialogue Ajout d'un gestionnaire de connexions Analysis Services](add-analysis-services-connection-manager-dialog-box-ui-reference.md)  
  
 Pour plus d’informations sur la configuration d’un gestionnaire de connexions par programmation, consultez <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> et [Ajout de connexions par programme](../building-packages-programmatically/adding-connections-programmatically.md).  
  
  
