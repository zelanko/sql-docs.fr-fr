---
title: Se connecter au serveur (page Connexion) — Integration Services | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.connecttodtsserver.login.f1
- sql12.swb.connecttodts.login.f1
ms.assetid: 402c2de4-f4ea-40b0-909f-3ddf3bd59950
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 53a9793fc2a8770c8d926c945ba31a335bdfed3f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62808726"
---
# <a name="connect-to-server-login-page-integration-services"></a>Se connecter au serveur (page Connexion) — Integration Services
  Utilisez cet onglet pour afficher ou spécifier les options suivantes pour la connexion à [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
## <a name="options"></a>Options  
 **Type de serveur**  
 Lorsque vous inscrivez un serveur depuis l'Explorateur d'objets, sélectionnez le type de serveur pour vous connecter à : [!INCLUDE[ssDE](../includes/ssde-md.md)], Analysis Services, Reporting Services ou Integration Services. Le reste de la boîte de dialogue affiche uniquement les options s'appliquant au type de serveur sélectionné. Au moment de l’inscription d’un serveur de la liste Serveurs inscrits, la zone **Type de serveur** est en lecture seule et indique le type de serveur affiché dans le composant Serveurs inscrits. Pour inscrire un autre type de serveur, sélectionnez [!INCLUDE[ssDE](../includes/ssde-md.md)], Analysis Services, Reporting Services ou Integration Services dans la barre d'outils Serveurs inscrits avant de commencer l'inscription d'un nouveau serveur.  
  
 **Nom du serveur**  
 Sélectionnez le serveur auquel vous connecter. La dernière instance de serveur à laquelle une connexion a été établie est affichée par défaut.  
  
> [!NOTE]  
>  N’utilisez pas  *\<nom_serveur >* \\ *\<nom_instance >* , car [!INCLUDE[ssIS](../includes/ssis-md.md)] ne prend pas en charge plusieurs instances sur un ordinateur.  
  
 **Authentification**  
 Seule l'authentification [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows est disponible pour [!INCLUDE[ssIS](../includes/ssis-md.md)]. Le mode d’authentification Windows permet à l’utilisateur de se connecter au moyen d’un compte d’utilisateur Windows.  
  
 **Nom d'utilisateur**  
 Cette option n'est pas disponible car seule l'authentification Windows est disponible pour [!INCLUDE[ssIS](../includes/ssis-md.md)].  
  
 **Mot de passe**  
 Cette option n'est pas disponible car seule l'authentification Windows est disponible pour [!INCLUDE[ssIS](../includes/ssis-md.md)].  
  
 **Mémoriser le mot de passe**  
 Cette option n'est pas disponible car seule l'authentification Windows est disponible pour [!INCLUDE[ssIS](../includes/ssis-md.md)].  
  
 **Connecterer**  
 Établit la connexion au serveur sélectionné.  
  
 **Options**  
 Cliquez sur cette option pour modifier l'apparence de la boîte de dialogue en masquant les options de connexion serveur supplémentaires, comme la mémorisation du mot de passe.  
  
  
