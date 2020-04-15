---
title: Cartographie SQLInstallTranslator (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLInstallTranslator function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLInstallTranslator
ms.assetid: bcd9ba4f-7834-4bc4-876e-c7478998e524
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8ab5ebccaac7ccf6374971c1d21040ad15fb3e55
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300581"
---
# <a name="sqlinstalltranslator-mapping"></a>SQLInstallTranslator, mappage
Lorsqu’une application ODBC *2.x* appelle **SQLInstallTranslator** par l’intermédiaire d’un conducteur ODBC *3.x,* le Driver Manager cartographie l’appel à **SQLInstallTranslatorEx**. Une demande ne devrait pas appeler **SQLInstallTranslator** dans le gestionnaire de conducteur ODBC *3.x* avec *l’argument lpszInfFile* réglé à une valeur autre que NULL. L’ODBC. Le fichier INF utilisé dans ODBC *2.x* n’est plus pris en charge dans ODBC *3.x*, même pour la compatibilité vers l’arrière.
