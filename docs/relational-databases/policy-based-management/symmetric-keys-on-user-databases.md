---
description: Clés symétriques sur les bases de données utilisateur
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
ms.openlocfilehash: c7882b4f3f425b600e3ef57fa836ffffd6756289
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88380965"
---
# <a name="symmetric-keys-on-user-databases"></a>Clés symétriques sur les bases de données utilisateur
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Cette règle vérifie que les clés dont la longueur est inférieure à 128 octets n'utilisent pas l'algorithme de chiffrement RC2 ou RC4.  
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
 Utilisez AES 128 bits ou supérieur pour créer des clés symétriques pour le chiffrement de données. Si AES n'est pas pris en charge par votre système d'exploitation, utilisez 3DES.  
  
## <a name="for-more-information"></a>Pour plus d'informations  
 [Choisir un algorithme de chiffrement](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôler et appliquer les bonnes pratiques à l’aide de la gestion basée sur des stratégies](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
