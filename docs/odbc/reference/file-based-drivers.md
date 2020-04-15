---
title: Pilotes basés sur les fichiers (en anglais seulement) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- file-based drivers [ODBC]
- ODBC architecture [ODBC], drivers
- drivers [ODBC], file-based drivers
ms.assetid: d92e0c5c-d176-4282-bbe1-d449e2223d50
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 223bd838754f1d656ac71ae37926389097af3ea1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306662"
---
# <a name="file-based-drivers"></a>Pilotes basés sur des fichiers
Les pilotes basés sur les fichiers sont utilisés avec des sources de données telles que dBASE qui ne fournissent pas un moteur de base de données autonome pour le conducteur à utiliser. Ces conducteurs accèdent directement aux données physiques et doivent mettre en œuvre un moteur de base de données pour traiter les relevés SQL. Comme pratique courante, les moteurs de base de données des pilotes basés sur des fichiers mettent en œuvre le sous-ensemble de SQL ODBC défini par le niveau minimum de conformité SQL; pour une liste des déclarations SQL dans ce niveau de conformité, voir [Annexe C: SQL Grammar](../../odbc/reference/appendixes/appendix-c-sql-grammar.md).  
  
 En comparant les pilotes basés sur les fichiers et les pilotes basés sur les fichiers, les pilotes basés sur des fichiers sont plus difficiles à écrire en raison du composant moteur de base de données, moins compliqué à configurer parce qu’il n’y a pas de pièces de réseau, et moins puissant parce que peu de gens ont le temps d’écrire des moteurs de base de données aussi puissants que ceux produits par les sociétés de base de données.  
  
 L’illustration suivante montre deux configurations différentes de pilotes basés sur des fichiers, l’une dans laquelle les données résident localement et l’autre dans laquelle elles se trouvent sur un serveur de fichiers réseau.  
  
 ![Deux configurations de fichiers&#45;pilotes basés](../../odbc/reference/media/pr06.gif "pr06")
