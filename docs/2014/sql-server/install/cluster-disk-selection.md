---
title: Sélection du disque de cluster | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- cluster disk selection
ms.assetid: 0d6b863d-5972-4a20-9990-64ee8016fea6
caps.latest.revision: 9
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ce08658fe769a356e4cd24e29ed094692892e48f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36045094"
---
# <a name="cluster-disk-selection"></a>Sélection du disque du cluster
  Utilisez la page **Sélection du disque du cluster** de l’Assistant Installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour sélectionner la ressource disque de cluster partagée pour votre cluster de basculement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le disque de cluster est l'emplacement où les données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] seront placées.  
  
 Un disque de cluster partagé n’est pas obligatoire pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] les installations de cluster. Un serveur de fichiers SMB est un stockage pris en charge pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] basculement les installations de cluster et peut être spécifié à l’aide de la **moteur de base de données – répertoires de données** page avant la fin de l’installation.  
  
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
  
  