---
title: Utiliser WQL pour accéder au fournisseur WMI
description: Utilisez cet exemple pour voir comment exécuter des instructions de langage de requête Windows Management Instrumentation pour le fournisseur WMI pour la gestion de l’ordinateur dans SQL Server.
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- query language [WMI]
- WMI Query Language [WMI]
- WQL [WMI]
- WMI Provider for Configuration Management, WQL
ms.assetid: 26499530-d93b-452b-bbe4-217ef1d11e68
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 6e9dc2e3d0faee311945552c485187c8179f3615
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85715141"
---
# <a name="access-wmi-provider-for-configuration-management-using-wql"></a>Accéder au fournisseur WMI pour Gestion de l'ordinateur à l'aide de WQL
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]
  Cette section décrit comment exécuter des instructions [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Management Instrumentation Query Language (WQL) contre le fournisseur WMI pour Gestion de l'ordinateur.  
  
 L'exemple utilise un éditeur WQL, WBEMtest.exe, pour exécuter des requêtes WQL contre le fournisseur WMI afin d'énumérer des services, des protocoles réseaux et des alias [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### <a name="querying-services-using-wbemtest"></a>Interrogation de services à l'aide de WBEMtest  
  
1.  Dans le menu **Démarrer** , cliquez sur **exécuter**, puis entrez **WBEMTest**.  
  
2.  La boîte de dialogue WBEMtest.exe apparaît. Cliquez sur **Connecter**.  
  
3.  Dans le premier champ de texte, tapez l'espace de noms de fournisseur WMI pour Gestion de l'ordinateur : root\Microsoft\SqlServer\ComputerManagement11. Cliquez sur **Connecter**.  
  
4.  Cliquez sur **Requête**. Tapez une requête qui retourne les services en cours d’exécution sur l’ordinateur local : **sélectionnez \* dans SqlService.** Cliquez sur **Appliquer**.  
  
5.  Affinez davantage la requête en ajoutant **Where ServiceName = "MSSQLSERVER"**.  
  
  
