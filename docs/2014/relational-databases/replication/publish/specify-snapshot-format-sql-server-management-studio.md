---
title: Spécifier le format d’instantané (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snapshots [SQL Server replication], formats
- snapshot replication [SQL Server], formats
ms.assetid: 7c95f545-731a-4743-9acb-0b325ef9b98b
caps.latest.revision: 36
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 0f3d7042d4359b31764fdeefbe4f42a281ed1849
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36042425"
---
# <a name="specify-snapshot-format-sql-server-management-studio"></a>Spécifier le format d'instantané (SQL Server Management Studio)
  Spécifiez le format d’instantané dans la page **Instantané** de la boîte de dialogue **Propriétés de la publication - \<Publication>**. Pour plus d'informations sur l'accès à cette boîte de dialogue, consultez [Afficher et modifier les propriétés d’un serveur de publication](view-and-modify-publication-properties.md).  
  
### <a name="to-specify-snapshot-format"></a>Pour spécifier le format d'instantané  
  
1.  Dans la page **Instantané** de la boîte de dialogue **Propriétés de la publication - \<Publication>**, sélectionnez **SQL Server natif - tous les Abonnés doivent être des serveurs qui exécutent SQL Server** ou **Caractère - obligatoire si un serveur de publication ou un Abonné n’exécute pas SQL Server**.  
  
    > [!NOTE]  
    >  Il est conseillé de sélectionner le format natif, à moins que cette publication ne doive prendre en charge les abonnements à une base de données [!INCLUDE[ssEW](../../../includes/ssew-md.md)] ou à une base de données non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer les propriétés d’instantané &#40;programmation Transact-SQL de la réplication&#41;](configure-snapshot-properties-replication-transact-sql-programming.md)   
 [Modifier les propriétés des publications et des articles](change-publication-and-article-properties.md)   
 [Initialiser un abonnement avec un instantané](../initialize-a-subscription-with-a-snapshot.md)  
  
  