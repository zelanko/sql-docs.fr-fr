---
title: "Exporter une base de connaissances dans un fichier .dqs | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a324ead5-c8aa-4e26-abe3-ef415add00f8
caps.latest.revision: 19
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 19
---
# Exporter une base de connaissances dans un fichier .dqs
  Cette rubrique décrit comment exporter une base de connaissances entière dans un fichier de données .dqs dans [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS). Vous pouvez exporter un domaine ou la totalité d'une base de connaissances vers un fichier de données. Pour plus d’informations sur l’exportation d’un domaine, consultez [Exporter un domaine vers un fichier .dqs](../data-quality-services/export-a-domain-to-a-dqs-file.md).  
  
 L'exportation d'une base de connaissances vers un fichier .dqs, puis son importation en tant que base de connaissances distincte, simplifie le processus de génération de connaissances, et permet d'économiser aussi bien du temps que des efforts. Cela vous permet de partager une base de connaissances et ses contenus avec d'autres. Le fichier .dqs contient toutes les informations de la base de connaissances, y compris les domaines et la stratégie de correspondance, à l'exception des informations de données de référence jointes. Vous devez joindre à nouveau les domaines requis aux services de données de référence appropriés, le cas échéant, après avoir importé le fichier .dqs. Les données publiées et non publiées dans une base de connaissances sont exportées.  
  
 Le fichier de données .dqs créé par le processus d'exportation est chiffré, de sorte que le contenu ne peut pas être affiché.  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Prerequisites"></a> Conditions préalables  
 Pour exporter une base de connaissances dans un fichier de données .dqs, vous devez avoir créé et ouvert une base de connaissances. Vous n'avez pas besoin de disposer d'un fichier .dqs vers lequel effectuer l'exportation ; il en sera créé un automatiquement.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Vous devez disposer du rôle dqs_kb_editor ou dqs_administrator sur la base de données DQS_MAIN pour exporter une base de connaissances dans un fichier de données .dqs.  
  
##  <a name="Export"></a> Exporter une base de connaissances dans un fichier .dqs  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)] [Exécutez l’Application Data Quality Client](../data-quality-services/run-the-data-quality-client-application.md).  
  
2.  Sur l'écran d'accueil de [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] , ouvrez une base de connaissances dans l'activité Gestion de l'arborescence du domaine.  
  
3.  Dans la page de gestion de domaine (avec n’importe quel onglet sélectionné), cliquez sur le **Exporter la Base de connaissances données** icône au-dessus de la liste des domaines, puis cliquez sur **Exporter la Base de connaissances**. Sinon, vous pouvez également avec le bouton droit dans le **domaine** liste, pointez sur **Exporter**, puis cliquez sur **Exporter la Base de connaissances**.  
  
4.  Dans la **Exporter vers un fichier de données** conserver de la boîte de dialogue, accédez au dossier que vous souhaitez enregistrer le fichier, nommez le fichier ou conservez le nom de la base de connaissances, **des fichiers de données DQS (\*.dqs)** comme le **Enregistrer en tant que** puis tapez **Enregistrer**.  
  
5.  Dans la boîte de dialogue **Exporter la Base de connaissances** , vérifiez que la ligne d'état indique que l'exportation est terminée. Cliquez sur **OK**.  
  
##  <a name="FollowUp"></a> Suivi : Après l'exportation d'un domaine vers un fichier .dqs  
 Après avoir exporté une base de connaissances dans un fichier .dqs, vous pouvez importer la base de connaissances dans le même [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] (avec un nouveau nom) ou dans un [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] différent.  
  
  