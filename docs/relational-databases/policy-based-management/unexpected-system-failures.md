---
title: "Défaillances inattendues du système | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance-monitor
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 1679bf9e-a2ef-4f90-8907-a002f7341a7d
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 57104ed0869aa6916d11d7329d18526cdaa72836
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/18/2018
---
# <a name="unexpected-system-failures"></a>Défaillances inattendues du système
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Cette règle recherche l’événement système 6008 dans le journal des événements de l’ordinateur. Cet événement indique un arrêt inattendu du système. Il est possible que le système soit instable et qu'il ne présente pas la stabilité et l'intégrité qui sont requises pour héberger une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
 Résolvez immédiatement le problème à l'origine du redémarrage inattendu du serveur ou déplacez l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur un autre ordinateur.  
  
  
