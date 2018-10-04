---
title: Défaillances inattendues du système | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 1679bf9e-a2ef-4f90-8907-a002f7341a7d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 4451b3103281038d383d3e2dda2ab0353ff1b90d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48207209"
---
# <a name="unexpected-system-failures"></a>Défaillances inattendues du système
  Cette règle recherche l'événement système 6008 dans le journal des événements de l'ordinateur. Cet événement indique un arrêt inattendu du système. Il est possible que le système soit instable et qu'il ne présente pas la stabilité et l'intégrité qui sont requises pour héberger une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
 Résolvez immédiatement le problème à l'origine du redémarrage inattendu du serveur ou déplacez l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur un autre ordinateur.  
  
  
