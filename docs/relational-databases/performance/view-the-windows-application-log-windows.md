---
title: "Afficher le journal des applications Windows (Windows) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "affichage des journaux"
  - "journaux des applications [SQL Server]"
  - "journaux [SQL Server], application"
  - "surveillance du journal des applications Windows NT [SQL Server]"
  - "journaux des applications Windows NT [SQL Server]"
  - "affichage des journaux"
  - "surveillance [SQL Server], événements"
  - "journaux [SQL Server], affichage"
ms.assetid: 168a6c6e-12df-46a9-9904-55d63ca8fe14
caps.latest.revision: 25
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
---
# Afficher le journal des applications Windows (Windows)
  Lorsque [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est configuré pour vous permettre d'utiliser le journal des applications Windows, chaque session [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y enregistre des nouveaux événements. Contrairement au journal des erreurs de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , un nouveau journal des applications n'est pas créé chaque fois que vous démarrez une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### Pour consulter le journal des applications Windows  
  
1.  Dans le menu **Démarrer** , pointez successivement sur **Tous les programmes**et **Outils d'administration**, puis cliquez sur **Observateur d’événements**.  
  
2.  Dans l'Observateur d'événements, cliquez sur **Application**.  
  
3.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Les événements sont identifiés par l’entrée **MSSQLSERVER** (**MSSQL$***<nom_instance>* pour les instances nommées) dans la colonne **Source**. Les événements de SQL Server Agent sont identifiés par l’entrée SQLSERVERAGENT (pour les instances [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nommées, les événements de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent sont identifiés par **SQLAgent$**\<*nom_instance*>). Les événements du service Microsoft Search sont identifiés par l'entrée **Microsoft Search**.  
  
4.  Pour afficher le journal d’un autre ordinateur, cliquez avec le bouton droit sur **Observateur d’événements**, cliquez sur **Se connecter à un autre ordinateur**, et renseignez la boîte de dialogue **Sélectionner un ordinateur**.  
  
5.  Pour afficher uniquement les événements [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , dans le menu **Affichage** , cliquez sur **Filtrer**et dans la liste **Source de l'événement** , sélectionnez **MSSQLSERVER**. Pour afficher uniquement les événements de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , sélectionnez **SQLSERVERAGENT** dans la liste **Source de l'événement** .  
  
6.  Pour obtenir plus de détails sur un événement particulier, double-cliquez sur cet événement.  
  
## Voir aussi  
 [Afficher le journal des erreurs SQL Server &#40;SQL Server Management Studio&#41;](../../relational-databases/performance/view-the-sql-server-error-log-sql-server-management-studio.md)  
  
  