---
title: Se connecter au serveur (Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.connection.login.reportserver.f1
ms.assetid: ef81b658-8eb5-4636-ac81-eead10cc7b9f
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 41e0ca3ee7ccaa7bb57e5667092c0660e35c4c52
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62808676"
---
# <a name="connect-to-server-reporting-services"></a>Se connecter au serveur (Reporting Services)
  Utilisez cette boîte de dialogue pour afficher ou spécifier les options [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]de connexion à.  
  
## <a name="options"></a>Options  
 **Type de serveur**  
 Lors de l’inscription d’un serveur à partir de l' **Explorateur d’objets**, sélectionnez le [!INCLUDE[ssDE](../includes/ssde-md.md)]type de serveur auquel vous souhaitez vous connecter :, Analysis Services, Reporting Services ou Integration Services. Le reste de la boîte de dialogue affiche uniquement les options s'appliquant au type de serveur sélectionné. Lors de l’inscription d’un serveur à partir de **serveurs inscrits**, la zone **type de serveur** est en lecture seule et correspond au type de serveur affiché dans le composant **serveurs inscrits** . Pour inscrire un autre type de serveur, sélectionnez [!INCLUDE[ssDE](../includes/ssde-md.md)], Analysis Services, Reporting Services ou Integration Services dans la barre d’outils **serveurs inscrits** avant de commencer à inscrire un nouveau serveur.  
  
 **Nom du serveur**  
 Le mode serveur de l'instance du serveur de rapports à laquelle vous vous connectez détermine la valeur que vous devez entrer.  
  
 Pour un serveur de rapports qui fonctionne en mode natif, spécifiez l'instance du serveur de rapports avec laquelle établir la connexion. Si vous utilisez l'instance par défaut, le nom du serveur est généralement celui de l'ordinateur. Si vous avez installé une instance nommée, ajoutez le nom de l’instance au nom du serveur au \<format suivant \\ : NomServeur\>><nom_instance. Reporting Services utilise la barre oblique inverse pour délimiter le nom de l'instance.  
  
 Pour un serveur de rapports qui s'exécute en mode intégré SharePoint, vous devez spécifier un site SharePoint. Vous pouvez spécifier n'importe quel site d'une collection de sites intégrée à [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. L'URL que vous fournissez doit inclure le préfixe HTTP ou HTTPS. Vous devez avoir l'autorisation d'accéder au site SharePoint pour vous y connecter à partir de Management Studio. Le niveau d'autorisation qui vous est assigné détermine les éléments que vous pouvez consulter et gérer. Pour plus d’informations, consultez [Se connecter à un serveur de rapports dans Management Studio](../reporting-services/tools/connect-to-a-report-server-in-management-studio.md).  
  
 **Authentification**  
 
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] peut être configuré pour accepter des demandes d’authentification Windows ou des demandes d’authentification par formulaire gérées par une extension d’authentification personnalisée que vous fournissez. Sélectionnez l'un des modes d'authentification ci-dessous pour vous connecter à [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]:  
  
 **Mode d’authentification Windows (authentification Windows)**  
 La connexion à l'instance de serveur de rapports s'effectue à l'aide de l'authentification [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows.  
  
 **Authentification de base**  
 Connectez-vous au moyen de l’ **Authentification de base** si votre installation Reporting Services est configurée pour utiliser l’authentification de base.  
  
 **Authentification par formulaire**  
 Connectez-vous au moyen de l’ **Authentification par formulaire** si votre installation Reporting Services est configurée pour utiliser une extension d’authentification personnalisée.  
  
 **Nom d’utilisateur**  
 Entrez le nom d'utilisateur à utiliser pour se connecter. Cette option n'est disponible que si vous avez choisi **Authentification de base** ou **Authentification par formulaire**.  
  
 **Mot de passe**  
 Entrez le mot de passe correspondant au nom d’utilisateur. Cette option n'est modifiable que si vous avez choisi **Authentification de base** ou **Authentification par formulaire**.  
  
 **Connexion**  
 Cliquez sur cette option pour vous connecter au serveur sélectionné.  
  
 **Options**  
 Cliquez ici pour afficher des options supplémentaires de connexion au serveur, comme l'inscription d'un serveur et la mémorisation du mot de passe.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer une connexion à la base de données du serveur de rapports &#40;SSRS Configuration Manager&#41;](../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)   
 [Se connecter à un serveur de rapports dans Management Studio](../reporting-services/tools/connect-to-a-report-server-in-management-studio.md)   
 [Authentification avec le serveur de rapports](../reporting-services/security/authentication-with-the-report-server.md)  
  
  
