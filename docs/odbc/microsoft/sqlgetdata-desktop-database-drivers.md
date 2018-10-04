---
title: SQLGetData (pilotes pour les postes de travail de base de données) | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 6f362d725f8b734ab9ecdbdc79c268af08a495b4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47622127"
---
# <a name="sqlgetdata-desktop-database-drivers"></a>SQLGetData (pilotes pour les bases de données de poste de travail)
Cette fonction peut récupérer des données à partir de n’importe quelle colonne, s’il existe des colonnes dépendantes après lui et quel que soit l’ordre dans lequel les colonnes sont récupérées.  
  
> [!NOTE]  
>  \*pcbValue dans **SQLGetData** peut retourner deux fois plus de caractères comme réellement disponibles lors de la liaison aux données ANSI dépasse 510 caractères sur une base de données Jet 4.0. Les valeurs de caractère de moins de 510 retournera le cbValue réel.
