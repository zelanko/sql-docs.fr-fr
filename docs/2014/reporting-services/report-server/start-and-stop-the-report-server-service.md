---
title: Démarrer et arrêter le service Report Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- stopping Report Server service
- Report Server Windows service, starting
- Report Server service, starting
- starting Report Server service
ms.assetid: 6ec69ac3-27b0-472d-91e1-733af9078ed2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bef23ec8291be1a1eeab8796a00e45487b82f60c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66103170"
---
# <a name="start-and-stop-the-report-server-service"></a>Démarrer et arrêter le service Report Server
  Un serveur de rapports est implémenté comme un service Windows unique qui contient le service Web Report Server, le Gestionnaire de rapports et une application de traitement en arrière-plan. Le service doit s'exécuter afin que vous puissiez utiliser les fonctionnalités du serveur de rapports. L'arrêt du service interrompt toutes les opérations du serveur de rapports.  
  
 Pendant que le service est arrêté, les requêtes de traitement des abonnements et des rapports planifiés, qui auraient eu lieu si le service était en cours d'exécution, sont ajoutées à la file d'attente. En effet, les travaux exécutés par l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] créent les événements. Si vous souhaitez éviter la création d'un journal des travaux en souffrance pendant que le service est interrompu, songez à arrêter également l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Vous disposez de toute une série d'outils pour démarrer ou arrêter le service Report Server, notamment l'outil de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , ainsi que l'outil Services proposé dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.  
  
 Si vous ne vous limitez pas au démarrage et à l'arrêt du service, par exemple si vous modifiez également le compte de service, vous devez utiliser l'outil de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . L'utilisation d'autres outils pour modifier le compte de service peut endommager votre installation de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Pour plus d’informations, consultez [Configurer le compte de service Report Server &#40;Gestionnaire de configuration de SSRS&#41;](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md).  
  
 Vous ne pouvez pas interrompre et reprendre le service. Il n'y a pas de paramètres de démarrage. Même s'il n'existe pas de dépendances explicites, l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit être en cours d'exécution si le serveur prend en charge des abonnements ou des opérations de rapport planifiées.  
  
### <a name="to-start-or-stop-the-service-using-the-reporting-services-configuration-tool"></a>Pour démarrer ou arrêter le service à l'aide de l'outil de configuration de Reporting Services.  
  
1.  Démarrez l'outil de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , puis connectez-vous au serveur de rapports.  
  
2.  Sur la page d'état du serveur de rapports, cliquez sur **Arrêter** ou sur **Démarrer**.  
  
### <a name="to-start-or-stop-the-service-using-services-in-administrative-tools"></a>Pour démarrer ou arrêter le service à l'aide de l'outil Services dans les Outils d'administration  
  
-   Dans Outils d’administration, ouvrez Services, cliquez avec le bouton droit sur **SQL Server Reporting Services (MSSQLSERVER)** , puis cliquez sur **Arrêter** ou sur **Redémarrer**.  
  
 Si vous exécutez plusieurs instances ou si le serveur de rapports s'exécute en tant qu'instance nommée, vérifiez que le nom de l'instance entre parenthèses correspond à l'instance du serveur de rapports que vous voulez arrêter ou redémarrer.  
  
### <a name="to-start-or-stop-the-service-using-sql-server-configuration-manager"></a>Pour démarrer ou arrêter le service à l'aide du Gestionnaire de configuration SQL Server  
  
1.  Démarrez le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
2.  Sélectionnez Services SQL Server, cliquez avec le bouton droit sur **SQL Server Reporting Services**, puis cliquez sur **Arrêter** ou sur **Redémarrer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestionnaire de configuration de Reporting Services &#40;mode natif&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  
