---
title: Lanceur de démon de filtre de texte intégral SQL (Gestionnaire de configuration SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: configuration-manager
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0dc03db-5f76-4558-b041-1ac7b9b5bb16
caps.latest.revision: 8
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 123cbf16970be0820dbda43b0eb51a5e1bca4852
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2018
---
# <a name="sql-full-text-filter-daemon-launcher-sql-server-configuration-manager"></a>Lanceur de démon de filtre de texte intégral SQL (Gestionnaire de configuration SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
À compter de [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], le service du lanceur de démon de filtre de texte intégral SQL (lanceur FDHOST) est utilisé par la recherche en texte intégral dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour démarrer le processus hôte de démon de filtre, qui gère l'analyse lexicale et le filtrage de recherche en texte intégral. Ce service doit être en cours d'exécution pour que la recherche en texte intégral puisse être utilisée. Le service du lanceur FDHOST est un service dépendant d’une instance qui est associé à une instance spécifique de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le service du lanceur FDHOST propage les informations sur le compte de service à chaque processus hôte de démon de filtre démarré. Pour plus d’informations sur les processus hôte de démon de filtre, consultez « Architecture de la recherche en texte intégral » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
  
