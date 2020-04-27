---
title: Définir les propriétés du service Integration Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services service, configuring
- Integration Services service, properties
ms.assetid: 3a8ad546-0f58-4b31-ab56-58d6313b1098
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: c40ec2d7da7dc8f46644632d29b6fb8d1101ff9b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66055637"
---
# <a name="set-the-properties-of-the-integration-services-service"></a>définir les propriétés du service Integration Services
    
> [!IMPORTANT]  
>  Cette rubrique présente le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , un service Windows qui permet de gérer les packages [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] prend en charge le service pour la compatibilité avec les versions antérieures de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. À compter de [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], vous pouvez gérer des objets tels que des packages sur le serveur Integration Services.  
  
 Le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] gère et surveille les packages dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Lorsque vous installez [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]pour la première [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] fois, le service est démarré et le type de démarrage du service est défini sur automatique.  
  
 Après avoir installé le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , vous pouvez définir les propriétés du service en utilisant le composant logiciel enfichable Gestionnaire de configuration SQL Server ou Services MMC.  
  
 Pour configurer d'autres fonctionnalités importantes du service, y compris les emplacements auxquels il stocke et gère les packages, vous devez modifier le fichier de configuration du service. Pour plus d’informations, consultez [Configuration du service Integration Services &#40;Service SSIS&#41;](service/integration-services-service-ssis-service.md).  
  
### <a name="to-set-properties-of-the-integration-services-service-by-using-sql-server-configuration-manager"></a>Pour définir les propriétés du service Integration Services à l'aide du Gestionnaire de configuration SQL Server  
  
1.  Dans le menu **Démarrer** , pointez sur **Tous les programmes**, sur **Microsoft SQL Server**, sur **Outils de configuration**, puis cliquez sur **Gestionnaire de configuration SQL Server**.  
  
2.  Dans le composant logiciel enfichable **Gestionnaire de configuration SQL Server** , recherchez **SQL Server Integration Services** dans la liste des services, cliquez avec le bouton droit sur **SQL Server Integration Services**, puis cliquez sur **Propriétés**.  
  
3.  Dans la boîte de dialogue **Propriétés du SQL Server Integration Services** , vous pouvez effectuer les opérations suivantes :  
  
    -   Cliquez sur l’onglet **Ouvrir une session** pour afficher les informations d’ouverture de session, comme le nom du compte.  
  
    -   Cliquez sur l’onglet **Service** pour afficher les informations relatives au service, comme le nom de l’ordinateur hôte, puis spécifiez le mode de démarrage du service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
        > [!NOTE]  
        >  L’onglet **Avancé** ne contient aucune information sur le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
4.  Cliquez sur **OK**.  
  
5.  Dans le menu **Fichier** , cliquez sur **Quitter** pour fermer le composant logiciel enfichable **Gestionnaire de configuration SQL Server** .  
  
### <a name="to-set-properties-of-the-integration-services-service-by-using-services"></a>Pour définir les propriétés du service Integration Services à l’aide de Services  
  
1.  Dans le **Panneau de configuration**, si vous utilisez l’affichage classique, cliquez sur **Outils d’administration**. Si vous utilisez l’affichage des catégories, cliquez sur **Performance et maintenance** puis sur **Outils d’administration**.  
  
2.  Cliquez sur **Services**.  
  
3.  Dans le composant logiciel enfichable **Services** , recherchez **SQL Server Integration Services** dans la liste des services, cliquez avec le bouton droit sur **SQL Server Integration Services**, puis cliquez sur **Propriétés**.  
  
4.  Dans la boîte de dialogue **Propriétés de SQL Server Integration Services** , vous pouvez effectuer les actions suivantes :  
  
    -   Cliquez sur l’onglet **général** . Pour activer le service, sélectionnez le type de démarrage manuel ou automatique. Pour désactiver le service, sélectionnez Désactiver dans la zone **Type de démarrage** . Le fait de sélectionner Désactiver n'arrête pas le service s'il est en cours d'exécution.  
  
         Si le service est déjà activé, vous pouvez cliquer sur **Arrêter** pour arrêter le service ou sur **Démarrer** pour le démarrer.  
  
    -   Cliquez sur l’onglet **Ouvrir une session** pour afficher ou modifier les informations d’ouverture de session.  
  
    -   Cliquez sur l’onglet **Récupération** pour afficher les réponses par défaut de l’ordinateur à l’échec du service. Vous pouvez modifier ces options pour les adapter à votre environnement.  
  
    -   Cliquez sur l’onglet **Dépendances** pour afficher la liste des services dépendants. Le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] n’a pas de dépendances.  
  
5.  Cliquez sur **OK**.  
  
6.  Si le type de démarrage est manuel ou automatique, vous pouvez si vous le souhaitez cliquer avec le bouton droit sur **SQL Server Integration Services** , puis cliquer sur **Démarrer, Arrêter ou Redémarrer**.  
  
7.  Dans le menu **Fichier** , cliquez sur **Quitter** pour fermer le composant logiciel enfichable **Services** .  
  
## <a name="see-also"></a>Voir aussi  
 [Gérer le service Integration Services](../../2014/integration-services/manage-the-integration-services-service.md)  
  
  
