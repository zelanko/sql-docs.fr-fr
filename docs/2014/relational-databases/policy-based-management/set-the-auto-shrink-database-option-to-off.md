---
title: Définir l’option de base de données AUTO_SHRINK sur OFF | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 16403850-d745-4754-b84f-5f01aaecd24e
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: c81885e5a3aaec197b8963c2e868b6f65a0b0544
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62691510"
---
# <a name="set-the-auto_shrink-database-option-to-off"></a>Définir l'option de base de données AUTO_SHRINK sur OFF
  Cette règle vérifie si l'option de base de données AUTO_SHRINK est définie avec la valeur OFF. La réduction et le développement fréquents d'une base de données peuvent entraîner une fragmentation physique.  
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
 Définissez l'option de base de données AUTO_SHRINK avec la valeur OFF. Si vous savez que vous n'aurez pas besoin de l'espace que vous récupérez, vous pouvez le récupérer en réduisant manuellement la base de données.  
  
## <a name="for-more-information"></a>Pour plus d'informations  
 Article [315512](https://go.microsoft.com/fwlink/?linkid=117750)de la Base de connaissances Microsoft  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôler et appliquer les bonnes pratiques à l’aide de la gestion basée sur des stratégies](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
