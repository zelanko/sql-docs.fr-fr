---
title: Gérer (ouvrir, déverrouiller, renommer et supprimer) un projet de qualité des données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.dqproject.opendqproject.f1
helpviewer_keywords:
- data quality project,delete
- data quality project,rename
- data quality project,unlock
- data quality project,open
ms.assetid: de8a2b04-4673-4beb-b4cf-96a28cdf3a93
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 062a02688a81235686635db4315754e16dc38d08
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84937500"
---
# <a name="manage-open-unlock-rename-and-delete-a-data-quality-project"></a>Gérer (ouvrir, déverrouiller, renommer et supprimer) un projet de qualité des données
  Cette rubrique explique comment gérer un projet de qualité des données à l'aide de [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] , par exemple ouvrir, déverrouiller, renommer et supprimer un projet de qualité des données.  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> Limitations et restrictions  
  
-   Vous ne pouvez pas ouvrir un projet verrouillé créé par un autre utilisateur.  
  
-   Vous ne pouvez pas déverrouiller, renommer ou supprimer un projet de qualité des données créé par un autre utilisateur.  
  
-   Vous ne pouvez pas supprimer un projet de qualité des données verrouillé. Vous devez d'abord le déverrouiller.  
  
-   Vous pouvez uniquement déverrouiller un projet de qualité des données que vous avez vous-même créé.  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Conditions préalables  
 Vous devez disposer d'au moins un projet de qualité des données à gérer.  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 Vous devez disposer du rôle dqs_kb_editor ou dqs_kb_operator sur la base de données DQS_MAIN pour gérer un projet de qualité des données.  
  
##  <a name="open-a-data-quality-project"></a><a name="Open"></a> Ouvrir un projet de qualité des données  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)][Exécutez l’Application Data Quality client](../../2014/data-quality-services/run-the-data-quality-client-application.md).  
  
2.  Dans l' [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] écran d’accueil, cliquez sur **ouvrir le projet de qualité des données**. L'écran **Ouvrir le projet** s'affiche.  
  
     Vous pouvez également ouvrir directement un projet de qualité des données répertorié sous la zone **Projet de qualité des données récent** en cliquant dessus.  
  
3.  Dans l'écran **Ouvrir le projet** , cliquez pour sélectionner le projet de qualité des données que vous voulez ouvrir, puis cliquez sur **Suivant**.  
  
4.  Le projet de qualité des données s'ouvre dans le même état d'activité que celui dans lequel il se trouvait lorsqu'il a été fermé pour la dernière fois. Un projet de qualité des données peut prendre les états suivants :  
  
    -   Pour l’activité de **nettoyage** , un projet de qualité des données peut avoir les États suivants : **nettoyage-mappage**, **nettoyage-nettoyer**, **nettoyage-gérer et afficher les résultats**et **nettoyage-exportation**.  
  
    -   Pour l’activité de **correspondance** , un projet de qualité des données peut avoir les États suivants : correspondance **-** correspondance, correspondance **-** correspondance, correspondance **-survie**et **exportation correspondante**.  
  
##  <a name="unlock-a-data-quality-project"></a><a name="Unlock"></a> Déverrouiller un projet de qualité des données  
 Lorsque vous créez un projet de qualité des données, il se trouve dans un état verrouillé pour empêcher son utilisation ou sa modification par d'autres utilisateurs. Vous devez déverrouiller le projet de qualité des données une fois votre travail terminé si vous voulez que d'autres utilisateurs travaillent dessus. Un symbole de verrou est affiché pour les projets verrouillés.  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)][Exécutez l’Application Data Quality client](../../2014/data-quality-services/run-the-data-quality-client-application.md).  
  
2.  Dans l' [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] écran d’accueil, cliquez sur **ouvrir le projet de qualité des données**. L'écran **Ouvrir le projet** s'affiche.  
  
3.  Dans l'écran **Ouvrir le projet** , cliquez avec le bouton droit sur un projet de qualité des données verrouillé que vous avez créé, puis cliquez sur **Déverrouiller** dans le menu contextuel. Une coche verte s'affiche pour le projet, indiquant qu'il est déverrouillé.  
  
##  <a name="rename-a-data-quality-project"></a><a name="Rename"></a> Renommer un projet de qualité des données  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)][Exécutez l’Application Data Quality client](../../2014/data-quality-services/run-the-data-quality-client-application.md).  
  
2.  Dans l' [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] écran d’accueil, cliquez sur **ouvrir le projet de qualité des données**. L'écran **Ouvrir le projet** s'affiche.  
  
3.  Dans l'écran **Ouvrir le projet** , cliquez avec le bouton droit sur un projet de qualité des données verrouillé que vous avez créé, puis cliquez sur **Renommer** dans le menu contextuel.  
  
4.  Le nom du projet de qualité des données peut être modifié dans la colonne **Nom** . Tapez un nouveau nom, puis appuyez sur Entrée.  
  
##  <a name="delete-a-data-quality-project"></a><a name="Delete"></a> Supprimer un projet de qualité des données  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)][Exécutez l’Application Data Quality client](../../2014/data-quality-services/run-the-data-quality-client-application.md).  
  
2.  Dans l' [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] écran d’accueil, cliquez sur **ouvrir le projet de qualité des données**. L'écran **Ouvrir le projet** s'affiche.  
  
3.  Dans l'écran **Ouvrir le projet** , cliquez avec le bouton droit sur un projet de qualité des données déverrouillé que vous avez créé, puis cliquez sur **Supprimer** dans le menu contextuel.  
  
4.  Un message de confirmation s’affiche. Cliquez sur **Oui**.  
  
  
