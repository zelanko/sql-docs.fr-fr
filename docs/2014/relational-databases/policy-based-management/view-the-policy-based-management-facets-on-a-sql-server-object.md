---
title: Afficher les facettes de gestion basée sur des stratégies sur un objet SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Policy-Based Management, view facets
ms.assetid: 5f423b9f-a6c4-41a7-9d8d-8f4926ce1fb4
caps.latest.revision: 7
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e95abe9e853c0e90bed9d58765fae1640f9885f8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36039959"
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
  
2.  Dans la boîte de dialogue **Afficher les facettes –***nom_objet*, sélectionnez une facette dans la liste **Facette** pour afficher ses propriétés. Pour plus d'informations sur les options disponibles dans cette boîte de dialogue, consultez [View Facets Dialog Box](view-facets-dialog-box.md).  
  
3.  Lorsque vous avez terminé, cliquez sur **OK**.  
  
  