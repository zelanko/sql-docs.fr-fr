---
title: Propriétés de l’abonné | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.configdistwizard.subscribers.f1
helpviewer_keywords:
- Subscriber Properties dialog box
ms.assetid: 32aa0347-64e4-4aa4-ac57-6bd3e5d52070
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b48e20c2dd1838ae01447c12d8f65a8929b9d5c3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48075499"
---
# <a name="subscriber-properties"></a>Propriétés de l'abonné
  La boîte de dialogue **Propriétés de l'Abonné** contient des informations relatives aux versions de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] exécutées par l'Abonné et antérieures à [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
## <a name="options"></a>Options  
 **Connexion de l'agent à l'Abonné**  
 Contexte dans lequel l'Agent de distribution et l'Agent de fusion se connectent à l'Abonné à partir du serveur de distribution. Ceci ne s'applique qu'aux versions antérieures à [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
 Choisissez l'option **Imiter le compte de processus de l'Agent** afin d'établir des connexions à l'Abonné grâce au contexte du compte de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur le Serveur de distribution, ou bien choisissez **Authentification SQL Server**et saisissez alors une valeur pour chacun des champs **Connexion** et **Mot de passe**. [!INCLUDE[msCoName](../../includes/msconame-md.md)] recommande de sélectionner plutôt l'option **Imiter le compte de processus de l'Agent**.  
  
 Pour [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et versions ultérieures, les informations de connexion sont spécifiées pour chaque abonnement dans l'Assistant Nouvel abonnement et vous pouvez les modifier dans la boîte de dialogue **Propriétés de l'abonnement** .  
  
 **Planifications des agents par défaut**  
 Planification par défaut utilisée dans l'Assistant Nouvel abonnement pour les Abonnés qui exécutent des versions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] antérieures à [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)].  
  
 **Divers**  
 Inclut des informations relatives à l'abonné et au type d'abonné.  
  
## <a name="see-also"></a>Voir aussi  
 [Afficher et modifier les propriétés d’un serveur de distribution et d’un serveur de publication](view-and-modify-distributor-and-publisher-properties.md)   
 [Référence des propriétés &#40;réplication&#41;](properties-reference-replication.md)   
 [S'abonner à des publications](subscribe-to-publications.md)  
  
  
