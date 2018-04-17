---
title: SQLGetData (pilotes d’ordinateur de bureau) | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQLGetData function [ODBC], Desktop Database Drivers
ms.assetid: c9d9a32d-5dc2-4189-9bfb-2b008bc3d6a3
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 79c1dded180e5cdf4e0b08af7add327343fdbe00
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="sqlgetdata-desktop-database-drivers"></a>SQLGetData (pilotes bureau de base de données)
Cette fonction peut récupérer des données à partir de n’importe quelle colonne, il existe des colonnes dépendantes après lui et quel que soit l’ordre dans lequel les colonnes sont récupérés ou non.  
  
> [!NOTE]  
>  \*pcbValue dans **SQLGetData** peut retourner deux fois plus de caractères comme réellement disponibles lors de la liaison aux données ANSI plues de 510 caractères sur une base de données Jet 4.0. Les valeurs de caractères inférieur ou égal à 510 retournera le cbValue réel.
