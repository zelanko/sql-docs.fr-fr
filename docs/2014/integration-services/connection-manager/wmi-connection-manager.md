---
title: Gestionnaire de connexions WMI | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], WMI
- connection managers [Integration Services], WMI
- WMI connection manager [Integration Services]
ms.assetid: fbfa4ba7-3d0d-4d6b-94ad-50741a88d03d
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 406faef2e7d2392776370f3fb5da49daf3dc175a
ms.sourcegitcommit: 08b3de02475314c07a82a88c77926d226098e23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49119117"
---
# <a name="wmi-connection-manager"></a>Gestionnaire de connexions WMI
  Un gestionnaire de connexions WMI permet à un package d'utiliser WMI (Windows Management Instrumentation) pour gérer des informations dans un environnement d'entreprise. La tâche de service web incluse dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] utilise un gestionnaire de connexions WMI.  
  
 Lorsque vous ajoutez un gestionnaire de connexions WMI à un package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crée une connexion de gestionnaire qui sera converti en une connexion WMI au moment de l’exécution, définit des propriétés du Gestionnaire de la connexion et ajoute le Gestionnaire de connexions à la `Connections` collection sur le package . La propriété `ConnectionManagerType` du gestionnaire de connexions a pour valeur `WMI`.  
  
## <a name="configuration-of-the-wmi-connection-manager"></a>Configuration du gestionnaire de connexions WMI  
 Vous pouvez configurer un gestionnaire de connexions WMI de plusieurs manières :  
  
-   Spécifiez le nom d'un serveur.  
  
-   Spécifiez un espace de noms sur le serveur.  
  
-   Sélectionnez le mode d'authentification pour la connexion au serveur.  
  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés que vous pouvez définir dans le Concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , consultez [Éditeur du gestionnaire de connexions WMI](../wmi-connection-manager-editor.md).  
  
 Pour plus d’informations sur la configuration d’un gestionnaire de connexions par programmation, consultez <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> et [Ajout de connexions par programme](../building-packages-programmatically/adding-connections-programmatically.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Tâche de service Web](../control-flow/web-service-task.md)   
 [Connexions Integration Services &#40;SSIS&#41;](integration-services-ssis-connections.md)  
  
  
