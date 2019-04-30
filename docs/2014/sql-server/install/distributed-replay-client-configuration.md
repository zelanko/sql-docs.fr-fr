---
title: Configuration de Distributed Replay Client | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: ccf03e32-6bd9-43c0-b9b6-9fe0d9163339
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e8b179d54ff39ffbb67193f88cd192aac6992d7d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63253621"
---
# <a name="distributed-replay-client-configuration"></a>Configuration de Distributed Replay Client
  Utilisez la page **Configuration de Distributed Replay Client** de l’Assistant Installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour spécifier les utilisateurs auxquels vous voulez accorder des autorisations administratives sur le service Distributed Replay Client.  
  
 Les utilisateurs qui disposent d'autorisations administratives ont un accès illimité au service Distributed Replay Client.  
  
## <a name="options"></a>Options  
 **Nom du contrôleur**  
 Il s’agit d’un paramètre facultatif, et la valeur par défaut est \< *vide*>.  
  
 Entrez le nom du contrôleur avec lequel l'ordinateur client communiquera pour le service Distributed Replay Client. Notez les points suivants :  
  
-   Le nom doit être un nom de domaine complet (FQDN). Par exemple, un hôte appelé server1 dans la hiérarchie de produits au sein de Microsoft peut avoir un nom de domaine complet server1.products.microsoft.com.  
  
-   Si vous avez déjà configuré un contrôleur, entrez son nom lors de la configuration de chaque client.  
  
-   Si vous n'avez pas encore configuré de contrôleur, vous n'êtes pas obligé de fournir le nom du contrôleur. Toutefois, vous devez entrer manuellement le nom du contrôleur dans le fichier de **configuration du client** .  
  
 **Répertoire de travail**  
 Spécifiez le répertoire de travail du service Distributed Replay Client.  
  
 Le répertoire de travail par défaut est \<*lettre de lecteur*>:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\DReplayClient\WorkingDir\\.  
  
 **Répertoire des résultats**  
 Spécifiez le répertoire des résultats du service Distributed Replay Client.  
  
 Le répertoire des résultats par défaut est \<*lettre de lecteur*>:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\DReplayClient\ResultDir\\.  
  
  
