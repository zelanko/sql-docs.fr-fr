---
title: Classement du serveur de Moteur de base de données incompatible (conseiller de mise à niveau) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 80f499d6-2c90-49eb-a5b3-0bb5b7faaa3b
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: fbd4c1e55bb49c6ae8f75d3d12cc243df963018a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "71952232"
---
# <a name="incompatible-database-engine-server-collation-upgrade-advisor"></a>Classement du serveur du moteur de base de données incompatible (Conseiller de mise à niveau)
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] conseiller de mise à niveau détecté utilise une instance du configuré pour utiliser un classement de serveur incompatible.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Mode SharePoint.|  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Description  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] conseiller de mise à niveau détecté utilise une instance du configuré pour utiliser un classement de serveur incompatible.  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Le mode SharePoint utilise l’architecture des services partagés SharePoint. SharePoint ne prend pas en charge le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] configuré pour respecter la casse ou des classements du serveur ou des classements du serveur binaires. Les classements incompatibles incluent les classements qui respectent la casse par défaut ou binaires et un classement de base qui est par défaut compatible, a ont été configuré avec l'un des indicateurs de classement suivants :  
  
-   **Binaire2**  
  
-   **Respect de la casse**  
  
-   **Point de code binaire**  
  
 Étant donné que le classement du serveur du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] actuel est incompatible, la mise à niveau est bloquée.  
  
## <a name="corrective-action"></a>Action corrective  
 La propriété de classement du serveur du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ne peut pas être modifiée. Vous ne pouvez pas effectuer une mise à niveau de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Vous devez migrer votre installation de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sur un nouveau serveur qui utilise un classement du serveur compatible. Pour plus d’informations, consultez les rubriques suivantes :  
  
-   [Upgrade and Migrate Reporting Services](https://go.microsoft.com/fwlink/?LinkId=233227)  
  
-   [Choix d'un classement SQL Server](https://go.microsoft.com/fwlink/?LinkId=233226)  
  
  
