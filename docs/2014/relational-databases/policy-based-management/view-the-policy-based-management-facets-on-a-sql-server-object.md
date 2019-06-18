---
title: Afficher les facettes de gestion basée sur des stratégies sur un objet SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, view facets
ms.assetid: 5f423b9f-a6c4-41a7-9d8d-8f4926ce1fb4
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: cb2a08d874dd022fdad3646ea263d34dd65b9739
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62677027"
---
# <a name="view-the-policy-based-management-facets-on-a-sql-server-object"></a>Afficher les facettes de gestion basée sur des stratégies sur un objet SQL Server
  Cette rubrique explique comment afficher toutes les facettes de gestion basée sur des stratégies appliquées à un objet spécifique de SQL Server dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour afficher toutes les facettes dans un objet à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Nécessite l'appartenance au rôle PolicyAdministratorRole dans la base de données msdb.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-view-all-of-the-facets-in-an-object"></a>Pour afficher toutes les facettes dans un objet  
  
1.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], un objet d’instance, une base de données ou un objet de base de données, puis cliquez sur **Facettes**.  
  
2.  Dans la boîte de dialogue **Afficher les facettes -** _nom_objet_, sélectionnez une facette dans la liste **Facette** pour afficher ses propriétés. Pour plus d'informations sur les options disponibles dans cette boîte de dialogue, consultez [View Facets Dialog Box](view-facets-dialog-box.md).  
  
3.  Lorsque vous avez terminé, cliquez sur **OK**.  
  
  
