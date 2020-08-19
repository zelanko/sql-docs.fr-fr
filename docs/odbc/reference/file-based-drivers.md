---
description: Pilotes basés sur des fichiers
title: Pilotes basés sur des fichiers | Microsoft Docs
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
ms.openlocfilehash: 770e8560c540e8423aebf0a79c0e8ee5c124c8e3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429081"
---
# <a name="file-based-drivers"></a>Pilotes basés sur des fichiers
Les pilotes basés sur des fichiers sont utilisés avec des sources de données telles que dBASE qui ne fournissent pas de moteur de base de données autonome pour le pilote à utiliser. Ces pilotes accèdent directement aux données physiques et doivent implémenter un moteur de base de données pour traiter les instructions SQL. En règle générale, les moteurs de base de données des pilotes basés sur des fichiers implémentent le sous-ensemble de SQL ODBC défini par le niveau de conformité SQL minimal. pour obtenir la liste des instructions SQL dans ce niveau de conformité, consultez l' [annexe C : grammaire SQL](../../odbc/reference/appendixes/appendix-c-sql-grammar.md).  
  
 Lors de la comparaison des pilotes basés sur des fichiers et SGBD, les pilotes basés sur des fichiers sont plus difficiles à écrire en raison du composant moteur de base de données, moins compliqué à configurer, car il n’y a pas d’éléments réseau et moins puissants, car peu de personnes ont le temps d’écrire des moteurs de base de données aussi puissants que ceux générés par les sociétés  
  
 L’illustration suivante montre deux configurations différentes de pilotes basés sur des fichiers, l’un dans lequel les données résident localement et l’autre dans laquelle elles résident sur un serveur de fichiers réseau.  
  
 ![Deux configurations de pilotes basés sur des&#45;de fichiers](../../odbc/reference/media/pr06.gif "pr06")
