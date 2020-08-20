---
description: Utilisation du pilote ODBC Visual FoxPro avec votre application Visual Basic
title: Utiliser le pilote ODBC de VFP FoxPro avec votre application Visual Basic | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 07ec83ccab43890bccbf5e12582628fdb98d29c2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88500052"
---
# <a name="using-the-vfp-foxpro-odbc-driver-with-your-visual-basic-application"></a>Utilisation du pilote ODBC Visual FoxPro avec votre application Visual Basic
Votre application Microsoft® Visual Basic® peut communiquer avec les données Visual FoxPro en créant un contrôle de données qui se connecte à une source de données Visual FoxPro.  
  
#### <a name="to-connect-to-visual-foxpro-data-using-the-data-control-in-visual-basic"></a>Pour vous connecter à des données Visual FoxPro à l’aide du contrôle de données dans Visual Basic  
  
1.  Créez une source de données nommée « test » qui se connecte à l’exemple de base de données TasTrade inclus dans Visual FoxPro. L’installation de Visual FoxPro par défaut place l’exemple de base de données TasTrade à l’emplacement suivant :  
  
    ```  
    c:\vfp\samples\mainsamp\data\tastrade.dbc  
    ```  
  
2.  Dans Visual Basic, créez un nouveau formulaire et placez-y une zone de texte et un contrôle de données.  
  
3.  Modifiez la propriété Connect du contrôle de données comme suit :  
  
    ```  
    ODBC;DATABASE=tastrade;DSN=test  
    ```  
  
4.  Modifiez la propriété TypeRecordset comme suit :  
  
    ```  
    2 - Snapshot  
    ```  
  
5.  Modifiez la propriété RecordSource comme suit :  
  
    ```  
    customer  
    ```  
  
6.  Remplacez la propriété DataSource de la zone de texte par le nom par défaut du contrôle de données par ce qui suit :  
  
    ```  
    data1  
    ```  
  
7.  Modifiez la propriété DataField de la zone de texte comme suit :  
  
    ```  
    customer_id  
    ```  
  
8.  Exécutez le formulaire et utilisez le contrôle Data pour ignorer les champs Customer ID de l’exemple de base de données TasTrade Visual FoxPro.
