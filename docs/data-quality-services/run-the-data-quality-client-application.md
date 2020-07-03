---
title: Exécuter l'application Data Quality Client
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql13.dqs.browseforservers.f1
- sql13.dqs.connecttoserver.f1
ms.assetid: 0b2aa202-7ab2-4c9d-b0f1-802588053a1e
author: swinarko
ms.author: sawinark
ms.openlocfilehash: 7125dd10e16b8013fccc1f584115550c026cc627
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85883340"
---
# <a name="run-the-data-quality-client-application"></a>Exécuter l'application Data Quality Client

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sqlserver.md)]

  Exécutez [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]et ouvrez une session sur un [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)].  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Conditions préalables  
 Vous devez avoir terminé l'installation du [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] en exécutant le fichier DQSInstaller.exe. Pour plus d’informations, consultez [Exécuter DQSInstaller.exe pour terminer l’installation du serveur DQS](../data-quality-services/install-windows/run-dqsinstaller-exe-to-complete-data-quality-server-installation.md).  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 Pour se connecter à [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)], un utilisateur doit disposer de l'un des trois rôles DQS suivants sur la base de données DQS_MAIN : dqs_administrator, dqs_kb_editor ou dqs_kb_operator.  
  
##  <a name="run-data-quality-client"></a><a name="Run"></a>Exécuter Data Quality Client  
 Pour exécuter [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] sur l’ordinateur où vous l’avez installé :  
  
1.  Cliquez sur **Démarrer**, pointez sur **Tous les programmes**, cliquez sur **[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]**, cliquez sur **Data Quality Services**, puis sur **Data Quality Client**.  
  
2.  Dans la boîte de dialogue **Se connecter au serveur** :  
  
    1.  Spécifiez le serveur auquel vous souhaitez connecter l'application [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] . Sélectionnez **(LOCAL)** pour vous connecter à [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] sur l'ordinateur local. Vous pouvez également cliquer sur la flèche vers le bas et sélectionner **\<Browse network for more servers>** pour vous connecter à un autre serveur (ou pour vous connecter au serveur local par son nom). La boîte de dialogue **Parcourir les serveurs** s'affiche. Vous pouvez sélectionner un serveur sous l'onglet **Serveurs locaux** ou sous l'onglet **Serveurs réseau** .  
  
    2.  Pour chiffrer le transfert de données entre [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] et [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)], cliquez sur **Options**, puis activez la case à cocher **Chiffrer la connexion** .  
  
3.  Cliquez sur **Connecter**.  
  
 L'écran d'accueil [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] apparaît. Pour plus d’informations, consultez [Écran d’accueil de Data Quality Client](../data-quality-services/data-quality-client-home-screen.md).  
  
  
