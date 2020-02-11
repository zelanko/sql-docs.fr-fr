---
title: Messages d’erreur (pilote ODBC Visual FoxPro) | Microsoft Docs
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67952516"
---
# <a name="error-messages-visual-foxpro-odbc-driver"></a>Messages d’erreur (pilote ODBC Visual FoxPro)
Lorsqu’une erreur se produit, le pilote Visual FoxPro retourne les informations suivantes :  
  
-   Le numéro d’erreur natif et le texte du message d’erreur  
  
-   Le texte SQLSTATE (un code d’erreur ODBC) et le texte du message d’erreur  
  
 Vous pouvez accéder à ces informations d’erreur en appelant [SQLError](../../odbc/microsoft/sqlerror-visual-foxpro-odbc-driver.md).  
  
## <a name="native-errors"></a>Erreurs natives  
 Pour les erreurs qui se produisent dans la source de données, le pilote Visual FoxPro retourne le numéro d’erreur natif et le texte du message d’erreur. Pour obtenir la liste des numéros d’erreur natifs, consultez [messages d’erreur natifs du pilote ODBC Visual FoxPro](../../odbc/microsoft/visual-foxpro-odbc-driver-native-error-messages.md).  
  
## <a name="sqlstate-odbc-error-codes"></a>SQLSTATE (codes d'erreur ODBC)  
 Pour les erreurs détectées et retournées par le pilote Visual FoxPro, le pilote mappe le numéro d’erreur native renvoyé à la valeur SQLSTATE appropriée. Si un numéro d’erreur natif n’a pas de code d’erreur ODBC à mapper, le pilote Visual FoxPro retourne SQLSTATE S1000 (erreur générale).  
  
 Pour obtenir la liste des valeurs SQLSTATE générées par le pilote ODBC Visual FoxPro pour les erreurs Visual FoxPro correspondantes, consultez [codes d’erreur ODBC](../../odbc/microsoft/odbc-error-codes-visual-foxpro-odbc-driver.md).  
  
## <a name="syntax"></a>Syntaxe  
 Les messages d’erreur ont le format suivant :  
  
 **[** *fournisseur* **] [** *ODBC_component* **]** *ERROR_MESSAGE*  
  
 Les préfixes entre crochets ([]) identifient la source de l’erreur, comme défini dans le tableau suivant.  
  
|Source de données|Préfixe|Valeur|  
|-----------------|------------|-----------|  
|Gestionnaire de pilote|hétérogène<br />[ODBC_component]<br />[data_source]|Librairie<br />[ODBC Driver Manager]<br />N/A|  
|Pilote Visual FoxPro|hétérogène<br />[ODBC_component]<br />[data_source]|Librairie<br />[Pilote ODBC Visual FoxPro]<br />N/A|  
  
 Par exemple, si le pilote ODBC Visual FoxPro n’a pas pu trouver le fichier Employee. DBF, le message d’erreur suivant peut s’afficher :  
  
 « [*Microsoft*] [*pilote ODBC Visual FoxPro*] le fichier «Employee. dbf » n’existe pas»
