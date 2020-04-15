---
title: Utilisez le pilote VFP FoxPro ODBC avec votre application de base visuelle (fr) Microsoft Docs
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
ms.openlocfilehash: 871c392166fa2f5726e6f9e8651bf758dc144a00
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292699"
---
# <a name="using-the-vfp-foxpro-odbc-driver-with-your-visual-basic-application"></a>Utilisation du pilote ODBC Visual FoxPro avec votre application Visual Basic
Votre application Microsoft® Visual Basic® peut communiquer avec les données Visual FoxPro en créant un contrôle de données qui se connecte à une source de données Visual FoxPro.  
  
#### <a name="to-connect-to-visual-foxpro-data-using-the-data-control-in-visual-basic"></a>Pour vous connecter aux données Visual FoxPro à l’aide du contrôle des données dans Visual Basic  
  
1.  Créez une source de données appelée « test » qui se connecte à la base de données de l’échantillon TasTrade incluse dans Visual FoxPro. L’installation visuelle par défaut de FoxPro place la base de données de l’échantillon TasTrade dans l’emplacement :  
  
    ```  
    c:\vfp\samples\mainsamp\data\tastrade.dbc  
    ```  
  
2.  Dans Visual Basic, créez une nouvelle forme et placez une boîte de texte et un contrôle de données dessus.  
  
3.  Modifier la propriété Connect du contrôle des données comme suit :  
  
    ```  
    ODBC;DATABASE=tastrade;DSN=test  
    ```  
  
4.  Modifier la propriété RecordsetType pour les suivants :  
  
    ```  
    2 - Snapshot  
    ```  
  
5.  Modifier la propriété RecordSource pour les suivants :  
  
    ```  
    customer  
    ```  
  
6.  Modifier la propriété DataSource pour la boîte de texte au nom par défaut du contrôle de données à ce qui suit :  
  
    ```  
    data1  
    ```  
  
7.  Modifier la propriété DataField de la boîte de texte à ce qui suit :  
  
    ```  
    customer_id  
    ```  
  
8.  Exécutez le formulaire et utilisez le contrôle des données pour sauter à travers les champs d’identification du client à partir de la base de données d’échantillons Visual FoxPro TasTrade.
