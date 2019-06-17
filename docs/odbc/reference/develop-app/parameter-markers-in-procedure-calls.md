---
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 00aa87461c1b4a82fbedc7bd7faf1da6ff327265
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63199144"
---
# <a name="parameter-markers-in-procedure-calls"></a>Marqueurs de paramètre dans les appels de procédure
Lors de l’appel des procédures qui acceptent des paramètres, applications interopérables doivent utiliser des marqueurs de paramètres au lieu de valeurs de paramètre literal. Certaines sources de données ne gèrent pas l’utilisation de valeurs de paramètre littéral dans les appels de procédure. Pour plus d’informations sur les paramètres, consultez [paramètres d’instruction](../../../odbc/reference/develop-app/statement-parameters.md). Pour plus d’informations sur l’appel de procédures, consultez [les appels de procédure](../../../odbc/reference/develop-app/procedure-calls.md), plus loin dans cette section.
