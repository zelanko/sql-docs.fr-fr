---
title: Autres problèmes de mise à niveau de réplication | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- system tables [SQL Server], replication
- passwords [SQL Server replication]
- versions [SQL Server replication]
- connections [SQL Server replication]
- scripts [SQL Server replication]
- ActiveX controls [SQL Server replication]
ms.assetid: 8a5e74be-4992-4f17-b20c-c3dce8f49329
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e5ffde063d94f0e08ea0e82e6b5998a6d23cfaac
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62473180"
---
# <a name="other-replication-upgrade-issues"></a>Autres problèmes de mise à niveau de la réplication
  Cette rubrique traite de plusieurs problèmes de mise à niveau qui ne sont pas signalés par le Conseiller de mise à niveau.  
  
## <a name="versions-supported"></a>Versions prises en charge  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] prend en charge la mise à niveau des bases de données répliquées à partir des versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il n'est pas nécessaire d'arrêter l'activité sur les autres nœuds pendant qu'un nœud est mis à niveau. Prenez soin de respecter les règles relatives aux versions qui sont prises en charge dans une topologie.  
  
 Lorsque vous répliquez entre ou parmi les différentes versions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous n’êtes généralement limité aux fonctionnalités de la version la plus ancienne qui est utilisée.  
  
> [!NOTE]  
>  Le format de stockage sur disque de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] étant le même dans les environnements 64 bits et 32 bits, une topologie de réplication peut combiner des instances de serveur qui s'exécutent dans un environnement 32 bits et des instances de serveur qui s'exécutent dans un environnement 64 bits.  
  
 Pour tous les types de réplication, la version du serveur de distribution ne doit pas être antérieure à la version du serveur de publication. (Dans la plupart des cas, les deux versions sont identiques.)  
  
 Pour la réplication transactionnelle, la version d'un Abonné à une publication transactionnelle peut être n'importe laquelle des deux versions du serveur de publication.  
  
 Pour la réplication de fusion, un Abonné à une publication de fusion peut être n'importe quelle version antérieure à la version du serveur de publication.  
  
## <a name="merge-replication-batches-changes"></a>Modifications des lots de réplication de fusion  
 Les modifications apportées par l'Agent de fusion sont regroupées de manière à améliorer les performances ; par conséquent, une même instruction permet d'insérer, de mettre à jour ou de supprimer plusieurs lignes. Si, dans les bases de données de publication ou d'abonnement, des tables publiées possèdent des déclencheurs, vérifiez que ceux-ci peuvent gérer les insertions, les mises à jour et les suppressions portant sur plusieurs lignes. Pour plus d'informations, consultez « Observations au sujet des lignes multiples pour les déclencheurs DML » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="activex-control-changes"></a>Modifications des contrôles ActiveX  
 Les modifications suivantes ont été apportées aux contrôles ActiveX de réplication :  
  
-   Tous les contrôles ActiveX sont marqués comme non sûrs pour l'écriture de scripts et l'initialisation.  
  
-   Le contrôle ActiveX d'instantané a été supprimé. Vous pouvez créer et gérer des instantanés à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou par programmation en utilisant des procédures stockées de réplication. Pour plus d’informations, consultez les rubriques « Comment : Créer et appliquer l’instantané Initial ([!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]) » et « comment : Créer l’instantané Initial (programmation Transact-SQL) » dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la documentation en ligne.  
  
-   Le contrôle ActiveX de distribution et le contrôle ActiveX de fusion ont été déconseillés. Une fonctionnalité semblable est fournie pour les applications de code managé à l'aide de Replication Management Objects. Pour plus d'informations, consultez « Synchronisation des abonnements (Programmation RMO) » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau de la réplication](../../../2014/sql-server/install/replication-upgrade-issues.md)  
  
  
