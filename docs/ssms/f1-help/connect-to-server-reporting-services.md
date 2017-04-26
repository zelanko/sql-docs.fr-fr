---
title: Se connecter au serveur (Reporting Services) | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.connection.login.reportserver.f1
ms.assetid: ef81b658-8eb5-4636-ac81-eead10cc7b9f
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: f48f75a346c30a4a142a67e83949b7f420030726
ms.lasthandoff: 04/11/2017

---
# <a name="connect-to-server-reporting-services"></a>Se connecter au serveur (Reporting Services)
Utilisez cette boîte de dialogue pour afficher ou spécifier des options de connexion à [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion_md.md)].  
  
## <a name="options"></a>Options  
**Type de serveur**  
Quand vous inscrivez un serveur à partir de **l’Explorateur d’objets**, sélectionnez le type de serveur auquel vous connecter : [!INCLUDE[ssDE](../../includes/ssde_md.md)], Analysis Services, Reporting Services ou Integration Services. Le reste de la boîte de dialogue affiche uniquement les options s'appliquant au type de serveur sélectionné. Lors de l’inscription d’un serveur de la liste **Serveurs inscrits**, la zone **Type de serveur** est en lecture seule et indique le type de serveur affiché dans le composant **Serveurs inscrits** . Pour inscrire un autre type de serveur, sélectionnez [!INCLUDE[ssDE](../../includes/ssde_md.md)], Analysis Services, Reporting Services ou Integration Services dans la barre d’outils **Serveurs inscrits** avant de commencer l’inscription d’un nouveau serveur.  
  
**Nom du serveur**  
Le mode serveur de l'instance du serveur de rapports à laquelle vous vous connectez détermine la valeur que vous devez entrer.  
  
Pour un serveur de rapports qui fonctionne en mode natif, spécifiez l'instance du serveur de rapports avec laquelle établir la connexion. Si vous utilisez l'instance par défaut, le nom du serveur est généralement celui de l'ordinateur. Si vous avez installé une instance nommée, ajoutez le nom de l’instance à la suite du nom du serveur, au format suivant : <servername>\\<InstanceName>. Reporting Services utilise la barre oblique inverse pour délimiter le nom de l'instance.  
  
Pour un serveur de rapports qui s'exécute en mode intégré SharePoint, vous devez spécifier un site SharePoint. Vous pouvez spécifier n'importe quel site d'une collection de sites intégrée à [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion_md.md)]. L'URL que vous fournissez doit inclure le préfixe HTTP ou HTTPS. Vous devez avoir l'autorisation d'accéder au site SharePoint pour vous y connecter à partir de Management Studio. Le niveau d'autorisation qui vous est assigné détermine les éléments que vous pouvez consulter et gérer. Pour plus d’informations, consultez [Procédure : inscription et connexion à un serveur de rapports](http://msdn.microsoft.com/en-us/c875ff87-ee7d-443a-a702-bdb4b6c27c6e).  
  
**Authentification**  
[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion_md.md)] peut être configuré pour accepter des demandes d’authentification Windows ou des demandes d’authentification par formulaire gérées par une extension d’authentification personnalisée que vous fournissez. Sélectionnez l'un des modes d'authentification ci-dessous pour vous connecter à [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion_md.md)]:  
  
**Mode d'authentification Windows (authentification Windows)**  
La connexion à l'instance de serveur de rapports s'effectue à l'aide de l'authentification [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows.  
  
**Authentification de base**  
Connectez-vous au moyen de l’ **Authentification de base** si votre installation Reporting Services est configurée pour utiliser l’authentification de base.  
  
**Authentification par formulaire**  
Connectez-vous au moyen de l’ **Authentification par formulaire** si votre installation Reporting Services est configurée pour utiliser une extension d’authentification personnalisée.  
  
**Nom d'utilisateur**  
Entrez le nom d'utilisateur à utiliser pour se connecter. Cette option n'est disponible que si vous avez choisi **Authentification de base** ou **Authentification par formulaire**.  
  
**Mot de passe**  
Entrez le mot de passe correspondant au nom d'utilisateur indiqué. Cette option n'est modifiable que si vous avez choisi **Authentification de base** ou **Authentification par formulaire**.  
  
**Connecterer**  
Cliquez sur cette option pour vous connecter au serveur sélectionné.  
  
**Options**  
Cliquez ici pour afficher des options supplémentaires de connexion au serveur, comme l'inscription d'un serveur et la mémorisation du mot de passe.  
  
## <a name="see-also"></a>Voir aussi  
[Configuration d’une connexion au serveur de rapports](http://msdn.microsoft.com/en-us/9759a9fb-35e9-4215-969b-a9f1fea18487)  
[Procédure : inscription et connexion à un serveur de rapports](http://msdn.microsoft.com/en-us/c875ff87-ee7d-443a-a702-bdb4b6c27c6e)  
[Configuration de l'authentification dans Reporting Services](http://msdn.microsoft.com/en-us/753c2542-0e97-4d8f-a5dd-4b07a5cd10ab)  
  

