---
description: ODBC test est une application compatible ODBC que vous pouvez utiliser pour tester des pilotes ODBC et le gestionnaire de pilotes ODBC.
title: Test d’ODBC
ms.custom: ''
ms.date: 09/01/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC test [ODBC]
- ODBC drivers [ODBC], testing
- gtrtst32.dll
- gtrts32w.dll [ODBC]
- odbct32w.exe [ODBC]
- odbcte32.exe [ODBC]
- testing ODBC drivers [ODBC]
ms.assetid: 7f13894c-5697-436c-be3d-fe16e1a02325
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 39869fe1230be75d9a76e13b8ba3938ec31ee5ee
ms.sourcegitcommit: b6ee0d434b3e42384b5d94f1585731fd7d0eff6f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89288244"
---
# <a name="odbc-test"></a>Test d’ODBC

## <a name="about"></a>À propos de

Microsoft® ODBC test est une application compatible ODBC que vous pouvez utiliser pour tester des pilotes ODBC et le gestionnaire de pilotes ODBC. Le test ODBC est inclus dans le [Kit de développement logiciel (SDK) Microsoft Data Access Components (MDAC) 2,8](https://www.microsoft.com/download/details.aspx?id=21995).

ODBC 3,51 comprend des versions ANSI et Unicode du test ODBC. Les fichiers correspondants sont les suivants :

- `Odbcte32.exe` et `Gtrtst32.dll` , pour la version ANSI.

- `Odbct32w.exe` et `Gtrts32w.dll` , pour la version Unicode.

Pour utiliser le test ODBC, vous devez comprendre l’API ODBC, le langage C et SQL. Pour plus d’informations sur l’API ODBC, consultez [Guide de référence du programmeur ODBC](../odbc/reference/odbc-programmer-s-reference.md).

Les rubriques d’aide qui étaient précédemment incluses dans cette section de la documentation sont maintenant contenues dans le programme de test ODBC. Ouvrez `Odbcte32.exe` ou `Odbct32w.exe` , ouvrez le menu **aide** , puis cliquez sur **rubriques d’aide**.

Notez que les versions 64 bits de ces applications, destinées aux systèmes d’exploitation Microsoft Windows 64 bits, ont les mêmes noms que les versions 32 bits, même s’il s’agit de fichiers distincts. par exemple, le nom de la version Unicode de la version 64 bits du test ODBC est `odbct32w.exe` .

## <a name="open-source"></a>Open source

Le test ODBC est open source. Pour afficher le code et générer la dernière version du test ODBC vous-même, accédez au [référentiel GitHub pour test ODBC](https://github.com/microsoft/ODBCTest).
