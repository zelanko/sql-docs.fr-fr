---
title: LOCALDB_ERROR_UNKNOWN_LANGUAGE_ID | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: fa082dca-bf88-46e7-b61e-7ac8835a3493
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: bfad881fb77bd17bbf91bfbcb34ec6ee3cea46aa
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63126063"
---
# <a name="localdb_error_unknown_language_id"></a>LOCALDB_ERROR_UNKNOWN_LANGUAGE_ID
    
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
  
  
