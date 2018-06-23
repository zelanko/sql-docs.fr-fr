---
title: SQLFreeHandle | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLFreeHandle function
ms.assetid: d374e5c8-ed35-43bf-8dd6-c37e38d9b5f1
caps.latest.revision: 28
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8ba108cf9efcd6e7e8fd91ccc026fe616c113d1d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36141277"
---
# <a name="sqlfreehandle"></a>SQLFreeHandle
  En mode de validation manuelle, l'appel de **SQLFreeHandle** sur un descripteur d'instruction avec une transaction ouverte provoque une restauration des modifications en attente de la base de données. L'appel de **SQLFreeHandle** sur un descripteur d'instruction ferme toujours tous les curseurs ouverts et ignore les résultats en attente, libérant toutes les ressources associées au descripteur d'instruction.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLFreeHandle, fonction](http://go.microsoft.com/fwlink/?LinkId=59345)   
 [Détails de l’implémentation d’API ODBC](odbc-api-implementation-details.md)  
  
  