---
title: Types de réplication | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], types
ms.assetid: c1655e8d-d14c-455a-a7f9-9d2f43e88ab4
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2fa6d02a8fc501f4b196c175056f18f7a9bff7c4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48162389"
---
# <a name="types-of-replication"></a>Types de réplication
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournit les types de réplication suivants à utiliser dans des applications distribuées :  
  
-   Réplication transactionnelle. Pour plus d’informations, consultez [Réplication transactionnelle](transactional/transactional-replication.md).  
  
-   Réplication de fusion. Pour plus d’informations, consultez [Réplication de fusion](merge/merge-replication.md).  
  
-   Réplication d'instantané. Pour plus d’informations, consultez [Réplication d’instantané](snapshot-replication.md).  
  
 Le type de réplication que vous choisissez pour une application dépend de nombreux facteurs, dont l'environnement physique de la réplication, le type et la quantité de données à répliquer et si les données sont ou non mises à jour sur l'Abonné. L'environnement physique comprend le nombre et l'emplacement des ordinateurs impliqués dans la réplication et le fait que ces ordinateurs sont des clients (stations de travail, ordinateurs portables ou ordinateurs de poche) ou des serveurs.  
  
 Chaque type de réplication commence par une synchronisation initiale des objets publiés entre le serveur de publication et les Abonnés. Cette synchronisation peut être effectuée par réplication avec un *instantané*, qui est une copie de tous les objets et de toutes les données spécifiées par une publication. Quand l'instantané est créé, il est remis aux Abonnés. Pour certaines applications, la réplication d'instantané est tout ce qui est requis. Pour d'autres types d'applications, il est important que les modifications de données suivantes soient transmises à l'Abonné de façon incrémentielle au fil du temps. Certaines applications requièrent aussi que les modifications transitent en sens inverse, de l'Abonné vers le serveur de publication. La réplication transactionnelle et la réplication de fusion comportent des options pour ces types d'applications.  
  
 Les modifications des données ne font pas l'objet d'un suivi dans la réplication d'instantané : chaque fois qu'un instantané est appliqué, il remplace complètement les données existantes. La réplication transactionnelle fait le suivi des modifications via le journal des transactions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ; la réplication de fusion fait le suivi des modifications via des déclencheurs et des tables de métadonnées.  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation des Agents de réplication](agents/replication-agents-overview.md)  
  
  
