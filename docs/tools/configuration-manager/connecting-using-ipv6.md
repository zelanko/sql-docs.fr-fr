---
title: "Connexion à l’aide de IPv6 | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: configuration-manager
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Internet Protocol
- IPv4
- IPv6
ms.assetid: 2669098c-f5f1-43da-aec6-e91003ac89f6
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3270ffb9899b8d8e4663c7e0d1b4dc52b8d89049
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2018
---
# <a name="connecting-using-ipv6"></a>Connexion avec IPv6
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client prend entièrement en charge le protocole Internet version 4 (IPv4) et le protocole Internet version 6 (IPv6). Quand Windows est configuré avec IPv6 les composants [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]détectent automatiquement la présence d'IPv6. Aucune configuration particulière de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'est nécessaire.  
  
 La prise en charge inclut, entre autres, les éléments suivants :  
  
-   Le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] et les autres composants serveur peuvent écouter simultanément sur les deux adresses IPv4 et IPv6. Quand IPv4 et IPv6 sont tous deux présents, vous pouvez utiliser le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Gestionnaire de configuration pour configurer le [!INCLUDE[ssDE](../../includes/ssde-md.md)] de façon à n'écouter que les adresses IPv4 ou IPv6.  
  
-   Quand le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser en cours d'exécution sur un ordinateur qui prend en charge à la fois IPv4 et IPv6 est interrogé sur une adresse IPv4, il répond avec une adresse IPv4 et le premier port TCP IPv4 de la liste. En cas d'interrogation sur une adresse IPv6, il répond avec une adresse IPv6 et le premier port TCP IPv6 de la liste. Pour éviter toute incohérence, nous recommandons de configurer les écouteurs IPv4 et IPv6 de façon à ce qu'ils écoutent sur le même port.  
  
-   Des outils comme [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] et le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] acceptent les deux formats IPv4 et IPv6 pour les adresses IP. Dans la plupart des cas, la chaîne de connexion n’avez pas besoin d’être modifiée si la \< *Nom_Ordinateur*>\\<*nom_instance*> est spécifié à l’aide du nom d’hôte du serveur ou le nom de domaine complet (FQDN). Si l'ordinateur serveur possède à la fois IPv4 et IPv6, son nom d'hôte ou son nom de domaine complet est résolu en plusieurs adresses IP, incluant au moins une adresse IPv4 et plusieurs adresses IPv6. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client tente d’établir des connexions à l’aide de ces adresses IP dans l’ordre reçu depuis TCP/IP et utilise la première connexion réussit. Du fait que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client est dans l'impossibilité de prévoir l'ordre, celui-ci doit être considéré comme aléatoire. Les adresses IPv4 sont tentées en premier si les adresses IPv4 et IPv6 sont toutes deux présentes. Pour les utilisateurs d'ODBC, OLE DB ou ADO.NET, la logique est totalement transparente.  
  
    > [!NOTE]  
    >  Si le [!INCLUDE[ssDE](../../includes/ssde-md.md)] n’écoute pas sur IPv4, la tentative de connexion IPv4 doit attendre la période d’expiration avant de tenter l’adresse IPv6. Pour pallier ce désagrément, connectez-vous directement à l'adresse IPv6 ou configurez un alias sur le client avec l'adresse IPv6.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestionnaire de configuration SQL Server](../../relational-databases/sql-server-configuration-manager.md)  
  
  
