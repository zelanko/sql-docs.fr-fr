---
title: MSSQL_ENG020574 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG02574 error
ms.assetid: 4e98f8de-287c-4090-81ee-dc8f80dfa6a1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fda701ce7c4ffa092725772e41265eadc522352e
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85010125"
---
# <a name="mssql_eng020574"></a>MSSQL_ENG020574
    
## <a name="message-details"></a>Détails du message  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|20574|  
|Source de l’événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique||  
|Texte du message|L'Abonné '%s' avec un abonnement à l'article '%s' de la publication '%s' n'a pas réussi la validation de données.|  
  
## <a name="explanation"></a>Explication  
 Lors de la validation des données de l'Abonné par rapport aux données du serveur de publication, les données ne correspondaient pas, par conséquent la validation a échoué. Pour plus d'informations sur la validation, consultez [Validate Replicated Data](validate-data-at-the-subscriber.md).  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Nous vous recommandons de procéder comme suit :  
  
-   Déterminez la raison de l'échec de la validation.  
  
-   Corrigez le problème sous-jacent qui est à l'origine de cet échec.  
  
-   Établissez la convergence des données en réinitialisant l'abonnement ou en utilisant une autre méthode.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des événements &#40;réplication&#41;](errors-and-events-reference-replication.md)  
  
  
