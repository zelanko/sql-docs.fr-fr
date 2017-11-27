---
title: "Propriétés de SQL Server Browser (onglet Ouvrir une session) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c77871ec-c2f4-4e4a-9a10-5aeb4ae70507
caps.latest.revision: "20"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ec0a1bc4679952a0df764f9230ba37e5f088e9f2
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="sql-server-browser-properties-log-on-tab"></a>Propriétés de SQL Server Browser (onglet Ouvrir une session)
  Le programme [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser s'exécute sur le serveur en tant que service. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser est à l'écoute des demandes entrantes pour les ressources [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et fournit des informations sur les instances [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installées sur l'ordinateur.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser est à l’écoute d’un port UDP et accepte les demandes non authentifiées à l’aide du protocole SSRP ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Resolution Protocol).  
  
 La modification du mot de passe d'un compte prend effet immédiatement sans redémarrer le service.  
  
## <a name="options"></a>Options  
 **Compte système local**  
 Exécutez le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser dans le contexte de sécurité du compte système local. Quand cela est possible, utilisez à la place de celui-ci un compte à faible niveau d'autorisation.  
  
 **Ce compte**  
 Spécifiez un compte d'utilisateur local ou de domaine qui utilise l'authentification Windows. Nous vous recommandons d'utiliser un compte d'utilisateur de domaine doté d'autorisations minimales pour les services. Pour plus d'informations sur la sélection d'un compte, consultez « Configuration des comptes de service Windows » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Parcourir**  
 Recherchez un principal de sécurité utilisateur ou intégré.  
  
> [!IMPORTANT]  
>  Utilisez un compte à faible niveau d'autorisation. Pour plus d’informations sur les autorisations nécessaires pour le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser, consultez la section relative à la sécurité de la rubrique [Service SQL Server Browser](../../tools/configuration-manager/sql-server-browser-service.md).  
  
 **Mot de passe**  
 Entrez le mot de passe du principal de sécurité.  
  
 **Confirmer le mot de passe**  
 Confirmez le mot de passe du principal de sécurité.  
  
 **État du service**  
 Indique si ce service est en cours d'exécution, arrêté ou désactivé. «**…**» indique qu'un changement d'état est en attente.  
  
 **Démarrer**  
 Démarre le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser.  
  
 **Arrêter**  
 Arrête le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser.  
  
 **Suspendre**  
 Interrompt le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser.  
  
 **Reprendre**  
 Reprend un service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser suspendu.  
  
## <a name="see-also"></a>Voir aussi  
 [Service SQL Server Browser](../../tools/configuration-manager/sql-server-browser-service.md)  
  
  
