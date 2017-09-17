---
title: "Restauration de l’historique de révision de membre (Master Data Services) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d39d3474-20e7-429f-9c8d-fcc4eb0854fc
caps.latest.revision: 5
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: a242f91eb8259b8941a61db94f59c4e331d5b06b
ms.contentlocale: fr-fr
ms.lasthandoff: 09/07/2017

---
# <a name="rollback-member-revision-history-master-data-services"></a>Restauration de l’historique de révision de membre (Master Data Services)
  Un historique de révision de membre est enregistré chaque fois qu’un membre fait l’objet d’une modification. Vous pouvez restaurer la version précédente d’un historique de révision de membre.  
  
## <a name="prerequisites"></a>Conditions préalables  
  
-   Vous devez disposer des autorisations requises pour mettre à jour au moins l’un des attributs du membre sélectionné. Lorsque vous restaurez un historique de révision, toutes les valeurs d’attribut qui peuvent être mises à jour sont restaurées à celles de la version précédente.  
  
-   L’historique de révision est disponible uniquement lorsque le type de journal des transactions de l’entité est un membre.  
  
 **Pour restaurer un historique de révision de membre**  
  
1.  Dans Master Data Manager, cliquez sur Explorateur  
  
2.  Choisissez l’entité et le membre à restaurer.  
  
3.  Cliquez sur **Afficher l’historique**.  
  
4.  Choisissez la révision à restaurer, puis cliquez sur **Restaurer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Historique de révision de membre &#40;Master Data Services&#41;](../master-data-services/member-revision-history-master-data-services.md)   
 [Changer le type du journal des transactions de l’entité &#40;Master Data Services&#41;](../master-data-services/change-the-entity-transaction-log-type-master-data-services.md)  
  
  
