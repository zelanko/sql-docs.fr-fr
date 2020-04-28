---
title: Types de données pris en charge (pilote ODBC Visual FoxPro) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Visual FoxPro ODBC driver [ODBC], data types
- FoxPro ODBC driver [ODBC], data types
- data types [ODBC], Visual FoxPro ODBC driver
ms.assetid: ab529cc6-d157-4b35-b6f9-6ffd09af098c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3fc28464a7c14f9801473cc125b0e90c50247d68
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81301099"
---
# <a name="supported-data-types-visual-foxpro-odbc-driver"></a>Types de données pris en charge (pilote ODBC Visual FoxPro)
La liste des types de données pris en charge par le pilote est présentée par le biais de l’API ODBC et de Microsoft Query.  
  
## <a name="data-types-in-c-applications"></a>Types de données dans les applications C  
 Vous pouvez obtenir la liste des types de données pris en charge par le pilote ODBC Visual FoxPro à l’aide de la fonction [SQLGetTypeInfo](../../odbc/microsoft/sqlgettypeinfo-visual-foxpro-odbc-driver.md) dans les applications C ou C++.  
  
## <a name="data-types-in-applications-using-microsoft-query"></a>Types de données dans les applications à l’aide de Microsoft Query  
 Si votre application utilise Microsoft Query pour créer une nouvelle table sur une source de données Visual FoxPro, Microsoft Query affiche la boîte de dialogue **nouvelle définition de table** . Sous **Description du champ**, la zone **type** répertorie les types de [données de champ Visual FoxPro](../../odbc/microsoft/visual-foxpro-field-data-types.md), représentés par des caractères uniques.
