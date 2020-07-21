---
title: MSSQLSERVER_17128 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17128 (Database Engine error)
ms.assetid: 7b15a5e6-fd41-47ce-ba87-54f72acea4bb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e3a2d500a16a90ce997273fad3eb7c2d8a82c1d6
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86553674"
---
# <a name="mssqlserver_17128"></a>MSSQLSERVER_17128
    
## <a name="details"></a>Détails  
  
|Attribut|Valeur|  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|17128|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|INIT_NOBUFSPACE|  
|Texte du message|initdata : aucune mémoire pour les tampons du noyau.|  
  
## <a name="explanation"></a>Explication  
 Les réservations ou les allocations de mémoire initiales du pool de mémoires tampons ont échoué, et SQL Server se termine.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Provoqué généralement par le démarrage de SQL Server sur un ordinateur extrêmement petit, beaucoup plus petit que la configuration requise minimale.  
  
  
