---
title: Blocages avec niveau d’Isolation Repeatable lecture | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- deadlocks in RDS [ADO]
- read repeatable in RDS [ADO]
ms.assetid: 29f3683f-12f3-4304-8a54-fe133c25a423
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e8d863ae660ae8c9792ce56d53288e2794c34eeb
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47735137"
---
# <a name="deadlocks-with-read-repeatable-isolation-level"></a>Interblocages avec le niveau d’isolation REPEATABLE READ
Si un objet métier personnalisé utilise un niveau d’isolation de lecture renouvelable pour accéder à un serveur SQL, et l’objet métier est appelé simultanément par deux clients qui envoient une requête et de mettre à jour dans la même transaction, un blocage est possible. Service de données distant est conçu pour permettre un processus à l’expiration du délai pour libérer le verrou mortel, mais la mise à jour échouent pour ce client.  
  
 Utilisez le [Service de curseur](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) **commande délai d’expiration** propriété dynamique pour modifier la longueur du délai d’attente.  
  
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="see-also"></a>Voir aussi  
 [Principes de base de RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)



