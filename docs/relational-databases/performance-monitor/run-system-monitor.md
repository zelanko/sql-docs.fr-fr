---
title: "Exécuter le Moniteur système | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- System Monitor [SQL Server], running
- Windows System Monitor [SQL Server], running
- remote procedure calls [SQL Server]
- starting Windows NT System Monitor
- RPC
ms.assetid: 05297984-bc8d-43df-829c-032387f7ea61
caps.latest.revision: 22
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e16624d722d65aceffa1582bce0d687cd66d1703
ms.contentlocale: fr-fr
ms.lasthandoff: 04/11/2017

---
# <a name="run-system-monitor"></a>Exécuter le Moniteur système
  Le Moniteur système utilise les appels de procédures distantes (RPC) pour collecter les informations de Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Tout utilisateur qui dispose des autorisations Microsoft Windows pour exécuter le Moniteur système peut l'utiliser pour surveiller le fonctionnement de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Lorsque vous utilisez le Moniteur système ou l'Analyseur de performances, vous ne pouvez pas vous connecter à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fonctionnant sous Microsoft Windows 98.  
  
 Comme avec tous les outils d'analyse de performances, attendez-vous à une certaine diminution des performances due à une surcharge du système, lorsque vous utilisez le Moniteur système pour surveiller [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La surcharge effective de toute instance particulière dépend de la plateforme matérielle, du nombre de compteurs et de la fréquence de mise à jour choisie. Cependant, l'intégration du Moniteur système à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est conçue pour minimiser toute diminution des performances.  
  
> [!NOTE]  
>  Si vous avez sélectionné les compteurs de performances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour les surveiller via le composant logiciel enfichable Moniteur système, vous verrez ces compteurs même si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne s'exécute pas.  
  
 Pour plus d’informations sur le démarrage du Moniteur système, consultez [Démarrer le Moniteur système &#40;Windows&#41;](../../relational-databases/performance/start-system-monitor-windows.md).  
  
  
