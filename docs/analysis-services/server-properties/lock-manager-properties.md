---
title: "Propri&#233;t&#233;s du gestionnaire de verrous | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "propriétés du gestionnaire de verrous [Analysis Services]"
  - "LockWaitGranularityMS, propriété"
  - "DefaultLockTimeoutMS, propriété"
  - "DeadlockDetectionGranularityMS, propriété"
ms.assetid: 15fe9ead-825b-4ac3-9191-7a07caa2861b
caps.latest.revision: 16
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 16
---
# Propri&#233;t&#233;s du gestionnaire de verrous
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] prend en charge les propriétés du serveur du gestionnaire de verrous répertoriées dans le tableau suivant. Pour plus d’informations sur les autres propriétés de serveur et la façon de les configurer, consultez [Propriétés du serveur dans Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md).  
  
 **S'applique à :** mode serveur multidimensionnel et tabulaire  
  
## Propriétés  
 **DefaultLockTimeoutMS**  
 Propriété dont la valeur est un entier 32 bits signé qui définit le délai d'expiration de verrouillage par défaut (en millisecondes) pour les demandes de verrous internes.  
  
 La valeur par défaut de cette propriété est -1, qui indique l'absence de délai d'expiration pour les demandes de verrous internes.  
  
 **LockWaitGranularityMS**  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **DeadlockDetectionGranularityMS**  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## Voir aussi  
 [propriétés du serveur dans Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md)   
 [Déterminer le mode serveur d'une instance Analysis Services](../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  