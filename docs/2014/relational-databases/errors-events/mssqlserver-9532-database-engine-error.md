---
title: MSSQLSERVER_9532 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 9532 (Database Engine error)
ms.assetid: ab95cce8-4f97-4aea-a746-a73eea7c9aab
caps.latest.revision: 10
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 75b484e68f58b534391c517b69bd7bced4e79046
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36043152"
---
# <a name="mssqlserver9532"></a>MSSQLSERVER_9532
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|9532|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|XMLERR_COLUMNSET_CANNOT_CONVERT_FROM_TO|  
|Texte du message|Dans l’opération de requête/DML impliquant le jeu de colonnes '%.*ls', la conversion a échoué lors de la conversion du type de données '%ls' en type de données '%ls' pour la colonne '%.\*ls'.|  
  
## <a name="explanation"></a>Explication  
 Un jeu de colonnes est une représentation XML non typée qui associe certaines colonnes d'une table dans une sortie structurée. Lorsque vous insérez ou mettez à jour des valeurs de colonnes éparses à l'aide du jeu de colonnes XML, les valeurs insérées dans les colonnes éparses sous-jacentes sont converties implicitement à partir du type de données `xml`. Une valeur a été fournie qui ne peut pas être convertie vers le type de données de la colonne.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Comme la valeur fournie n'a pas pu être convertie implicitement, il peut s'agir d'une entrée non valide. Corrigez l'erreur et réessayez. Si la valeur est correcte, modifiez l'instruction pour utiliser les colonnes individuelles à la place du jeu de colonnes. Cela vous permettra de convertir explicitement le type de la valeur vers le type de données correct.  
  
  