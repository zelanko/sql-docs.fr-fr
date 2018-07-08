---
title: Configurer un pare-feu Windows pour l’accès au Service SSIS | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- security [Integration Services], firewalls
- Windows Firewall [Integration Services]
- unauthorized access [Integration Services]
- Integration Services service, firewalls
- firewall systems [Integration Services]
- SQL Server Integration Services, firewalls
- SSIS, firewalls
ms.assetid: 39975cf2-c351-4205-8c39-27a0fadfb010
caps.latest.revision: 42
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 67a1206afe217ce2f0e358c56ee4df2b16691b8c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37163000"
---
# <a name="configure-a-windows-firewall-for-access-to-the-ssis-service"></a>Configurer un Pare-feu Windows pour l'accès au service SSIS
    
> [!IMPORTANT]  
>  Cette rubrique présente le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , un service Windows qui permet de gérer les packages [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] prend en charge le service pour la compatibilité avec les versions antérieures de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. À compter de [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], vous pouvez gérer des objets tels que des packages sur le serveur Integration Services.  
  
 Le système de pare-feu Windows (windowsfirewall) permet d'empêcher l'accès non autorisé à des ressources informatiques sur une connexion réseau. Pour accéder à [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] à travers ce pare-feu, vous devez configurer le pare-feu de façon à autoriser l’accès.  
  
