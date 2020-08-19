---
description: Liaison de colonnes pour une utilisation avec des curseurs de bloc
title: Colonnes de liaison à utiliser avec des curseurs de bloc | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- column-wise binding [ODBC]
- row-wise binding [ODBC]
- result sets [ODBC], binding columns
- cursors [ODBC], block
- binding columns [ODBC]
- block cursors [ODBC]
- result sets [ODBC], block cursors
ms.assetid: 231beede-cdfa-4e28-8b10-2760b983250f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a58e6359bd7b0ad5d44f75a3d844ef2e9872f2a8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429441"
---
# <a name="binding-columns-for-use-with-block-cursors"></a>Liaison de colonnes pour une utilisation avec des curseurs de bloc
Étant donné que les curseurs de bloc retournent plusieurs lignes, les applications qui les utilisent doivent lier un tableau de variables à chaque colonne au lieu d’une variable unique. Ces tableaux sont collectivement connus sous le nom de *mémoires tampons d’ensemble de lignes*. Voici les deux styles de liaison :  
  
-   Liez un tableau à chaque colonne. C’est ce que l’on appelle une liaison selon les *colonnes* , car chaque structure de données (tableau) contient des données pour une colonne unique.  
  
-   Définissez une structure qui contiendra les données pour une ligne entière et liez un tableau de ces structures. C’est ce que l’on appelle une liaison selon les *lignes* , car chaque structure de données contient les données d’une seule ligne.  
  
 Comme lorsque l’application lie des variables uniques à des colonnes, elle appelle **SQLBindCol** pour lier des tableaux aux colonnes. La seule différence est que les adresses transmises sont des adresses de tableau, et non des adresses à variable unique. L’application définit l’attribut d’instruction SQL_BIND_BY_COLUMN pour spécifier s’il utilise une liaison selon les colonnes ou les lignes. L’utilisation de la liaison selon les colonnes ou les lignes dépend principalement des préférences de l’application. La liaison selon les lignes peut correspondre plus étroitement à la disposition des données de l’application, auquel cas elle offre de meilleures performances.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Liaison selon les colonnes](../../../odbc/reference/develop-app/column-wise-binding.md)  
  
-   [Liaison selon les lignes](../../../odbc/reference/develop-app/row-wise-binding.md)
