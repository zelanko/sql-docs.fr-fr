---
title: Configurer les journaux des erreurs SQL Server | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: configure-windows
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.swb.configurelogs.configureerrorlogs.f1
ms.assetid: 03f0d463-9b0b-4af9-a853-da936d75e5af
caps.latest.revision: "18"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: c71daa7b5d1b18c78a1368a5d0731b21d8d2010f
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/18/2018
---
# <a name="scm-services---configure-sql-server-error-logs"></a>Services SCM - Configurer les journaux des erreurs SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Cette rubrique indique comment consulter ou modifier la méthode de recyclage des journaux d’erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="to-open-the-configure-sql-server-error-logs-dialog-box"></a>Pour ouvrir la boîte de dialogue Configurer les journaux d'erreurs SQL Server  
  
1.  Dans l’Explorateur d’objets, développez l’instance de SQL Server, puis **Gestion**, cliquez avec le bouton droit sur **Journaux SQL Server**, puis sélectionnez **Configurer**.  
  
2.  Dans la boîte de dialogue **Configurer les journaux d'erreurs SQL Server** , choisissez l'une des options suivantes.  
  
     **Limiter le nombre de fichiers de journaux d'erreurs avant qu'ils ne soient recyclés**  
     Activez cette option pour limiter le nombre de journaux d'erreurs créés avant le recyclage. Un nouveau journal des erreurs est créé à chaque démarrage d'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] conserve des copies de sauvegarde des six derniers journaux, sauf si vous avez activé cette option et spécifié un autre nombre maximal de fichiers de journaux des erreurs ci-dessous.  
  
     **Nombre maximal de fichiers de journaux d'erreurs**  
     Spécifiez le nombre maximal de fichiers de journaux d'erreurs pouvant être créés avant le recyclage. La valeur par défaut est 6, ce qui correspond au nombre de journaux sauvegardés que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] conserve avant de les recycler.  
  
  
