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
manager: craigg
ms.openlocfilehash: 31e24d4cd5e790751b4a43773f2b7d0156b4b7da
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62915455"
---
# <a name="mssqlserver_15661"></a>MSSQLSERVER_15661
    
## <a name="details"></a>Détails  
  
|||  
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
  
  
