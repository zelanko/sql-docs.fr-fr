---
title: Se connecter à une instance à partir de l’Explorateur d’objets | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 9803a8a0-a8f1-4b65-87b8-989b06850194
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9f2d811dc542bf24c2cf75fe792a079046830076
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43815505"
---
# <a name="connect-to-an-instance-from-object-explorer"></a>Se connecter à une instance à partir de l’Explorateur d’objets
  Pour gérer des objets à l'aide de l'Explorateur d'objets, vous devez d'abord connecter l'Explorateur d'objets à l'instance qui contient les objets. Vous pouvez connecter l'Explorateur d'objets à plusieurs instances à la fois.  
  
## <a name="connecting-object-explorer-to-a-server"></a>Connexion de l'Explorateur d'objets à un serveur  
 Pour pouvoir utiliser l'Explorateur d'objets, vous devez le connecter à un serveur. Cliquez sur **Se connecter** dans la barre d’outils de l’Explorateur d’objets, puis choisissez le type du serveur dans la liste déroulante. La boîte de dialogue **Se connecter au serveur** s'ouvre. Pour établir la connexion, vous devez fournir au moins le nom du serveur et les informations correctes d'authentification.  
  
## <a name="optional-object-explorer-connection-settings"></a>Paramètres de connexion facultatifs de l'Explorateur d'objets  
 Quand vous vous connectez à un serveur, vous pouvez fournir d’autres informations de connexion dans la boîte de dialogue **Se connecter au serveur**. Cette boîte de dialogue conserve les derniers paramètres utilisés (les nouvelles connexions, telles que des nouvelles fenêtres d’éditeur de code, utiliseront ces paramètres).  
  
 Pour définir des paramètres de connexion facultatifs, procédez comme suit :  
  
1.  Cliquez sur **Se connecter** dans la barre d’outils de l’Explorateur d’objets, puis sur le type du serveur auquel se connecter. La boîte de dialogue **Se connecter au serveur** s'ouvre.  
  
2.  Dans la zone **Nom du serveur** , tapez le nom de l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
3.  Cliquez sur **Options**. La boîte de dialogue **Se connecter au serveur** affiche d’autres options.  
  
4.  Cliquez sur l’onglet **Propriétés de connexion** pour configurer les autres paramètres. Les paramètres disponibles varient selon le type du serveur. Les paramètres ci-dessous sont disponibles pour le [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
    |Paramètre|Description|  
    |-------------|-----------------|  
    |**Se connecter à la base de données**|Choisissez une base de données parmi les bases de données disponibles sur le serveur. Cette liste affiche uniquement les bases de données que vous êtes autorisé à afficher.|  
    |**Protocole réseau**|Sélectionnez Mémoire partagée, TCP/IP ou Canaux nommés.|  
    |**Taille du paquet réseau**|Utilisez des octets pour la configuration. Le paramètre par défaut est 4 096 octets.|  
    |**Délai de connexion**|Utilisez des secondes pour la configuration. Le paramètre par défaut est 15 secondes.|  
    |**Délai d’exécution**|Utilisez des secondes pour la configuration. Le paramètre par défaut (0) indique que l'exécution ne dépassera jamais le délai d'exécution.|  
    |**Chiffrer la connexion**|Force le chiffrement.|  
  
5.  Pour ajouter le serveur spécifié à votre liste de serveurs inscrits, cliquez sur l’onglet **Serveurs inscrits** , sur l’emplacement où vous souhaitez que le nouveau serveur s’affiche, puis terminez la connexion.  
  
> [!NOTE]  
>  Vous pouvez utiliser la page **Paramètres de connexion supplémentaires** pour ajouter d’autres paramètres de connexion à la chaîne de connexion. Pour plus d’informations, consultez [Se connecter au serveur &#40;page Paramètes de connexion supplémentaires&#41;](../../database-engine/connect-to-server-additional-connection-parameters-page.md).  
  
  
