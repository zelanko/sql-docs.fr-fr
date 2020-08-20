---
description: Fonctionnement des procédures stockées étendues
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
ms.openlocfilehash: 49c5f3491d93ee71a0ce118a5f4ba387da770f1c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88460814"
---
# <a name="how-extended-stored-procedures-work"></a>Fonctionnement des procédures stockées étendues

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Utilisez l’intégration CLR à la place.  
  
 Le processus de fonctionnement d'une procédure stockée étendue est le suivant :  
  
1.  Lorsqu’un client exécute une procédure stockée étendue, la demande est transmise au format tabular data stream (TDS) ou SOAP (Simple Object Access Protocol) à partir de l’application cliente vers [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
2.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] recherche la DLL associée à la procédure stockée étendue et la charge si elle ne l'est déjà.  
  
3.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] appelle la procédure stockée étendue demandée (implémentée comme fonction à l'intérieur de la DLL).  
  
4.  La procédure stockée étendue transmet les jeux de résultats et retourne les paramètres au serveur via l'API de la procédure stockée étendue.  

