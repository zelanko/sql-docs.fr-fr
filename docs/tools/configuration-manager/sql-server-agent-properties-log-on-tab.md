---
title: Propriétés de SQL Server Agent (onglet Ouvrir une session) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 01fc6329-5d6b-4186-9565-395f375477bb
author: stevestein
ms.author: sstein
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
manager: craigg
ms.openlocfilehash: 120b1eefa2ef80e8c8d6174ff2be9dcf7eab7955
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47641557"
---
# <a name="sql-server-agent-properties-log-on-tab"></a>Propriétés de l'Agent SQL Server (onglet Ouvrir une session)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  L'onglet **Ouvrir une session** de la boîte de dialogue **Propriétés de l'Agent SQL Server** permet de spécifier le compte utilisé par le service de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , ainsi que de démarrer et d'arrêter ce service. La modification du mot de passe d'un compte prend effet immédiatement sans redémarrer le service.  
  
> [!NOTE]  
>  Lorsque vous modifiez le nom du compte utilisé par un service sur une instance cluster, le nouveau compte doit être un membre du groupe de domaine spécifié au cours de l'installation pour le service modifié ou vous devez disposer de l'autorisation d'ajouter des membres à ce groupe. Si vous ne disposez pas de l'autorisation de modifier l'appartenance aux groupes, contactez l'administrateur de domaine.  
  
## <a name="options"></a>Options  
 **Compte système local**  
 Spécifie un compte système local, qui ne requiert pas de mot de passe. Cependant, le compte système local peut limiter l'interaction du service avec les autres serveurs, en fonction des privilèges accordés au compte.  
  
 **Ce compte**  
 Spécifiez un compte d'utilisateur local ou de domaine qui utilise l'authentification Windows. [!INCLUDE[msCoName](../../includes/msconame-md.md)] recommande d'utiliser un compte d'utilisateur de domaine doté d'autorisations minimales pour les services. Pour plus d'informations sur la sélection d'un compte, recherchez « Configuration des comptes de service Windows » dans la documentation en ligne.  
  
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
  
  
