---
description: Définition du mode de validation
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6a71d6f97f4683f9177c940be7d6ca1cc4a27c01
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88494623"
---
# <a name="setting-the-commit-mode"></a>Définition du mode de validation
Les applications spécifient le mode de transaction avec l’attribut de connexion SQL_ATTR_AUTOCOMMIT. Par défaut, les transactions ODBC sont en mode de validation automatique (sauf si **SQLSetConnectAttr** et **SQLSetConnectOption** ne sont pas pris en charge, ce qui est peu probable). Le passage du mode de validation manuelle au mode de validation automatique valide toutes les transactions ouvertes sur la connexion.
