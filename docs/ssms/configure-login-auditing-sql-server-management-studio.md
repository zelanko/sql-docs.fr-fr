---
title: Configurer l’audit de connexion en cours (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- auditing [SQL Server]
- audits [SQL Server], logins
- logins [SQL Server], auditing
ms.assetid: 16961116-57ac-4eef-8037-791b26ade548
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 341344db9bd0e33d044ab9746bc89c8a7d648837
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "42776600"
---
# <a name="configure-login-auditing-sql-server-management-studio"></a>Configurer l'audit de connexion en cours (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Cette rubrique explique comment configurer l'audit de connexion dans [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] pour surveiller l'activité de connexion de [!INCLUDE[ssDEnoversion](../includes/ssdenoversion_md.md)]. L'audit de connexion en cours peut être configuré pour écrire les événements suivants dans le journal des erreurs.  
  
-   Échecs de connexion  
  
-   Connexions réussies  
  
-   Échecs et réussites de connexion  
  
Vous devez redémarrer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] pour que cette option prenne effet.  
  
## <a name="SSMSProcedure"></a>Utilisation de SQL Server Management Studio  
  
#### <a name="to-configure-login-auditing"></a>Pour configurer l'audit de connexion en cours  
  
1.  Dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], connectez-vous à une instance de [!INCLUDE[ssDEnoversion](../includes/ssdenoversion_md.md)] au moyen de l'Explorateur d'objets.  
  
2.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur le nom du serveur, puis sélectionnez **Propriétés**.  
  
3.  Dans la page **Sécurité** , sous **Audit de connexion en cours** , cliquez sur l’option de votre choix, puis fermez la page **Propriétés du serveur** .  
  
4.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur le nom du serveur, puis cliquez sur **Redémarrer**.  
  
