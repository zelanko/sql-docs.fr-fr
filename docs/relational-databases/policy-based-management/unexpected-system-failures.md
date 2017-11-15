---
title: "Défaillances inattendues du système | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Best Practices [Database Engine]
ms.assetid: 1679bf9e-a2ef-4f90-8907-a002f7341a7d
caps.latest.revision: "8"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 748ae11aba0fafb4f04f8b0dc54af247aece3074
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="unexpected-system-failures"></a>Défaillances inattendues du système
  Cette règle recherche l'événement système 6008 dans le journal des événements de l'ordinateur. Cet événement indique un arrêt inattendu du système. Il est possible que le système soit instable et qu'il ne présente pas la stabilité et l'intégrité qui sont requises pour héberger une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
 Résolvez immédiatement le problème à l'origine du redémarrage inattendu du serveur ou déplacez l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur un autre ordinateur.  
  
  
