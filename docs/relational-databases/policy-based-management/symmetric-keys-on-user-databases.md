---
title: "Clés symétriques sur les bases de données utilisateur | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance-monitor
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Best Practices [Database Engine]
ms.assetid: 3333ab5b-2518-4753-a0a8-57df5e5af74f
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cb25dc5548378c8057c7f3f90168bab5d85c8e7b
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="symmetric-keys-on-user-databases"></a>Clés symétriques sur les bases de données utilisateur
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Cette règle vérifie que les clés dont la longueur est inférieure à 128 octets n’utilisent pas l’algorithme de chiffrement RC2 ou RC4.  
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
 Utilisez AES 128 bits ou supérieur pour créer des clés symétriques pour le chiffrement de données. Si AES n'est pas pris en charge par votre système d'exploitation, utilisez 3DES.  
  
## <a name="for-more-information"></a>Pour plus d'informations  
 [Choisir un algorithme de chiffrement](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôler et appliquer les meilleures pratiques à l'aide de la Gestion basée sur des stratégies](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
