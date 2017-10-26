---
title: "La taille du paquet réseau ne doit pas dépasser 8060 octets | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 86db5da1-afe4-4fbb-8bf8-33cedc7e4361
caps.latest.revision: 8
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: cb2e255e501d739ddfe8f822c7c62b212aa14db8
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="network-packet-size-should-not-exceed-8060-bytes"></a>La taille du paquet réseau ne doit pas dépasser 8060 octets
  Si la valeur spécifiée pour sp_configure 'network packet size' ou si la taille du paquet réseau de tout utilisateur connecté est supérieure à 8060 octets, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] effectue des opérations d'allocation de mémoire différentes. Cela peut entraîner une augmentation de l'espace d'adressage virtuel de processus qui n'est pas réservé pour le pool de mémoires tampons.  
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
 La taille du paquet réseau ne doit pas dépasser 8060 octets.  
  
## <a name="for-more-information"></a>Pour plus d'informations  
 [Article 903002 de la Base de connaissances Microsoft](http://go.microsoft.com/fwlink/?linkid=117749)  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôler et appliquer les meilleures pratiques à l'aide de la Gestion basée sur des stratégies](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  

