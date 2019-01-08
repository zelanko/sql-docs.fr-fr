---
title: Gestionnaire de connexions MSMQ | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], message queues
- connection managers [Integration Services], MSMQ
- MSMQ connection manager
- message queue connections [Integration Services]
ms.assetid: a86900e2-450e-479f-b207-e1b02361d395
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 015488fc30b364b9f82086acb995df3967eb5b10
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52766851"
---
# <a name="msmq-connection-manager"></a>Gestionnaire de connexions MSMQ
  Un gestionnaire de connexions MSMQ permet à un package de se connecter à une file d'attente de messages qui utilise Message Queuing (MSMQ). La tâche MSMQ incluse dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] utilise un gestionnaire de connexions MSMQ.  
  
 Lorsque vous ajoutez un gestionnaire de connexions MSMQ à un package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crée un gestionnaire de connexions qui sera résolu en une connexion MSMQ au moment de l'exécution, définit les propriétés du gestionnaire de connexions et ajoute le gestionnaire de connexions à la collection `Connections` sur le package. La propriété `ConnectionManagerType` du gestionnaire de connexions a pour valeur `MSMQ`.  
  
 Vous pouvez configurer le gestionnaire de connexions MSMQ de plusieurs manières :  
  
-   Spécifiez une chaîne de connexion.  
  
-   Spécifiez le chemin d'accès à la file d'attente de messages à laquelle se connecter.  
  
 Le format du chemin dépend du type de file d'attente, comme le montre le tableau suivant.  
  
|Type de file d'attente|Exemple de chemin d'accès|  
|----------------|-----------------|  
|Public|\<nom_ordinateur >\\<nom_file_attente\>|  
|Privé|\<nom_ordinateur >\Private$\\<nom_file_attente\>|  
  
 Vous pouvez utiliser un point (.) pour représenter l'ordinateur local.  
  
## <a name="configuration-of-the-msmq-connection-manager"></a>Configuration du gestionnaire de connexions MSMQ  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés que vous pouvez définir dans le Concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , consultez [Éditeur du gestionnaire de connexions MSMQ](../msmq-connection-manager-editor.md).  
  
 Pour plus d’informations sur la configuration d’un gestionnaire de connexions par programmation, consultez <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> et [Ajout de connexions par programme](../building-packages-programmatically/adding-connections-programmatically.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Tâche MSMQ](../control-flow/message-queue-task.md)   
 [Connexions Integration Services &#40;SSIS&#41;](integration-services-ssis-connections.md)  
  
  
