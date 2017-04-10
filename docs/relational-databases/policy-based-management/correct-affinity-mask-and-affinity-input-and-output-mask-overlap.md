---
title: "Correct Affinity Mask and Affinity Input and Output Mask Overlap | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "meilleures pratiques [moteur de base de données]"
ms.assetid: 1a0da6df-57ff-4f3f-aae9-2fbc4897508c
caps.latest.revision: 11
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 11
---
# Correct Affinity Mask and Affinity Input and Output Mask Overlap
  Cette règle vérifie si l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a un ou plusieurs processeurs prévus pour être utilisés à la fois avec l'option affinity mask (masque d'affinité) et l'option affinity I/O mask (masque d'affinité d'E/S). Sur un ordinateur doté de plusieurs processeurs, les options affinity mask et affinity I/O mask sont utilisées pour désigner quels processeurs sont utilisés par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. L'activation d'un processeur à la fois dans affinity mask et dans affinity I/O mask peut ralentir les performances en forçant l'utilisation excessive du processeur.  
  
## Meilleures pratiques recommandées  
 Lorsque vous définissez l'option affinity mask, vous devez également définir l'option affinity I/O mask, et inversement, mais vous ne devez activer chaque processeur que dans l'une de ces options.  
  
 N'activez pas le même processeur à la fois dans l'option affinity mask et dans l'option affinity I/O mask. Les bits correspondant à chaque processeur doivent présenter l'un des états suivants :  
  
-   0 dans l'option affinity mask et dans l'option affinity I/O mask  
  
-   0 dans l'option affinity mask et 1 dans l'option affinity I/O mask  
  
-   1 dans l'option affinity mask et 0 dans l'option affinity I/O mask  
  
## Pour plus d'informations  
 [Masque d'affinité (option de configuration de serveur)](../../database-engine/configure-windows/affinity-mask-server-configuration-option.md)  
  
 [option de configuration de serveur Masque d’affinité d’E/S](../../database-engine/configure-windows/affinity-input-output-mask-server-configuration-option.md)  
  
 [Masque d'affinité 64 (option de configuration de serveur)](../../database-engine/configure-windows/affinity64-mask-server-configuration-option.md)  
  
 [option de configuration du serveur affinity64 Input-Output mask](../../database-engine/configure-windows/affinity64-input-output-mask-server-configuration-option.md)  
  
## Voir aussi  
 [Contrôler et appliquer les meilleures pratiques à l'aide de la Gestion basée sur des stratégies](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  