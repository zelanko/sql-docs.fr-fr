---
title: MSSQLSERVER_17128 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 17128 (Database Engine error)
ms.assetid: 7b15a5e6-fd41-47ce-ba87-54f72acea4bb
caps.latest.revision: 14
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 271533cfd9ab0cdec919e5a885e0334caa4beaab
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37428858"
---
# <a name="mssqlserver17128"></a>MSSQLSERVER_17128
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|17128|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|INIT_NOBUFSPACE|  
|Texte du message|initdata : aucune mémoire pour les tampons du noyau.|  
  
## <a name="explanation"></a>Explication  
 Les réservations ou les allocations de mémoire initiales du pool de mémoires tampons ont échoué, et SQL Server se termine.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Provoqué généralement par le démarrage de SQL Server sur un ordinateur extrêmement petit, beaucoup plus petit que la configuration requise minimale.  
  
  
