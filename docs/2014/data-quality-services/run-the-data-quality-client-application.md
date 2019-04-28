---
title: Exécuter l’application Data Quality Client | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.browseforservers.f1
- sql12.dqs.connecttoserver.f1
ms.assetid: 0b2aa202-7ab2-4c9d-b0f1-802588053a1e
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 3b40e0243b8ab330a4c865514d6bc047f7b0b2d5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62792297"
---
# <a name="run-the-data-quality-client-application"></a>Exécuter l'application Data Quality Client
  Vous pouvez utiliser [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) en exécutant [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] et en ouvrant une session sur [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)].  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Prerequisites"></a> Conditions préalables  
 Vous devez avoir terminé l'installation du [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] en exécutant le fichier DQSInstaller.exe. Pour plus d’informations, consultez [Exécuter DQSInstaller.exe pour terminer l’installation du serveur DQS](install-windows/run-dqsinstaller-exe-to-complete-data-quality-server-installation.md).  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Pour se connecter à [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)], un utilisateur doit disposer de l'un des trois rôles DQS suivants sur la base de données DQS_MAIN : dqs_administrator, dqs_kb_editor ou dqs_kb_operator.  
  
##  <a name="Run"></a> Exécuter Data Quality Client  
 Pour exécuter [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] sur l'ordinateur où vous l'avez installé, opérez comme suit :  
  
1.  Cliquez sur **Démarrer**, pointez sur **Tous les programmes**, cliquez sur **[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]**, cliquez sur **Data Quality Services**, puis sur **Data Quality Client**.  
  
2.  Dans la boîte de dialogue **Se connecter au serveur** :  
  
    1.  Spécifiez le serveur auquel vous souhaitez connecter l'application [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] . Sélectionnez **(LOCAL)** pour vous connecter à [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] sur l'ordinateur local. Vous pouvez également cliquer sur la flèche bas et sélectionner **\<Rechercher d’autres serveurs sur le réseau>** pour vous connecter à un serveur différent (ou pour vous connecter au serveur local par son nom). La boîte de dialogue **Parcourir les serveurs** s'affiche. Vous pouvez sélectionner un serveur sous l’onglet **Serveurs locaux** ou sous l’onglet **Serveurs réseau**.  
  
    2.  Si vous souhaitez chiffrer le transfert de données entre [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] et [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)], cliquez sur **Options**, puis cochez **Chiffrer la connexion**.  
  
3.  Cliquer sur **Se connecter**.  
  
 L’écran d’accueil [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] s’affiche. Pour plus d’informations, consultez [Écran d’accueil de Data Quality Client](../../2014/data-quality-services/data-quality-client-home-screen.md).  
  
  
