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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: da899e4dc47daff03c31277b3edd4d9c642b87cb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305290"
---
# <a name="cursors"></a>Curseurs
Une application récupère des données avec un *curseur*. Un curseur est différent d’un ensemble de résultats : un ensemble de résultats est l’ensemble de lignes qui correspond à des critères de recherche particuliers, tandis qu’un curseur est le logiciel qui renvoie ces lignes à l’application. Le *curseur* de nom, tel qu’il s’applique aux bases de données, provient probablement du curseur clignotant d’un terminal informatique. Tout comme ce curseur indique la position actuelle sur l’écran et où les mots dactylographiés apparaîtront ensuite, un curseur sur un ensemble de résultats indique la position actuelle dans l’ensemble de résultats et quelle ligne sera retournée ensuite.  
  
 Le modèle de curseur dans ODBC est basé sur le modèle de curseur dans SQL intégré. Une différence notable entre ces modèles est la façon dont les curseurs sont ouverts. Dans SQL intégré, un curseur doit être explicitement déclaré et ouvert avant qu’il puisse être utilisé. Dans ODBC, un curseur est implicitement ouvert lorsqu’une déclaration qui crée un ensemble de résultats est exécutée. Lorsque le curseur est ouvert, il est positionné avant la première rangée de l’ensemble de résultats. Dans SQL intégré et ODBC, un curseur doit être fermé après que l’application a fini de l’utiliser.  
  
 Différents curseurs ont des caractéristiques différentes. Le type le plus commun de curseur, qui est appelé un *curseur avant-seulement,* ne peut aller de l’avant à travers l’ensemble de résultats. Pour revenir à une rangée précédente, l’application doit fermer et rouvrir le curseur, puis lire les lignes dès le début du résultat fixé jusqu’à ce qu’il atteigne la rangée requise. Les curseurs avant-seulement fournissent un mécanisme rapide pour faire une seule passe à travers un ensemble de résultats.  
  
 Les curseurs avant-seulement sont moins utiles pour les applications basées sur l’écran, dans lesquelles l’utilisateur fait défiler vers l’arrière et vers l’avant à travers les données. Ces applications peuvent utiliser un curseur avant seulement en lisant l’ensemble de résultat une fois, en cachant les données localement et en effectuant elles-mêmes le défilement. Cependant, cela ne fonctionne bien qu’avec de petites quantités de données. Une meilleure solution est d’utiliser un *curseur défilementable,* qui fournit un accès aléatoire à l’ensemble de résultats. Ces applications peuvent également augmenter les performances en obtenant plus d’une rangée de données à la fois, en utilisant ce qu’on appelle un *curseur de bloc.* Pour plus d’informations sur les curseurs de bloc, voir [Using Block Cursors](../../../odbc/reference/develop-app/using-block-cursors.md).  
  
 Le curseur avant seulement est le type de curseur par défaut dans ODBC et est discuté dans les sections suivantes. Pour plus d’informations sur les curseurs de bloc et les curseurs défilementables, voir [Cursesors block](../../../odbc/reference/develop-app/block-cursors.md) et [Cursesors défilants](../../../odbc/reference/develop-app/scrollable-cursors.md).  
  
> [!IMPORTANT]  
>  L’engagement ou le recul d’une transaction, soit en appelant explicitement **SQLEndTran,** soit en fonction du mode auto-commit, fait fermer certaines sources de données à tous les curseurs sur toutes les instructions sur une connexion. Pour plus d’informations, consultez les attributs SQL_CURSOR_COMMIT_BEHAVIOR et SQL_CURSOR_ROLLBACK_BEHAVIOR dans la description de la fonction [SQLGetInfo.](../../../odbc/reference/syntax/sqlgetinfo-function.md)
