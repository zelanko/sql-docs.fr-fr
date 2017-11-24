---
title: "Utilisation de synonymes, avec des procédures stockées | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- stored procedures [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], stored procedures
ms.assetid: 8620b039-a086-4534-8710-cc8b1787dc80
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b922f443b911c3885b706e6788cd220446fdc12f
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="using-synonyms-with-stored-procedures"></a>Utilisation de synonymes avec des procédures stockées
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Au lieu de cela, utilisez le pilote ODBC fourni par Oracle.  
  
 Le pilote Microsoft ODBC pour les versions 2.0 et 2.5 d’Oracle ne gèrent pas de synonymes lorsque Oracle appelant des procédures stockées. Synonymes fonctionnent comme prévu lorsqu’il est utilisé avec d’autres objets de base de données Oracle tels que des tables.
