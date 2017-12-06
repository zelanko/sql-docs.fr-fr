---
title: "Lanceur de démon de filtre de texte intégral SQL (onglet Ouvrir une session) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: configuration-manager
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 13e260f9-a75f-430b-88a3-959ddcead8fe
caps.latest.revision: "9"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 88b20c4eb7da9731885989284da6f893f4755839
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2017
---
# <a name="sql-full-text-filter-daemon-launcher-log-on-tab"></a>Lanceur de démon de filtre de texte intégral SQL (onglet Ouvrir une session)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]À compter de [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], le service Lanceur de démon de filtre SQL en texte intégral (Lanceur FDHOST) est utilisé par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] recherche en texte intégral. Ce service doit être en cours d'exécution pendant que vous utilisez la recherche en texte intégral. Pour plus d'informations sur les processus hôte de démon de filtre, consultez « Architecture de la recherche en texte intégral » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 L'onglet **Ouvrir une session** de la boîte de dialogue **Propriétés de Lanceur de démon de filtre de texte intégral SQL** permet de spécifier le compte utilisé par le service de recherche en texte intégral [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , de modifier le mot de passe d'un compte, ainsi que de démarrer et d'arrêter ce service. La modification du mot de passe d'un compte prend effet après le redémarrage du service.  
  
> [!NOTE]  
>  Lorsque vous modifiez le nom du compte utilisé par un service sur une instance en cluster, soit le nouveau compte doit être un membre du groupe de domaine spécifié au cours de l'installation pour le service, soit vous devez disposer de l'autorisation d'ajouter des membres à ce groupe. Si vous ne disposez pas de l'autorisation de modifier l'appartenance aux groupes, contactez l'administrateur de domaine.  
>   
>  Pour plus d'informations sur la sélection d'un compte pour exécuter le service, consultez « Configuration des comptes de service Windows » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="options"></a>Options  
 **Compte intégré**  
 **Système local**  
 Spécifiez le compte système local. Ce compte ne nécessite pas de mot de passe. Toutefois, le compte système local peut empêcher le service d'interagir avec les autres serveurs, en fonction des privilèges accordés au compte.  
  
 **Service local**  
 Spécifiez le compte de service local. Ce compte ne nécessite pas de mot de passe. Cependant, le compte de service local peut empêcher le service d'interagir avec les autres serveurs, en fonction des privilèges accordés au compte.  
  
 **Service réseau**  
 Il est recommandé de ne pas utiliser le compte de service réseau pour les services [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Les comptes d'utilisateur local et d'utilisateur de domaine conviennent mieux à ces services.  
  
 **Ce compte**  
 Spécifiez un compte d'utilisateur local ou de domaine qui utilise l'authentification Windows. Nous vous recommandons d'utiliser un compte d'utilisateur de domaine doté d'autorisations minimales pour les services.  
  
 **Nom du compte**  
 Spécifie le nom de compte d'utilisateur local ou de domaine.  
  
 **Mot de passe**  
 Tapez le mot de passe du compte.  
  
 **Confirmer le mot de passe**  
 Tapez de nouveau le mot de passe du compte.  
  
 **Démarrer**  
 Démarrez le service.  
  
 **Arrêter**  
 Arrête le service.  
  
 **Suspendre**  
 Suspend le service. Non disponible pour ce service.  
  
 **Reprendre**  
 Reprend un service suspendu.  
  
  
