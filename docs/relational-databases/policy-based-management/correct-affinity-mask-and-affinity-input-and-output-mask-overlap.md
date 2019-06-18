---
title: Corriger le chevauchement des options Masque d’affinité et Masque d’affinité d’E/S | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 1a0da6df-57ff-4f3f-aae9-2fbc4897508c
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 96473ebbee3a0cd946c1ecbe3ebaae2b05ce4b3f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63007574"
---
# <a name="correct-affinity-mask-and-affinity-input-and-output-mask-overlap"></a>Corriger le chevauchement des options Masque d’affinité et Masque d’affinité d’E/S
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Cette règle vérifie si l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a un ou plusieurs processeurs prévus pour être utilisés à la fois avec l'option affinity mask (masque d'affinité) et l'option affinity I/O mask (masque d'affinité d'E/S). Sur un ordinateur doté de plusieurs processeurs, les options affinity mask et affinity I/O mask sont utilisées pour désigner quels processeurs sont utilisés par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. L'activation d'un processeur à la fois dans affinity mask et dans affinity I/O mask peut ralentir les performances en forçant l'utilisation excessive du processeur.  
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
 Lorsque vous définissez l'option affinity mask, vous devez également définir l'option affinity I/O mask, et inversement, mais vous ne devez activer chaque processeur que dans l'une de ces options.  
  
 N'activez pas le même processeur à la fois dans l'option affinity mask et dans l'option affinity I/O mask. Les bits correspondant à chaque processeur doivent présenter l'un des états suivants :  
  
-   0 dans l'option affinity mask et dans l'option affinity I/O mask  
  
-   0 dans l'option affinity mask et 1 dans l'option affinity I/O mask  
  
-   1 dans l'option affinity mask et 0 dans l'option affinity I/O mask  
  
## <a name="for-more-information"></a>Pour plus d'informations  
 [Masque d'affinité (option de configuration de serveur)](../../database-engine/configure-windows/affinity-mask-server-configuration-option.md)  
  
 [option de configuration de serveur Masque d’affinité d’E/S](../../database-engine/configure-windows/affinity-input-output-mask-server-configuration-option.md)  
  
 [Masque d'affinité 64 (option de configuration de serveur)](../../database-engine/configure-windows/affinity64-mask-server-configuration-option.md)  
  
 [option de configuration du serveur affinity64 Input-Output mask](../../database-engine/configure-windows/affinity64-input-output-mask-server-configuration-option.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôler et appliquer les meilleures pratiques à l'aide de la Gestion basée sur des stratégies](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
