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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2b102d8435831d45aad3c2049581513e0493de9a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304120"
---
# <a name="sqlgetdata-desktop-database-drivers"></a>SQLGetData (pilotes pour les bases de données de poste de travail)
Cette fonction peut extraire des données de n’importe quelle colonne, qu’il y ait ou non des colonnes liées après celle-ci et quel que soit l’ordre dans lequel les colonnes sont récupérées.  
  
> [!NOTE]  
>  \*pcbValue dans **SQLGetData** peut retourner deux fois plus de caractères que ce qui est réellement disponible lors de la liaison à des données ANSI de plus de 510 caractères sur une base de données Jet 4,0. Les valeurs de caractères inférieures ou égales à 510 renverront le cbValue réel.
