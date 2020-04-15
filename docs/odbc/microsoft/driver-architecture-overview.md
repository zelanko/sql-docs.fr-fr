---
title: Aperçu de l’architecture du conducteur (en anglais seulement) Microsoft Docs
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
ms.openlocfilehash: cd55290e09fbd35f5a1559ce4209693ef8eaaf73
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303460"
---
# <a name="driver-architecture-overview"></a>Vue d’ensemble de l’architecture du pilote
Le Microsoft Visual FoxPro ODBC Driver est un pilote 32 bits qui vous permet d’ouvrir et de interroger une base de données Microsoft Visual FoxPro ou des tables FoxPro via l’interface Open Database Connectivity (ODBC). Vous pouvez accéder aux données FoxPro à l’aide des types d’applications suivants :  
  
-   Une application Microsoft Office, comme Microsoft Excel ou Microsoft Word, qui utilise Microsoft Query pour communiquer avec ODBC.  
  
-   Une application écrite dans Microsoft Visual C ou C qui utilise l’API SDK ODBC.  
  
-   Une application écrite dans Microsoft Visual Basic ou Microsoft Visual Basic pour les applications.  
  
 Dans chaque cas, la demande d’information utilise l’API ODBC. Le driver Manager ODBC travaille avec le Visual FoxPro ODBC Driver pour ouvrir et récupérer des données à partir de tables et de bases de données FoxPro.  
  
 L’architecture est représentée dans le diagramme suivant :  
  
 ![Affiche l’architecture ODBC Driver](../../odbc/microsoft/media/vfparch.gif "vfparch (vfparch)")  
  
 Cette section contient les rubriques suivantes :  
  
-   [Terminologie Visual FoxPro](../../odbc/microsoft/visual-foxpro-terminology.md)  
  
-   [Installation et configuration du pilote Visual FoxPro ODBC](../../odbc/microsoft/installing-and-configuring.md)  
  
-   [Utilisation du pilote ODBC Visual FoxPro](../../odbc/microsoft/using-the-visual-foxpro-odbc-driver.md)
