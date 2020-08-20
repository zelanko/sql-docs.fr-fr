---
description: Créer une base de connaissances
title: Créer une base de connaissances
ms.date: 06/04/2013
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql13.dqs.kb.selectkb.f1
- sql13.dqs.kb.newkb.f1
ms.assetid: 2733a284-975f-4650-abcc-cc2aad074cab
author: swinarko
ms.author: sawinark
ms.openlocfilehash: 1dd8e0379d25b231de873ccfd1529284e62f0f1d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88487902"
---
# <a name="create-a-knowledge-base"></a>Créer une base de connaissances

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sqlserver.md)]

  Cette rubrique explique comment créer une base de connaissances dans [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) et la préparer pour la gestion de l'arborescence des domaines, la découverte de la connaissance ou l'ajout d'une stratégie correspondante.  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Conditions préalables  
 Pour créer une base de connaissances, vous devez avoir installé [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] et [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 Vous devez disposer du rôle dqs_kb_editor ou dqs_administrator sur la base de données DQS_MAIN pour créer une base de connaissances.  
  
##  <a name="create-a-knowledge-base"></a><a name="Createaknowledgebase"></a> Créer une base de connaissances  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)][Exécutez l’Application Data Quality client](../data-quality-services/run-the-data-quality-client-application.md).  
  
2.  Dans l'écran d'accueil de [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] , cliquez sur **Nouvelle base de connaissances**.  
  
3.  Entrez un nom et une description pour la nouvelle base de connaissances.  
  
4.  Dans **Créer la base de connaissances à partir de**, sélectionnez l'élément sur lequel fonder la base de connaissances :  
  
    -   Sélectionnez **Aucun** si vous ne souhaitez pas fonder la nouvelle base de connaissances sur une base de connaissances ou un fichier de données existants.  
  
    -   Sélectionnez **Base de connaissances existante** pour fonder la nouvelle base de connaissances sur une base de connaissances qui a déjà été créée sur [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]ou sur la base de connaissances par défaut. Sélectionnez la base de connaissances dans la liste déroulante **Sélectionner la Base de connaissances** ou cliquez sur **Parcourir** pour afficher la boîte de dialogue **Sélectionner une Base de connaissances** , sélectionnez une base de connaissances existante sur laquelle fonder la nouvelle base de connaissances, puis cliquez **OK**. Lorsque vous sélectionnez une base de connaissances à partir de la Tablet PC, les domaines et les règles correspondantes de la base de connaissances seront affichés dans le volet droit de la boîte de dialogue. Vous pouvez également sélectionner la base de connaissances **Données DQS** , qui est la base de connaissances par défaut contenant les domaines courants prêts à l’emploi et les connaissances relatives aux sociétés, adresses et données externes aux États-Unis.  
  
    -   Sélectionnez **Importer à partir d'un fichier DQS** pour fonder la nouvelle base de connaissances sur un fichier DQS de [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]. Cliquez **Parcourir**, sélectionnez un fichier de données de DQS avec une extension .dqs, puis cliquez **OK**.  
  
5.  Dans **Sélectionner une activité**, sélectionnez l'activité que vous souhaitez effectuer sur la nouvelle base de connaissances :  
  
    -   Sélectionnez **Gestion de l'arborescence du domaine** pour créer la base de connaissances et accédez aux écrans que vous utilisez pour modifier les domaines de la base de connaissances.  
  
    -   Sélectionnez **Découverte des connaissances** pour créer la base de connaissances et accédez à l'Assistant que vous utilisez pour analyser un échantillon de données et remplir les domaines de la base de connaissances avec les résultats.  
  
    -   Sélectionnez **Stratégie de correspondance** pour créer une stratégie de correspondance et l'ajouter à la base de connaissances.  
  
6.  Cliquez sur **Créer**.  
  
##  <a name="follow-up-after-creating-a-knowledge-base"></a><a name="FollowUp"></a> Suivi : après avoir créé une base de connaissances  
 Après avoir créé une base de connaissances, vous voyez s'afficher un Assistant qui vous permet d'effectuer la découverte des connaissances, un Assistant qui vous permet de créer une stratégie de correspondance, ou des pages pour exécuter la gestion des domaines. Pour plus d’informations sur la découverte des connaissances, la gestion de domaine ou la stratégie de correspondance, consultez [Effectuer une découverte des connaissances](../data-quality-services/perform-knowledge-discovery.md), [Gestion d’un domaine](../data-quality-services/managing-a-domain.md) ou [Créer une stratégie de correspondance](../data-quality-services/create-a-matching-policy.md).  
  
  
