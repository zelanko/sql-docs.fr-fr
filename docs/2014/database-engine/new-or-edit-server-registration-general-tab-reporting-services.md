---
title: Nouvelle inscription de serveur ou modifier l’inscription du serveur (onglet général) (Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.registerserver.general.reportserver.f1
ms.assetid: 5f899a8e-52ef-46b5-b7a9-f200ccd9f724
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e0e6d6d3ad57726c42556c9ecc2662edce102e57
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62844265"
---
# <a name="new-or-edit-server-registration-general-tab-reporting-services"></a>Nouvelle inscription de serveur ou Modifier l'enregistrement du serveur (onglet Général) (Reporting Services)
  Cet onglet vous permet de spécifier des options lors de l'inscription d'une instance de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
 Pour accéder à cette page, dans Serveurs inscrits, cliquez sur **Reporting Services** dans la barre d’outils **Serveurs inscrits** , cliquez avec le bouton droit sur un groupe de serveurs inscrits quelconque, tel que **Reporting Services**, pointez sur **Nouveau**, puis cliquez sur **Inscription du serveur**.  
  
## <a name="options"></a>Options  
 **Type de serveur**  
 Lorsqu’un serveur est inscrit à partir de serveurs inscrits, la zone **type de serveur** est en lecture seule et correspond au type de serveur affiché dans le volet **serveurs inscrits** . Pour inscrire un autre type de serveur, cliquez sur le serveur souhaité dans la barre d'outils **Serveurs inscrits** avant de commencer l'inscription du nouveau serveur.  
  
 **Nom du serveur**  
 Spécifiez l'instance de serveur de rapports à laquelle se connecter. Dans [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], vous pouvez accéder à un serveur de rapports par son nom d'instance. Vous pouvez avoir une instance de serveur de rapports pour chaque instance SQL Server que vous installez. Si vous utilisez l'instance par défaut, tapez le nom de l'instance SQL Server. Si vous utilisez une instance nommée, spécifiez cette instance nommée pour vous connecter au serveur de rapports, sous le format MSSQL$InstanceName.  
  
 **Authentification**  
 L'authentification sur un serveur de rapports s'effectue par l'intermédiaire d'IIS (Internet Information Services). Sélectionnez l'un des modes d'authentification ci-dessous pour vous connecter à Reporting Services :  
  
 **Mode d'authentification Windows (authentification Windows)**  
 La connexion à l'instance de serveur de rapports s'effectue à l'aide de l'authentification [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows.  
  
 **Authentification de base**  
 Connectez-vous au moyen de l’ **Authentification de base** si votre installation Reporting Services est configurée pour utiliser l’authentification de base.  
  
 **Authentification par formulaire**  
 Connectez-vous au moyen de l’ **Authentification par formulaire** si votre installation Reporting Services est configurée pour utiliser une extension d’authentification personnalisée.  
  
 **Nom d’utilisateur**  
 Entrez le nom d'utilisateur à utiliser pour se connecter. Cette option n'est disponible que si vous avez choisi **Authentification de base** ou **Authentification par formulaire**.  
  
 **Mot de passe**  
 Entrez le mot de passe correspondant au nom d'utilisateur indiqué. Cette option n'est modifiable que si vous avez choisi **Authentification de base** ou **Authentification par formulaire**.  
  
 **Se souvenir du mot de passe**  
 Permet d'enregistrer le mot de passe que vous avez entré. Cette option n'est disponible que si vous avez cliqué sur **Authentification de base** ou **Authentification par formulaire**.  
  
> [!NOTE]  
>   Si vous avez activé la case à cocher d'enregistrement du mot de passe et si vous ne voulez plus continuer à l'enregistrer, désactivez la case à cocher, puis cliquez sur **Enregistrer**.  
  
 **Nom du serveur inscrit**  
 Le nom qui doit apparaître dans Serveurs inscrits. Il n'est pas nécessaire que ce nom corresponde à celui de la zone **Nom du serveur** .  
  
 **Description du serveur inscrit**  
 Entrez une description facultative du serveur.  
  
 **Test**  
 Cliquez sur cette option pour tester la connexion au serveur sélectionné dans la zone **Nom du serveur**.  
  
 **Save**  
 Cliquez sur ce bouton pour enregistrer les paramètres des serveurs inscrits.  
  
  
