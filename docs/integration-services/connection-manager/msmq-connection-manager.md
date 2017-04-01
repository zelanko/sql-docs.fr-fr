---
title: "Gestionnaire de connexions MSMQ | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "connexions [Integration Services], files d’attente de messages"
  - "gestionnaires de connexions [Integration Services], MSMQ"
  - "Gestionnaire de connexions MSMQ"
  - "connexions de files d'attente de messages [Integration Services]"
ms.assetid: a86900e2-450e-479f-b207-e1b02361d395
caps.latest.revision: 35
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 35
---
# Gestionnaire de connexions MSMQ
  Un gestionnaire de connexions MSMQ permet à un package de se connecter à une file d'attente de messages qui utilise Message Queuing (MSMQ). La tâche MSMQ incluse dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] utilise un gestionnaire de connexions MSMQ.  
  
 Quand vous ajoutez un gestionnaire de connexions MSMQ à un package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crée un gestionnaire de connexions qui sera résolu en une connexion MSMQ au moment de l’exécution, définit les propriétés du gestionnaire de connexions et ajoute le gestionnaire de connexions à la collection **Connections** sur le package. La propriété **ConnectionManagerType** du gestionnaire de connexions a pour valeur **MSMQ**.  
  
 Vous pouvez configurer le gestionnaire de connexions MSMQ de plusieurs manières :  
  
-   Spécifiez une chaîne de connexion.  
  
-   Spécifiez le chemin d'accès à la file d'attente de messages à laquelle se connecter.  
  
 Le format du chemin dépend du type de file d'attente, comme le montre le tableau suivant.  
  
|Type de file d'attente|Exemple de chemin d'accès|  
|----------------|-----------------|  
|Public|\<nom de l’ordinateur>\\<nom de la file d’attente\>|  
|Privé|\<nom de l’ordinateur>\Private$\\<nom de la file d’attente\>|  
  
 Vous pouvez utiliser un point (.) pour représenter l'ordinateur local.  
  
## Configuration du gestionnaire de connexions MSMQ  
 Vous pouvez définir des propriétés au moyen du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés que vous pouvez définir dans le Concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)], consultez [Éditeur du gestionnaire de connexions MSMQ](../../integration-services/connection-manager/msmq-connection-manager-editor.md).  
  
 Pour plus d’informations sur la configuration d’un gestionnaire de connexions par programmation, consultez <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> et [Ajout de connexions par programmation](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md).  
  
## Voir aussi  
 [Tâche MSMQ](../../integration-services/control-flow/message-queue-task.md)   
 [Connexions Integration Services &#40;SSIS&#41;](../../integration-services/connection-manager/integration-services-ssis-connections.md)  
  
  