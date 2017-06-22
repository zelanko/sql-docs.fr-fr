---
title: "Se connecter au serveur (Moteur de base de données) | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 01/30/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.connectoserverunknownservertype.f1
- sql13.swb.connection.login.sqlce.f1
- sql13.swb.connecttoce.f1
- SQL13.SWB.CONNECTION.LOGIN.SQLSERVER.F1
- sql13.swb.connection.login.sqlserver.f1
- sql13.swb.manageSS2k.f1
ms.assetid: ee9017b4-8a19-4360-9003-9e6484082d41
caps.latest.revision: 6
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: d421bcb09ec7ebde28b5d1cce6eca2263cfb1c48
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="connect-to-server-database-engine"></a>Se connecter au serveur (Moteur de base de données)
Utilisez cette boîte de dialogue pour afficher ou spécifier des options de connexion à [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]. Dans la plupart des cas, vous pouvez vous connecter en entrant le nom d’ordinateur du serveur de base de données dans la zone **Nom du serveur** et en cliquant sur **Se connecter**. Si vous vous connectez à [!INCLUDE[ssExpress](../../includes/ssexpress_md.md)], utilisez le nom d’ordinateur suivi de **\sqlexpress**.  
  
De nombreux facteurs affectent votre capacité à vous connecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
## <a name="options"></a>Options  
**Type de serveur**  
Lors de l'inscription d'un serveur dans l'Explorateur d'objets, sélectionnez le type de serveur auquel se connecter : [!INCLUDE[ssDE](../../includes/ssde_md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion_md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion_md.md)]ou [!INCLUDE[ssISnoversion](../../includes/ssisnoversion_md.md)]. Le reste de la boîte de dialogue affiche uniquement les options s'appliquant au type de serveur sélectionné. Lors de l’inscription d’un serveur de la liste Serveurs inscrits, la zone **Type de serveur** est en lecture seule et indique le type de serveur affiché dans le composant Serveurs inscrits. Pour inscrire un autre type de serveur, sélectionnez [!INCLUDE[ssDE](../../includes/ssde_md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion_md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion_md.md)], [!INCLUDE[ssEW](../../includes/ssew_md.md)]ou [!INCLUDE[ssISnoversion](../../includes/ssisnoversion_md.md)] dans la barre d'outils Serveurs inscrits avant d'entamer l'inscription d'un nouveau serveur.  
  
**Nom du serveur**  
Sélectionnez l'instance de serveur à laquelle se connecter. La dernière instance de serveur à laquelle une connexion a été établie est affichée par défaut.  
  
> [!NOTE]  
> Pour vous connecter à une instance utilisateur active de [!INCLUDE[ssExpress](../../includes/ssexpress_md.md)] , utilisez le protocole des canaux nommés en spécifiant le nom du canal, par exemple np:\\\\.\pipe\3C3DF6B1-2262-47\tsql\query. Pour plus d’informations, consultez la documentation de [!INCLUDE[ssExpress](../../includes/ssexpress_md.md)] .  
  
**Authentification**  
Trois modes d’authentification sont disponibles lors de la connexion à une instance du [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
**Authentification Windows**  
[!INCLUDE[msCoName](../../includes/msconame_md.md)] Le mode d’authentification Windows permet à l’utilisateur de se connecter au moyen d’un compte d’utilisateur Windows.  
  
**Authentification SQL Server**  
Quand un utilisateur se connecte avec un nom d’accès et un mot de passe spécifiés à partir d’une connexion non autorisée, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] réalise l’authentification en vérifiant si un compte de connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] a été défini et si le mot de passe spécifié correspond à celui enregistré précédemment. Si [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ne possède pas de compte de connexion, l'authentification échoue et un message d'erreur est envoyé à l'utilisateur.  
  
> [!IMPORTANT]  
> Si possible, utilisez l’authentification Windows ou l’authentification par mot de passe Active Directory.  
  
**Authentification Active Directory universelle**  
L’authentification Active Directory universelle est un processus interactif qui prend en charge Azure Multi-Factor Authentication (MFA). Azure MFA contribue à protéger l’accès aux données et aux applications tout en répondant à la volonté des utilisateur d’avoir un processus d’authentification simple. Il fournit une authentification renforcée avec un éventail d’options de vérification simples (appel téléphonique, SMS, cartes à puce avec code confidentiel ou notification d’application mobile), ce qui permet aux utilisateurs de choisir la méthode qu’ils préfèrent. Quand le compte d’utilisateur est configuré pour MFA, le processus d’authentification interactif demande une plus grande intervention de l’utilisateur par le biais de boîtes de dialogue contextuelles, d’utilisation de carte à puce, et ainsi de suite. Quand le compte d’utilisateur est configuré pour MFA, l’utilisateur doit sélectionner Authentification universelle Azure pour se connecter. Si le compte d’utilisateur ne nécessite pas MFA, l’utilisateur peut toujours utiliser les deux autres options d’authentification Azure Active Directory. Pour plus d’informations, consultez [Prise en charge SSMS pour Azure AD MFA avec SQL Database et SQL Data Warehouse](https://azure.microsoft.com/documentation/articles/sql-database-ssms-mfa-authentication/). Nécessite au moins SSMS version 16.3 (août 2016).

**Authentification par mot de passe Active Directory**  
L’authentification Azure Active Directory est un mécanisme de connexion à [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssSDSfull](../../includes/sssdsfull_md.md)] à l’aide d’identités dans Azure Active Directory (Azure AD).  Utilisez cette méthode pour vous connecter à [!INCLUDE[ssSDS](../../includes/sssds_md.md)] si vous êtes connecté à Windows à l’aide d’informations d’identification d’un domaine qui n’est pas fédéré avec Azure, ou si vous utilisez l’authentification Azure AD avec Azure AD basée sur le domaine client ou initial. Pour plus d’informations, voir [Connexion à la base de données SQL à l’aide de l’authentification Azure Active Directory](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/).  
  
**Authentification intégrée à Active Directory**  
L’authentification Azure Active Directory est un mécanisme de connexion à [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssSDSfull](../../includes/sssdsfull_md.md)] à l’aide d’identités dans Azure Active Directory (Azure AD). Utilisez cette méthode pour vous connecter à [!INCLUDE[ssSDS](../../includes/sssds_md.md)] si vous êtes connecté à Windows à l’aide de vos informations d’identification Azure Active Directory à partir d’un domaine fédéré. Pour plus d’informations, voir [Connexion à la base de données SQL à l’aide de l’authentification Azure Active Directory](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/).  
  
**Nom d'utilisateur**  
Nom d’utilisateur Windows avec lequel vous connecter. Cette option est disponible uniquement si vous avez choisi la connexion avec **l’Authentification par mot de passe Active Directory**. Elle est en lecture seule quand vous sélectionnez **Authentification Windows**.  
  
**Connexion**  
Entrez le nom d'accès avec lequel se connecter. Cette option est disponible uniquement si vous avez choisi la connexion avec l’Authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou l’Authentification par mot de passe Active Directory.  
  
**Mot de passe**  
Entrez le mot de passe utilisé avec la connexion. Cette option est modifiable uniquement si vous avez choisi la connexion avec l’Authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou l’Authentification par mot de passe Active Directory.  
  
**Se connecter**  
Cliquez sur cette option pour vous connecter au serveur sélectionné.  
  
**Options**  
Cliquez ici pour afficher des options supplémentaires de connexion au serveur, comme l'inscription d'un serveur et la mémorisation du mot de passe.  
  

