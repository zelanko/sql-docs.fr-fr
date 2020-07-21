---
title: MSSQLSERVER_41399 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41399 (Database Engine error)
ms.assetid: 5e5acb07-16ca-4329-8210-cd2bab0c904f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6e2624eaa767a6607aa5a5fc81c65ddad29e77b0
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86551334"
---
# <a name="mssqlserver_41399"></a>MSSQLSERVER_41399
    
## <a name="details"></a>Détails  
  
|Attribut|Valeur|  
|-|-|  
|Nom du produit|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID de l’événement|41399|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|MAX_SORT_ROW_WIDTH_EXCEEDED|  
|Texte du message|L'opération de tri est trop complexe. Consultez la documentation en ligne de SQL Server pour plus d'informations.|  
  
## <a name="explanation"></a>Explication  
 Le tri des résultats des opérations de jointure et d'agrégation augmente la complexité de l'opération de tri en accroissant la taille de la ligne dans le tampon de tri. Cette erreur indique que la taille de la ligne dépasse la taille maximale prise en charge par l'opérateur de tri dans des procédures stockées compilées en mode natif. Notez que la taille d'une ligne dans le tampon de tri est déterminée uniquement par le nombre de jointures et le nombre et le type de fonctions d'agrégation. La taille des lignes dans les tables de base n'affecte pas la taille de la ligne dans le tampon.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Réduisez la complexité de la requête en supprimant des jointures ou des fonctions d'agrégation.  
  
## <a name="see-also"></a>Voir aussi  
 [OLTP en mémoire &#40;Optimisation en mémoire&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
