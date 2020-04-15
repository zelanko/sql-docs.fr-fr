---
title: Types de concordance (en anglais seulement) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 642301d09c5aa189276db534e58aca0c5e00e3ce
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299099"
---
# <a name="concurrency-types"></a>Types d’accès concurrentiels
Pour résoudre le problème de la concurrence réduite dans les curseurs, ODBC expose quatre types différents de concurrence curseurr:  
  
-   **Lire-seulement** Le curseur peut lire les données mais ne peut pas mettre à jour ou supprimer des données. Il s’agit du type de concordance par défaut. Bien que le DBMS puisse verrouiller des lignes pour appliquer les niveaux d’isolement répétables Read et Serializable, il peut utiliser des serrures de lecture au lieu d’écrire des serrures. Il en résulte une plus grande concurrence parce que d’autres transactions peuvent au moins lire les données.  
  
-   **Verrouillage** Le curseur utilise le niveau le plus bas de verrouillage nécessaire pour s’assurer qu’il peut mettre à jour ou supprimer les lignes dans l’ensemble de résultat. Cela se traduit généralement par des niveaux de concurrence très faibles, en particulier aux niveaux d’isolement des transactions Répétables Read et Serializable.  
  
-   **Concurrence optimiste à l’aide de versions en ligne et de concordance optimiste à l’aide de valeurs** Le curseur utilise une concordance optimiste : il ne met à jour ou supprime les lignes que si elles n’ont pas changé depuis leur dernière lecture. Pour détecter les changements, il compare les versions ou les valeurs de la ligne. Il n’y a aucune garantie que le curseur sera en mesure de mettre à jour ou de supprimer une ligne, mais la concurrence est beaucoup plus élevée que lorsque le verrouillage est utilisé. Pour plus d’informations, voir la section suivante, [Concordurrency Optimiste](../../../odbc/reference/develop-app/optimistic-concurrency.md).  
  
 Une application précise quel type de concurrence elle veut que le curseur utilise avec l’attribut de l’SQL_ATTR_CONCURRENCY déclaration. Pour déterminer quels types sont pris en charge, il appelle **SQLGetInfo** avec l’option SQL_SCROLL_CONCURRENCY.
