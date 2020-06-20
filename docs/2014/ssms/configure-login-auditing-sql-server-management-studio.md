---
title: Configurer l’audit de connexion en cours (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- auditing [SQL Server]
- audits [SQL Server], logins
- logins [SQL Server], auditing
ms.assetid: 16961116-57ac-4eef-8037-791b26ade548
author: stevestein
ms.author: sstein
ms.openlocfilehash: 89f4d5a65dc7c4a32fc0e90cec2226cffa12c6a2
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84995036"
---
# <a name="configure-login-auditing-sql-server-management-studio"></a>Configurer l'audit de connexion en cours (SQL Server Management Studio)
  Cette rubrique explique comment configurer l'audit de connexion dans [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] pour surveiller l'activité de connexion de [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]. L'audit de connexion en cours peut être configuré pour écrire les événements suivants dans le journal des erreurs.  
  
-   Échecs de connexion  
  
-   Connexions réussies  
  
-   Échecs et réussites de connexion  
  
 Vous devez redémarrer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] pour que cette option prenne effet.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-configure-login-auditing"></a>Pour configurer l'audit de connexion en cours  
  
1.  Dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], connectez-vous à une instance de [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] au moyen de l'Explorateur d'objets.  
  
2.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur le nom du serveur, puis sélectionnez **Propriétés**.  
  
3.  Dans la page **Sécurité** , sous **Audit de connexion en cours** , cliquez sur l’option de votre choix, puis fermez la page **Propriétés du serveur** .  
  
4.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur le nom du serveur, puis cliquez sur **Redémarrer**.  
  
  
