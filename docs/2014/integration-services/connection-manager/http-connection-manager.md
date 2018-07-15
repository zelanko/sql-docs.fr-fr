---
title: Gestionnaire de connexions HTTP | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- HTTP connection manager
- Web site connections [Integration Services]
- connection managers [Integration Services], HTTP
- Web server connections [Integration Services]
- connections [Integration Services], HTTP
ms.assetid: 26b2b3e1-d02c-46ca-8d31-7aef2bbc3c53
caps.latest.revision: 44
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 02df4c5dff88988bd6a233208646e9eb9a7f0e2d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37314449"
---
# <a name="http-connection-manager"></a>Gestionnaire de connexions HTTP
  Une connexion HTTP permet à un package d'accéder à un serveur Web via HTTP pour l'envoi et la réception de fichiers. La tâche de service Web incluse dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] utilise ce gestionnaire de connexions.  
  
 Lorsque vous ajoutez un gestionnaire de connexions HTTP à un package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crée un gestionnaire de connexions qui sera converti en connexion HTTP au moment de l'exécution, définit les propriétés du gestionnaire de connexions et ajoute le gestionnaire de connexions à la collection `Connections` du package.  
  
 Le `ConnectionManagerType` a la valeur de propriété du Gestionnaire de connexions `HTTP.`  
  
 Vous pouvez configurer le gestionnaire de connexions HTTP de plusieurs manières :  
  
-   Utilisez des informations d'identification. Si le gestionnaire de connexions utilise des informations d'identification, ses propriétés incluent le nom d'utilisateur, le mot de passe et le domaine.  
  
    > [!IMPORTANT]  
    >  Le gestionnaire de connexions HTTP prend en charge uniquement l'authentification anonyme et l'authentification de base. Il ne prend pas en charge l'authentification Windows.  
  
-   Utilisez un certificat client. Si le gestionnaire de connexions utilise un certificat client, ses propriétés incluent le nom du certificat.  
  
-   Indiquez un délai de connexion au serveur et une taille de segment pour l'écriture de données.  
  
-   Utilisez un serveur proxy. Le serveur Proxy peut également être configuré pour utiliser les informations d'identification et pour ignorer le serveur proxy et utiliser à la place des adresses locales.  
  
## <a name="configuration-of-the-http-connection-manager"></a>Configuration du gestionnaire de connexions HTTP  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d'informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur l'une des rubriques suivantes :  
  
-   [Éditeur du Gestionnaire de connexions HTTP &#40;Page du serveur&#41;](../http-connection-manager-editor-server-page.md)  
  
-   [Éditeur du Gestionnaire de connexions HTTP &#40;Page Proxy&#41;](../http-connection-manager-editor-proxy-page.md)  
  
 Pour plus d’informations sur la configuration d’un gestionnaire de connexions par programmation, consultez <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager>.  
  
## <a name="see-also"></a>Voir aussi  
 [Tâche de Service Web](../control-flow/web-service-task.md)   
 [Integration Services &#40;SSIS&#41; connexions](integration-services-ssis-connections.md)  
  
  
