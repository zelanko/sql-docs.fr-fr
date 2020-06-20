---
title: Applications multithread | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- threads [SQL Server], multithreaded applications
- ODBC applications, multithreaded applications
- asynchronous operations [SQL Server Native Client]
- SQL Server Native Client ODBC driver, multithreaded applications
- multithreaded applications [SQL Server Native Client]
ms.assetid: d352c91a-6e08-4e50-9f3e-a37892d9c2cc
author: rothja
ms.author: jroth
ms.openlocfilehash: b680086f76e0c1a1e8c8cfc2f4ef82099957b3fd
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85055913"
---
# <a name="multithreaded-applications"></a>Applications multithread
  Le pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client est un pilote multithread. L'écriture d'une application multithread est une alternative à l'utilisation d'appels asynchrones pour traiter plusieurs appels ODBC. Un thread peut effectuer un appel ODBC synchrone et d'autres threads peuvent être traités pendant que le premier thread est bloqué dans l'attente d'une réponse à son appel. Ce modèle est plus efficace qu'effectuer des appels asynchrones, car il élimine les surcharges telles que le trafic réseau, et qu'effectuer des appels de fonctions ODBC répétés en testant SQL_STILL_EXECUTING.  
  
 Le mode asynchrone est encore une méthode de traitement efficace. Les améliorations des performances d'un modèle multithread ne sont pas suffisantes pour justifier la réécriture d'applications asynchrones. Si les utilisateurs convertissent des applications DB-Library qui utilisent le modèle asynchrone DB-Library, il est plus facile de les convertir au modèle asynchrone ODBC.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’une application de pilote ODBC SQL Server Native Client](creating-a-driver-application.md)  
  
  
