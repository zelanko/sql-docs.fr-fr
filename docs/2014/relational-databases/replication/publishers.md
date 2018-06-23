---
title: Serveurs de publication | Microsoft Docs
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.rep.configuredistributionwizard.enablepublishers.f1
ms.assetid: 116cd6a5-32ac-4273-81a2-d184408e0f07
caps.latest.revision: 20
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 1b7869e3673e89aa2a1bcbc8805cdd8fa696ef5f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36141781"
---
# <a name="publishers"></a>Serveurs de publication
  Vous pouvez autoriser les autres serveurs de publication à utiliser ce serveur de distribution. Notez que l'activation d'un serveur de publication pour utiliser ce serveur en tant que serveur de distribution distant ne fait pas de ce serveur un serveur de publication. Vous devez vous connecter au serveur de publication, le configurer pour la publication, et choisir ce serveur comme distributeur. Vous pouvez configurer le serveur de publication et choisir un serveur de distribution à l'aide de l'Assistant Nouvelle publication.  
  
 Les serveurs, que vous sélectionnez en tant que serveurs de publication, utilisent la base de données de distribution spécifiée dans la page **Base de données de distribution** de cet Assistant. Si vous souhaitez utiliser une autre base de données de distribution, n'activez pas le serveur de publication. Utilisez plutôt la boîte de dialogue **Propriétés du serveur de distribution** pour ajouter des serveurs de publication après avoir terminé l'exécution de l'Assistant Configuration de la distribution.  
  
## <a name="options"></a>Options  
 **Serveurs de publication**  
 Sélectionnez les serveurs autorisés à utiliser ce serveur de distribution. Cliquez sur le bouton des propriétés (**...**) en regard d'un serveur de publication pour afficher et définir des propriétés supplémentaires.  
  
 **Ajouter**  
 Si le serveur souhaité ne figure pas dans la liste, cliquez sur **Ajouter** afin d'ajouter un serveur de publication [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou Oracle Publisher à la liste des serveurs de publication disponibles.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer la distribution](configure-distribution.md)   
 [Configurer la publication et la distribution](configure-publishing-and-distribution.md)   
 [Afficher et modifier les propriétés d’un serveur de distribution et d’un serveur de publication](view-and-modify-distributor-and-publisher-properties.md)   
 [Créer une publication](publish/create-a-publication.md)  
  
  