---
title: MSSQLSERVER_7915 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 7915 (Database Engine error)
ms.assetid: 63338587-7dd3-40e6-b70e-d8ae18fff47b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f58c6d1767666d1965bbfa99d9d257e0ed90022b
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "68125535"
---
# <a name="mssqlserver_7915"></a>MSSQLSERVER_7915
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|7915|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBCC2_REPAIR_IAM_CHAIN_REBUILT|  
|Texte du message|Réparation : la chaîne IAM pour l'ID d'objet O_ID, ID d'index I_ID, ID de partition PN_ID, ID d'unité d'allocation A_ID (type TYPE), a été tronquée avant la page P_ID et sera reconstruite.|  
  
## <a name="explanation"></a>Explication  
Ceci est un message d'information envoyé par REPAIR, qui indique que la chaîne IAM (Index Allocation Map) spécifiée a été corrigée afin de pouvoir être reconstruite. Cette correction peut avoir requis l'allocation d'une nouvelle tête de la chaîne IAM ou la suppression de pages incorrectes de la chaîne.  
  
## <a name="user-action"></a>Action de l'utilisateur  
None  
  
