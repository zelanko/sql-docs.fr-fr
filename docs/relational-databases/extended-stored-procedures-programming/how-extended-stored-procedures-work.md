---
title: Fonctionnement des procédures stockées étendues | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], about extended stored procedures
ms.assetid: 6e946d8c-3268-4b59-8a1c-1637909cd701
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: f7bbc9fad964f5d58efeb48683b052275f7fb166
ms.sourcegitcommit: cff8dd63959d7a45c5446cadf1f5d15ae08406d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/05/2019
ms.locfileid: "67583328"
---
# <a name="how-extended-stored-procedures-work"></a>Fonctionnement des procédures stockées étendues

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Utilisez l’intégration CLR à la place.  
  
 Le processus de fonctionnement d'une procédure stockée étendue est le suivant :  
  
1.  Lorsqu’un client exécute une procédure stockée étendue, la demande est transmise dans le flux de données tabulaires (TDS) ou format SOAP Simple Object Access Protocol () à partir de l’application cliente pour [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] recherche la DLL associée à la procédure stockée étendue et la charge si elle ne l'est déjà.  
  
3.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] appelle la procédure stockée étendue demandée (implémentée comme fonction à l'intérieur de la DLL).  
  
4.  La procédure stockée étendue transmet les jeux de résultats et retourne les paramètres au serveur via l'API de la procédure stockée étendue.  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

