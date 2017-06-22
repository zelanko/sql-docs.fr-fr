---
title: "Gérer des espaces disque logiques Oracle"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Oracle publishing [SQL Server replication], managing tablespaces
- tablespaces [SQL Server replication]
ms.assetid: b8ea6c3b-01d6-4efc-bbfb-03b264530bbd
caps.latest.revision: 33
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 6eaa6d1c6836cee6d8367e0c0893b3f8a73184f3
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="manage-oracle-tablespaces"></a>Gérer des espaces disque logiques Oracle
  Un espace disque logique est une unité de stockage de base de données qui est à peu près équivalent à un groupe de fichiers dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Les espaces disque logiques permettent le stockage et la gestion d'objets de base de données au sein de groupes individuels. Pour plus d'informations, consultez votre documentation Oracle.  
  
 Quand vous configurez une table comme composant d'une publication Oracle, vous pouvez spécifier en option un espace disque logique Oracle existant à utiliser lors du stockage d'informations de journalisation de la réplication. S'il n'est pas spécifié, l'espace disque logique pour les objets de réplication est l'espace disque logique associé au schéma utilisateur d'administration de réplication qui a été configuré lors de la configuration du serveur de publication.  
  
 **Pour spécifier un espace disque logique pour une table de journalisation d'articles**:  
  
-   Spécifiez un espace disque logique dans la boîte de dialogue **Propriétés de l'article** . Pour plus d'informations sur l'accès à cette boîte de dialogue, consultez [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
-   Utilisez [sp_changearticle &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md). Pour utiliser **sp_changearticle**, spécifiez les éléments suivants :  
  
    -   Nom du serveur de publication Oracle pour le paramètre **@publisher**.  
  
    -   Nom du serveur de publication Oracle pour le paramètre **@publication**.  
  
    -   Nom de l'article pour le paramètre **@article**.  
  
    -   Une valeur d'espace disque logique pour le paramètre **@property**.  
  
    -   Le nom de l'espace disque logique pour le paramètre **@value**.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer un serveur de publication Oracle](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)   
 [Objets créés sur le serveur de publication Oracle](../../../relational-databases/replication/non-sql/objects-created-on-the-oracle-publisher.md)  
  
  
