---
description: Curseurs avec défilement
title: Curseurs de défilement | Microsoft Docs
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
ms.openlocfilehash: 9c347dcb130a2f1f899f2e1b83ae28289ff0a923
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476481"
---
# <a name="scrollable-cursors"></a>Curseurs avec défilement
Dans les applications modernes basées sur l’écran, l’utilisateur fait défiler les données vers l’avant et vers l’arrière. Pour de telles applications, le retour à une ligne extraite précédemment pose problème. L’une des possibilités consiste à fermer et à rouvrir le curseur, puis à extraire les lignes jusqu’à ce que le curseur atteigne la ligne requise. Une autre possibilité consiste à lire le jeu de résultats, à le mettre en cache localement et à implémenter le défilement dans l’application. Les deux possibilités fonctionnent bien uniquement avec les petits jeux de résultats, et cette dernière possibilité est difficile à implémenter. Une meilleure solution consiste à utiliser un *curseur de défilement,* qui peut se déplacer vers l’avant et vers l’arrière dans le jeu de résultats.  
  
 Un *curseur à défilement* est couramment utilisé dans les applications modernes basées sur les écrans, dans lesquelles l’utilisateur fait défiler les données vers l’avant et l’arrière. Toutefois, les applications doivent utiliser des curseurs de défilement uniquement lorsque les curseurs avant uniquement n’effectuent pas le travail, car les curseurs de défilement sont généralement plus chers que les curseurs avant uniquement.  
  
 La possibilité de revenir en arrière déclenche une question non applicable aux curseurs avant uniquement : un curseur de défilement doit-il détecter les modifications apportées aux lignes précédemment extraites ? C’est-à-dire qu’il doit détecter les lignes mises à jour, supprimées et récemment insérées ?  
  
 Cette question est due au fait que la définition d’un jeu de résultats-l’ensemble de lignes qui correspond à certains critères-n’indique pas quand les lignes sont vérifiées pour déterminer si elles correspondent à ces critères, et qu’elle indique si les lignes doivent contenir les mêmes données chaque fois qu’elles sont extraites. La première omission permet aux curseurs de défilement de détecter si des lignes ont été insérées ou supprimées, tandis que ces derniers permettent de détecter les données mises à jour.  
  
 La possibilité de détecter des modifications est parfois utile, parfois pas. Par exemple, une application de gestion des comptes a besoin d’un curseur qui ignore toutes les modifications ; l’équilibrage des livres est impossible si le curseur affiche les dernières modifications. D’un autre côté, un système de réservation de compagnies aériennes a besoin d’un curseur qui indique les dernières modifications apportées aux données ; sans ce type de curseur, il doit continuellement interroger la base de données pour afficher la disponibilité de vol la plus récente.  
  
 Pour couvrir les besoins des différentes applications, ODBC définit quatre types différents de curseurs à défilement. Ces curseurs varient à la fois en termes de dépenses et en fonction de leur capacité à détecter les modifications apportées au jeu de résultats. Notez que si un curseur de défilement peut détecter des modifications apportées aux lignes, il peut les détecter uniquement lorsqu’il tente de récupérer ces lignes. Il n’existe aucun moyen pour la source de données d’informer le curseur des modifications apportées aux lignes actuellement récupérées. Notez également que la visibilité des modifications est également contrôlée par le niveau d’isolation de la transaction. Pour plus d’informations, consultez [isolation des transactions](../../../odbc/reference/develop-app/transaction-isolation.md).  
  
 Cette section contient les rubriques suivantes :  
  
-   [Types de curseurs avec défilement](../../../odbc/reference/develop-app/scrollable-cursor-types.md)  
  
-   [Utilisation des curseurs avec défilement](../../../odbc/reference/develop-app/using-scrollable-cursors.md)  
  
-   [Défilement relatif et absolu](../../../odbc/reference/develop-app/relative-and-absolute-scrolling.md)  
  
-   [Signets](../../../odbc/reference/develop-app/bookmarks-odbc.md)
