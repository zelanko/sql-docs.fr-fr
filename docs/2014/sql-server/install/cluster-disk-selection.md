---
title: Sélection du disque de cluster | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
f1_keywords:
- cluster disk selection
ms.assetid: 0d6b863d-5972-4a20-9990-64ee8016fea6
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 55c4bd42e1a025543bfb249c82453903670e713f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48102669"
---
# <a name="cluster-disk-selection"></a>Sélection du disque du cluster
  Utilisez la page **Sélection du disque du cluster** de l’Assistant Installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour sélectionner la ressource disque de cluster partagée pour votre cluster de basculement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le disque de cluster est l'emplacement où les données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] seront placées.  
  
 Un disque de cluster partagé n’est pas une exigence pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] installations de cluster. Un serveur de fichiers SMB est un stockage pris en charge pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] basculement installations de cluster et peut être spécifié à l’aide de la **moteur de base de données – répertoires de données** page avant la fin de l’installation.  
  
> [!WARNING]  
>  Si vous avez sélectionné Analysis Services pour l'installer, vous devez spécifier un disque de cluster partagé.  
>   
>  Si vous envisagez d'activer FILESTREAM sur cette instance du cluster de basculement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous devez spécifier un disque de cluster partagé.  
  
## <a name="options"></a>Options  
 **Disques partagés**  
 Sélectionnez un disque dans la liste. Le disque de cluster est l'emplacement où les données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] seront placées.  
  
 Un seul disque peut être spécifié. Si vous sélectionnez le groupe contenant la ressource quorum du cluster, un avertissement s'affiche. Il est recommandé de ne pas procéder à l'installation dans cette ressource.  
  
 **Disques partagés disponibles**  
 Affiche une liste de disques disponibles, indique si chacun d'eux est qualifié en tant que disque partagé et fournit une description de chaque ressource de disque.  
  
  
