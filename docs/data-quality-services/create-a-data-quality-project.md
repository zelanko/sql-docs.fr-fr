---
title: "Cr&#233;er un projet de qualit&#233; des donn&#233;es | Microsoft Docs"
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
  - "sql13.dqs.dqproject.newdqproject.f1"
helpviewer_keywords: 
  - "create,data quality project"
  - "projets de qualité des données, création"
ms.assetid: 19c52d2b-d28e-4449-ab59-5fe0dc326cd9
caps.latest.revision: 10
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 10
---
# Cr&#233;er un projet de qualit&#233; des donn&#233;es
  Cette rubrique explique comment créer un projet de qualité des données à l'aide de [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]. Un projet de qualité des données est utilisé pour exécuter l'activité de nettoyage ou de correspondance dans [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Prerequisites"></a> Conditions préalables  
 Vous devez disposer d'une base de connaissances appropriée à utiliser dans le projet de qualité des données pour l'activité de nettoyage ou de correspondance.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Vous devez disposer du rôle dqs_kb_editor ou dqs_kb_operator sur la base de données DQS_MAIN pour créer un projet de qualité des données.  
  
##  <a name="Create"></a> Créer un projet de qualité des données  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)] [Exécutez l’Application Data Quality Client](../data-quality-services/run-the-data-quality-client-application.md).  
  
2.  Dans l'écran d'accueil [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] , cliquez sur **Nouveau projet de qualité des données**.  
  
3.  Dans l'écran **Nouveau projet de qualité des données** :  
  
    1.  Dans la zone **Nom** , entrez un nom pour le nouveau projet de qualité des données.  
  
    2.  (Facultatif) Dans la **Description** tapez une description pour le nouveau projet de qualité des données.  
  
    3.  Dans la liste **Utiliser la Base de connaissances** , cliquez pour sélectionner une base de connaissances à utiliser pour le projet de qualité des données. Le **Détails de la base de connaissances : \< nom_base_de_connaissances >** zone située à droite affiche les noms de domaine disponibles dans la base de connaissances sélectionnée.  
  
    4.  Dans la zone **Sélectionner une activité** , cliquez sur l'activité que vous souhaitez exécuter à l'aide de ce projet de qualité des données :  
  
        -   **Nettoyage**: sélectionnez cette activité pour nettoyer les données sources.  
  
        -   **Correspondance**: sélectionnez cette activité pour effectuer la correspondance. Cette activité est disponible uniquement si la base de connaissances sélectionnée pour le projet de qualité des données contient une stratégie correspondante.  
  
4.  Cliquez sur **Créer** pour créer un projet de qualité des données.  
  
##  <a name="FollowUp"></a> Suivi : Après la création d'un projet de qualité des données  
 Après avoir créé un projet de qualité des données, un Assistant vous est proposé pour effectuer l'activité sélectionnée : nettoyage ou correspondance. Pour plus d’informations sur le nettoyage des activités et de correspondance, consultez [nettoyage des données](../data-quality-services/data-cleansing.md) et [correspondance des données](../data-quality-services/data-matching.md).  
  
  