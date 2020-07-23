---
title: Curseurs (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- forward-only cursors [ODBC]
- scrollable cursors [ODBC]
- cursors [ODBC], about cursors
- cursors [ODBC]
- fetches [ODBC], cursors
- result sets [ODBC], fetching
- block cursors [ODBC]
ms.assetid: 0b114352-3c63-4d33-9220-182ede90e4aa
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3a7484de48edaecea56fc135ca3b803875f9557c
ms.sourcegitcommit: 08f331b6a5fe72d68ef1b2eccc5d16cb80c6ee39
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "86977776"
---
# <a name="cursors"></a>Curseurs
Une application extrait les données à l’aide d’un *curseur*. Un curseur est différent d’un jeu de résultats : un jeu de résultats est l’ensemble de lignes correspondant à des critères de recherche particuliers, tandis qu’un curseur est le logiciel qui renvoie ces lignes à l’application. Le curseur de nom *,* tel qu’il s’applique aux bases de données, provient probablement du curseur clignotant sur un terminal informatique. Tout comme le curseur indique la position actuelle à l’écran et l’endroit où les mots tapés s’affichent ensuite, un curseur sur un jeu de résultats indique la position actuelle dans le jeu de résultats et la ligne qui sera retournée ensuite.  
  
 Le modèle de curseur dans ODBC est basé sur le modèle de curseur dans Embedded SQL. La différence notable entre ces modèles est la façon dont les curseurs sont ouverts. Dans EmbeddedSQL, un curseur doit être explicitement déclaré et ouvert avant de pouvoir être utilisé. Dans ODBC, un curseur est implicitement ouvert lorsqu’une instruction qui crée un jeu de résultats est exécutée. Lorsque le curseur est ouvert, il est positionné avant la première ligne du jeu de résultats. Dans Embedded SQL et ODBC, un curseur doit être fermé une fois que l’application a fini de l’utiliser.  
  
 Différents curseurs ont des caractéristiques différentes. Le type de curseur le plus courant, appelé *curseur avant uniquement,* ne peut pas avancer dans le jeu de résultats. Pour revenir à une ligne précédente, l’application doit fermer et rouvrir le curseur, puis lire les lignes à partir du début du jeu de résultats jusqu’à ce qu’elle atteigne la ligne requise. Les curseurs avant uniquement fournissent un mécanisme rapide pour effectuer une seule passe dans un jeu de résultats.  
  
 Les curseurs avant uniquement sont moins utiles pour les applications basées sur l’écran, dans lesquels l’utilisateur fait défiler les données vers l’avant et vers l’arrière. De telles applications peuvent utiliser un curseur avant uniquement en lisant le jeu de résultats une seule fois, en mettant en cache les données localement et en effectuant eux-mêmes le défilement. Toutefois, cela fonctionne bien uniquement avec de petites quantités de données. Une meilleure solution consiste à utiliser un *curseur de défilement,* qui fournit un accès aléatoire au jeu de résultats. De telles applications peuvent également améliorer les performances en extrayant plusieurs lignes de données à la fois, à l’aide de ce que l’on appelle un *curseur de bloc.* Pour plus d’informations sur les curseurs de bloc, consultez [utilisation de curseurs de bloc](../../../odbc/reference/develop-app/using-block-cursors.md).  
  
 Le curseur avant uniquement est le type de curseur par défaut dans ODBC et est abordé dans les sections suivantes. Pour plus d’informations sur les curseurs de bloc et les curseurs de défilement, consultez [bloquer](../../../odbc/reference/develop-app/block-cursors.md) les curseurs et les curseurs avec [défilement](../../../odbc/reference/develop-app/scrollable-cursors.md).  
  
> [!IMPORTANT]  
>  La validation ou la restauration d’une transaction, soit en appelant explicitement **SQLEndTran** ou en mode de validation automatique, provoque la fermeture par certaines sources de données de tous les curseurs sur toutes les instructions d’une connexion. Pour plus d’informations, consultez les attributs SQL_CURSOR_COMMIT_BEHAVIOR et SQL_CURSOR_ROLLBACK_BEHAVIOR dans la description de la fonction [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) .
