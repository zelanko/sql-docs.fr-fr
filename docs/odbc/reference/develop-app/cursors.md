---
title: Curseurs | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 91765f0572d8c880f7505948f7756b373fe28f62
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63042125"
---
# <a name="cursors"></a>Curseurs
Une application extrait les données avec un *curseur*. Un curseur est différent à partir d’un jeu de résultats : Un jeu de résultats est l’ensemble de lignes qui correspond aux critères de recherche spécifique, tandis qu’un curseur est le logiciel qui retourne les lignes à l’application. Le nom *curseur,* tel qu’il s’applique aux bases de données, provient probablement à partir du curseur clignotant, appelé sur un ordinateur Terminal Server. Comme ce curseur indique la position actuelle sur l’écran et où les mots typés apparaissent suivants, un curseur sur un jeu de résultats indique la position actuelle dans le jeu de résultats et quelle ligne sera ensuite retournée.  
  
 Le modèle de curseur dans ODBC est basé sur le modèle de curseur dans embedded SQL. Une différence notable entre ces modèles est que les curseurs de façon sont ouverts. Dans embedded SQL, un curseur doit être explicitement déclaré et ouverts avant de pouvoir être utilisé. Dans ODBC, un curseur est implicitement ouvert lorsqu’une instruction qui crée un jeu de résultats est exécutée. Lorsque le curseur est ouvert, il est positionné avant la première ligne du jeu de résultats. Dans embedded SQL et ODBC, un curseur doit être fermé une fois que l’application a fini de l’utiliser.  
  
 Curseurs différents ont des caractéristiques différentes. Le type le plus courant de curseur, ce qui est appelé un *curseur avant uniquement,* peut uniquement avancer dans le jeu de résultats. Pour revenir à une ligne précédente, l’application doit fermer et rouvrir le curseur et puis lecture de lignes à partir du début du jeu jusqu'à ce qu’il atteigne la ligne obligatoire de résultats. Curseurs avant uniquement et fournissent un mécanisme rapide pour une seule passe via un jeu de résultats.  
  
 Les curseurs avant uniquement sont moins utile pour les applications basées sur un écran dans lequel l’utilisateur fait défiler vers le haut et vers l’avant via les données. Ces applications peuvent utiliser un curseur avant uniquement en lisant le résultat défini une fois, la mise en cache les données localement et en exécutant le défilement eux-mêmes. Toutefois, cela fonctionne bien uniquement avec petites quantités de données. Une meilleure solution consiste à utiliser un *curseur permettant le défilement,* qui fournit un accès aléatoire au jeu de résultats. De telles applications peuvent également augmenter les performances en extraire plusieurs lignes de données à la fois, à l’aide de ce que l'on appelle un *curseur de bloc.* Pour plus d’informations sur les curseurs de bloc, consultez [à l’aide des curseurs de bloc](../../../odbc/reference/develop-app/using-block-cursors.md).  
  
 Le curseur avant uniquement est le type de curseur par défaut dans ODBC et est décrit dans les sections suivantes. Pour plus d’informations sur les curseurs de bloc et de curseurs avec défilement, consultez [curseurs de bloc](../../../odbc/reference/develop-app/block-cursors.md) et [curseurs avec défilement](../../../odbc/reference/develop-app/scrollable-cursors.md).  
  
> [!IMPORTANT]  
>  Validation ou la restauration d’une transaction, soit en appelant explicitement **SQLEndTran** ou par fonctionne en mode de validation automatique, entraîne certaines sources de données fermer tous les curseurs sur toutes les instructions sur une connexion. Pour plus d’informations, voir les attributs SQL_CURSOR_COMMIT_BEHAVIOR et SQL_CURSOR_ROLLBACK_BEHAVIOR le [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) description de fonction.
