---
title: Messages d’erreur (Visual FoxPro ODBC Driver) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- error messages [ODBC], Visual FoxPro ODBC driver
- Visual FoxPro ODBC driver [ODBC], error messages
- SQLSTATE [ODBC]
- FoxPro ODBC driver [ODBC], error messages
ms.assetid: 58ea9734-4edf-44da-ba80-938aa7b340e4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 31f894e58da93fe6091dba306f8b765d14bac2cb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81286399"
---
# <a name="error-messages-visual-foxpro-odbc-driver"></a>Messages d’erreur (pilote ODBC Visual FoxPro)
Lorsqu’une erreur se produit, le pilote Visual FoxPro renvoie les informations suivantes :  
  
-   Le numéro d’erreur natif et le texte de message d’erreur  
  
-   Le SQLSTATE (un code d’erreur ODBC) et le texte de message d’erreur  
  
 Vous accédez à ces informations d’erreur en appelant [SQLError](../../odbc/microsoft/sqlerror-visual-foxpro-odbc-driver.md).  
  
## <a name="native-errors"></a>Erreurs natives  
 Pour les erreurs qui se produisent dans la source de données, le pilote Visual FoxPro renvoie le numéro d’erreur natif et le texte de message d’erreur. Pour une liste de numéros d’erreur natifs, voir [Visual FoxPro ODBC Driver Native Error Messages](../../odbc/microsoft/visual-foxpro-odbc-driver-native-error-messages.md).  
  
## <a name="sqlstate-odbc-error-codes"></a>SQLSTATE (codes d'erreur ODBC)  
 Pour les erreurs détectées et retournées par le pilote Visual FoxPro, le conducteur cartographie le numéro d’erreur natif retourné au SQLSTATE approprié. Si un numéro d’erreur natif n’a pas de code d’erreur ODBC à cartographier, le pilote Visual FoxPro renvoie SQLSTATE S1000 (erreur générale).  
  
 Pour une liste des valeurs SQLSTATE générées par le visual FoxPro ODBC Driver pour les erreurs visuelles correspondantes de FoxPro, voir [ODBC Error Codes](../../odbc/microsoft/odbc-error-codes-visual-foxpro-odbc-driver.md).  
  
## <a name="syntax"></a>Syntaxe  
 Les messages d’erreur ont le format suivant :  
  
 **[vendeur** *vendor* **] [** *ODBC_component* **]** *error_message*  
  
 Les préfixes entre parenthèses ([]) identifient la source de l’erreur telle que définie dans le tableau suivant.  
  
|Source de données|Préfixe|Value|  
|-----------------|------------|-----------|  
|Gestionnaire de pilote|[vendeur]<br />[ODBC_component]<br />[data_source]|[Microsoft]<br />[ODBC Driver Manager]<br />N/A|  
|Pilote Visual FoxPro|vendeur]<br />[ODBC_component]<br />[data_source]|[Microsoft]<br />[ODBC Visual FoxPro driver]<br />N/A|  
  
 Par exemple, si le visual FoxPro ODBC Driver n’a pas pu trouver l’employé du fichier.dbf, il peut retourner le message d’erreur suivant:  
  
 "[*Microsoft*]*[ODBC Visual FoxPro Driver*] File 'employee.dbf' n’existe pas"
