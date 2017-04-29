---
title: "Clés symétriques sur les bases de données utilisateur | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 3333ab5b-2518-4753-a0a8-57df5e5af74f
caps.latest.revision: 6
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 77d055855124273c93485ac3ddce692188e1e36b
ms.lasthandoff: 04/11/2017

---
# <a name="symmetric-keys-on-user-databases"></a>Clés symétriques sur les bases de données utilisateur
  Cette règle vérifie que les clés dont la longueur est inférieure à 128 octets n'utilisent pas l'algorithme de chiffrement RC2 ou RC4.  
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
 Utilisez AES 128 bits ou supérieur pour créer des clés symétriques pour le chiffrement de données. Si AES n'est pas pris en charge par votre système d'exploitation, utilisez 3DES.  
  
## <a name="for-more-information"></a>Pour plus d'informations  
 [Choisir un algorithme de chiffrement](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôler et appliquer les meilleures pratiques à l'aide de la Gestion basée sur des stratégies](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
