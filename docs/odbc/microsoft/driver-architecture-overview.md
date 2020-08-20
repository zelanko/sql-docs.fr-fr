---
description: Vue d’ensemble de l’architecture du pilote
title: Vue d’ensemble de l’architecture des pilotes | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Visual FoxPro ODBC driver [ODBC], architecture
- FoxPro ODBC driver [ODBC], architecture
ms.assetid: ef5a91cd-158e-40bf-b5a8-8ba535c4705e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d71a2c28825ee8c7d4e12e047234f3e336b339e0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88466441"
---
# <a name="driver-architecture-overview"></a>Vue d’ensemble de l’architecture du pilote
Le pilote ODBC Microsoft Visual FoxPro est un pilote 32 bits qui vous permet d’ouvrir et d’interroger une base de données Microsoft Visual FoxPro ou des tables FoxPro par le biais de l’interface Open Database Connectivity (ODBC). Vous pouvez accéder aux données FoxPro à l’aide des types d’applications suivants :  
  
-   Une application Microsoft Office, telle que Microsoft Excel ou Microsoft Word, qui utilise Microsoft Query pour communiquer avec ODBC.  
  
-   Une application écrite en Microsoft Visual C++ ou C qui utilise l’API ODBC SDK.  
  
-   Une application écrite dans Microsoft Visual Basic ou Microsoft Visual Basic pour Applications.  
  
 Dans chaque cas, la demande d’informations utilise l’API ODBC. Le gestionnaire de pilotes ODBC fonctionne avec le pilote ODBC Visual FoxPro pour ouvrir et récupérer des données à partir de tables et de bases de données FoxPro.  
  
 L’architecture est représentée dans le diagramme suivant :  
  
 ![Présente l’architecture du pilote ODBC](../../odbc/microsoft/media/vfparch.gif "vfparch")  
  
 Cette section contient les rubriques suivantes :  
  
-   [Terminologie Visual FoxPro](../../odbc/microsoft/visual-foxpro-terminology.md)  
  
-   [Installation et configuration du pilote ODBC Visual FoxPro](../../odbc/microsoft/installing-and-configuring.md)  
  
-   [Utilisation du pilote ODBC Visual FoxPro](../../odbc/microsoft/using-the-visual-foxpro-odbc-driver.md)
