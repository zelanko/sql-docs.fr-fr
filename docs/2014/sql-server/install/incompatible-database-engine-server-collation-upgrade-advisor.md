---
title: Classement de serveur du moteur de base de données incompatible (Conseiller de mise à niveau) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 80f499d6-2c90-49eb-a5b3-0bb5b7faaa3b
caps.latest.revision: 8
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: 5a81084ff6eba37d8a6fcc2643a760d879dcf13c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36051860"
---
# <a name="incompatible-database-engine-server-collation-upgrade-advisor"></a>Classement du serveur du moteur de base de données incompatible (Conseiller de mise à niveau)
  A détecté le Conseiller de mise à niveau [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] utilise une instance de la [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] qui est configuré pour utiliser un classement du serveur incompatible.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Mode SharePoint.|  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Description  
 A détecté le Conseiller de mise à niveau [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] utilise une instance de la [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] qui est configuré pour utiliser un classement du serveur incompatible.  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] En mode SharePoint utilise l’architecture de services partagés SharePoint. SharePoint ne prend pas en charge le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] configuré pour respecter la casse ou des classements du serveur ou des classements du serveur binaires. Les classements incompatibles incluent les classements qui respectent la casse par défaut ou binaires et un classement de base qui est par défaut compatible, a ont été configuré avec l'un des indicateurs de classement suivants :  
  
-   **Binaire**  
  
-   **La casse**  
  
-   **Point de code binaire**  
  
 Étant donné que le classement du serveur du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] actuel est incompatible, la mise à niveau est bloquée.  
  
## <a name="corrective-action"></a>Action corrective  
 La propriété de classement du serveur du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ne peut pas être modifiée. Vous ne pouvez pas effectuer une mise à niveau de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Vous devez migrer votre installation de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sur un nouveau serveur qui utilise un classement du serveur compatible. Pour plus d'informations, consultez les documents suivants :  
  
-   [Mettre à niveau et migrer Reporting Services](http://go.microsoft.com/fwlink/?LinkId=233227)  
  
-   [Sélection d’un classement SQL Server](http://go.microsoft.com/fwlink/?LinkId=233226)  
  
  