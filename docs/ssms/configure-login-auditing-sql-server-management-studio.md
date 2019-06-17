---
title: Configurer l’audit de connexion en cours (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- auditing [SQL Server]
- audits [SQL Server], logins
- logins [SQL Server], auditing
ms.assetid: 16961116-57ac-4eef-8037-791b26ade548
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 1ce5c0323d98e2b8f05813513b3a2f44444a6695
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65102781"
---
# <a name="configure-login-auditing-sql-server-management-studio"></a>Configurer l'audit de connexion en cours (SQL Server Management Studio)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
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
  
