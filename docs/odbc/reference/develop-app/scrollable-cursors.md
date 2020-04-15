---
title: Cursors défilementables (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- scrollable cursors [ODBC]
- cursors [ODBC], scrollable
ms.assetid: 2c8a5f50-9b37-452f-8160-05f42bc4d97e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2762ffc7fa179fc6a68f92c23f92ca12803f5ab7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304210"
---
# <a name="scrollable-cursors"></a>Curseurs avec défilement
Dans les applications modernes basées sur l’écran, l’utilisateur fait défiler vers l’arrière et vers l’avant à travers les données. Pour de telles applications, le retour à une rangée précédemment récupérée est un problème. Une possibilité est de fermer et de rouvrir le curseur, puis d’aller chercher des rangées jusqu’à ce que le curseur atteigne la rangée requise. Une autre possibilité est de lire l’ensemble de résultats, le mettre en cache localement, et implémenter le défilement dans l’application. Les deux possibilités ne fonctionnent bien qu’avec de petits ensembles de résultats, et cette dernière possibilité est difficile à mettre en œuvre. Une meilleure solution est d’utiliser un *curseur défilementable,* qui peut se déplacer vers l’arrière et vers l’avant dans l’ensemble de résultats.  
  
 Un *curseur défilementable* est couramment utilisé dans les applications modernes basées sur l’écran dans lesquelles l’utilisateur fait défiler les données. Toutefois, les applications ne doivent utiliser des curseurs défilementibles que lorsque les curseurs avant-seulement ne feront pas le travail, car les curseurs défilementables sont généralement plus chers que les curseurs avant-seulement.  
  
 La capacité de reculer soulève une question qui ne s’applique pas aux curseurs avant-seulement : un curseur défilementable devrait-il détecter les modifications apportées aux lignes précédemment récupérées? Autrement dit, devrait-il détecter les lignes mises à jour, supprimées et nouvellement insérées?  
  
 Cette question se pose parce que la définition d’un ensemble de résultats - l’ensemble de lignes qui correspond à certains critères - ne précise pas quand les lignes sont vérifiées pour voir si elles correspondent à ces critères, ni indique si les lignes doivent contenir les mêmes données chaque fois qu’elles sont récupérées. La première omission permet aux curseurs défilementables de détecter si les lignes ont été insérées ou supprimées, tandis que celle-ci leur permet de détecter les données mises à jour.  
  
 La capacité de détecter les changements est parfois utile, parfois pas. Par exemple, une demande comptable a besoin d’un curseur qui ne tient pas compte de tous les changements; l’équilibrage des livres est impossible si le curseur affiche les derniers changements. D’autre part, un système de réservation de compagnie aérienne a besoin d’un curseur qui montre les dernières modifications apportées aux données; sans un tel curseur, il doit continuellement requery la base de données pour afficher la disponibilité de vol la plus à jour.  
  
 Pour couvrir les besoins de différentes applications, ODBC définit quatre types différents de curseurs défilementables. Ces curseurs varient à la fois dans les dépenses et dans leur capacité à détecter les changements à l’ensemble de résultats. Notez que si un curseur défilementable peut détecter les changements aux lignes, il ne peut les détecter que lorsqu’il tente de réfélévoir ces lignes; il n’y a aucun moyen pour la source de données d’aviser le curseur des modifications apportées aux lignes actuellement récupérées. Notez également que la visibilité des changements est également contrôlée par le niveau d’isolement des transactions; pour plus d’informations, voir [Transaction Isolation](../../../odbc/reference/develop-app/transaction-isolation.md).  
  
 Cette section contient les rubriques suivantes :  
  
-   [Types de curseurs avec défilement](../../../odbc/reference/develop-app/scrollable-cursor-types.md)  
  
-   [Utilisation des curseurs avec défilement](../../../odbc/reference/develop-app/using-scrollable-cursors.md)  
  
-   [Défilement relatif et absolu](../../../odbc/reference/develop-app/relative-and-absolute-scrolling.md)  
  
-   [Signets](../../../odbc/reference/develop-app/bookmarks-odbc.md)
