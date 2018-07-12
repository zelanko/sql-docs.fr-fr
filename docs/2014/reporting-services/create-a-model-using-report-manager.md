---
title: Créer un modèle à l’aide du Gestionnaire de rapports | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- report models [Reporting Services], creating
- Report Manager [Reporting Services], model creation
ms.assetid: 8e5d2bd3-48ec-45f3-afee-6d86797c8f28
caps.latest.revision: 28
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: e3a4f951a901361e47e1582146d306955da0e9bb
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37175088"
---
# <a name="create-a-model-using-report-manager"></a>Créer un modèle à l'aide du Gestionnaire de rapports
  Vous pouvez générer des modèles à partir d'un cube [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , d'une base de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ou d'une base de données Oracle à l'aide du Gestionnaire de rapports. Les modèles de rapport sont générés à partir de sources de données partagées publiées sur le serveur de rapports. Si vous ne possédez pas déjà une source de données partagée, vous devez en créer une.  
  
 Le modèle de rapport que vous générez est entièrement basé sur le schéma de la source de données partagée. Vous ne pouvez pas choisir les parties de la source de données à inclure dans le modèle, ni modifier les règles ou les métadonnées d'un modèle généré. Toutefois, vous pouvez définir des propriétés du modèle une fois celui-ci généré et définir les attributions de rôles qui limitent l'accès à l'ensemble ou une partie du modèle.  
  
> [!NOTE]  
>  Un modèle basé sur Oracle et généré à l’aide du Gestionnaire de rapports ou [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[offSPServ](../includes/offspserv-md.md)] 2007 [!INCLUDE[SPS2010](../includes/sps2010-md.md)] inclut des objets de base de données qui font partie du schéma pour le compte d’utilisateur utilisé pour se connecter à la source de données Oracle. Le nom du compte d'utilisateur est spécifié dans les informations d'identification des propriétés de la source de données.  
  
### <a name="to-create-a-new-data-source-for-a-report-model-using-report-manager"></a>Pour créer une nouvelle source de données pour un modèle de rapport à l'aide du Gestionnaire de rapports  
  
1.  Dans le navigateur Web, tapez l'URL du serveur de rapports dans la barre d'adresses.  
  
2.  Cliquez sur **Nouvelle source de données**.  
  
3.  Dans la zone **Nom** , entrez un nom pour la source de données.  
  
4.  Si vous le souhaitez, entrez une brève description du modèle dans la zone **Description** .  
  
5.  Vérifiez que la case à cocher **Activer cette source de données** est activée.  
  
6.  Dans la liste **Type de connexion** , sélectionnez le type de source de données auquel vous souhaitez vous connecter. Il doit s'agir de l'un des types de connexions suivants : **Oracle**, **Microsoft SQL Server** ou **Microsoft SQL Server Analysis Services**.  
  
7.  Dans la zone **Chaîne de connexion** , entrez la chaîne de connexion qui pointe vers la base de données.  
  
8.  Sélectionnez la méthode de connexion dont les utilisateurs du Générateur de rapports devront se servir pour se connecter à la base de données.  
  
    -   Authentification Windows : sélectionnez cette option si vous souhaitez que le système d'exploitation authentifie les utilisateurs [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Cette option permet à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] d'utiliser les fonctionnalités de sécurité de Windows, telles que le chiffrement des mots de passe, pour authentifier les utilisateurs. Nous vous recommandons vivement de sélectionner cette option.  
  
    -   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentification : Sélectionnez cette option lorsque vous souhaitez que les utilisateurs d’utiliser un [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] compte de connexion que vous avez créé. Les utilisateurs doivent fournir un nom et un mot de passe de connexion [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] valides.  
  
        > [!CAUTION]  
        >  Dans la mesure du possible, utilisez l’authentification Windows.  
  
9. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-create-a-report-model-using-report-manager"></a>Pour créer un modèle de rapport à l'aide du Gestionnaire de rapports  
  
1.  Dans le Gestionnaire de rapports, sélectionnez la source de données à utiliser pour votre modèle.  
  
     La page Propriétés apparaît.  
  
2.  Vérifiez que vous souhaitez utiliser les options spécifiées pour la source de données.  
  
3.  Cliquez sur **Générer le modèle**.  
  
     La page Général apparaît pour la source de données.  
  
4.  Dans la zone **Nom** , entrez un nom pour le modèle de rapport.  
  
5.  Dans la zone **Description** , entrez une brève description du modèle.  
  
6.  Pour spécifier un nouvel emplacement dans lequel enregistrer le modèle de rapport, cliquez sur **Modifier l'emplacement**.  
  
     Par défaut, le modèle de rapport est enregistré dans la page d'accueil du Gestionnaire de rapports.  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     Le modèle de rapport est créé et enregistré à l'emplacement que vous avez spécifié. Vous pouvez octroyer des autorisations à ce modèle à l'aide du Gestionnaire de rapports.  
  
## <a name="see-also"></a>Voir aussi  
 [Octroi d'autorisations sur un serveur de rapports en mode natif](security/granting-permissions-on-a-native-mode-report-server.md)   
 [Connexions de données, Sources de données et chaînes de connexion dans Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md)   
 [Page Nouvelle source de données &#40;Gestionnaire de rapports&#41;](../../2014/reporting-services/new-data-source-page-report-manager.md)  
  
  
