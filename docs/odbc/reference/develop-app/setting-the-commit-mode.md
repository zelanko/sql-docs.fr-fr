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
ms.openlocfilehash: a43a78ad9453f65d9b12595851bd622f720b409a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68094225"
---
# <a name="setting-the-commit-mode"></a>Définition du mode de validation
Les applications spécifier le mode de transaction avec l’attribut de connexion SQL_ATTR_AUTOCOMMIT. Par défaut, les transactions de ODBC sont en mode de validation automatique (à moins que **SQLSetConnectAttr** et **SQLSetConnectOption** ne sont pas pris en charge, ce qui est peu probable). Changement du mode de validation manuelle automatiquement en mode de validation automatique valide une transaction ouverte sur la connexion.
