---
title: MSSQLSERVER_15661 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 15661 (Database Engine error)
ms.assetid: 88b01bfb-74ce-4aa0-aec0-7885261c7ef3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 43ea3ea139bfb252e74110b148ac998132c18452
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "68100398"
---
# <a name="mssqlserver_15661"></a>MSSQLSERVER_15661
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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
  
