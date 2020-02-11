---
title: SQLGetData (pilotes de base de données de bureau) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetData function [ODBC], Desktop Database Drivers
ms.assetid: c9d9a32d-5dc2-4189-9bfb-2b008bc3d6a3
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 086c5381f1801baf919508525c17faab93746ca0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68003358"
---
# <a name="sqlgetdata-desktop-database-drivers"></a>SQLGetData (pilotes pour les bases de données de poste de travail)
Cette fonction peut extraire des données de n’importe quelle colonne, qu’il y ait ou non des colonnes liées après celle-ci et quel que soit l’ordre dans lequel les colonnes sont récupérées.  
  
> [!NOTE]  
>  \*pcbValue dans **SQLGetData** peut retourner deux fois plus de caractères que ce qui est réellement disponible lors de la liaison à des données ANSI de plus de 510 caractères sur une base de données Jet 4,0. Les valeurs de caractères inférieures ou égales à 510 renverront le cbValue réel.
