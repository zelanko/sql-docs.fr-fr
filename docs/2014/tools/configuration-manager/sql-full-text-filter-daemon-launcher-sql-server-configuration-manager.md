---
title: Lanceur de démon de filtre de texte intégral SQL (Gestionnaire de configuration SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- configmgr-client
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: d0dc03db-5f76-4558-b041-1ac7b9b5bb16
caps.latest.revision: 7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b8c1e4bc30abd7773a3059d804b31c877ee36e9c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37172030"
---
# <a name="sql-full-text-filter-daemon-launcher-sql-server-configuration-manager"></a>Lanceur de démon de filtre de texte intégral SQL (Gestionnaire de configuration SQL Server)
  À compter de [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], le service du lanceur de démon de filtre de texte intégral SQL (lanceur FDHOST) est utilisé par la recherche en texte intégral dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour démarrer le processus hôte de démon de filtre, qui gère l'analyse lexicale et le filtrage de recherche en texte intégral. Ce service doit être en cours d'exécution pour que la recherche en texte intégral puisse être utilisée. Le service du lanceur FDHOST est un service dépendant d’une instance qui est associé à une instance spécifique de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le service du lanceur FDHOST propage les informations sur le compte de service à chaque processus hôte de démon de filtre démarré. Pour plus d’informations sur les processus hôte de démon de filtre, consultez « Architecture de la recherche en texte intégral » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
  
