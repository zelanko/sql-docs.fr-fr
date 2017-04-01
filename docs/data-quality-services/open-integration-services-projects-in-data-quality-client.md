---
title: "Ouvrir des projets Integration Services dans Data Quality Client | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a8bad2f1-8fb0-4d14-a978-11a5720e62d6
caps.latest.revision: 9
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 9
---
# Ouvrir des projets Integration Services dans Data Quality Client
  Le composant de nettoyage DQs dans Integration Services vous permet d’exécuter un projet de nettoyage en mode batch. Toutefois, vous pouvez parfois examiner les résultats de nettoyage dans un package Integration Services de la même façon que vous pouvez examiner les résultats de nettoyage dans l'onglet **Gérer et afficher les résultats** d'une activité de nettoyage dans un projet de qualité des données dans DQS. DQS vous permet d'ouvrir des projets Integration Services dans [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] comme tout autre projet de qualité des données à partir de l'écran **Ouvrir le projet** et d'avoir une expérience de nettoyage interactif des résultats de nettoyage dans un projet Integration Services.  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="LimitationsRestrictions"></a> Limitations et restrictions  
  
-   Seuls les projets Integration Services finalisés sont disponibles dans l'écran **Ouvrir le projet** dans [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]. Les projets qui ont échoué ou en cours d'exécution ne sont pas disponibles dans l'écran **Ouvrir le projet** .  
  
-   Ouvriront des projets Integration Services à l’étape de nettoyage interactif (**Gérer la vue et les résultats** onglet) dans [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]. Vous ne pouvez pas accéder aux onglets **Nettoyer** ou **Mapper** . Vous pouvez uniquement accéder à l'onglet **Exporter** en cliquant sur **Suivant**.  
  
-   Vous ne pouvez pas supprimer un projet Integration Services verrouillé dans [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]. Vous devez d'abord le déverrouiller.  
  
###  <a name="Prerequisites"></a> Conditions préalables  
 Vous devez avoir correctement exécuté un projet Integration Services contenant un package avec un composant de nettoyage DQS pour l'afficher et l'ouvrir dans [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 Vous devez disposer du rôle dqs_kb_editor ou dqs_kb_operator sur la base de données DQS_MAIN pour ouvrir un projet Integration Services.  
  
  
##  <a name="Open"></a> Ouvrir un projet Integration Services  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)] [Exécutez l’Application Data Quality Client](../data-quality-services/run-the-data-quality-client-application.md).  
  
2.  Dans l'écran d'accueil de [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] , cliquez sur **Ouvrir le projet de qualité des données**. L'écran **Ouvrir le projet** s'affiche.  
  
3.  Dans l'écran **Ouvrir le projet** , vous pouvez identifier un projet Integration Services de l'une des manières suivantes :  
  
    1.  **Nom du projet**: projets Integration Services sont répertoriés à l’aide de la terminologie d’affectation de noms suivante : « Package.DQS Cleansing_*\< DATE>**\< heure>*_ {GUID}. » Chaque fois que vous exécutez correctement le même package dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], un nouveau projet est répertorié dans l’écran **Ouvrir le projet** .  
  
    2.  **Type de projet**: les projets Integration Services ont **SSIS** comme type de projet dans l'écran **Ouvrir le projet** .  
  
     Sélectionnez un projet, puis cliquez sur **Suivant**.  
  
4.  Le projet Integration Services s’ouvre à l’étape de nettoyage interactif (**Gérer la vue et les résultats** onglet). Vous pouvez effectuer un nettoyage interactif sur les données dans le projet Integration Services. Pour plus d’informations sur la **gérer et afficher les résultats** consultez la rubrique [étape de nettoyage interactif](../data-quality-services/cleanse-data-using-dqs-internal-knowledge.md#Interactive) dans [Data à l’aide de DQS nettoyer &#40 ; interne &#41 ; Base de connaissances](../data-quality-services/cleanse-data-using-dqs-internal-knowledge.md).  
  
5.  Cliquez sur **Suivant** pour accéder à l'onglet **Exporter** où vous pouvez exporter les données traitées vers l'un des éléments suivants : une nouvelle table dans la base de données SQL Server, un fichier .csv ou un fichier Excel. Pour plus d’informations sur la **Exporter** consultez la rubrique [étape d’exportation](../data-quality-services/cleanse-data-using-dqs-internal-knowledge.md#Export) dans [Data à l’aide de DQS nettoyer &#40 ; interne &#41 ; Base de connaissances](../data-quality-services/cleanse-data-using-dqs-internal-knowledge.md)  
  
6.  Après l'exportation des données, cliquez sur **Terminer** pour fermer le projet Integration Services.  

  
## Voir aussi  
 [Transformation de nettoyage DQS](../integration-services/data-flow/transformations/dqs-cleansing-transformation.md)   
 [Integration Services (SSIS) projets](https://msdn.microsoft.com/library/ms138028.aspx)  
  
  