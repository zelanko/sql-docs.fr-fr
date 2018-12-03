---
title: Exécuter le Moniteur système | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
s.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- System Monitor [SQL Server], running
- Windows System Monitor [SQL Server], running
- remote procedure calls [SQL Server]
- starting Windows NT System Monitor
- RPC
ms.assetid: 05297984-bc8d-43df-829c-032387f7ea61
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 9ceac8451a8c1043876efa7025d41d7420ce150d
ms.sourcegitcommit: ca038f1ef180e4e1b27910bbc5d87822cd1ed176
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52158767"
---
# <a name="run-system-monitor"></a>Exécuter le Moniteur système
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Le Moniteur système utilise les appels de procédures distantes (RPC) pour collecter les informations de Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Tout utilisateur qui dispose des autorisations Microsoft Windows pour exécuter le Moniteur système peut l'utiliser pour surveiller le fonctionnement de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Lorsque vous utilisez le Moniteur système ou l'Analyseur de performances, vous ne pouvez pas vous connecter à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fonctionnant sous Microsoft Windows 98.  
  
 Comme avec tous les outils d'analyse de performances, attendez-vous à une certaine diminution des performances due à une surcharge du système, lorsque vous utilisez le Moniteur système pour surveiller [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La surcharge effective de toute instance particulière dépend de la plateforme matérielle, du nombre de compteurs et de la fréquence de mise à jour choisie. Cependant, l'intégration du Moniteur système à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est conçue pour minimiser toute diminution des performances.  
  
> [!NOTE]  
>  Si vous avez sélectionné les compteurs de performances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour les surveiller via le composant logiciel enfichable Moniteur système, vous verrez ces compteurs même si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne s'exécute pas.  
  
 Pour plus d’informations sur le démarrage du Moniteur système, consultez [Démarrer le Moniteur système &#40;Windows&#41;](../../relational-databases/performance/start-system-monitor-windows.md).  
  
  
