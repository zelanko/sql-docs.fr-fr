---
title: Se connecter au serveur (Moteur de base de données) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.connectoserverunknownservertype.f1
- sql12.swb.connection.login.sqlserver.f1
- sql12.swb.connection.login.sqlce.f1
- sql12.swb.manageSS2k.f1
- sql12.swb.connecttoce.f1
- sql12.swb.connecttoce.connectionproperties.f1
ms.assetid: ee9017b4-8a19-4360-9003-9e6484082d41
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 018ca302bf4d5fe8271369008ffbfec7d228cfbf
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63245740"
---
# <a name="connect-to-server-database-engine"></a>Se connecter au serveur (Moteur de base de données)
  Utilisez cette boîte de dialogue pour afficher ou spécifier des options de connexion à [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Dans la plupart des cas, vous pouvez vous connecter en entrant le nom d’ordinateur du serveur de base de données dans la zone **Nom du serveur** et en cliquant sur **Se connecter**. Si vous vous connectez à [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], utilisez le nom d’ordinateur suivi de **\sqlexpress**.  
  
 De nombreux facteurs affectent votre capacité à vous connecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="options"></a>Options  
 **Type de serveur**  
 Lors de l'inscription d'un serveur dans l'Explorateur d'objets, sélectionnez le type de serveur auquel se connecter : [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]ou [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Le reste de la boîte de dialogue affiche uniquement les options s'appliquant au type de serveur sélectionné. Lors de l’inscription d’un serveur de la liste Serveurs inscrits, la zone **Type de serveur** est en lecture seule et indique le type de serveur affiché dans le composant Serveurs inscrits. Pour inscrire un autre type de serveur, sélectionnez [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], [!INCLUDE[ssEW](../../includes/ssew-md.md)]ou [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] dans la barre d'outils Serveurs inscrits avant d'entamer l'inscription d'un nouveau serveur.  
  
 **Nom du serveur**  
 Sélectionnez l'instance de serveur à laquelle se connecter. La dernière instance de serveur à laquelle une connexion a été établie est affichée par défaut.  
  
> [!NOTE]  
>  Pour vous connecter à une instance utilisateur active de [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] , utilisez le protocole des canaux nommés en spécifiant le nom du canal, par exemple np:\\\\.\pipe\3C3DF6B1-2262-47\tsql\query. Pour plus d’informations, consultez la documentation de [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] .  
  
 **Authentification**  
 Deux modes d’authentification sont disponibles lors de la connexion à une instance de la [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
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
  
 **Se connecter**  
 Cliquez sur cette option pour vous connecter au serveur sélectionné.  
  
 **Options**  
 Cliquez ici pour afficher des options supplémentaires de connexion au serveur, comme l'inscription d'un serveur et la mémorisation du mot de passe.  
  
  
