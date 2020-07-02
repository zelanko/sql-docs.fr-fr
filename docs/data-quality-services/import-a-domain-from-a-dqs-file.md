---
title: Importer un domaine à partir d'un fichier .dqs
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: fabd88b0-22b3-4543-a993-6d5b202ded80
author: swinarko
ms.author: sawinark
ms.openlocfilehash: 03f43c756ab01874042f38ea2e06c83bf7ac1e51
ms.sourcegitcommit: 6be9a0ff0717f412ece7f8ede07ef01f66ea2061
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85812154"
---
# <a name="import-a-domain-from-a-dqs-file"></a>Importer un domaine à partir d'un fichier .dqs

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  Cette rubrique explique comment importer un domaine à partir d'un fichier .dqs vers une base de connaissances existante dans [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS). Un fichier de données .dqs est créé en exportant un domaine ou une base de connaissances à partir de l'application [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] . Un fichier de données .dqs est chiffré, et ne peut pas être affiché.  
  
 L'utilisation d'un fichier de données .dqs pour exporter un domaine d'une base de connaissances puis l'importer vers une autre base de connaissances simplifie le processus de génération de connaissances, et permet d'économiser aussi bien du temps que des efforts. Il vous permet de partager un domaine et ses connaissances avec d'autres, ce qui leur fait gagner du temps. Vous pouvez importer un domaine unique ou un domaine composite (contenant plusieurs domaines uniques). Un fichier .dqs contenant un domaine unique inclut toutes les données du domaine avec les propriétés de domaine, les valeurs et les données des règles, à l'exception des informations de données de référence mappées. Un fichier .dqs contenant un domaine composite inclut toutes les données du domaine composite, notamment toutes les données des domaines uniques contenus dans le domaine composite, ainsi que les propriétés, les relations de valeur et les règles du domaine composite, à l'exception des données de référence mappées. Les données publiées et non publiées seront importées.  
  
 Lorsque vous importez un domaine, le nom du domaine reste le même que le nom du domaine exporté à l’origine, à moins que ce nom de domaine existe déjà, auquel cas DQS ajoute « _1 » au nom. C'est également le cas si vous importez un domaine composite qui contient un domaine individuel portant le même nom qu'un domaine existant.  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Conditions préalables  
 Pour importer un domaine à partir d'un fichier .dqs, vous devez avoir déjà exporté un domaine unique ou un domaine composite (contenant plusieurs domaines uniques) vers le fichier .dqs. Le fichier .dqs doit contenir un seul domaine. Vous devez également avoir créé et ouvert une base de connaissances dans laquelle importer le domaine.  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 Vous devez disposer du rôle dqs_kb_editor ou dqs_administrator sur la base de données DQS_MAIN pour importer un domaine à partir d'un fichier de données .dqs.  
  
##  <a name="import-a-domain-from-a-dqs-file"></a><a name="Import"></a>Importer un domaine à partir d’un fichier. DQS  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)][Exécutez l’Application Data Quality client](../data-quality-services/run-the-data-quality-client-application.md).  
  
2.  Sur l'écran d'accueil de [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] , ouvrez une base de connaissances dans l'activité Gestion de l'arborescence du domaine.  
  
3.  Cliquez sur l'icône **Importer un domaine à partir d'un fichier de données** .  
  
4.  Dans la boîte de dialogue **Importer à partir d'un fichier de données** , accédez au dossier à partir duquel vous voulez importer le fichier, sélectionnez le fichier (de type Fichier DQS), puis cliquez sur **Ouvrir**.  
  
5.  Dans la boîte de dialogue **Importer un domaine** , cliquez sur **OK**.  
  
    > [!NOTE]  
    >  L'opération d'importation réussit uniquement si le fichier .dqs à partir duquel vous effectuez l'importation ne contient qu'un domaine unique ou un domaine composite (contenant plusieurs domaines uniques).  
  
6.  Vérifiez que le domaine que vous avez importé s'affiche dans la liste **Domaine** . Si vous avez importé un domaine composite, vérifiez que le domaine composite et les domaines uniques qu'il contient figurent tous dans la liste **Domaine** .  
  
##  <a name="follow-up-after-importing-a-domain-from-a-dqs-file"></a><a name="FollowUp"></a> Suivi : Après l'importation d'un domaine à partir d'un fichier .dqs  
 Après avoir importé un domaine à partir d'un fichier .dqs, vous pouvez ajouter des connaissances au domaine ou utiliser le domaine dans un projet de nettoyage ou de correspondance, en fonction du contenu du domaine. Pour plus d’informations, consultez [Effectuer une découverte des connaissances](../data-quality-services/perform-knowledge-discovery.md), [Gestion d’un domaine](../data-quality-services/managing-a-domain.md), [Gestion d’un domaine composite](../data-quality-services/managing-a-composite-domain.md), [Créer une stratégie de correspondance](../data-quality-services/create-a-matching-policy.md), [Nettoyage des données](../data-quality-services/data-cleansing.md) ou [Correspondance de données](../data-quality-services/data-matching.md).  
  
  
