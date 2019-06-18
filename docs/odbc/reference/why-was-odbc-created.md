---
title: Pourquoi ODBC a-t-il été créé ? | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC [ODBC], about ODBC
ms.assetid: ba6eb993-316b-4650-bab8-d76583c00e53
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 871919554975f04fae0aeaa1b8e6ec684c6650a4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62714146"
---
# <a name="why-was-odbc-created"></a>Pourquoi ODBC a-t-il été créé ?
Historiquement, les entreprises utilisent un SGBD unique. Tous les accès de base de données a été effectuée via le serveur frontal de ce système ou les applications écrites pour fonctionner exclusivement avec ce système. Toutefois, quand l’utilisation d’ordinateurs a augmenté et plus de matériel informatique et de logiciels sont devenues disponibles, entreprises ont commencé acquérir des différents SGBD. Les raisons étaient nombreuses : Personnes a acheté ce qui était moins coûteux, ce qui a été le plus rapide, ce qu’ils déjà savais, ce qui était la plus récente sur le marché, ce qui a fonctionné mieux pour une application unique. Pour d’autres raisons ont été réorganisations et les fusions, où les départements qui avait précédemment un SGBD unique devaient désormais plusieurs.  
  
 Le problème a augmenté encore plus complexe avec l’avènement des ordinateurs personnels. Ces ordinateurs dans un large éventail d’outils pour interroger, analyser et affichage des données, ainsi que plusieurs bases de données peu coûteuses, facile à utiliser. Dès lors, une seule corporation était souvent des données répartis sur une multitude de postes de travail, serveurs et miniordinateurs, stockées dans diverses bases de données incompatibles et accessibles par un grand nombre de différents outils, peu d'entre eux peuvent accéder à toutes les données.  
  
 Le défi final fournie avec l’arrivée du client/serveur informatique, qui cherche à rendre l’utilisation plus efficace des ressources de l’ordinateur. Les ordinateurs personnels peu onéreux (les clients) se trouvent sur le bureau et fournir à la fois un graphique front-end pour les données et un nombre d’outils à moindre coût, tels que des feuilles de calcul, graphiques à des programmes et des générateurs de rapports. Miniordinateurs et des ordinateurs centraux (serveurs) hébergent les SGBD, où ils peuvent utiliser leur puissance de calcul et un emplacement central pour fournir l’accès aux données rapide et coordonnée. Comment était le logiciel frontal d’être connecté à la base de données principale ?  
  
 Un problème similaire confrontés à des éditeurs de logiciels indépendants (ISV). Fournisseurs d’écriture de logiciels de base de données pour le miniordinateurs et des ordinateurs centraux ont été généralement obligés d’écrire une version d’une application pour chaque SGBD ou écrire du code de SGBD spécifiques pour chaque SGBD il souhaite accéder. Écriture de logiciels pour ordinateurs personnels des fournisseurs devaient écrire des routines d’accès aux données pour chaque SGBD différent avec lequel il souhaite utiliser. Cela signifiait souvent une énorme quantité de ressources ont été passées en écriture et la maintenance d’accès aux données routines plutôt que les applications et les applications ont été vendues souvent pas sur leur qualité, mais si ils Impossible d’accès aux données dans un SGBD donné.  
  
 Ce que les deux groupes de développeurs fallait un moyen d’accéder aux données dans différents SGBD. Le groupe de macroordinateur et ses besoin d’une méthode pour fusionner les données de SGBD différents dans une application unique, tandis que le groupe d’ordinateurs personnels nécessaire cette capacité, ainsi que d’écrire une seule application qui a été indépendante de tout un SGBD. En bref, les deux groupes nécessaires à un moyen interopérable pour accéder aux données ; ils nécessitent ouvrir la connectivité de base de données.
