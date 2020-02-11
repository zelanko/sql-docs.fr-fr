---
title: Sélection du disque du cluster | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- cluster disk selection
ms.assetid: 0d6b863d-5972-4a20-9990-64ee8016fea6
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 156c17d7dae5c4de07033a96f2e936448d8d02ed
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66096495"
---
# <a name="cluster-disk-selection"></a>Sélection du disque du cluster
  Utilisez la page **Sélection du disque du cluster** de l’Assistant Installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour sélectionner la ressource disque de cluster partagée pour votre cluster de basculement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le disque de cluster est l'emplacement où les données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] seront placées.  
  
 Un disque de cluster partagé n’est pas obligatoire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] pour les installations de cluster. Un serveur de fichiers SMB est un stockage pris [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] en charge pour les installations de cluster de basculement et peut être spécifié à l’aide de la page **moteur de base de données-répertoires de données** avant d’effectuer l’installation.  
  
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
  
  
