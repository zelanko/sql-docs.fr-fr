---
title: LOCALDB_ERROR_INSUFFICIENT_BUFFER | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: ff67bda8-7e5c-4b06-8d7b-9985b6059a98
author: stevestein
ms.author: sstein
ms.openlocfilehash: 372ec1bbee84b90a9a30ec768fd7a35e3f6112d5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67995786"
---
# <a name="localdb_error_insufficient_buffer"></a>LOCALDB_ERROR_INSUFFICIENT_BUFFER
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|276|  
|Source de l’événement|Runtime de base de données locale SQL Server 12.0|  
|Composant|API d'exécution de la base de données locale|  
|Texte du message|La tampon transmis à la méthode d'API d'instance de base de données locale a une taille insuffisante.|  
  
## <a name="explanation"></a>Explication  
 Le tampon d'entrée est trop court, et la troncation n'a pas été demandée.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Fournissez un tampon de la taille spécifiée.  
  
  
