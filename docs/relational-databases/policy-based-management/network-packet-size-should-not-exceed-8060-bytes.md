---
title: "La taille du paquet réseau ne doit pas dépasser 8060 octets | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Best Practices [Database Engine]
ms.assetid: 86db5da1-afe4-4fbb-8bf8-33cedc7e4361
caps.latest.revision: "8"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 365d969fdc6ebe3af7f8c2a93782e59a611c0717
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="network-packet-size-should-not-exceed-8060-bytes"></a>La taille du paquet réseau ne doit pas dépasser 8060 octets
  Si la valeur spécifiée pour sp_configure 'network packet size' ou si la taille du paquet réseau de tout utilisateur connecté est supérieure à 8060 octets, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] effectue des opérations d'allocation de mémoire différentes. Cela peut entraîner une augmentation de l'espace d'adressage virtuel de processus qui n'est pas réservé pour le pool de mémoires tampons.  
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
 La taille du paquet réseau ne doit pas dépasser 8060 octets.  
  
## <a name="for-more-information"></a>Pour plus d'informations  
 [Article 903002 de la Base de connaissances Microsoft](http://go.microsoft.com/fwlink/?linkid=117749)  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôler et appliquer les meilleures pratiques à l'aide de la Gestion basée sur des stratégies](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
