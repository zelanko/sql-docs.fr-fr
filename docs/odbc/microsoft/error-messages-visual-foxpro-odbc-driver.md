---
title: Messages d’erreur (pilote ODBC de Visual FoxPro) | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6072a6e317ab87118376b08790fc0fb49c495e3b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67952516"
---
# <a name="error-messages-visual-foxpro-odbc-driver"></a>Messages d’erreur (pilote ODBC Visual FoxPro)
Lorsqu’une erreur se produit, le pilote de Visual FoxPro retourne les informations suivantes :  
  
-   Le numéro d’erreur natif et le texte du message d’erreur  
  
-   Le SQLSTATE (un code d’erreur ODBC) et le texte du message d’erreur  
  
 Vous accéder à ces informations d’erreur en appelant [SQLError](../../odbc/microsoft/sqlerror-visual-foxpro-odbc-driver.md).  
  
## <a name="native-errors"></a>Erreurs natives  
 Pour les erreurs qui se produisent dans la source de données, le pilote Visual FoxPro retourne le numéro d’erreur natif et le texte du message d’erreur. Pour obtenir la liste de numéros d’erreur natifs, consultez [Visual FoxPro ODBC pilote natif Messages d’erreur](../../odbc/microsoft/visual-foxpro-odbc-driver-native-error-messages.md).  
  
## <a name="sqlstate-odbc-error-codes"></a>SQLSTATE (codes d'erreur ODBC)  
 Pour les erreurs qui sont détectées et retournées par le pilote Visual FoxPro, le pilote mappe le numéro d’erreur natif retourné avec le SQLSTATE approprié. Si un numéro d’erreur natif n’a pas un code d’erreur ODBC pour mapper à, le pilote de Visual FoxPro retourne SQLSTATE S1000 (erreur générale).  
  
 Pour obtenir la liste de valeurs SQLSTATE générés par le pilote ODBC Visual FoxPro pour les erreurs Visual FoxPro correspondantes, consultez [Codes d’erreur ODBC](../../odbc/microsoft/odbc-error-codes-visual-foxpro-odbc-driver.md).  
  
## <a name="syntax"></a>Syntaxe  
 Messages d’erreur ont le format suivant :  
  
 **[** *vendor* **][** *ODBC_component* **]** *error_message*  
  
 Les préfixes de crochets ([]) identifient la source de l’erreur, tel que défini dans le tableau suivant.  
  
|Source de données|Prefix|Value|  
|-----------------|------------|-----------|  
|Gestionnaire de pilote|[fournisseur]<br />[ODBC_component]<br />[data_source]|[Microsoft]<br />[Gestionnaire de pilotes ODBC]<br />N/A|  
|Pilote Visual FoxPro|fournisseur]<br />[ODBC_component]<br />[data_source]|[Microsoft]<br />[Pilote ODBC Visual FoxPro]<br />N/A|  
  
 Par exemple, si le pilote ODBC Visual FoxPro n’a pas trouvé le fichier employee.dbf, elle peut retourner le message d’erreur suivant :  
  
 « [*Microsoft*] [*le pilote ODBC Visual FoxPro*] fichier 'employee.dbf' n’existe pas »
