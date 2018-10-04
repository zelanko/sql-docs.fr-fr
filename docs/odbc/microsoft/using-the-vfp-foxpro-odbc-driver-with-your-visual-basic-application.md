---
title: Utiliser le pilote ODBC de FoxPro VFP avec votre Application Visual Basic | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Visual FoxPro ODBC driver [ODBC], visual basic applications
- Visual Basic applications [ODBC]
- FoxPro ODBC driver [ODBC], visual basic applications
- Visual FoxPro data [ODBC], visual basic applications
ms.assetid: 5223ca23-5df6-4ebc-aa3b-70682ff27a8c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4b77fdee70ff73772710c9758eeb2bf2594f365d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47697879"
---
# <a name="using-the-vfp-foxpro-odbc-driver-with-your-visual-basic-application"></a>Utilisation du pilote ODBC Visual FoxPro avec votre application Visual Basic
Application de votre Microsoft® Visual Basic® peut communiquer avec les données Visual FoxPro en créant un contrôle de données qui se connecte à une source de données Visual FoxPro.  
  
#### <a name="to-connect-to-visual-foxpro-data-using-the-data-control-in-visual-basic"></a>Se connecter aux données Visual FoxPro à l’aide du contrôle de données en Visual Basic  
  
1.  Créer une source de données nommée « test » qui se connecte à la base de données exemple TasTrade inclus dans Visual FoxPro. L’installation de Visual FoxPro par défaut place la base de données exemple TasTrade dans l’emplacement :  
  
    ```  
    c:\vfp\samples\mainsamp\data\tastrade.dbc  
    ```  
  
2.  Dans Visual Basic, créer un nouveau formulaire et placez une zone de texte et un contrôle de données dessus.  
  
3.  Modifier les propriétés de connexion du contrôle de données comme suit :  
  
    ```  
    ODBC;DATABASE=tastrade;DSN=test  
    ```  
  
4.  Modifiez la propriété RecordsetType comme suit :  
  
    ```  
    2 - Snapshot  
    ```  
  
5.  Modifiez la propriété source comme suit :  
  
    ```  
    customer  
    ```  
  
6.  Modifier la propriété de source de données pour la zone de texte pour le nom par défaut pour le contrôle de données à ce qui suit :  
  
    ```  
    data1  
    ```  
  
7.  Modifier la propriété DataField de la zone de texte à ce qui suit :  
  
    ```  
    customer_id  
    ```  
  
8.  Exécutez le formulaire et le contrôle de données permet d’ignorer via les champs d’id de client à partir de la base de données Visual FoxPro TasTrade.
