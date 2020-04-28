---
title: Modifier un emplacement de point d'arrêt
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL debugger, breakpoint location
ms.assetid: 5c28e411-0377-4210-a7ce-2a5c13dcdf74
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f2b5bb55452333014aa3ccf5a797d19667dca753
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "75244886"
---
# <a name="edit-a-breakpoint-location"></a>Modifier un emplacement de point d'arrêt
  L'emplacement du point d'arrêt spécifie la ligne et le caractère où réside ce point d'arrêt dans un fichier de script [!INCLUDE[tsql](../../includes/tsql-md.md)] . Vous pouvez modifier cet emplacement pour déplacer le point d'arrêt vers un autre emplacement du script ou vers un script différent.  
  
## <a name="editing-a-location"></a>Modification d'un emplacement  
 Lorsque vous modifiez l'emplacement d'un point d'arrêt, ce point d'arrêt se déplace jusqu'à son nouvel emplacement et conserve toutes ses propriétés existantes, telles que le nombre d'accès ou la condition.  
  
#### <a name="to-edit-a-breakpoint-location"></a>Pour modifier l'emplacement d'un point d'arrêt  
  
1.  Dans la fenêtre de l’éditeur, cliquez avec le bouton droit sur le glyphe du point d’arrêt, puis cliquez sur **Emplacement** dans le menu contextuel.  
  
     -ou-  
  
     Dans la fenêtre **Points d’arrêt** , cliquez avec le bouton droit sur le glyphe du point d’arrêt, puis cliquez sur **Emplacement** dans le menu contextuel.  
  
2.  Dans la boîte de dialogue **Point d’arrêt sur fichier** , modifiez **Fichier** pour spécifier un nouveau fichier, **Ligne** pour spécifier une nouvelle ligne ou **Caractère** pour spécifier un nouvel emplacement dans la ligne. Si le nouveau fichier que vous spécifiez est déjà ouvert dans une fenêtre de l'éditeur de requête, le point d'arrêt est déplacé vers cette fenêtre de l'éditeur. Si le fichier n'est pas ouvert, une nouvelle fenêtre d'éditeur s'ouvre, le fichier y est chargé et le point d'arrêt est déplacé vers le nouvel emplacement.  
  
     L’option **Permettre que le code source soit différent de la version d’origine** n’a aucun effet lors du débogage de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Spécifier un nombre d’accès](specify-a-hit-count.md)   
 [Spécifier une action de point d’arrêt](specify-a-breakpoint-action.md)   
 [Spécifier une condition de point d’arrêt](specify-a-breakpoint-condition.md)   
 [Pour spécifier un filtre de point d’arrêt](specify-a-breakpoint-filter.md)  
