---
title: "Se connecter au serveur (page Connexion) — Moteur de base de données | Microsoft Docs"
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
- sql13.swb.connecttosqlserver.login.f1
ms.assetid: e08cfbc3-bed5-4401-a13b-1c66d902fe32
caps.latest.revision: 6
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 1556c7facc4a671767fe2d6c061b4f6655ba521b
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="connect-to-server-login-page-database-engine"></a>Se connecter au serveur (page Connexion) — Moteur de base de données
Utilisez cet onglet pour afficher ou spécifier les options de connexion à [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)].  
  
> [!NOTE]  
> Pour vous connecter avec l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] , [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] doit être configuré en mode d'authentification Windows et [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] . Pour plus d’informations sur la détermination et la modification du mode d’authentification, consultez [Procédure : modification du mode d’authentification du serveur](http://msdn.microsoft.com/en-us/79babcf8-19fd-4495-b8eb-453dc575cac0).  
  
## <a name="options"></a>Options  
**Type de serveur**  
Lorsque vous inscrivez un serveur depuis l'Explorateur d'objets, sélectionnez le type de serveur pour vous connecter à : [!INCLUDE[ssDE](../../includes/ssde_md.md)], Analysis Services, Reporting Services ou Integration Services. Le reste de la boîte de dialogue affiche uniquement les options s'appliquant au type de serveur sélectionné. Lors de l’inscription d’un serveur de la liste Serveurs inscrits, la zone **Type de serveur** est en lecture seule et indique le type de serveur affiché dans le composant Serveurs inscrits. Pour inscrire un autre type de serveur, sélectionnez [!INCLUDE[ssDE](../../includes/ssde_md.md)], Analysis Services, Reporting Services ou Integration Services dans la barre d'outils Serveurs inscrits avant de commencer l'inscription d'un nouveau serveur.  
  
Quand vous vous connectez à une instance du moteur de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] par le biais du [!INCLUDE[ssSDSfull](../../includes/sssdsfull_md.md)], vous devez utiliser l’authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] et spécifier une base de données dans la boîte de dialogue **Se connecter au serveur** , sous l’onglet **Propriétés de connexion** . Vérifiez que vous avez coché la case **Chiffrer la connexion** .  
  
Par défaut, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] se connecte à **master**. Si vous spécifiez une base de données utilisateur, vous ne verrez que la base de données et ses objets dans l'Explorateur d'objets. Si vous vous connectez à **master**, vous pouvez consulter toutes les bases de données. Pour plus d’informations, consultez [Présentation de Microsoft Azure SQL Database](http://go.microsoft.com/fwlink/?LinkId=163948).  
  
**Nom du serveur**  
Sélectionnez l'instance de serveur à laquelle se connecter. La dernière instance de serveur à laquelle une connexion a été établie est affichée par défaut.  
  
**Authentification**  
Deux modes d'authentification sont disponibles lors de la connexion à une instance de [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)].  
  
Quand vous vous connectez à une instance du moteur de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] par le biais du [!INCLUDE[ssSDS](../../includes/sssds_md.md)], vous devez utiliser l’authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] et spécifier une base de données dans la boîte de dialogue **Se connecter au serveur** , sous l’onglet **Propriétés de connexion** . Vérifiez que vous avez coché la case **Chiffrer la connexion** .  
  
