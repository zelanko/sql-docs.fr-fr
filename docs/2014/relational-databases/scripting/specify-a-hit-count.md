---
title: Spécifier un nombre d'accès
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- vs.debug.breakpt.hitcount
helpviewer_keywords:
- Transact-SQL debugger, breakpoint hit count
ms.assetid: 24836939-94ed-4e57-aa85-5d6938d859e4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a049491513b826b2b050081b40cb5319ca74160f
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75243211"
---
# <a name="specify-a-hit-count"></a>Spécifier un nombre d'accès
  Un nombre d'accès à un point d'arrêt est un compteur incrémenté par le débogueur [!INCLUDE[tsql](../../includes/tsql-md.md)] chaque fois que le point d'arrêt est atteint. Si le nombre d'accès spécifié est atteint et si les conditions de point d'arrêt spécifiées sont satisfaites, le débogueur effectue l'action spécifiée pour le point d'arrêt.  
  
## <a name="hit-count-considerations"></a>Considérations sur le nombre d'accès  
 Par défaut, l'exécution s'arrête pour chaque accès à un point d'arrêt. Vous pouvez choisir entre les options suivantes :  
  
-   Toujours s'arrêter (valeur par défaut).  
  
-   Arrêter lorsque le nombre d'accès est égal à une valeur spécifiée.  
  
-   Arrêter lorsque le nombre d'accès est égal au multiple d'une valeur spécifiée.  
  
-   Arrêter lorsque le nombre d'accès est supérieur ou égal à une valeur spécifiée.  
  
 Les nombres d'accès à un point d'arrêt sont incrémentés dans le cadre de l'étendue d'une session de débogage. Tous les nombres d'accès sont remis à zéro au démarrage de chaque session de débogage.  
  
 Si vous souhaitez connaître le nombre d'accès à un point d'arrêt sans que l'exécution s'arrête, spécifiez un nombre d'accès avec une valeur très élevée afin que le point d'arrêt n'entraîne jamais l'arrêt.  
  
 L'action par défaut pour un point d'arrêt consiste à arrêter l'exécution lorsque le nombre d'accès et la condition de point d'arrêt sont tous les deux satisfaits. Pour plus d’informations sur la spécification d’autres actions, consultez [Spécifier une action de point d’arrêt](specify-a-breakpoint-action.md).  
  
#### <a name="to-specify-a-hit-count"></a>Pour spécifier un nombre d'accès  
  
1.  Dans la fenêtre de l’éditeur, cliquez avec le bouton droit sur le glyphe du point d’arrêt, puis cliquez sur **Nombre d’accès** dans le menu contextuel.  
  
     - ou -  
  
     Dans la fenêtre **Points d’arrêt** , cliquez avec le bouton droit sur le glyphe du point d’arrêt, puis cliquez sur **Nombre d’accès** dans le menu contextuel.  
  
2.  Dans la boîte de dialogue **Nombre d’accès à un point d’arrêt** , sélectionnez le comportement que vous souhaitez dans la zone **Lorsque le point d’arrêt est atteint** .  
  
     Si vous choisissez un paramètre autre que **Toujours s’arrêter**, une zone de texte apparaît à droite de la liste. Entrez un entier dans cette zone de texte pour spécifier le nombre d'accès souhaité.  
  
3.  Cliquez sur **OK** pour implémenter les modifications ou sur **Annuler** pour fermer sans appliquer les modifications.  
  
#### <a name="to-view-or-reset-the-current-hit-count"></a>Afficher ou réinitialiser le nombre d'accès actuel  
  
1.  Dans la fenêtre de l’éditeur, cliquez avec le bouton droit sur le glyphe du point d’arrêt, puis cliquez sur **Nombre d’accès** dans le menu contextuel.  
  
     - ou -  
  
     Dans la fenêtre **Points d’arrêt** , cliquez avec le bouton droit sur le glyphe du point d’arrêt, puis cliquez sur **Nombre d’accès** dans le menu contextuel.  
  
2.  Dans la boîte de dialogue **Nombre d’accès à un point d’arrêt** , le **Nombre d’accès actuel** est affiché juste au-dessus du bouton **Réinitialiser** .  
  
3.  Cliquez sur **Réinitialiser** si vous souhaitez réinitialiser le nombre d’accès actuel à zéro.  
  
4.  Cliquez sur **OK** ou sur **Annuler** pour fermer la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Spécifier une condition de point d'arrêt](specify-a-breakpoint-condition.md)  
  
  
