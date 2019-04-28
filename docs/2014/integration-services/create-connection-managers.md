---
title: Créer des gestionnaires de connexions | Microsoft Docs
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.connectionmanager.f1
helpviewer_keywords:
- Integration Services packages, connections
- SSIS packages, connections
- packages [Integration Services], connections
- connection managers [Integration Services], creating
- SQL Server Integration Services packages, connections
ms.assetid: 6ca317b8-0061-4d9d-b830-ee8c21268345
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: ef2ea7fa43556f0c4f12ee41101aedf396a23382
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62832001"
---
# <a name="create-connection-managers"></a>Créer des gestionnaires de connexions
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] propose différents gestionnaires de connexions pour répondre aux besoins de tâches qui se connectent à différents types de serveurs et de sources de données. Les gestionnaires de connexions sont utilisés par les composants de flux de données qui extraient et chargent des données dans différents types de banques de données et par les modules fournisseurs d'informations qui enregistrent des journaux sur un serveur, dans une table [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ou dans un fichier. Par exemple, un package contenant une tâche Envoyer un message utilise un gestionnaire de connexions SMTP pour se connecter à un serveur SMTP (Simple Mail Transfer Protocol). Un package contenant une tâche d'exécution SQL peut utiliser un gestionnaire de connexions OLE DB pour se connecter à une base de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Pour plus d’informations, consultez [Connexions Integration Services &#40;SSIS&#41;](connection-manager/integration-services-ssis-connections.md).  
  
 Pour créer et configurer automatiquement des gestionnaires de connexions quand vous créez un package, vous pouvez utiliser l’Assistant Importation et exportation [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Cet Assistant vous aide aussi à créer et configurer les sources et destinations qui utilisent les gestionnaires de connexions. Pour plus d’informations, consultez [Create Packages in SQL Server Data Tools](create-packages-in-sql-server-data-tools.md).  
  
 Pour créer manuellement un nouveau gestionnaire de connexions et l'ajouter à un package existant, utilisez la zone **Gestionnaires de connexions** sous les onglets **Flux de contrôle**, **Flux de données**et **Gestionnaires d'événements** du concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] . Dans la zone **Gestionnaire de connexions** , vous devez choisir le type de gestionnaire de connexions à créer, puis définir ses propriétés dans la boîte de dialogue fournie à cet effet dans le concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] . Pour plus d'informations, consultez la section « Utilisation de la zone Gestionnaire de connexions », plus loin dans cette rubrique.  
  
 Une fois le gestionnaire de connexions ajouté à un package, vous pouvez l'utiliser dans des tâches, des conteneurs de boucles Foreach, des sources, des transformations et des destinations. Pour plus d’informations, consultez [Tâches Integration Services](control-flow/integration-services-tasks.md), [Conteneur de boucles Foreach](control-flow/foreach-loop-container.md) et [Flux de données](data-flow/data-flow.md).  
  
## <a name="using-the-connection-managers-area"></a>Utilisation de la zone Gestionnaires de connexions  
 Vous pouvez créer des gestionnaires de connexions lorsque l'onglet **Flux de contrôle**, **Flux de données**ou **Gestionnaires d'événements** du concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] est actif.  
  
 Le diagramme qui suit montre la zone **Gestionnaires de connexions** de l'onglet **Flux de contrôle** du concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
 ![Capture d’écran du concepteur de flux de contrôle avec le package](media/samplecontrolflow.gif "Capture d’écran du concepteur de flux de contrôle avec le package")  
  
#### <a name="to-add-configure-or-delete-a-connection-manager-in-ssis-designer"></a>Pour ajouter, configurer ou supprimer un gestionnaire de connexions dans le concepteur SSIS  
  
-   [Ajouter, supprimer ou partager un gestionnaire de connexions dans un package](../../2014/integration-services/add-delete-or-share-a-connection-manager-in-a-package.md)  
  
-   [Définir les propriétés d’un gestionnaire de connexions](../../2014/integration-services/set-the-properties-of-a-connection-manager.md)  
  
## <a name="32-bit-and-64-bit-providers-for-connection-managers"></a>Fournisseurs 32 bits et 64 bits pour gestionnaires de connexions  
 De nombreux fournisseurs utilisés par des gestionnaires de connexions sont disponibles en versions 32 bits et 64 bits. L'environnement de conception [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] est un environnement 32 bits et vous ne pouvez voir que des fournisseurs 32 bits pendant la conception d'un package. Par conséquent, vous pouvez configurer un gestionnaire de connexions pour utiliser un fournisseur 64 bits spécifique uniquement si la version 32 bits du même fournisseur est également installée.  
  
 Au moment de l'exécution, la version appropriée est employée même si vous avez spécifié la version 32 bits du fournisseur lors de la conception. La version 64 bits du fournisseur peut être exécutée même si le package est utilisé dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
 Les deux versions du fournisseur ont le même ID. Pour spécifier si l’exécution de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] utilise une version 64 bits disponible du fournisseur, vous devez définir la propriété Run64BitRuntime du projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Si la propriété Run64BitRuntime a la valeur `true`, l’exécution trouve et utilise le fournisseur 64 bits ; si Run64BitRuntime est `false`, l’exécution trouve et utilise le fournisseur 32 bits. Pour plus d’informations sur les propriétés que vous pouvez définir sur les projets [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], consultez [Integration Services &#40;SSIS&#41; et environnements de Studio](integration-services-ssis-development-and-management-tools.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Flux de contrôle](control-flow/control-flow.md)   
 [Flux de données](data-flow/data-flow.md)   
 [Gestionnaires d’événements Integration Services &#40;SSIS&#41](integration-services-ssis-event-handlers.md)  
  
  
