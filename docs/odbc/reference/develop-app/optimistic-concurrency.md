---
title: Accès concurrentiel optimiste | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- transactions [ODBC], concurrency control
- concurrency control [ODBC]
- optimistic concurrency [ODBC]
ms.assetid: 9d71e09e-bc68-4c1f-9229-ed2a7be7d324
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 30eba3ea03b4c798a74a8cb928014b582846607b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81282482"
---
# <a name="optimistic-concurrency"></a>Accès concurrentiel optimiste
L' *accès concurrentiel optimiste* dérive son nom de l’hypothèse optimiste selon laquelle les collisions entre les transactions sont rarement effectuées. une collision est réputée se produire lorsqu’une autre transaction met à jour ou supprime une ligne de données entre le moment où elle est lue par la transaction en cours et l’heure à laquelle elle est mise à jour ou supprimée. C’est l’opposé de l' *accès concurrentiel pessimiste,* ou le verrouillage, dans lequel le développeur d’applications estime que ces collisions sont courantes.  
  
 Dans l’accès concurrentiel optimiste, une ligne reste déverrouillée jusqu’à ce que l’heure soit mise à jour ou supprimée. À ce stade, la ligne est lue et vérifiée pour voir si elle a été modifiée depuis sa dernière lecture. Si la ligne a été modifiée, la mise à jour ou la suppression échoue et doit être réessayée.  
  
 Pour déterminer si une ligne a été modifiée, sa nouvelle version est vérifiée par rapport à une version mise en cache de la ligne. Cette vérification peut être basée sur la version de ligne, telle que la colonne timestamp dans SQL Server, ou sur les valeurs de chaque colonne dans la ligne. De nombreux SGBD ne prennent pas en charge les versions de ligne.  
  
 L’accès concurrentiel optimiste peut être implémenté par la source de données ou l’application. Dans les deux cas, l’application doit utiliser un niveau d’isolation de transaction faible, tel que Read Committed ; l’utilisation d’un niveau supérieur nie l’augmentation de la concurrence en utilisant l’accès concurrentiel optimiste.  
  
 Si l’accès concurrentiel optimiste est implémenté par la source de données, l’application définit l’attribut d’instruction SQL_ATTR_CONCURRENCY sur SQL_CONCUR_ROWVER ou SQL_CONCUR_VALUES. Pour mettre à jour ou supprimer une ligne, elle exécute une instruction UPDATE ou DELETE positionnée ou appelle **SQLSetPos** comme c’est le cas avec l’accès concurrentiel pessimiste ; le pilote ou la source de données retourne SQLSTATE 01001 (conflit d’opération de curseur) si la mise à jour ou la suppression échoue en raison d’une collision.  
  
 Si l’application elle-même implémente l’accès concurrentiel optimiste, elle définit l’attribut d’instruction SQL_ATTR_CONCURRENCY sur SQL_CONCUR_READ_ONLY pour lire une ligne. Si elle compare les versions de ligne et ne connaît pas la colonne de version de ligne, elle appelle **SQLSpecialColumns** avec l’option SQL_ROWVER pour déterminer le nom de cette colonne.  
  
 L’application met à jour ou supprime la ligne en faisant passer la concurrence à SQL_CONCUR_LOCK (pour obtenir un accès en écriture à la ligne) et en exécutant une instruction **Update** ou **Delete** avec une clause **Where** qui spécifie la version ou les valeurs de la ligne lorsque l’application la lit. Si la ligne a été modifiée depuis, l’instruction échoue. Si la clause **Where** n’identifie pas de façon unique la ligne, l’instruction peut également mettre à jour ou supprimer d’autres lignes ; les versions de ligne identifient toujours de manière unique les lignes, mais les valeurs de ligne identifient les lignes de manière unique uniquement si elles incluent la clé primaire.