Par défaut, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] se connecte à **master**. Si vous spécifiez une base de données utilisateur, vous ne verrez que la base de données et ses objets dans l'Explorateur d'objets. Si vous vous connectez à **master**, vous pouvez consulter toutes les bases de données. Pour plus d’informations, consultez [Présentation de Microsoft Azure SQL Database](http://go.microsoft.com/fwlink/?LinkId=163948).  
  
**Authentification Windows**  
[!INCLUDE[msCoName](../../includes/msconame_md.md)] Le mode d’authentification Windows permet à l’utilisateur de se connecter au moyen d’un compte d’utilisateur Windows.  
  
**Authentification SQL Server**  
Quand un utilisateur se connecte avec un nom d’accès et un mot de passe spécifiés à partir d’une connexion non autorisée, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] réalise l’authentification en vérifiant si un compte de connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] a été défini et si le mot de passe spécifié correspond à celui enregistré précédemment. Si [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ne possède pas de compte de connexion, l'authentification échoue et un message d'erreur est envoyé à l'utilisateur.  
  
> [!IMPORTANT]  
> Lorsque c'est possible, utilisez l'authentification Windows.  
  
**Authentification Active Directory universelle**  
L’authentification Active Directory universelle est un processus interactif qui prend en charge Azure Multi-Factor Authentication (MFA). Azure MFA contribue à protéger l’accès aux données et aux applications tout en répondant à la volonté des utilisateur d’avoir un processus d’authentification simple. Il fournit une authentification renforcée avec un éventail d’options de vérification simples (appel téléphonique, SMS, cartes à puce avec code confidentiel ou notification d’application mobile), ce qui permet aux utilisateurs de choisir la méthode qu’ils préfèrent. Quand le compte d’utilisateur est configuré pour MFA, le processus d’authentification interactif demande une plus grande intervention de l’utilisateur par le biais de boîtes de dialogue contextuelles, d’utilisation de carte à puce, et ainsi de suite. Quand le compte d’utilisateur est configuré pour MFA, l’utilisateur doit sélectionner Authentification universelle Azure pour se connecter. Si le compte d’utilisateur ne nécessite pas MFA, l’utilisateur peut toujours utiliser les deux autres options d’authentification Azure Active Directory. Pour plus d’informations, consultez [Prise en charge SSMS pour Azure AD MFA avec SQL Database et SQL Data Warehouse](https://azure.microsoft.com/documentation/articles/sql-database-ssms-mfa-authentication/). Nécessite au moins SSMS version 16.3 (août 2016).
  
**Authentification par mot de passe Active Directory**  
L’authentification Azure Active Directory est un mécanisme de connexion à [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssSDSfull](../../includes/sssdsfull_md.md)] à l’aide d’identités dans Azure Active Directory (Azure AD).  Utilisez cette méthode pour vous connecter à [!INCLUDE[ssSDS](../../includes/sssds_md.md)] si vous êtes connecté à Windows à l’aide d’informations d’identification d’un domaine qui n’est pas fédéré avec Azure, ou si vous utilisez l’authentification Azure AD avec Azure AD basée sur le domaine client ou initial. Pour plus d’informations, voir [Connexion à la base de données SQL à l’aide de l’authentification Azure Active Directory](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/).  
  
**Authentification intégrée à Active Directory**  
L’authentification Azure Active Directory est un mécanisme de connexion à [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssSDSfull](../../includes/sssdsfull_md.md)] à l’aide d’identités dans Azure Active Directory (Azure AD). Utilisez cette méthode pour vous connecter à [!INCLUDE[ssSDS](../../includes/sssds_md.md)] si vous êtes connecté à Windows à l’aide de vos informations d’identification Azure Active Directory à partir d’un domaine fédéré. Pour plus d’informations, voir [Connexion à la base de données SQL à l’aide de l’authentification Azure Active Directory](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/).  
  
**Nom d'utilisateur**  
Nom d’utilisateur Windows avec lequel vous connecter. Cette option est disponible uniquement si vous avez choisi la connexion avec **l’Authentification par mot de passe Active Directory**. Elle est en lecture seule quand vous sélectionnez **Authentification Windows**.  
  
**Connexion**  
Entrez le nom d'accès avec lequel se connecter. Cette option est uniquement disponible si vous avez choisi la connexion avec l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .  
  
**Mot de passe**  
Entrez le mot de passe utilisé avec la connexion. Ce mot de passe ne peut être modifié que si vous avez choisi la connexion avec l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .  
  
**Mémoriser le mot de passe**  
Cliquez sur cette option pour que [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] enregistre le mot de passe entré. Cette option n’est affichée que si vous avez choisi la connexion avec l’authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .  
  
**Connecter**  
Cliquez sur cette option pour vous connecter au serveur sélectionné.  
  
**Options**  
Cliquez sur cette option pour modifier l’apparence de la boîte de dialogue en masquant les options de connexion serveur supplémentaires, comme la mémorisation du mot de passe.  
  

