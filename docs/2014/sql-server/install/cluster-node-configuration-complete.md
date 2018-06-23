---
title: Configuration du nœud (complète) du cluster | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 64174d54-edee-49b8-9b43-039574bf2ca1
caps.latest.revision: 10
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 61643e7a5d21d106430d0bc9fbd4672efe0924f0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36152964"
---
# <a name="cluster-node-configuration-complete"></a>Configuration du nœud de cluster (Complète)
  Utilisez la page Configuration du nœud de clusters (Complète) pour spécifier une instance existante de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui a été préparée pour le clustering. Pour installer ou mettre à niveau un cluster de basculement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , vous devez exécuter le programme d'installation sur chaque nœud du cluster de basculement. Pour ajouter un nœud à un cluster de basculement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] existant, vous devez exécuter le programme d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur le nœud destiné à être ajouté à l'instance de cluster de basculement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="options"></a>Options  
 Dans les zones de liste déroulante :  
  
-   Nom de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] — Sélectionnez le nom de l'instance pour le cluster de basculement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Nom de ce nœud — Ce champ est prérempli avec le nom de l'ordinateur où le programme d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'exécute.  
  
-   Nom réseau du cluster de basculement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]— Ce champ n'est pas prérempli. Indiquez le nom réseau de la nouvelle instance de cluster de basculement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Il s'agit du nom qui identifie l'instance de cluster de basculement sur le réseau.  
  
  