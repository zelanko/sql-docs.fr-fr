---
title: Gérer des espaces disque logiques Oracle
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Oracle publishing [SQL Server replication], managing tablespaces
- tablespaces [SQL Server replication]
ms.assetid: b8ea6c3b-01d6-4efc-bbfb-03b264530bbd
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9a6bf22c7649646506b65628f556b52fead23375
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63022299"
---
# <a name="manage-oracle-tablespaces"></a>Gérer des espaces disque logiques Oracle
  Un espace disque logique est une unité de stockage de base de données qui est à peu près équivalent à un groupe de fichiers dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Les espaces disque logiques permettent le stockage et la gestion d'objets de base de données au sein de groupes individuels. Pour plus d'informations, consultez votre documentation Oracle.  
  
 Quand vous configurez une table comme composant d'une publication Oracle, vous pouvez spécifier en option un espace disque logique Oracle existant à utiliser lors du stockage d'informations de journalisation de la réplication. S'il n'est pas spécifié, l'espace disque logique pour les objets de réplication est l'espace disque logique associé au schéma utilisateur d'administration de réplication qui a été configuré lors de la configuration du serveur de publication.  
  
 **Pour spécifier un espace disque logique pour une table de journalisation d'articles**:  
  
-   Spécifiez un espace disque logique dans la boîte de dialogue **Propriétés de l'article** . Pour plus d'informations sur l'accès à cette boîte de dialogue, consultez [Afficher et modifier les propriétés d’un serveur de publication](../publish/view-and-modify-publication-properties.md).  
  
-   Utilisez [sp_changearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql). Pour utiliser **sp_changearticle**, spécifiez les éléments suivants :  
  
    -   Nom du serveur de publication Oracle pour le paramètre **@publisher** .  
  
    -   Nom du serveur de publication Oracle pour le paramètre **@publication** .  
  
    -   Nom de l'article pour le paramètre **@article** .  
  
    -   Une valeur d'espace disque logique pour le paramètre **@property** .  
  
    -   Le nom de l'espace disque logique pour le paramètre **@value** .  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer un serveur de publication Oracle](configure-an-oracle-publisher.md)   
 [Objets créés sur le serveur de publication Oracle](objects-created-on-the-oracle-publisher.md)  
  
  
