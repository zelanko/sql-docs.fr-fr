---
title: MSSQLSERVER_41399 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 41399 (Database Engine error)
ms.assetid: 5e5acb07-16ca-4329-8210-cd2bab0c904f
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8f1dd8f616de43a0442e4110ba755cc66e397c43
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47832987"
---
# <a name="mssqlserver41399"></a>MSSQLSERVER_41399
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID d'événement|41399|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|MAX_SORT_ROW_WIDTH_EXCEEDED|  
|Texte du message|L'opération de tri est trop complexe. Consultez la documentation en ligne de SQL Server pour plus d'informations.|  
  
## <a name="explanation"></a>Explication  
Le tri des résultats des opérations de jointure et d'agrégation augmente la complexité de l'opération de tri en accroissant la taille de la ligne dans le tampon de tri. Cette erreur indique que la taille de la ligne dépasse la taille maximale prise en charge par l'opérateur de tri dans des procédures stockées compilées en mode natif. Notez que la taille d'une ligne dans le tampon de tri est déterminée uniquement par le nombre de jointures et le nombre et le type de fonctions d'agrégation. La taille des lignes dans les tables de base n'affecte pas la taille de la ligne dans le tampon.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Réduisez la complexité de la requête en supprimant des jointures ou des fonctions d'agrégation.  
  
## <a name="see-also"></a> Voir aussi  
[OLTP en mémoire &#40;Optimisation en mémoire&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
