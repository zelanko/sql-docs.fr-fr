---
title: Ajouter un Abonné non-SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.rep.newsubwizard.addnonsqlsubscriber.f1
ms.assetid: 21beeaa0-4b9e-48da-be63-1b9ff14e03d2
caps.latest.revision: 10
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: be1939b2c9f0f56a0c8d4ef82978f772ef9d229c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36152094"
---
# <a name="add-non-sql-server-subscriber"></a>Ajouter un Abonné non-SQL Server
  La réplication prend en charge la création d'abonnement par envoi de données (push) à des publications d'instantané et transactionnelles pour les abonnés Oracle et IBM DB2.  
  
## <a name="options"></a>Options  
 **Type d'Abonné à ajouter**  
 Sélectionnez un abonné Oracle ou IBM DB2. Pour plus d’informations sur la prise en charge de ces Abonnés, consultez [Abonnés non-SQL Server](non-sql/non-sql-server-subscribers.md).  
  
 **Nom de la source des données**  
 Nom utilisé pour localiser la base de données sur un réseau. La réplication produit une chaîne de connexion pour la base de données en utilisant le nom de la source de données, combiné à la connexion, au mot de passe et à toute autre option spécifiée dans la page **Sécurité de l'Agent de distribution** de cet Assistant.  
  
> [!NOTE]  
>  Le nom de la source de données et la chaîne de connexion ne sont pas validés par [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tant que l’Agent de distribution n’a pas tenté d’initialiser l’abonnement.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer un abonnement pour un abonné non-SQL Server](create-a-subscription-for-a-non-sql-server-subscriber.md)   
 [Non-SQL Server Subscribers](non-sql/non-sql-server-subscribers.md)   
 [S'abonner à des publications](subscribe-to-publications.md)  
  
  