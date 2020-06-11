---
title: Exécution d’options de requête (page ANSI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.query.ansi.f1
ms.assetid: c90d7cdf-3309-46f4-b900-220521bb9552
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: b20ab1851d02e493035414dd4682fc5330296b19
ms.sourcegitcommit: 18a7c77be31f9af92ad9d0d3ac5eecebe8eec959
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83858621"
---
# <a name="query-options-execution-ansi-page"></a>Options de requête (page ANSI)
  Utilisez cette page pour spécifier que [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] exécute les requêtes à l’aide de l’ensemble ou d’une partie des paramètres spécifiés dans la norme ISO (ANSI).  
  
## <a name="ui-element-list"></a>Liste des éléments d’interface utilisateur  
 **SET ANSI_DEFAULTS**  
 Sélectionne tous les paramètres ISO par défaut. Par défaut, cette zone n'est pas disponible car seuls certains des paramètres ISO sont configurés.  
  
 **SET QUOTED_IDENTIFIER**  
 Place les identificateurs d'objets entre guillemets. Cette option est activée par défaut.  
  
 **SET ANSI_NULL_DFLT_ON**  
 Autorise les valeurs NULL pour tous les types de données définis par l’utilisateur ou les colonnes non explicitement définies comme NOTNULL lors d’une instruction CREATE TABLE ou ALTER TABLE (état par défaut). Cette option est activée par défaut.  
  
 **SET IMPLICIT_TRANSACTIONS**  
 Cette option est désactivée par défaut.  
  
 **SET CURSOR_CLOSE_ON_COMMIT**  
 Ferme automatiquement tous les curseurs ouverts (conformément à la norme ISO) lors de la validation d'une transaction. Lorsque cette option est désactivée (OFF), les curseurs restent ouverts d'une transaction à l'autre, ne se fermant que lors de la fermeture de la connexion ou sur demande explicite. Cette option est désactivée par défaut.  
  
 **SET ANSI_PADDING**  
 Contrôle la façon dont la colonne stocke les valeurs plus courtes que la taille définie de la colonne, ainsi que la façon dont la colonne stocke les valeurs qui ont des espaces à droite dans les données **char**, **varchar**, **Binary**et **varbinary** . Cette valeur affecte uniquement la définition de nouvelles colonnes. Une fois la colonne créée, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] stocke les valeurs en fonction du paramètre en vigueur lors de la création de la colonne. Les colonnes existantes ne sont pas affectées par toute modification ultérieure du paramètre. Cette case à cocher est activée par défaut.  
  
 **SET ANSI_WARNINGS**  
 Spécifie le comportement conforme à la norme ISO pour plusieurs conditions d'erreur :  
  
-   Lorsque cette case à cocher est activée, si des valeurs de type NULL apparaissent dans des fonctions d'agrégation (telles que SUM, AVG, MAX, MIN, STDEV, STDEVP, VAR, VARP ou COUNT), le système génère un message d'avertissement. Lorsque la valeur est **OFF**, aucun avertissement n'est émis.  
  
-   Lorsque cette case à cocher est désactivée, les erreurs de division par zéro et de dépassement arithmétique provoquent l'annulation de l'instruction et l'émission d'un message d'erreur. Lorsque la valeur est OFF, les erreurs de division par zéro et de dépassement arithmétique entraînent le renvoi de valeurs NULL. Une erreur de division par zéro ou de dépassement arithmétique provoque le renvoi de valeurs NULL si une instruction INSERT ou UPDATE est tentée sur une colonne de type character, Unicode ou binary contenant une nouvelle valeur dont la longueur est supérieure à la taille maximale de la colonne. Si **SET ANSI_WARNINGS** a la valeur on, l’opération d’insertion ou de mise à jour est annulée comme spécifié par la norme ISO. Les espaces de fin sont ignorés dans des colonnes character et les zéros à droite sont ignorés dans les colonnes binary. Lorsque la valeur est définie à OFF, les données sont tronquées de façon à correspondre à la taille de la colonne, et l'instruction s'exécute correctement.  
  
 Cette option est activée par défaut.  
  
 **SET ANSI_NULLS**  
 Spécifie le comportement conforme à la norme ISO, des opérateurs d'égalité (`=`) et de différence (`<>`), lorsqu'ils sont utilisés avec des valeurs NULL. Conformément à la norme ISO, quand **SET ANSI_NULLS** est sélectionné, toutes les comparaisons effectuées sur une valeur NULL retournent la valeur UNKNOWN. Quand **SET ANSI_NULLS** n’est pas sélectionné, les comparaisons de toutes les données par rapport à une valeur NULL sont vraies (TRUE) si la valeur des données est NULL. Cette option est activée par défaut.  
  
 **Rétablir les valeurs par défaut**  
 Rétablit toutes les valeurs par défaut initiales des options de cette page.  
  
  
