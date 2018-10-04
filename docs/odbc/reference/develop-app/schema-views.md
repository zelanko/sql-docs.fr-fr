---
title: Vues de schéma | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- schema views [ODBC]
- functions [ODBC], catalog functions
- catalog functions [ODBC], schema views
ms.assetid: f1dfb3e8-a7bd-46c3-92b6-c19531e8409d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 782dec08b76a9e5a97719d6af39e2c30c0f92d19
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47797387"
---
# <a name="schema-views"></a>Vues de schéma
Une application peut extraire des informations de métadonnées à partir de SGBD en appelant les fonctions de catalogue ODBC ou à l’aide de vues INFORMATION_SCHEMA. Les vues sont définies par la norme ANSI SQL-92.  
  
 Si la prise en charge par le SGBD et le pilote, les vues INFORMATION_SCHEMA fournissent un moyen plus puissant et complet de la récupération de métadonnées que de fournissent les fonctions de catalogue ODBC. Une application puisse exécuter sa propre valeur personnalisée **sélectionnez** instruction par rapport à un de ces affichages, joindre des vues, ou peut effectuer une union sur des vues. Tout en offrant l’utilitaire supérieure et une plus large gamme de métadonnées, les vues INFORMATION_SCHEMA ne sont pas souvent pris en charge par le SGBD. Cela peut changer en plus des SGBD et des pilotes à se conformer SQL-92.  
  
 Pour déterminer les modes d’affichage sont pris en charge, une application appelle **SQLGetInfo** avec l’option SQL_INFO_SCHEMA_VIEWS. Pour récupérer les métadonnées à partir d’une vue pris en charge, l’application exécute une **sélectionnez** instruction qui spécifie les informations de schéma requises.
