---
title: Se connecter au serveur (page Connexion) — Moteur de base de données | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.connecttosqlserver.login.f1
ms.assetid: e08cfbc3-bed5-4401-a13b-1c66d902fe32
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2fe246a1f8baf1ab9f60ab1fa73e21e81c052aa1
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "70153706"
---
# <a name="connect-to-server-login-page-database-engine"></a>Se connecter au serveur (page Connexion) — Moteur de base de données
  Utilisez cet onglet pour afficher ou spécifier les options de connexion à [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
> [!NOTE]  
>  Pour vous connecter avec l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit être configuré en mode d'authentification Windows et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour plus d’informations sur la façon de déterminer le mode d’authentification et de modifier le mode d’authentification, consultez [modifier le mode d’authentification du serveur](../../database-engine/configure-windows/change-server-authentication-mode.md).  
  
## <a name="options"></a>Options  
 **Type de serveur**  
 Lorsque vous inscrivez un serveur depuis l'Explorateur d'objets, sélectionnez le type de serveur pour vous connecter à : [!INCLUDE[ssDE](../../includes/ssde-md.md)], Analysis Services, Reporting Services ou Integration Services. Le reste de la boîte de dialogue affiche uniquement les options s'appliquant au type de serveur sélectionné. Lors de l’inscription d’un serveur de la liste Serveurs inscrits, la zone **Type de serveur** est en lecture seule et indique le type de serveur affiché dans le composant Serveurs inscrits. Pour inscrire un autre type de serveur, sélectionnez [!INCLUDE[ssDE](../../includes/ssde-md.md)], Analysis Services, Reporting Services ou Integration Services dans la barre d'outils Serveurs inscrits avant de commencer l'inscription d'un nouveau serveur.  
  
 Quand vous vous connectez à une instance du moteur de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par le biais de [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], vous devez utiliser l’authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et spécifier une base de données dans la boîte de dialogue **Se connecter au serveur** , sous l’onglet **Propriétés de connexion** . Vérifiez que vous avez coché la case **Chiffrer la connexion** .  
  
 Par défaut, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se connecte à **master**. Si vous spécifiez une base de données utilisateur, vous ne verrez que la base de données et ses objets dans l'Explorateur d'objets. Si vous vous connectez à **master**, vous pouvez consulter toutes les bases de données. Pour plus d’informations, consultez la [vue d’ensemble de Azure SQL Database](/azure/sql-database/sql-database-technical-overview).  
  
 **Nom du serveur**  
 Sélectionnez l'instance de serveur à laquelle se connecter. La dernière instance de serveur à laquelle une connexion a été établie est affichée par défaut.  
  
 **Authentification**  
 Deux modes d'authentification sont disponibles lors de la connexion à une instance de [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
 Quand vous vous connectez à une instance du moteur de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par le biais de [!INCLUDE[ssSDS](../../includes/sssds-md.md)], vous devez utiliser l’authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et spécifier une base de données dans la boîte de dialogue **Se connecter au serveur** , sous l’onglet **Propriétés de connexion** . Vérifiez que vous avez coché la case **Chiffrer la connexion** .  
  
 Par défaut, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se connecte à **master**. Si vous spécifiez une base de données utilisateur, vous ne verrez que la base de données et ses objets dans l'Explorateur d'objets. Si vous vous connectez à **master**, vous pouvez consulter toutes les bases de données. Pour plus d’informations, consultez la [vue d’ensemble de Azure SQL Database](/azure/sql-database/sql-database-technical-overview).  
  
 **Mode d'authentification Windows (authentification Windows)**  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Le mode d’authentification Windows permet à l’utilisateur de se connecter au moyen d’un compte d’utilisateur Windows.  
  
 **Authentification SQL Server**  
 Quand un utilisateur se connecte avec un nom d’accès et un mot de passe spécifiés à partir d’une connexion non autorisée, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] réalise l’authentification en vérifiant si un compte de connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a été défini et si le mot de passe spécifié correspond à celui enregistré précédemment. Si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne possède pas de compte de connexion, l'authentification échoue et un message d'erreur est envoyé à l'utilisateur.  
  
> [!IMPORTANT]  
>  Lorsque c'est possible, utilisez l'authentification Windows.  
  
 **Nom d'utilisateur**  
 Entrez le nom d'utilisateur avec lequel se connecter. Cette option est uniquement disponible si vous avez choisi la connexion avec l'authentification Windows.  
  
 **Connexion**  
 Entrez le nom d'accès avec lequel se connecter. Cette option est uniquement disponible si vous avez choisi la connexion avec l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Mot de passe**  
 Entrez le mot de passe utilisé avec la connexion. Ce mot de passe ne peut être modifié que si vous avez choisi la connexion avec l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Se souvenir du mot de passe**  
 Cliquez sur cette option pour que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] enregistre le mot de passe entré. Cette option n’est affichée que si vous avez choisi la connexion avec l’authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Connexion**  
 Cliquez sur cette option pour vous connecter au serveur sélectionné.  
  
 **Options**  
 Cliquez sur cette option pour modifier l’apparence de la boîte de dialogue en masquant les options de connexion serveur supplémentaires, comme la mémorisation du mot de passe.  
  
  
