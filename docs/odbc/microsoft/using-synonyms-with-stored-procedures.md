---
title: Utilisation de synonymes, avec des procédures stockées | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], stored procedures
ms.assetid: 8620b039-a086-4534-8710-cc8b1787dc80
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cf56bcc674299fd576529929da10763c26a74ed4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47711457"
---
# <a name="using-synonyms-with-stored-procedures"></a>Utilisation de synonymes avec des procédures stockées
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Au lieu de cela, utilisez le pilote ODBC fourni par Oracle.  
  
 Le pilote ODBC de Microsoft pour les versions 2.0 et 2.5 d’Oracle ne gèrent pas de synonymes lorsque Oracle appelant des procédures stockées. Synonymes fonctionnent comme prévu lorsqu’il est utilisé avec d’autres objets de base de données Oracle tels que des tables.
