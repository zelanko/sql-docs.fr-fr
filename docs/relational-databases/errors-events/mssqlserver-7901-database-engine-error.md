---
title: MSSQLSERVER_7901 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 7901 (Database Engine error)
ms.assetid: 2d0d19b9-947b-4474-9ff8-7e03019ab93d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1a10e03f2dc09bb53078faaaaea36c60e313e0eb
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "67951560"
---
# <a name="mssqlserver_7901"></a>MSSQLSERVER_7901
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|7901|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBCC2_DATABASE_IN_EMERGENCY_MODE|  
|Texte du message|L’instruction de réparation n’a pas été traitée. Ce niveau de réparation n'est pas pris en charge lorsque la base de données est en mode d'urgence.|  
  
## <a name="explanation"></a>Explication  
La base de données est en mode d'urgence et un niveau de réparation autre que REPAIR_ALLOW_DATA_LOSS a été spécifié. Les réparations ne peuvent pas être effectuées en mode d'urgence si REPAIR_ALLOW_DATA_LOSS n'est pas spécifié.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Exécutez de nouveau la commande et spécifiez l'option REPAIR_ALLOW_DATA_LOSS.  
  
