---
title: Ouvrir des projets Integration Services dans Data Quality Client | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: a8bad2f1-8fb0-4d14-a978-11a5720e62d6
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: aac86ed6438197bc788f08cf9bc618608a65475f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "65480373"
---
# <a name="open-integration-services-projects-in-data-quality-client"></a>Ouvrir des projets Integration Services dans Data Quality Client
  
  [!INCLUDE[ssDQSCleansingLong](../includes/ssdqscleansinglong-md.md)] vous permet d'exécuter un projet de nettoyage en mode batch. Toutefois, vous pouvez parfois examiner les résultats de nettoyage dans un package Integration Services de la même façon que vous pouvez examiner les résultats de nettoyage dans l'onglet **Gérer et afficher les résultats** d'une activité de nettoyage dans un projet de qualité des données dans DQS. DQS vous permet d'ouvrir des projets Integration Services dans [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] comme tout autre projet de qualité des données à partir de l'écran **Ouvrir le projet** et d'avoir une expérience de nettoyage interactif des résultats de nettoyage dans un projet Integration Services.  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="LimitationsRestrictions"></a> Limitations et restrictions  
  
-   Seuls les projets Integration Services finalisés sont disponibles dans l'écran **Ouvrir le projet** dans [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]. Les projets qui ont échoué ou en cours d'exécution ne sont pas disponibles dans l'écran **Ouvrir le projet** .  
  
-   Les projets Integration Services s'ouvrent à l'étape de nettoyage interactif (onglet**Gérer la vue et les résultats** ) dans [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]. Vous ne pouvez pas accéder aux onglets **Nettoyer** ou **Mapper** . Vous pouvez uniquement accéder à l'onglet **Exporter** en cliquant sur **Suivant**.  
  
-   Vous ne pouvez pas supprimer un projet Integration Services verrouillé dans [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]. Vous devez d'abord le déverrouiller.  
  
###  <a name="Prerequisites"></a>Conditions préalables  
 Vous devez avoir correctement exécuté un projet Integration Services contenant un package avec un composant de nettoyage DQS pour l'afficher et l'ouvrir dans [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Vous devez disposer du rôle dqs_kb_editor ou dqs_kb_operator sur la base de données DQS_MAIN pour ouvrir un projet Integration Services.  
  
##  <a name="Open"></a>Ouvrir un projet Integration Services  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)][Exécutez l’Application Data Quality client](../../2014/data-quality-services/run-the-data-quality-client-application.md).  
  
2.  Dans l' [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] écran d’accueil, cliquez sur **ouvrir le projet de qualité des données**. L'écran **Ouvrir le projet** s'affiche.  
  
3.  Dans l'écran **Ouvrir le projet** , vous pouvez identifier un projet Integration Services de l'une des manières suivantes :  
  
    1.  **Nom du projet**: les projets Integration Services sont répertoriés à l’aide de la terminologie de dénomination suivante : « Package. DQS Cleansing_*\<date> * *\<heure>*_ {GUID} ». Chaque fois que vous exécutez correctement le même package dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], un nouveau projet est répertorié dans l’écran **Ouvrir le projet** .  
  
    2.  **Type de projet**: Integration Services les projets ont **SSIS** comme type de projet dans l’écran **ouvrir le projet** .  
  
     Sélectionnez un projet, puis cliquez sur **Suivant**.  
  
4.  Le projet Integration Services s'ouvre à l'étape de nettoyage interactif (onglet**Gérer la vue et les résultats** ). Vous pouvez effectuer un nettoyage interactif sur les données dans le projet Integration Services. Pour plus d’informations sur l’onglet **Gérer et afficher les résultats**, consultez [Étape de nettoyage interactif](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md#Interactive) dans [Nettoyer des données à l’aide de la base de connaissances DQS &#40;interne&#41;](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md).  
  
5.  Cliquez sur **Suivant** pour accéder à l'onglet **Exporter** où vous pouvez exporter les données traitées vers l'un des éléments suivants : une nouvelle table dans la base de données SQL Server, un fichier .csv ou un fichier Excel. Pour plus d’informations sur l’onglet **Exporter**, consultez [Étape d’exportation](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md#Export) dans [Nettoyer des données à l’aide de la base de connaissances DQS &#40;interne&#41;](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md)  
  
6.  Après l'exportation des données, cliquez sur **Terminer** pour fermer le projet Integration Services.  
  
## <a name="see-also"></a>Voir aussi  
 [Transformation de nettoyage DQS](../integration-services/data-flow/transformations/dqs-cleansing-transformation.md)   
 [Projets Integration Services &#40;SSIS&#41;](../integration-services/integration-services-ssis-projects-and-solutions.md)  
