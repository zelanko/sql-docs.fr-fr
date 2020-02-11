---
title: Fonctionnement des procédures stockées étendues | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], about extended stored procedures
ms.assetid: 6e946d8c-3268-4b59-8a1c-1637909cd701
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 9b52e8fd5cda7d0b05ebbddbb422f74bd81b1993
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62512991"
---
# <a name="how-extended-stored-procedures-work"></a>Fonctionnement des procédures stockées étendues
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]Utilisez plutôt l’intégration du CLR.  
  
 Le processus de fonctionnement d'une procédure stockée étendue est le suivant :  
  
1.  Lorsqu’un client exécute une procédure stockée étendue, la demande est transmise au format tabular data stream (TDS) ou SOAP (Simple Object Access Protocol) à partir de l' [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]application cliente vers.  
  
2.  
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] recherche la DLL associée à la procédure stockée étendue et la charge si elle ne l'est déjà.  
  
3.  
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] appelle la procédure stockée étendue demandée (implémentée comme fonction à l'intérieur de la DLL).  
  
4.  La procédure stockée étendue transmet les jeux de résultats et retourne les paramètres au serveur via l'API de la procédure stockée étendue.  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation de procédure stockée étendue de moteur de base de données](../database-engine-extended-stored-procedure-programming.md)  
  
  
