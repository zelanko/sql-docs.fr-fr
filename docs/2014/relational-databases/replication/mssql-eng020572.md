---
title: MSSQL_ENG020572 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSSQL_ENG020572 error
ms.assetid: 636566db-ffcf-4109-8c11-15b8c7cb9cd9
caps.latest.revision: 10
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 6bbb02650086562959ba1eaef862887803abb9eb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36052813"
---
# <a name="mssqleng020572"></a>MSSQL_ENG020572
    
## <a name="message-details"></a>Détails du message  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|20572|  
|Source de l'événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique||  
|Texte du message|L'Abonné '%s' avec un abonnement à l'article '%s' de la publication '%s' a été réinitialisé après l'échec de la validation.|  
  
## <a name="explanation"></a>Explication  
 Lors de la validation des données de l'Abonné par rapport aux données du serveur de publication, les données ne correspondaient pas, par conséquent la validation a échoué. Lorsque vous avez spécifié qu'il était nécessaire d'effectuer la validation, vous avez sélectionné l'option selon laquelle un abonnement devait être réinitialisé en cas d'échec de la validation. La réinitialisation d'un abonnement implique d'appliquer un nouvel instantané à l'Abonné. Pour plus d'informations sur la validation, consultez [Validate Replicated Data](validate-replicated-data.md).  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Les données du serveur de publication et de l'Abonné concorderont une fois que le nouvel instantané sera appliqué à l'Abonné.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des événements &#40;réplication&#41;](errors-and-events-reference-replication.md)  
  
  