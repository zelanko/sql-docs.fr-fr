---
title: MSSQLSERVER_102 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 102 (Database Engine error)
ms.assetid: 264dc1a2-c8a0-4c89-b5f6-951baf950299
caps.latest.revision: 8
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: d4184a493ecfcb3d22c8e6e6fdd93b8e9fe756a9
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver102"></a>MSSQLSERVER_102
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|102|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|P_SYNTAXERR2|  
|Texte du message|Syntaxe incorrecte près de '%.*ls'.|  
  
## <a name="explanation"></a>Explication  
Indique une erreur de syntaxe. Aucune information supplémentaire n'est disponible, car l'erreur empêche le [!INCLUDE[ssDE](../../includes/ssde-md.md)] de traiter l'instruction.  
  
Cela peut être dû à une tentative de création d'une clé symétrique à l'aide du chiffrement RC4 ou RC4_128 déconseillé, hors du mode compatibilité 90 ou 100.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Recherchez l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] pour les erreurs de syntaxe.  
  
Si vous créez une clé symétrique à l'aide de RC4 ou RC4_128, sélectionnez un chiffrement plus récent, par exemple un des algorithmes AES. (Recommandé.) Si vous devez utiliser RC4, utilisez ALTER DATABASE SET COMPATIBILITY_LEVEL pour définir la base de données au niveau de compatibilité 90 ou 100. (Non recommandé.)  
  

