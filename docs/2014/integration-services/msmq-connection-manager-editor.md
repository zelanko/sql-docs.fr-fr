---
title: Éditeur du Gestionnaire de connexions MSMQ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.msmqconnectionmanager.f1
helpviewer_keywords:
- MSMQ Connection Manager Editor
ms.assetid: ef842cb4-82da-4550-85fe-9bedbc1e77c7
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: d532433c36f3b4c18b39d16dcbbe81a3d969acfc
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58393067"
---
# <a name="msmq-connection-manager-editor"></a>Éditeur du gestionnaire de connexions MSMQ
  La boîte de dialogue **Gestionnaire de connexions MSMQ** permet de spécifier le chemin d’une file d’attente de messages MSMQ (Message Queuing).  
  
 Pour en savoir plus sur le gestionnaire de connexions MSMQ, consultez [MSMQ Connection Manager](connection-manager/msmq-connection-manager.md).  
  
> [!NOTE]  
>  Le gestionnaire de connexions MSMQ prend en charge les files d'attente privées et publiques locales et les files d'attente publiques distantes. Il ne prend pas en charge les files d'attente privées distantes. Pour une solution de contournement qui utilise la tâche de script, consultez [Envoi vers une file d'attente de messages privée distante à l'aide de la tâche de script](control-flow/script-task.md).  
  
## <a name="options"></a>Options  
 **Nom**  
 Fournissez un nom unique pour le gestionnaire de connexions MSMQ dans le flux de travail. Le nom fourni sera affiché dans le concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
 **Description**  
 Décrivez le gestionnaire de connexions. Il est recommandé d'indiquer ici l'usage auquel le gestionnaire de connexions est destiné, de sorte que les packages soient correctement documentés et plus faciles à gérer.  
  
 **Chemin d'accès**  
 Tapez le chemin d'accès complet de la file d'attente de messages. Le format du chemin d'accès dépend du type de file d'attente.  
  
|Type de file d'attente|Exemple de chemin d'accès|  
|----------------|-----------------|  
|Public|\<nom_ordinateur >\\<nom_file_attente\>|  
|Privé|\<nom_ordinateur >\Private$\\<nom_file_attente\>|  
  
 Vous pouvez utiliser "." pour représenter l'ordinateur local.  
  
 **Test**  
 Après avoir configuré le gestionnaire de connexions MSMQ, vérifiez si la connexion est opérationnelle en cliquant sur **Tester**.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
