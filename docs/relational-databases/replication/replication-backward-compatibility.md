---
title: Compatibilité descendante de la réplication | Microsoft Docs
ms.custom: ''
ms.date: 03/02/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- transactional replication, backward compatibility
- backward compatibility [SQL Server replication]
- merge replication backward compatibility [SQL Server replication]
- replication [SQL Server], backward compatibility
- backward compatibility [SQL Server], replication
- snapshot replication [SQL Server], backward compatibility
- compatibility [SQL Server replication]
ms.assetid: 091c51dc-8b32-4b4f-847e-b317456c8394
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 265f7fa72b6cdcd59ff7c74ec456e533471ddd0a
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "76287399"
---
# <a name="replication-backward-compatibility"></a>Compatibilité descendante de la réplication
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

Il est important de comprendre la compatibilité descendante si vous effectuez une mise à niveau ou si vous avez plusieurs versions de SQL Server dans une topologie de réplication. 

Les règles générales sont les suivantes : 

-   Toute version convient pour le serveur de distribution dès lors qu'elle est égale ou supérieure à celle du serveur de publication (en général, l'instance du serveur de distribution est la même que celle du serveur de publication).    
-   Toute version convient pour le serveur de publication dès lors qu'elle est inférieure ou égale à celle du serveur de distribution.    
-   La version de l'Abonné dépend du type de publication :    
    - La version d'un Abonné à une publication transactionnelle peut être n'importe laquelle des deux versions du serveur de publication. Par exemple : un éditeur SQL Server 2012 (11.x) peut avoir des abonnés SQL Server 2014 (12.x) et SQL Server 2016 (13.x), et un éditeur SQL Server 2016 (13.x) peut avoir des abonnés SQL Server 2014 (12.x) et SQL Server 2012 (11.x).     
    - Un abonné à une publication de fusion peut avoir toute version égale ou inférieure à la version de l’éditeur qui est prise en charge selon le cycle de prise en charge du cycle de vie des versions.  


## <a name="replication-matrix"></a>Matrice de réplication
[!INCLUDE[repl matrix](../../includes/replication-compat-matrix.md)]


## <a name="additional-resources"></a>Ressources supplémentaires
 [Fonctionnalités dépréciées dans la réplication SQL Server](../../relational-databases/replication/deprecated-features-in-sql-server-replication.md)  
 Fonctionnalités de réplication qui ont été conservées dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] pour permettre la compatibilité descendante, mais qui seront supprimées dans une version ultérieure de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Dernières modifications dans la réplication SQL Server](../../relational-databases/replication/breaking-changes-in-sql-server-replication.md)  
 Modifications des fonctionnalités de réplication qui peuvent imposer des modifications dans les applications. 

 [Mettre à niveau des bases de données répliquées](../../database-engine/install-windows/upgrade-replicated-databases.md)  
 Étapes et considérations relatives à la mise à niveau de serveurs SQL Server inscrits dans une topologie de réplication. 
  
  
