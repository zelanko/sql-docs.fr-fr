---
title: Définition du Mode de validation | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- transactions [ODBC], commit modes
- committing transactions [ODBC]
- commit modes [ODBC]
ms.assetid: b60d0d74-0655-4013-8d5a-bc1866eaa166
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: efc999a3644a9146e7195f0bbbb07d130172d30d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47762397"
---
# <a name="setting-the-commit-mode"></a>Définition du mode de validation
Les applications spécifier le mode de transaction avec l’attribut de connexion SQL_ATTR_AUTOCOMMIT. Par défaut, les transactions de ODBC sont en mode de validation automatique (à moins que **SQLSetConnectAttr** et **SQLSetConnectOption** ne sont pas pris en charge, ce qui est peu probable). Changement du mode de validation manuelle automatiquement en mode de validation automatique valide une transaction ouverte sur la connexion.
