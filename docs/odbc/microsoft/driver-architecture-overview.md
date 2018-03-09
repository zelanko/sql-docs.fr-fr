---
title: "Présentation de l’Architecture pilote | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual FoxPro ODBC driver [ODBC], architecture
- FoxPro ODBC driver [ODBC], architecture
ms.assetid: ef5a91cd-158e-40bf-b5a8-8ba535c4705e
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2778161fa117e164a4c49e57a5511b0682507b37
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="driver-architecture-overview"></a>Présentation de l’Architecture pilote
Le pilote ODBC Microsoft Visual FoxPro est un pilote 32 bits qui vous permet d’ouvrir et d’interroger une base de données Microsoft Visual FoxPro ou tables FoxPro via l’interface de base de données connectivité ODBC (Open). Vous pouvez accéder à des données FoxPro utilisant les types d’applications suivants :  
  
-   Une application Microsoft Office, telles que Microsoft Excel ou Microsoft Word, qui utilise Microsoft Query pour communiquer avec ODBC.  
  
-   Une application écrite en Microsoft Visual C++ ou C qui utilise l’API du Kit de développement logiciel ODBC.  
  
-   Une application écrite en Microsoft Visual Basic ou Microsoft Visual Basic pour Applications.  
  
 Dans chaque cas, la demande d’informations utilise l’API ODBC. Le Gestionnaire de pilotes ODBC fonctionne avec le pilote ODBC Visual FoxPro pour ouvrir et récupérer des données à partir de bases de données et tables FoxPro.  
  
 L’architecture est représentée dans le diagramme suivant :  
  
 ![Illustre l’architecture du pilote ODBC](../../odbc/microsoft/media/vfparch.gif "vfparch")  
  
 Cette section contient les rubriques suivantes.  
  
-   [Terminologie Visual FoxPro](../../odbc/microsoft/visual-foxpro-terminology.md)  
  
-   [Installer et configurer le pilote ODBC Visual FoxPro](../../odbc/microsoft/installing-and-configuring.md)  
  
-   [Utilisation du pilote ODBC Visual FoxPro](../../odbc/microsoft/using-the-visual-foxpro-odbc-driver.md)
