---
title: "SQLGetData (pilotes d’ordinateur de bureau) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SQLGetData function [ODBC], Desktop Database Drivers
ms.assetid: c9d9a32d-5dc2-4189-9bfb-2b008bc3d6a3
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2bd9088fa327783019d0b025ab4daaacd951852b
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="sqlgetdata-desktop-database-drivers"></a>SQLGetData (pilotes bureau de base de données)
Cette fonction peut récupérer des données à partir de n’importe quelle colonne, il existe des colonnes dépendantes après lui et quel que soit l’ordre dans lequel les colonnes sont récupérés ou non.  
  
> [!NOTE]  
>  \*pcbValue dans **SQLGetData** peut retourner deux fois plus de caractères comme réellement disponibles lors de la liaison aux données ANSI plues de 510 caractères sur une base de données Jet 4.0. Les valeurs de caractères inférieur ou égal à 510 retournera le cbValue réel.
