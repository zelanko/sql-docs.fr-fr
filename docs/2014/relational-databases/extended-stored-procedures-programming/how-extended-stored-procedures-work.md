---
title: Fonctionnement des procédures stockées étendues | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], about extended stored procedures
ms.assetid: 6e946d8c-3268-4b59-8a1c-1637909cd701
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 7ceb2fd3c9069d762d5e0a317a256fcd92dbe186
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48184739"
---
# <a name="how-extended-stored-procedures-work"></a>Fonctionnement des procédures stockées étendues
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Utilisez l’intégration CLR à la place.  
  
 Le processus de fonctionnement d'une procédure stockée étendue est le suivant :  
  
1.  Lorsqu’un client exécute une procédure stockée étendue, la demande est transmise dans le flux de données tabulaires (TDS) ou format SOAP Simple Object Access Protocol () à partir de l’application cliente pour [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] recherche la DLL associée à la procédure stockée étendue et la charge si elle ne l'est déjà.  
  
3.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] appelle la procédure stockée étendue demandée (implémentée comme fonction à l'intérieur de la DLL).  
  
4.  La procédure stockée étendue transmet les jeux de résultats et retourne les paramètres au serveur via l'API de la procédure stockée étendue.  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation de procédure stockée étendue de moteur de base de données](../database-engine-extended-stored-procedure-programming.md)  
  
  
