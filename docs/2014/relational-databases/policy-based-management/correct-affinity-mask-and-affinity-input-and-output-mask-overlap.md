---
title: Chevauchement de masque correct Affinity Mask et Affinity d’entrée/sortie | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 1a0da6df-57ff-4f3f-aae9-2fbc4897508c
caps.latest.revision: 11
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9a5cc744eb941d309ff938452fef01a24716a946
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36142027"
---
# <a name="correct-affinity-mask-and-affinity-input-output-mask-overlap"></a>Masque d’affinité correcte et le chevauchement de masque d’affinité d’entrée/sortie
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
 [Contrôler et appliquer les meilleures pratiques à l'aide de la Gestion basée sur des stratégies](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  