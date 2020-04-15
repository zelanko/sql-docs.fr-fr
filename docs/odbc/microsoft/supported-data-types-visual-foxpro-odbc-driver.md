---
title: Types de données pris en charge (Visual FoxPro ODBC Driver) Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301099"
---
# <a name="supported-data-types-visual-foxpro-odbc-driver"></a>Types de données pris en charge (pilote ODBC Visual FoxPro)
La liste des types de données pris en charge par le pilote sont présentées par l’intermédiaire de l’API ODBC et dans Microsoft Query.  
  
## <a name="data-types-in-c-applications"></a>Types de données dans les applications C  
 Vous pouvez obtenir une liste de types de données pris en charge par le visual FoxPro ODBC Driver en utilisant la fonction [SQLGetTypeInfo](../../odbc/microsoft/sqlgettypeinfo-visual-foxpro-odbc-driver.md) dans les applications C ou C.  
  
## <a name="data-types-in-applications-using-microsoft-query"></a>Types de données dans les applications utilisant microsoft Requête  
 Si votre application utilise Microsoft Query pour créer un nouveau tableau sur une source de données Visual FoxPro, Microsoft Query affiche la boîte de dialogue **New Table Definition.** Sous **la description de champ**, la boîte de **type** répertorie [visual FoxPro types de données de champ](../../odbc/microsoft/visual-foxpro-field-data-types.md), représentés par des caractères simples.
