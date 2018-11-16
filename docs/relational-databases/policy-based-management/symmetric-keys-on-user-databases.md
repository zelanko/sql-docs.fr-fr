---
title: Clés symétriques sur les bases de données utilisateur | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 3333ab5b-2518-4753-a0a8-57df5e5af74f
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: e8d11021d3e88aa62696d5cf1743359884fa672a
ms.sourcegitcommit: ef6e3ec273b0521e7c79d5c2a4cb4dcba1744e67
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2018
ms.locfileid: "51512494"
---
# <a name="symmetric-keys-on-user-databases"></a>Clés symétriques sur les bases de données utilisateur
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Cette règle vérifie que les clés dont la longueur est inférieure à 128 octets n'utilisent pas l'algorithme de chiffrement RC2 ou RC4.  
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
 Utilisez AES 128 bits ou supérieur pour créer des clés symétriques pour le chiffrement de données. Si AES n'est pas pris en charge par votre système d'exploitation, utilisez 3DES.  
  
## <a name="for-more-information"></a>Pour plus d'informations  
 [Choisir un algorithme de chiffrement](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)  
  
## <a name="see-also"></a> Voir aussi  
 [Contrôler et appliquer les meilleures pratiques à l'aide de la Gestion basée sur des stratégies](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
