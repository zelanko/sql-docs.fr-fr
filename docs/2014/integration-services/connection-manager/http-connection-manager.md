---
title: Gestionnaire de connexions HTTP | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- HTTP connection manager
- Web site connections [Integration Services]
- connection managers [Integration Services], HTTP
- Web server connections [Integration Services]
- connections [Integration Services], HTTP
ms.assetid: 26b2b3e1-d02c-46ca-8d31-7aef2bbc3c53
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: f79a882e3a3e4520cb8cfcd4468f3c908b79abf5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62833746"
---
# <a name="http-connection-manager"></a>Gestionnaire de connexions HTTP
  Une connexion HTTP permet à un package d'accéder à un serveur Web via HTTP pour l'envoi et la réception de fichiers. La tâche de service Web incluse dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] utilise ce gestionnaire de connexions.  
  
 Lorsque vous ajoutez un gestionnaire de connexions HTTP à un package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crée un gestionnaire de connexions qui sera converti en connexion HTTP au moment de l'exécution, définit les propriétés du gestionnaire de connexions et ajoute le gestionnaire de connexions à la collection `Connections` du package.  
  
 La propriété `ConnectionManagerType` du gestionnaire de connexions a pour valeur `HTTP.`  
  
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
  
-   [Éditeur du gestionnaire de connexions HTTP &#40;page Serveur&#41;](../http-connection-manager-editor-server-page.md)  
  
-   [Éditeur du gestionnaire de connexions HTTP &#40;page Proxy&#41;](../http-connection-manager-editor-proxy-page.md)  
  
 Pour plus d’informations sur la configuration d’un gestionnaire de connexions par programmation, consultez <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager>.  
  
## <a name="see-also"></a>Voir aussi  
 [Tâche de service Web](../control-flow/web-service-task.md)   
 [Connexions Integration Services &#40;SSIS&#41;](integration-services-ssis-connections.md)  
  
  
