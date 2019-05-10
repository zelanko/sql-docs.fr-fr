---
title: Créer un projet de qualité des données | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql13.dqs.dqproject.newdqproject.f1
helpviewer_keywords:
- create,data quality project
- data quality project,create
ms.assetid: 19c52d2b-d28e-4449-ab59-5fe0dc326cd9
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: fb7b3f6a0932df1490eade1e3745182b05071da9
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65486340"
---
# <a name="create-a-data-quality-project"></a>Créer un projet de qualité des données

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Cette rubrique explique comment créer un projet de qualité des données à l'aide de [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]. Un projet de qualité des données est utilisé pour exécuter l'activité de nettoyage ou de correspondance dans [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Prerequisites"></a> Conditions préalables  
 Vous devez disposer d'une base de connaissances appropriée à utiliser dans le projet de qualité des données pour l'activité de nettoyage ou de correspondance.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Vous devez disposer du rôle dqs_kb_editor ou dqs_kb_operator sur la base de données DQS_MAIN pour créer un projet de qualité des données.  
  
##  <a name="Create"></a> Créer un projet de qualité des données  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)] [Exécutez l’application Data Quality Client](../data-quality-services/run-the-data-quality-client-application.md).  
  
2.  Dans l'écran d'accueil [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] , cliquez sur **Nouveau projet de qualité des données**.  
  
3.  Dans l'écran **Nouveau projet de qualité des données** :  
  
    1.  Dans la zone **Nom** , entrez un nom pour le nouveau projet de qualité des données.  
  
    2.  (Facultatif) Dans la zone de **Description** , tapez une description du nouveau projet de qualité des données.  
  
    3.  Dans la liste **Utiliser la Base de connaissances** , cliquez pour sélectionner une base de connaissances à utiliser pour le projet de qualité des données. La zone **Détails de la base de connaissances : <nom_base_de_connaissances>** sur le côté droit affiche les noms de domaine disponibles dans la base de connaissances sélectionnée.  
  
    4.  Dans la zone **Sélectionner une activité** , cliquez sur l'activité que vous souhaitez exécuter à l'aide de ce projet de qualité des données :  
  
        -   **Nettoyage** : sélectionnez cette activité pour nettoyer les données sources.  
  
        -   **Correspondance** : sélectionnez cette activité pour effectuer la correspondance. Cette activité est disponible uniquement si la base de connaissances sélectionnée pour le projet de qualité des données contient une stratégie correspondante.  
  
4.  Cliquez sur **Créer** pour créer un projet de qualité des données.  
  
##  <a name="FollowUp"></a> Suivi : Après la création d’un projet de qualité des données  
 Après avoir créé un projet de qualité des données, un Assistant vous est proposé pour effectuer l'activité sélectionnée : nettoyage ou correspondance. Pour plus d’informations sur les activités de nettoyage et de correspondance, consultez [Nettoyage des données](../data-quality-services/data-cleansing.md) et [Correspondance de données](../data-quality-services/data-matching.md).  
  
  
