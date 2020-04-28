---
title: LOCALDB_ERROR_UNKNOWN_LANGUAGE_ID | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: fa082dca-bf88-46e7-b61e-7ac8835a3493
author: stevestein
ms.author: sstein
ms.openlocfilehash: 93d770fde71fe51b06bfe8fc95b87d023765eb5d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68127030"
---
# <a name="localdb_error_unknown_language_id"></a>LOCALDB_ERROR_UNKNOWN_LANGUAGE_ID
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|270|  
|Source de l’événement|Runtime de base de données locale SQL Server 12.0|  
|Composant|API d'exécution de la base de données locale|  
|Texte du message|Erreur de réception du message d'erreur localisé. La langue spécifiée par le paramètre 'ID de langue' est inconnue.|  
  
## <a name="explanation"></a>Explication  
 La langue demandée pour le message d'erreur d'exécution de base de données locale est inconnue ou non prise en charge.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Tentez de demander une langue prise en charge pour les messages d'erreur d'exécution de base de données locale, ou la langue par défaut.  
  
  
