---
title: Didacticiels sur la réplication | Microsoft Docs
ms.custom: ''
ms.date: 04/09/2018
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- tutorials [SQL Server replication]
- walkthroughs [SQL Server replication]
- replication [SQL Server], tutorials
ms.assetid: 19fbd10e-5b59-4cd0-a988-52d5d9206242
caps.latest.revision: 13
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 3900aae4e96b5490b0b65cbbee004fc66337ff63
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="replication-tutorials"></a>Didacticiels sur la réplication
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
La réplication est une solution efficace pour transférer des données, ou des sous-ensembles de données, entre des serveurs. Vous pouvez répliquer des données entre des serveurs intégralement connectés à l’aide de la réplication transactionnelle. Vous pouvez également répliquer des données entre des serveurs et des clients qui sont connectés par intermittence à l’aide de la réplication de fusion. Ci-après, vous trouverez des tutoriels qui vous aident à préparer votre serveur pour la réplication, puis vous apprennent à configurer la réplication transactionnelle et la réplication de fusion. 
  
Dans les tutoriels sur la réplication, « serveur de publication » fait référence au serveur qui contient les données source en cours de réplication et « Abonné » au serveur de destination. Le serveur de publication et l'Abonné peuvent partager la même instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], mais ce n'est pas une obligation. Pour plus d’informations, consultez [Présentation du modèle de publication de réplication](../../relational-databases/replication/publish/replication-publishing-model-overview.md).  

Ces tutoriels utilisent NODE1\SQL2016 comme serveur de publication et serveur de distribution et NODE2\SQL2016 comme Abonné. 
  
> [!NOTE]  
> La plupart des tâches expliquées dans ces didacticiels peuvent être effectuées par programme. Pour plus d’informations, consultez [Guide du développeur (réplication)](../../relational-databases/replication/concepts/replication-developer-documentation.md).  
  
## <a name="replication-tutorials"></a>Didacticiels sur la réplication  
[Tutoriel : Préparer SQL Server pour la réplication : serveur de publication, base de données du serveur de distribution, Abonné](../../relational-databases/replication/tutorial-preparing-the-server-for-replication.md) 
 
Apprenez à préparer les serveurs afin que la réplication puisse s'exécuter avec les privilèges minimaux. Ce didacticiel doit être effectué avant les autres didacticiels sur la réplication.  
  
[Tutoriel : Configurer la réplication entre deux serveurs intégralement connectés (réplication transactionnelle)](../../relational-databases/replication/tutorial-replicating-data-between-continuously-connected-servers.md)

Apprenez à configurer la réplication transactionnelle pour répliquer les données entre serveurs intégralement connectés. Ce tutoriel inclut également une méthodologie de résolution des erreurs de base. 

  
[Tutoriel : Configurer la réplication entre un serveur et des clients mobiles (réplication de fusion)](../../relational-databases/replication/tutorial-replicating-data-with-mobile-clients.md)

Apprenez à configurer la réplication de fusion pour échanger les données entre un serveur et un ou plusieurs clients connectés uniquement de façon occasionnelle.  
  
## <a name="see-also"></a> Voir aussi  
[Sécurité et protection pour la réplication](../../relational-databases/replication/security/security-and-protection-replication.md) 

[Présentation de la réplication transactionnelle](https://docs.microsoft.com/en-us/sql/relational-databases/replication/transactional/transactional-replication) 

[Présentation de la réplication de fusion](https://docs.microsoft.com/en-us/sql/relational-databases/replication/merge/merge-replication)

  