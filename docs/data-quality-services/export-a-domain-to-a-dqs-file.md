---
title: "Exporter un domaine vers un fichier&#160;.dqs | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eba10d3d-b5c4-447b-8a30-fa07996cb28e
caps.latest.revision: 18
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 18
---
# Exporter un domaine vers un fichier&#160;.dqs
  Cette rubrique explique comment exporter un domaine vers un fichier .dqs dans [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS). Vous pouvez exporter un domaine ou la totalité d'une base de connaissances vers un fichier de données. Pour plus d’informations sur l’exportation d’une base de connaissances, consultez [Exporter une Base de connaissances dans un fichier .dqs](../data-quality-services/export-a-knowledge-base-to-a-dqs-file.md).  
  
 L'exportation d'un domaine d'une base de connaissances vers un fichier de données .dqs, puis son importation vers une autre base de connaissances, simplifie le processus de génération de connaissances, et permet d'économiser aussi bien du temps que des efforts. Il vous permet de partager un domaine et ses connaissances avec d'autres.  
  
 Vous pouvez exporter un domaine unique ou un domaine composite. Un fichier .dqs contenant un domaine unique inclut toutes les données du domaine avec les propriétés de domaine, les valeurs et les règles, à l'exception des informations de données de référence jointes. Un fichier .dqs contenant un domaine composite inclut toutes les données du domaine composite, notamment toutes les données des domaines contenus dans le domaine composite, ainsi que les propriétés, les relations et les règles du domaine composite, à l'exception des informations des données de référence. Vous devez joindre à nouveau le domaine ou le domaine composite aux données de référence appropriées, le cas échéant, après avoir importé le fichier .dqs. Les données publiées et non publiées seront exportées.  
  
 Le fichier de données .dqs créé par le processus d'exportation est chiffré, de sorte que le contenu ne peut pas être affiché.  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Prerequisites"></a> Conditions préalables  
 Pour exporter un domaine vers un fichier de données .dqs, vous devez avoir créé et sélectionné un domaine unique ou un domaine composite contenant plusieurs domaines uniques. Vous n'avez pas besoin de disposer d'un fichier .dqs vers lequel effectuer l'exportation ; il en sera créé un automatiquement.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Vous devez disposer du rôle dqs_kb_editor ou dqs_administrator sur la base de données DQS_MAIN pour exporter un domaine vers un fichier de données .dqs.  
  
##  <a name="Export"></a> Exporter un domaine vers un fichier .dqs  
 Vous pouvez effectuer une exportation à partir de n'importe quelle page Gestion de l'arborescence du domaine. La commande d'exportation est disponible aussi bien à partir d'un contrôle dans l'interface utilisateur qu'à partir d'une commande dans le menu contextuel du volet Liste des domaines.  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)] [Exécutez l’Application Data Quality Client](../data-quality-services/run-the-data-quality-client-application.md).  
  
2.  Sur l'écran d'accueil de [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] , ouvrez une base de connaissances dans l'activité Gestion de l'arborescence du domaine.  
  
3.  Dans le **page de gestion de domaine** (avec n’importe quel onglet sélectionné), sélectionnez un domaine unique ou un domaine composite dans la **domaine** liste.  
  
4.  Cliquez sur l'icône **Exporter des données d'une base de connaissances** située au-dessus de la liste de domaines, puis cliquez sur **Exporter le domaine**. Vous pouvez également cliquer sur le domaine dans le **domaine** liste, pointez sur **Exporter**, puis cliquez sur **Exporter le domaine**.  
  
5.  Dans la **Exporter vers un fichier de données** conserver de la boîte de dialogue, accédez au dossier que vous souhaitez enregistrer le fichier, nommez le fichier ou conservez le nom par défaut, **des fichiers de données DQS (\*.dqs)** comme le **Enregistrer en tant que type**, puis cliquez sur **Enregistrer**.  
  
6.  Dans la boîte de dialogue **Exporter le domaine** , vérifiez que la ligne d'état indique que l'exportation est terminée. Cliquez sur **OK**.  
  
##  <a name="FollowUp"></a> Suivi : Après l'exportation d'un domaine vers un fichier .dqs  
 Après avoir exporté un domaine vers un fichier .dqs, vous pouvez importer le domaine dans une autre base de connaissances.  
  
  