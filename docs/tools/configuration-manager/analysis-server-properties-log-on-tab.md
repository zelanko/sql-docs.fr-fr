---
title: Propriétés de Analysis Server (onglet Ouvrir une session)
description: En savoir plus sur l’onglet Ouvrir une session de la boîte de dialogue Propriétés Analysis Server. Découvrez comment l’utiliser pour spécifier le compte de service SSAS et démarrer ou arrêter le service.
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: a82e0c98-efaa-4b0b-9582-3c879ee42444
author: markingmyname
ms.author: maghan
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 51406cb5941cecb5670008e8da7de7543b4040b3
ms.sourcegitcommit: 6d53ecfdc463914f045c20eda96da39dec22acca
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2020
ms.locfileid: "88900601"
---
# <a name="analysis-server-properties-log-on-tab"></a>Propriétés de Analysis Server (onglet Ouvrir une session)
[!INCLUDE [SQL Server Windows Only - ASDBMI ](../../includes/applies-to-version/sql-windows-only-asdbmi.md)]
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
  
 **Start**  
 Démarrez le service.  
  
 **Stop**  
 Arrête le service.  
  
 **Suspendre**  
 Suspend le service.  
  
 **Reprendre**  
 Reprend un service suspendu.  
  
  
