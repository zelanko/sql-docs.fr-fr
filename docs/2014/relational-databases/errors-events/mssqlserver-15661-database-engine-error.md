---
title: MSSQLSERVER_15661 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 15661 (Database Engine error)
ms.assetid: 88b01bfb-74ce-4aa0-aec0-7885261c7ef3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9ad20f630056ac4e2f0fe37686955012c0239234
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86553744"
---
# <a name="mssqlserver_15661"></a>MSSQLSERVER_15661
    
## <a name="details"></a>Détails  
  
|Attribut|Valeur|  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|15661|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|SQLErrorNum15661|  
|Texte du message|La procédure stockée sp_estimate_data_compression_savings ne peut pas être utilisée pour les tables temporaires.|  
  
## <a name="explanation"></a>Explication  
 Une table temporaire a été utilisée comme argument de la procédure stockée sp_estimate_data_compression_savings. Bien que la compression de tables temporaires soit prise en charge, vous ne pouvez pas utiliser sp_estimate_data_compression_savings pour estimer les économies de compression.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Supprimez la table temporaire comme argument de sp_estimate_data_compression_savings.  
  
  
