---
title: Curseurs avec défilement | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 80be6994c7094b365bc24dd135bdda6ec4e561ab
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62468385"
---
# <a name="scrollable-cursors"></a>Curseurs avec défilement
Dans les applications modernes sur un écran, l’utilisateur fait défiler vers le haut et vers l’avant les données. Pour de telles applications, il existe un problème de retour à une ligne extraite précédemment. Une possibilité consiste à fermer et rouvrir le curseur et ensuite extraire les lignes jusqu'à ce que le curseur atteint la ligne requise. Une autre possibilité consiste à lire le jeu de résultats, le met en cache localement et implémenter le défilement dans l’application. Les deux possibilités fonctionnent bien uniquement avec les petits jeux de résultats, et la possibilité de ce dernier est difficile à implémenter. Une meilleure solution consiste à utiliser un *curseur permettant le défilement,* ce qui peut déplacer vers le haut et en avant dans le jeu de résultats.  
  
 Un *curseur permettant le défilement* est couramment utilisé dans les applications modernes sur un écran dans lequel l’utilisateur fait défiler dans les deux sens les données. Toutefois, applications doivent utiliser de curseurs avec défilement uniquement lorsque les curseurs avant uniquement ne fera le travail, comme les curseurs avec défilement sont généralement plus coûteuses que les curseurs avant uniquement.  
  
 La capacité à déplacer vers l’arrière soulève une question non applicable pour les curseurs avant uniquement : Un curseur de défilement doit détecter les modifications apportées aux lignes extraites précédemment ? Autrement dit, il doit pour détecter des lignes nouvellement insérées, supprimées et mises à jour ?  
  
 Cette question se pose, car la définition d’un jeu de résultats - l’ensemble de lignes correspondant à certains critères - ne précise pas lorsque les lignes sont vérifiées pour voir s’ils correspondent aux critères, ni le fait d’état si lignes doivent contenir les mêmes données chaque fois qu’ils sont extraites. L’omission d’ancienne rend possible pour les curseurs avec défilement détecter si les lignes ont été insérés ou supprimés, tandis que ce dernier permet de détecter les données mises à jour.  
  
 La capacité à détecter des modifications est parfois utile, parfois pas. Par exemple, une application de comptabilité a besoin d’un curseur qui ignore toutes les modifications ; Il est impossible si le curseur affiche les dernières modifications de l’équilibrage de la documentation. En revanche, un système de réservation des compagnies aériennes a besoin d’un curseur qui affiche les dernières modifications apportées aux données ; sans ce type de curseur, il doit en permanence actualiser la base de données pour afficher la disponibilité de vol plus récente.  
  
 Pour couvrir les besoins de différentes applications, ODBC définit quatre types de curseurs avec défilement. Ces curseurs varient à la fois dans les notes de frais et définissez leur capacité à détecter les modifications apportées au résultat. Notez que si un curseur de défilement peut détecter les modifications apportées aux lignes, il peut détecter uniquement les lorsqu’il tente de récupérer à nouveau ces lignes ; Il n’existe aucun moyen pour la source de données d’informer le curseur des modifications apportées aux lignes extraites en cours. Notez également que la visibilité des modifications est également contrôlée par le niveau d’isolation de transaction ; Pour plus d’informations, consultez [d’Isolation des transactions](../../../odbc/reference/develop-app/transaction-isolation.md).  
  
 Cette section contient les rubriques suivantes.  
  
-   [Types de curseurs avec défilement](../../../odbc/reference/develop-app/scrollable-cursor-types.md)  
  
-   [Utilisation des curseurs avec défilement](../../../odbc/reference/develop-app/using-scrollable-cursors.md)  
  
-   [Défilement relatif et absolu](../../../odbc/reference/develop-app/relative-and-absolute-scrolling.md)  
  
-   [Signets](../../../odbc/reference/develop-app/bookmarks-odbc.md)