> [!IMPORTANT]  
>  Pour gérer des packages stockés sur un serveur distant, vous ne devez pas vous connecter à l’instance du service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sur ce serveur distant. Au lieu de cela, modifiez le fichier de configuration du service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] afin que [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] affiche les packages stockés sur le serveur distant. Pour plus d’informations, consultez [Configuring the Integration Services Service &#40;SSIS Service&#41;](configuring-the-integration-services-service-ssis-service.md).  
  
 Le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] utilise le protocole DCOM. Pour plus d’informations sur le fonctionnement du protocole DCOM à travers les pare-feu, consultez l’article «[Using Distributed COM with Firewalls](http://go.microsoft.com/fwlink/?LinkId=12490)» (Utilisation de Distributed COM avec des pare-feu) dans MSDN Library.  
  
 De nombreux systèmes de pare-feu sont disponibles. Si vous exécutez un pare-feu différent du pare-feu Windows (windowsfirewall), consultez la documentation de votre pare-feu pour obtenir des informations spécifiques au système utilisé.  
  
 Si le pare-feu prend en charge le filtrage au niveau application, vous pouvez utiliser l'interface utilisateur fournie par Windows pour spécifier les exceptions qui sont autorisées à traverser le pare-feu, telles que certains programmes ou services. Autrement, vous devez configurer DCOM de façon à utiliser un jeu de ports TCP limité. Le lien vers le site Web de Microsoft fourni ci-dessus contient des informations sur la façon de spécifier les ports TCP à utiliser.  
  
 Le service Integration Services utilise le port 135 ; ce port ne peut pas être modifié. Vous devez ouvrir le port TCP 135 pour accéder au gestionnaire de contrôle de services. Celui-ci effectue des tâches telles que le démarrage et l’arrêt des services [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , et la transmission de demandes de contrôle au service en cours d’exécution.  
  
 Les informations de la section suivante sont spécifiques au pare-feu Windows (windowsfirewall). Vous pouvez configurer le système de pare-feu Windows (windowsfirewall) en exécutant une commande à l'invite ou en définissant des propriétés dans la boîte de dialogue Pare-feu Windows (windowsfirewall).  
  
 Pour plus d’informations sur les paramètres par défaut du Pare-feu Windows et pour obtenir une description des ports TCP qui affectent le moteur de base de données, Analysis Services, Reporting Services et Integration Services, consultez [Configurer le Pare-feu Windows pour autoriser l’accès à SQL Server](../../2014/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).  
  
## <a name="configuring-a-windowsfirewall"></a>Configuration d'un Pare-feu Windows (windowsfirewall)  
 Vous pouvez utiliser les commandes suivantes pour ouvrir le port TCP 135, ajouter MsDtsSrvr.exe à la liste d'exceptions et spécifier la portée du déblocage pour le pare-feu.  
  
#### <a name="to-configure-a-windowsfirewall-using-the-command-prompt-window"></a>Pour configurer un Pare-feu Windows (windowsfirewall) à l'aide de la fenêtre d'invite de commandes  
  
1.  Exécutez la commande suivante : `netsh firewall add portopening protocol=TCP port=135 name="RPC (TCP/135)" mode=ENABLE scope=SUBNET`  
  
2.  Exécutez la commande suivante : `netsh firewall add allowedprogram program="%ProgramFiles%\Microsoft SQL Server\100\DTS\Binn\MsDtsSrvr.exe" name="SSIS Service" scope=SUBNET`  
  
    > [!NOTE]  
    >  Pour ouvrir le pare-feu pour tous les ordinateurs et également pour ceux sur Internet, remplacez scope=SUBNET par scope=ALL.  
  
 La procédure suivante décrit la façon d'utiliser l'interface utilisateur Windows pour ouvrir le port TCP 135, ajouter MsDtsSrvr.exe à la liste d'exceptions et spécifier la portée du déblocage pour le pare-feu.  
  
#### <a name="to-configure-a-firewall-using-the-windowsfirewall-dialog-box"></a>Pour configurer un pare-feu à l'aide de la boîte de dialogue Pare-feu Windows (windowsfirewall)  
  
1.  Dans le Panneau de configuration, double-cliquez sur **Pare-feu Windows**.  
  
2.  Dans la boîte de dialogue **Pare-feu Windows** , cliquez sur l’onglet **Exceptions** , puis sur **Ajouter un programme**.  
  
3.  Dans la boîte de dialogue **Ajouter un programme** , cliquez sur **Parcourir**, naviguez jusqu’au dossier Program Files\Microsoft SQL Server\100\DTS\Binn, cliquez sur MsDtsSrvr.exe, puis sur **Ouvrir**. Cliquez sur **OK** pour fermer la boîte de dialogue **Ajouter un programme** .  
  
4.  Sous l’onglet **Exceptions** , cliquez sur **Ajouter un port**.  
  
5.  Dans la boîte de dialogue **Ajouter un port** , tapez **RPC(TCP/135)** ou un autre nom descriptif dans la zone **Nom**, tapez **135** dans la zone **Numéro de port** , puis sélectionnez **TCP**.  
  
    > [!IMPORTANT]  
    >  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service utilise toujours le port 135. Vous ne pouvez pas spécifier un autre port.  
  
6.  Dans la boîte de dialogue **Ajouter un port** , vous pouvez éventuellement cliquer sur **Modifier l’étendue** pour modifier l’étendue par défaut.  
  
7.  Dans la boîte de dialogue **Modifier l’étendue** , sélectionnez **Uniquement mon réseau (ou sous-réseau)** ou tapez une liste personnalisée, puis cliquez sur **OK**.  
  
8.  Pour fermer la boîte de dialogue **Ajouter un port** , cliquez sur **OK**.  
  
9. Pour fermer la boîte de dialogue **Pare-feu Windows** , cliquez sur **OK**.  
  
    > [!NOTE]  
    >  Pour configurer le Pare-feu Windows, cette procédure utilise l’élément **Pare-feu Windows** dans le Panneau de configuration. L’élément **Pare-feu Windows** configure uniquement le pare-feu du profil d’emplacement réseau actuel. Toutefois, vous pouvez configurer également le Pare-feu Windows à l’aide de l’outil en ligne de commande **netsh** ou du composant logiciel enfichable MMC ( [!INCLUDE[msCoName](../includes/msconame-md.md)] Management Console) appelé Pare-feu Windows avec fonctions avancées de sécurité. Pour plus d’informations sur ces outils, consultez [Configurer le Pare-feu Windows pour autoriser l’accès à SQL Server](../../2014/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de l’intégration des Services Service &#40;Service SSIS&#41;](service/integration-services-service-ssis-service.md)   
 [Service Integration Services &#40;Service SSIS&#41;](service/integration-services-service-ssis-service.md)  
  
  
