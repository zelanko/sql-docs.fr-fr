---
title: "Ex&#233;cuter l&#39;application Data Quality Client | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dqs.browseforservers.f1"
  - "sql13.dqs.connecttoserver.f1"
ms.assetid: 0b2aa202-7ab2-4c9d-b0f1-802588053a1e
caps.latest.revision: 13
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 13
---
# Ex&#233;cuter l&#39;application Data Quality Client
  Exécutez [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)], et ouvrez une session sur un [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)].  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Prerequisites"></a> Conditions préalables  
 Vous devez avoir terminé l'installation du [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] en exécutant le fichier DQSInstaller.exe. Pour plus d’informations, consultez [exécuter DQSInstaller.exe pour terminer l’Installation Data Quality Server](../data-quality-services/install-windows/run-dqsinstaller-exe-to-complete-data-quality-server-installation.md).  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Pour se connecter à [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)], un utilisateur doit disposer de l'un des trois rôles DQS suivants sur la base de données DQS_MAIN : dqs_administrator, dqs_kb_editor ou dqs_kb_operator.  
  
##  <a name="Run"></a> Exécuter Data Quality Client  
 Pour exécuter [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] sur l’ordinateur où vous avez installé :  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, cliquez sur **[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]**, cliquez sur **Data Quality Services**, puis cliquez sur **Data Quality Client**.  
  
2.  Dans le **se connecter au serveur** boîte de dialogue :  
  
    1.  Spécifiez le serveur auquel vous souhaitez connecter l'application [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] . Sélectionnez **(LOCAL)** pour se connecter à [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] sur l’ordinateur local. Vous pouvez également cliquez sur la flèche vers le bas et sélectionnez **\< réseau parcourir d’autres serveurs>** pour se connecter à un autre serveur (ou se connecter au serveur local par nom). Le **Parcourir les serveurs** boîte de dialogue s’affiche. Vous pouvez sélectionner un serveur dans les **serveurs locaux** onglet ou dans les **serveurs réseau** onglet.  
  
    2.  Pour chiffrer les transferts de données entre [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] et [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)], cliquez sur **Options**, puis sélectionnez le **chiffrer la connexion** case à cocher.  
  
3.  Cliquez sur **Se connecter**.  
  
 L'écran d'accueil [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] apparaît. Pour plus d’informations, consultez [Data Quality Client écran d’accueil](../data-quality-services/data-quality-client-home-screen.md).  
  
  