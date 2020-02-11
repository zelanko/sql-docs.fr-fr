---
title: Créer un modèle à l’aide de Gestionnaire de rapports | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- report models [Reporting Services], creating
- Report Manager [Reporting Services], model creation
ms.assetid: 8e5d2bd3-48ec-45f3-afee-6d86797c8f28
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7b67e2a7048520d8a411789e501dbbe545d3cc02
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66109671"
---
# <a name="create-a-model-using-report-manager"></a>Créer un modèle à l'aide du Gestionnaire de rapports
  Vous pouvez générer des modèles à partir d'un cube [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , d'une base de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ou d'une base de données Oracle à l'aide du Gestionnaire de rapports. Les modèles de rapport sont générés à partir de sources de données partagées publiées sur le serveur de rapports. Si vous ne possédez pas déjà une source de données partagée, vous devez en créer une.  
  
 Le modèle de rapport que vous générez est entièrement basé sur le schéma de la source de données partagée. Vous ne pouvez pas choisir les parties de la source de données à inclure dans le modèle, ni modifier les règles ou les métadonnées d'un modèle généré. Toutefois, vous pouvez définir des propriétés du modèle une fois celui-ci généré et définir les attributions de rôles qui limitent l'accès à l'ensemble ou une partie du modèle.  
  
> [!NOTE]  
>  Un modèle basé sur Oracle, généré à l' [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[offSPServ](../includes/offspserv-md.md)] aide [!INCLUDE[SPS2010](../includes/sps2010-md.md)] de gestionnaire de rapports ou 2007, inclut des objets de base de données qui font partie du schéma du compte d’utilisateur utilisé pour se connecter à la source de données Oracle. Le nom du compte d'utilisateur est spécifié dans les informations d'identification des propriétés de la source de données.  
  
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
  
    -   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Authentification : sélectionnez cette option si vous souhaitez que les utilisateurs utilisent [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] un compte de connexion que vous avez créé. Les utilisateurs doivent fournir un nom et un mot de passe de connexion [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] valides.  
  
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
 [Connexions de données, sources de données et chaînes de connexion dans Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md)   
 [Page nouvelle source de données &#40;Gestionnaire de rapports&#41;](../../2014/reporting-services/new-data-source-page-report-manager.md)  
  
  
