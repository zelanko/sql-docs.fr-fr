---
description: Marqueurs de paramètre dans les appels de procédure
title: Marqueurs de paramètres dans les appels de procédure | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- parameter markers [ODBC]
- interoperability of SQL statements [ODBC], parameter markers
ms.assetid: cda56f2b-6eec-4cbc-8dbb-36d8fa9f9216
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bdd8409d3ddd2d0191da95a7cc7285ef24289aa7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476531"
---
# <a name="parameter-markers-in-procedure-calls"></a>Marqueurs de paramètre dans les appels de procédure
Lors de l’appel de procédures qui acceptent des paramètres, les applications interopérables doivent utiliser des marqueurs de paramètres plutôt que des valeurs de paramètre littéral. Certaines sources de données ne prennent pas en charge l’utilisation de valeurs de paramètre littérales dans les appels de procédure. Pour plus d’informations sur les paramètres, consultez [paramètres d’instruction](../../../odbc/reference/develop-app/statement-parameters.md). Pour plus d’informations sur l’appel de procédures, consultez [appels de procédure](../../../odbc/reference/develop-app/procedure-calls.md), plus loin dans cette section.
