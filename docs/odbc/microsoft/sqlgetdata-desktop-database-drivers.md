---
title: SQLGetData (Desktop Database Drivers) Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304120"
---
# <a name="sqlgetdata-desktop-database-drivers"></a>SQLGetData (pilotes pour les bases de données de poste de travail)
Cette fonction peut récupérer des données de n’importe quelle colonne, qu’il y ait ou non des colonnes liées après elle et indépendamment de l’ordre dans lequel les colonnes sont récupérées.  
  
> [!NOTE]  
>  \*pcbValue dans **SQLGetData** peut retourner deux fois plus de caractères que réellement disponibles lors de la liaison aux données ANSI plus de 510 caractères sur une base de données Jet 4.0. Les valeurs de caractère de 510 ou moins retourneront la cbValue réelle.
