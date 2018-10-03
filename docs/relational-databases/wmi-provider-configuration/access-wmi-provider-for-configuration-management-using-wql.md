---
title: Accéder au fournisseur WMI pour la gestion de Configuration à l’aide de WQL | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- query language [WMI]
- WMI Query Language [WMI]
- WQL [WMI]
- WMI Provider for Configuration Management, WQL
ms.assetid: 26499530-d93b-452b-bbe4-217ef1d11e68
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: e05bbb4a9d41f88c4c2981aff9a3565bbc14bb92
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47692827"
---
# <a name="access-wmi-provider-for-configuration-management-using-wql"></a>Accéder au fournisseur WMI pour Gestion de l'ordinateur à l'aide de WQL
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Cette section décrit comment exécuter des instructions [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Management Instrumentation Query Language (WQL) contre le fournisseur WMI pour Gestion de l'ordinateur.  
  
 L'exemple utilise un éditeur WQL, WBEMtest.exe, pour exécuter des requêtes WQL contre le fournisseur WMI afin d'énumérer des services, des protocoles réseaux et des alias [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### <a name="querying-services-using-wbemtest"></a>Interrogation de services à l'aide de WBEMtest  
  
1.  À partir de la **Démarrer** menu, cliquez sur **exécuter**, puis entrez **WBEMtest**.  
  
2.  La boîte de dialogue WBEMtest.exe apparaît. Cliquez sur **Se connecter**.  
  
3.  Dans le premier champ de texte, tapez l'espace de noms de fournisseur WMI pour Gestion de l'ordinateur : root\Microsoft\SqlServer\ComputerManagement11. Cliquez sur **Se connecter**.  
  
4.  Cliquez sur **requête**. Tapez une requête qui retourne les services actuels en cours d’exécution sur l’ordinateur local : **sélectionnez \* à partir de SqlService.** Cliquez sur **Appliquer**.  
  
5.  Affiner la requête en ajoutant **où ServiceName = « MSSQLSERVER »**.  
  
  
