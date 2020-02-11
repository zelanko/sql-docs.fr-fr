---
title: Types d’accès concurrentiel | Microsoft Docs
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
- locking concurrency control [ODBC]
- optimistic concurrency [ODBC]
- read-only concurrency control [ODBC]
ms.assetid: 46762ae5-17dd-4777-968e-58156f470fe1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 63d7c7dce51fe4f514232cfd0d5ae2e5abeb5b70
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68083182"
---
# <a name="concurrency-types"></a>Types d’accès concurrentiels
Pour résoudre le problème d’accès concurrentiel réduit dans les curseurs, ODBC expose quatre types différents d’accès concurrentiel de curseur :  
  
-   **Lecture seule** Le curseur peut lire les données, mais ne peut pas mettre à jour ou supprimer des données. Il s’agit du type de concurrence par défaut. Bien que le SGBD puisse verrouiller des lignes pour appliquer les niveaux d’isolation Repeatable Read et Serializable, il peut utiliser des verrous en lecture au lieu de verrous en écriture. Cela entraîne une plus grande concurrence, car les autres transactions peuvent au moins lire les données.  
  
-   **Verrouillage** Le curseur utilise le niveau de verrouillage le plus bas nécessaire pour s’assurer qu’il peut mettre à jour ou supprimer des lignes dans le jeu de résultats. Cela entraîne généralement des niveaux de concurrence très faibles, en particulier dans les niveaux d’isolation des transactions Repeatable Read et Serializable.  
  
-   **Accès concurrentiel optimiste à l’aide des versions de ligne et de l’accès concurrentiel optimiste à l’aide de valeurs** Le curseur utilise l’accès concurrentiel optimiste : il met à jour ou supprime des lignes uniquement s’ils n’ont pas été modifiés depuis leur dernière lecture. Pour détecter les modifications, il compare les versions de ligne ou les valeurs. Il n’y a aucune garantie que le curseur sera en mesure de mettre à jour ou de supprimer une ligne, mais la concurrence est bien plus élevée que lors de l’utilisation du verrouillage. Pour plus d’informations, consultez la section suivante, [accès concurrentiel optimiste](../../../odbc/reference/develop-app/optimistic-concurrency.md).  
  
 Une application spécifie le type de concurrence qu’elle souhaite que le curseur utilise avec l’attribut d’instruction SQL_ATTR_CONCURRENCY. Pour déterminer les types pris en charge, il appelle **SQLGetInfo** avec l’option SQL_SCROLL_CONCURRENCY.
