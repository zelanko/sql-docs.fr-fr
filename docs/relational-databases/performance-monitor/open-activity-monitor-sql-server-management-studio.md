---
title: Ouvrir le Moniteur d’activité (SSMS)
description: Guide pratique pour ouvrir le moniteur d’activité dans SSMS (SQL Server Management Studio).
ms.custom: seo-dt-2019
ms.date: 08/05/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Activity Monitor [SQL Server], setting the refresh interval
- refresh interval for Activity Monitor
- Activity Monitor [SQL Server], opening
- opening Activity Monitor
ms.assetid: 0a6eeb16-f02b-479d-9a60-543e40ebf46b
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 16d08bbc2b651ef21ee80be1e8af74a00b45a253
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85787436"
---
# <a name="open-activity-monitor-in-sql-server-management-studio-ssms"></a>Ouvrir le moniteur d’activité dans SSMS (SQL Server Management Studio)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
   
 Le Moniteur d'activité exécute des requêtes sur l'instance analysée afin d'obtenir des informations pour ses volets d'informations. Si l'intervalle d'actualisation est défini sur une valeur inférieure à 10 secondes, le temps nécessaire à l'exécution de ces requêtes peut affecter les performances du serveur.  
  
  
##  <a name="check-your-permissions"></a><a name="Permissions"></a> Vérifier les autorisations dont vous bénéficiez  
 Pour afficher l’activité courante, vous devez avoir l’autorisation VIEW SERVER STATE. Pour afficher la section E/S du fichier de données du Moniteur d'activité, vous devez disposer de l'autorisation CREATE DATABASE, ALTER ANY DATABASE ou VIEW ANY DEFINITION en plus de VIEW SERVER STATE.  
  
 Pour pouvoir mettre fin (KILL) à un processus, un utilisateur doit être membre des rôles serveur fixe sysadmin ou processadmin.  
  
  
## <a name="open-activity-monitor"></a>Ouvrir le Moniteur d’activité  

### <a name="keyboard-shortcut"></a>Raccourci clavier  
 - Tapez **CTRL+ALT+A** pour ouvrir le moniteur d’activité à tout moment.

 >**Conseil** Survolez une icône de SSMS afin de découvrir sa fonction et de connaître le raccourci clavier qui l’active.

### <a name="toolbar"></a>Barre d'outils

Dans la barre d’outils standard, cliquez sur l’icône **Moniteur d’activité** . Elle se trouve au centre, à la droite des boutons d’annulation/de rétablissement.
![Activity_Monitor_icon](../../relational-databases/performance-monitor/media/activity-monitor-icon.png)  
  
Remplissez la boîte de dialogue **Se connecter au serveur** si vous n’êtes pas encore connecté à une instance de SQL Server que vous souhaitez surveiller.
  
## <a name="launch-activity-monitor-and-object-explorer-on-startup"></a>Lancer le moniteur d’activité et l’explorateur d’objets au démarrage
  
1.  Dans le menu **Outils** , cliquez sur **Options**.  
  
2.  Dans la boîte de dialogue **Options** , développez **Environnement**, puis sélectionnez **Démarrage**.  
  
3.  Dans la liste déroulante **Au démarrage** , sélectionnez **Ouvrir l’Explorateur d’objets et le Moniteur d’activité**.  

4.  Cliquez sur **OK**.

![open_object_explorer](../../relational-databases/performance-monitor/media/open-object-explorer.png)
  
  
## <a name="set-the-activity-monitor-refresh-interval"></a>Définir l’intervalle d’actualisation du Moniteur d’activité  
  
1.   Ouvrez le Moniteur d'activité.  
  
2.   Cliquez avec le bouton droit sur **Vue d’ensemble**, sélectionnez **Intervalle d’actualisation**, puis choisissez l’intervalle dans lequel le Moniteur d’activité doit obtenir de nouvelles informations sur l’instance.  
  
  
