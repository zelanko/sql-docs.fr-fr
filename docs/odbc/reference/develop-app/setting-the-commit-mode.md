---
title: Définition du mode de validation | Microsoft Docs
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68094225"
---
# <a name="setting-the-commit-mode"></a>Définition du mode de validation
Les applications spécifient le mode de transaction avec l’attribut de connexion SQL_ATTR_AUTOCOMMIT. Par défaut, les transactions ODBC sont en mode de validation automatique (sauf si **SQLSetConnectAttr** et **SQLSetConnectOption** ne sont pas pris en charge, ce qui est peu probable). Le passage du mode de validation manuelle au mode de validation automatique valide toutes les transactions ouvertes sur la connexion.
