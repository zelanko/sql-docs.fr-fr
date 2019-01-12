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
ms.sourcegitcommit: 78e32562f9c1fbf2e50d3be645941d4aa457e31f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54100824"
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
  
####  <a name="Permissions"></a> Permissions  
 Nécessite l'appartenance au rôle PolicyAdministratorRole dans la base de données msdb.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-view-all-of-the-facets-in-an-object"></a>Pour afficher toutes les facettes dans un objet  
  
1.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], un objet d’instance, une base de données ou un objet de base de données, puis cliquez sur **Facettes**.  
  
2.  Dans le **afficher les facettes -**_object_name_ boîte de dialogue le **facette** liste, sélectionnez une facette pour afficher ses propriétés. Pour plus d'informations sur les options disponibles dans cette boîte de dialogue, consultez [View Facets Dialog Box](view-facets-dialog-box.md).  
  
3.  Lorsque vous avez terminé, cliquez sur **OK**.  
  
  
