---
title: Présentation de l’Architecture pilote | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0fdb1789c6640c072ec013c341bd4889b28bb469
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47771867"
---
# <a name="driver-architecture-overview"></a>Vue d’ensemble de l’architecture du pilote
Le pilote ODBC Visual FoxPro Microsoft est un pilote 32 bits qui vous permet d’ouvrir et d’interroger une base de données Microsoft Visual FoxPro ou tables FoxPro via l’interface de base de données connectivité ODBC (Open). Vous pouvez accéder données FoxPro avec les types d’applications suivants :  
  
-   Une application Microsoft Office, telles que Microsoft Excel ou Microsoft Word, qui utilise Microsoft Query pour communiquer avec ODBC.  
  
-   Une application écrite en Microsoft Visual C++ ou C qui utilise l’API du Kit de développement logiciel ODBC.  
  
-   Une application écrite en Microsoft Visual Basic ou Microsoft Visual Basic pour Applications.  
  
 Dans chaque cas, la demande d’informations utilise l’API ODBC. Le Gestionnaire de pilotes ODBC fonctionne avec le pilote ODBC Visual FoxPro pour ouvrir et de récupérer des données à partir de bases de données et tables FoxPro.  
  
 L’architecture est représentée dans le diagramme suivant :  
  
 ![Illustre l’architecture de pilote ODBC](../../odbc/microsoft/media/vfparch.gif "vfparch")  
  
 Cette section contient les rubriques suivantes.  
  
-   [Terminologie Visual FoxPro](../../odbc/microsoft/visual-foxpro-terminology.md)  
  
-   [Installation et configuration du pilote ODBC Visual FoxPro](../../odbc/microsoft/installing-and-configuring.md)  
  
-   [Utilisation du pilote ODBC Visual FoxPro](../../odbc/microsoft/using-the-visual-foxpro-odbc-driver.md)
