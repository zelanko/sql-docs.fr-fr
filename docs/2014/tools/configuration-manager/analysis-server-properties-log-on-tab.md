---
title: Propriétés de Analysis Server (onglet Ouvrir une session) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- configmgr-client
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a82e0c98-efaa-4b0b-9582-3c879ee42444
caps.latest.revision: 16
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 2687a9e046529927f694b8da0d0d8f11bfccf7f2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36043270"
---
# <a name="analysis-server-properties-log-on-tab"></a>Propriétés de Analysis Server (onglet Ouvrir une session)
  L'onglet **Ouvrir une session** de la boîte de dialogue **Propriétés de Analysis Server** permet de spécifier le compte utilisé par le service [!INCLUDE[ssAS](../../includes/ssas-md.md)] , ainsi que de démarrer et d'arrêter ce service.  
  
> [!NOTE]  
>  Lorsque vous modifiez le **Nom du compte** utilisé par un service sur une instance cluster, le nouveau compte doit être un membre du groupe de domaine spécifié au cours de l'installation pour le service modifié ou vous devez posséder l'autorisation d'ajouter des membres à ce groupe. Si vous ne disposez pas de l'autorisation de modifier l'appartenance aux groupes, contactez l'administrateur de domaine.  
  
## <a name="options"></a>Options  
 **Compte système local**  
 Spécifie un compte système local, qui ne requiert pas de mot de passe. Cependant, le compte système local peut limiter l'interaction du service avec les autres serveurs, en fonction des privilèges accordés au compte.  
  
 **Ce compte**  
 Spécifiez un compte d'utilisateur local ou de domaine qui utilise l'authentification [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. [!INCLUDE[msCoName](../../includes/msconame-md.md)] recommande d'utiliser un compte d'utilisateur de domaine doté d'autorisations minimales pour les services. Pour plus d'informations sur la sélection d'un compte, recherchez dans la documentation en ligne la rubrique « Configuration des comptes de services Windows ».  
  
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
 Suspend le service.  
  
 **Reprendre**  
 Reprend un service suspendu.  
  
  